# Data Structures and Algorithms

**Purpose:** Solve small tasks correctly and explain costs.
**Created / last updated:** 31 October 2026
**Status:** Original drills; not employer questions.

## 1. Complexity and selection

| Structure / operation | Typical time | Important qualification |
|---|---|---|
| Array indexing | O(1) | Middle insertion/removal usually O(n) |
| Array append | Amortised O(1) | Resizing occasionally costs O(n) |
| Hash lookup | Expected O(1) | Collisions can degrade performance |
| Balanced BST lookup | O(log n) | Unbalanced tree worst case O(n) |
| Heap min/max | Peek O(1), insert/pop O(log n) | Not a fully sorted list |
| Binary search | O(log n) | Requires ordered/searchable domain |
| Merge sort | O(n log n) | Common implementation uses O(n) extra space |
| Quicksort | Expected O(n log n) | Worst case O(n²) without safeguards |
| BFS / DFS | O(V+E) | With adjacency lists and visited tracking |

A stack is LIFO; a queue is FIFO. A linked-list insertion is O(1) **given the node/location**, not including search. A set handles membership; a map associates values. Do not sort merely to find one maximum.

## 2. Interview protocol

Clarify input/output → state assumptions → give a small example → choose structure → implement → test boundaries → explain time and extra space. Specify whether strings mean ASCII characters, Unicode code points or user-perceived graphemes. Ask whether mutation is allowed.

## 3. Fifteen original problems and solutions

Solutions use pseudocode or TypeScript-like notation. `Map`/`Set` costs below assume expected constant-time operations.

### 1 — Reverse characters
Input ASCII `"amber"`; output `"rebma"`. `return [...text].reverse().join("")`. O(n) time/space. The spread handles code points but not all grapheme clusters. Test empty and one-character strings.

### 2 — Normalised palindrome
Define ASCII letters/digits only, case-insensitive. Filter and lowercase, then compare left/right characters, moving inward. O(n) time, O(n) filtered storage. Test `"A man, a plan, a canal: Panama"`, empty string, and `"ab"`. If no filtered copy is allowed, skip non-alphanumerics with two pointers.

### 3 — Frequency count
For each value: `counts.set(x, (counts.get(x) ?? 0) + 1)`. O(n) time, O(k) space for k distinct values. Return counts, not only the most frequent value; define ties if asked to return one winner.

### 4 — First duplicate
Scan left to right. If set contains x, return x; otherwise add x. Return null when none exists. O(n) time/O(n) space. Clarify that "first" means the earliest repeated occurrence, not the smallest duplicated value.

### 5 — Two sum
```ts
function twoSum(values: number[], target: number): [number, number] | null {
  const seen = new Map<number, number>();
  for (let i = 0; i < values.length; i++) {
    const previous = seen.get(target - values[i]);
    if (previous !== undefined) return [previous, i];
    seen.set(values[i], i);
  }
  return null;
}
```
O(n) time/space. `[3,3]`, target 6 must return distinct indices. Avoid `if(previous)` because index 0 is falsy.

### 6 — Binary search
Set lo=0, hi=n−1. While lo≤hi, mid=lo+floor((hi−lo)/2). Compare target with a[mid], update hi=mid−1 or lo=mid+1. O(log n) time/O(1) extra space. Test missing target, empty input, first/last values. Ordinary search returns any match; lower-bound search is different.

### 7 — Balanced brackets
Push opening brackets. For a closer, pop and check its matching opener; fail on empty stack or mismatch. Finish with an empty stack. O(n) time/O(n) space. Test `([{}])`, `([)]`, `]`, and empty input. Define handling of other characters.

### 8 — Merge two sorted arrays
Maintain i and j. Append smaller current value, advance its pointer; append remaining suffix. O(n+m) time/O(n+m) output space. Test either array empty, duplicates, and negative numbers. Do not repeatedly shift JavaScript arrays.

### 9 — Maximum sum of k consecutive values
Require integer 1≤k≤n. Sum first k, then add incoming value and subtract outgoing value at each step. Track maximum initialised to first window, not zero. O(n) time/O(1) extra space. Test all-negative input and k=n.

### 10 — Longest substring with no repeated character
Keep last-seen index map and left boundary. At index right, set left=max(left,lastSeen[current]+1) if seen. Update best= max(best,right−left+1). O(n) time/O(k) space. `"abba"` should produce length 2; do not move left backwards.

### 11 — Reverse a linked list
Set previous=null and current=head. Save next, point current.next at previous, then advance previous/current. Return previous. O(n) time/O(1) space. Saving next before overwriting is essential. Test null, one node and two nodes.

### 12 — Breadth-first traversal
Queue the root and mark it visited. Consume with a head index, enqueue unvisited neighbours and mark **on enqueue**. O(V+E) time/O(V) space. Handles cycles; returns shortest edge-count distances only for unweighted/equal-weight graphs.

### 13 — Tree depth
`depth(null)=0; depth(node)=1+max(depth(left),depth(right))`. O(n) time/O(h) call stack. An unbalanced tree may overflow the stack; use explicit iterative traversal for adversarial depth. Define depth as node count here.

### 14 — Top k largest values
Maintain a min-heap of at most k. Insert until full; replace root only when incoming value is larger. O(n log k) time/O(k) space, plus optional O(k log k) sorting of output. For tiny n, sorting once is simpler. Validate k=0 and k>n policy.

### 15 — Stable unique list
Scan and add unseen values to a set and output array. O(n) time/O(n) space. `[2,1,2,3,1]` → `[2,1,3]`. `new Set(array)` preserves insertion order for primitive JS values; object equality is identity, not structural equality.

## 4. Common failure modes

- Stating O(1) hash lookup as a universal worst-case guarantee.
- Ignoring output storage while claiming "constant space".
- Sorting input without permission, or changing the caller's array unexpectedly.
- Using nested loops without noticing n×m work.
- Comparing arrays/objects by reference when the requirement expects value equality.
- Recursing without a base case or progress toward it.
- Optimising before clarifying duplicates, null input or tie-breaking.

## 5. Twenty-minute drill

5 minutes: two sum; 5 minutes: binary search; 5 minutes: sliding window; 5 minutes: explain tests and costs aloud. Repeat unfamiliar problems, not remembered outputs.

**Recommended references, not newly retrieved:** https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map ; https://visualgo.net/en ; https://leetcode.com/studyplan/ . Compiled 31 Oct 2026. Prefer free introductory problems over last-minute subscription purchases.
