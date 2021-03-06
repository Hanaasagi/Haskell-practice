#### Description
The maximum sum subarray problem consists in finding the maximum sum of a contiguous subsequence in an array or list of integers:

```
maxSequence [-2, 1, -3, 4, -1, 2, 1, -5, 4]
-- should be 6: [4, -1, 2, 1]
```

Easy case is when the list is made up of only positive numbers and the maximum sum is the sum of the whole array. If the list is made up of only negative numbers, return 0 instead.

Empty list is considered to have zero greatest sum. Note that the empty list or array is also a valid sublist/subarray.

#### Solution

```Haskell
module MaxSequence where

-- Return the greatest subarray sum within the array of integers passed in.
maxSequence :: [Int] -> Int
maxSequence xs = doMaxSequence xs 0 0

doMaxSequence :: [Int] -> Int -> Int -> Int
doMaxSequence [] _ maxx = maxx
doMaxSequence (x: xs) sub_max maxx =
  doMaxSequence xs (max 0 sub_max_cur) (max sub_max_cur maxx)
  where sub_max_cur = sub_max + x
```
