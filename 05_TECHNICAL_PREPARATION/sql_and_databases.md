# SQL and Databases

**Purpose:** Practise relational reasoning beyond `SELECT *`.
**Created / last updated:** 31 October 2026
**Dialect:** PostgreSQL. Educational schema, not any real candidate/client database.
**Execution status:** Examples reviewed by reasoning; not executed against a PostgreSQL server in this session.

## 1. Concepts you must explain

Primary key: row identity; foreign key: referenced-row integrity; UNIQUE: candidate-key constraint (null behaviour differs); CHECK: valid row values. A foreign key does not automatically create an index on the referencing column in PostgreSQL.

1NF: scalar values in the chosen relational representation, no repeating column groups. 2NF: no non-key attribute depending on only part of a candidate key. 3NF: for every nontrivial dependency X→A, X is a superkey or A is prime; junior shorthand is avoiding non-key facts depending transitively on the key. Do not store department name repeatedly in every employee row. Denormalisation is a measured optimisation, not the starting point.

INNER JOIN retains matches; LEFT JOIN retains every left row; RIGHT JOIN is the reversed form; FULL JOIN retains unmatched rows on both sides. MySQL lacks native FULL OUTER JOIN; emulate carefully with unions. A right-side filter in WHERE can eliminate the unmatched rows of a LEFT JOIN. `COUNT(*)` counts rows; `COUNT(e.id)` ignores null placeholders.

WHERE filters rows before grouping; HAVING filters groups. CTEs improve expression and may affect optimisation depending on engine/version; they are not automatically faster. A window function preserves rows while computing group/rank information. `ROW_NUMBER` breaks ties only deterministically when ordering contains a unique tiebreaker; `RANK` leaves gaps; `DENSE_RANK` does not.

## 2. Practice schema and seed data

Run in an empty practice schema only. No destructive setup is required.

```sql
CREATE TABLE departments (
  id integer PRIMARY KEY, name text NOT NULL UNIQUE
);
CREATE TABLE employees (
  id integer PRIMARY KEY, name text NOT NULL,
  department_id integer REFERENCES departments(id),
  salary numeric(12,2) NOT NULL CHECK (salary >= 0),
  hired_on date NOT NULL
);
CREATE TABLE projects (
  id integer PRIMARY KEY, name text NOT NULL,
  department_id integer NOT NULL REFERENCES departments(id),
  budget numeric(14,2) NOT NULL CHECK (budget >= 0)
);
CREATE TABLE attendance (
  employee_id integer REFERENCES employees(id), work_date date NOT NULL,
  status text NOT NULL CHECK (status IN ('present','absent','leave')),
  PRIMARY KEY (employee_id, work_date)
);
INSERT INTO departments VALUES (1,'Engineering'),(2,'Operations'),(3,'Finance');
INSERT INTO employees VALUES
 (1,'Ari',1,8000000,'2025-01-01'),(2,'Bela',1,10000000,'2025-02-01'),
 (3,'Cici',2,7000000,'2025-03-01'),(4,'Dodi',NULL,6000000,'2025-04-01');
INSERT INTO projects VALUES (1,'Portal',1,200000000),(2,'Audit',3,50000000);
INSERT INTO attendance VALUES
 (1,'2026-10-01','present'),(1,'2026-10-02','absent'),
 (2,'2026-10-01','present'),(3,'2026-10-01','leave');
```

## 3. Twenty queries: cover the solution and write first

```sql
-- 01 Foundation: salaries at least 8 million; deterministic order.
SELECT id, name, salary FROM employees
WHERE salary >= 8000000 ORDER BY salary DESC, id;

-- 02 Foundation: employee with department; exclude unassigned employees.
SELECT e.name, d.name AS department FROM employees e
JOIN departments d ON d.id = e.department_id;

-- 03 Foundation: retain unassigned employees.
SELECT e.name, d.name AS department FROM employees e
LEFT JOIN departments d ON d.id = e.department_id;

-- 04 Foundation: headcount including zero-employee departments.
SELECT d.id, d.name, COUNT(e.id) AS headcount FROM departments d
LEFT JOIN employees e ON e.department_id = d.id
GROUP BY d.id, d.name ORDER BY d.id;

-- 05 Foundation: departments with at least two employees.
SELECT department_id, COUNT(*) AS headcount FROM employees
WHERE department_id IS NOT NULL GROUP BY department_id HAVING COUNT(*) >= 2;

-- 06 Foundation: average salary by assigned department.
SELECT department_id, AVG(salary) AS average_salary FROM employees
WHERE department_id IS NOT NULL GROUP BY department_id;

-- 07 Intermediate: departments with no employees, using anti-join logic.
SELECT d.id, d.name FROM departments d
WHERE NOT EXISTS (SELECT 1 FROM employees e WHERE e.department_id = d.id);

-- 08 Intermediate: employees paid above their department average.
SELECT e.id, e.name FROM employees e WHERE e.salary > (
 SELECT AVG(p.salary) FROM employees p WHERE p.department_id = e.department_id
);

-- 09 Intermediate: present days per employee in October, including zeros.
SELECT e.id, e.name, COUNT(a.employee_id) AS present_days FROM employees e
LEFT JOIN attendance a ON a.employee_id = e.id AND a.status = 'present'
 AND a.work_date >= DATE '2026-10-01' AND a.work_date < DATE '2026-11-01'
GROUP BY e.id, e.name ORDER BY e.id;

-- 10 Intermediate: employees with no attendance record in October.
SELECT e.id, e.name FROM employees e WHERE NOT EXISTS (
 SELECT 1 FROM attendance a WHERE a.employee_id = e.id
 AND a.work_date >= DATE '2026-10-01' AND a.work_date < DATE '2026-11-01'
);

-- 11 Intermediate: project budgets by department, including zeros.
SELECT d.id, d.name, COALESCE(SUM(p.budget),0) AS budget FROM departments d
LEFT JOIN projects p ON p.department_id = d.id GROUP BY d.id, d.name;

-- 12 Intermediate: headcount and budget without join multiplication.
WITH hc AS (
 SELECT department_id, COUNT(*) AS n FROM employees GROUP BY department_id
), pb AS (
 SELECT department_id, SUM(budget) AS total FROM projects GROUP BY department_id
)
SELECT d.id, COALESCE(hc.n,0) AS headcount, COALESCE(pb.total,0) AS budget
FROM departments d LEFT JOIN hc ON hc.department_id=d.id
LEFT JOIN pb ON pb.department_id=d.id;

-- 13 Intermediate: salary ranking within each department.
SELECT id, name, department_id,
 RANK() OVER (PARTITION BY department_id ORDER BY salary DESC) AS salary_rank
FROM employees WHERE department_id IS NOT NULL;

-- 14 Advanced: at most two highest-paid employees per department.
WITH ranked AS (
 SELECT *, ROW_NUMBER() OVER (
  PARTITION BY department_id ORDER BY salary DESC, id
 ) AS rn FROM employees WHERE department_id IS NOT NULL
)
SELECT id, name, department_id, salary FROM ranked WHERE rn <= 2;

-- 15 Intermediate: second distinct highest salary; NULL if unavailable.
SELECT MAX(salary) AS second_highest FROM employees
WHERE salary < (SELECT MAX(salary) FROM employees);

-- 16 Advanced: cumulative present days for each employee by recorded date.
SELECT employee_id, work_date,
 SUM(CASE WHEN status='present' THEN 1 ELSE 0 END) OVER (
  PARTITION BY employee_id ORDER BY work_date
  ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
 ) AS cumulative_present FROM attendance;

-- 17 Intermediate: attendance percentage among recorded days (not scheduled days).
SELECT employee_id,
 100.0 * SUM(CASE WHEN status='present' THEN 1 ELSE 0 END) / COUNT(*) AS pct
FROM attendance GROUP BY employee_id;

-- 18 Advanced: latest record per employee, preserving those with no record.
WITH latest AS (
 SELECT *, ROW_NUMBER() OVER (
  PARTITION BY employee_id ORDER BY work_date DESC
 ) AS rn FROM attendance
)
SELECT e.id, e.name, a.work_date, a.status FROM employees e
LEFT JOIN latest a ON a.employee_id=e.id AND a.rn=1;

-- 19 Intermediate: keyset page after employee ID 2.
SELECT id, name FROM employees WHERE id > 2 ORDER BY id LIMIT 2;

-- 20 Advanced: repeatable upsert; practice mutation, not a production command.
INSERT INTO attendance(employee_id,work_date,status)
VALUES (1,DATE '2026-10-02','present')
ON CONFLICT (employee_id,work_date) DO UPDATE SET status=EXCLUDED.status;
```

**Expected checks before query 20:** Q4 counts = Engineering 2, Operations 1, Finance 0; Q7 Finance; Q8 Bela; Q9 present days Ari 1/Bela 1/Cici 0/Dodi 0; Q10 Dodi; Q15 8,000,000. Q17 Ari 50%, Bela 100%, Cici 0%. Missing dates are not automatically absences. A school/HR attendance rate needs a schedule/calendar denominator.

## 4. Indexes, integrity and performance

Consider `(employee_id, work_date)` for employee histories (already provided by the primary key), and `employees(department_id)` for department lookups. B-tree composite-index effectiveness depends on filters/order, especially leading columns. Small tables, low-selectivity predicates, functions on indexed columns and mismatched types may make a scan preferable. Use `EXPLAIN (ANALYZE, BUFFERS)` only on safe queries in an appropriate environment; ANALYZE executes the statement.

N+1 means one parent query plus one query per parent. Fetch related rows in a set or use a join, while watching row multiplication. OFFSET pagination becomes expensive and unstable under concurrent inserts; keyset pagination needs a stable unique ordering, often `(created_at,id)`.

ACID: atomicity, consistency with enforced invariants, isolation, durability. Read Committed, Repeatable Read and Serializable differ by engine; serializable transactions may need retries. A transaction alone does not prevent overselling if it performs an unsafe read-then-write. Use a conditional atomic update or lock the row, verify stock, then write ledger and order together. Acquire locks consistently; retry deadlocks safely with bounded attempts.

Soft deletion (`deleted_at`) complicates uniqueness, reporting and retention; it is not automatically legal erasure. Use migrations with version control, backfills and compatibility planning. Never assume every engine supports transactional DDL identically.

**MySQL notes:** use supported version 8+ for CTEs/windows; replace PostgreSQL `ON CONFLICT` with a suitable `ON DUPLICATE KEY UPDATE`; FULL JOIN requires emulation. Check text types, date arithmetic and null ordering. Do not mechanically paste one dialect into another.

**Recommended docs, not newly retrieved:** https://www.postgresql.org/docs/current/tutorial.html ; https://www.postgresql.org/docs/current/transaction-iso.html ; https://dev.mysql.com/doc/ . Compiled 31 Oct 2026.
