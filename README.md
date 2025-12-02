# Move All Zeros to the End (In-Place)

## Problem
Given an integer array, move all `0`s to the end while preserving the relative order of every non-zero element. The transformation must be done **in-place** without allocating extra space.

## Algorithm – Single-Pass Partitioning (Two Pointers)

We maintain a write pointer `k` that always points to the position where the next non-zero element should be placed.

1. Initialize `k = 0`.
2. Iterate `i` from `0` to `len-1`:
   - Whenever a non-zero element is found at index `i`, swap it with the element at index `k`.
   - Increment `k`.
3. After the loop finishes:
   - All elements from index `0` to `k-1` are non-zero and appear in their original relative order.
   - All elements from index `k` to the end are zeros (placed there by previous swaps).

### Why it works
- Every non-zero value is eventually swapped forward to the earliest available position (`k`).
- Zeros are naturally pushed backward with each swap.
- When `i == k` (i.e., we are already at the write position), the swap is with itself — harmless and keeps the algorithm simple.

## Complexity
- **Time**: O(n) – exactly one pass over the array.
- **Space**: O(1) – only one extra integer variable.

## Example

Input:  [0, 1, 0, 3, 12]


Step-by-step:

i=0 → zero, skip

i=1 → 1 ≠ 0 → swap with k=0 → [1, 0, 0, 3, 12], k=1

i=2 → zero, skip

i=3 → 3 ≠ 0 → swap with k=1 → [1, 3, 0, 0, 12], k=2

i=4 → 12 ≠ 0 → swap with k=2 → [1, 3, 12, 0, 0], k=3

Result: [1, 3, 12, 0, 0]
