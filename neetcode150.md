# NeetCode 150 - Java Solutions with Explanations

Each problem includes a short description, a Java solution, a `main` method with sample runs, and an explanation of the approach and complexity.

## Index

**[Arrays & Hashing](#arrays--hashing)**

1. [Contains Duplicate](#1-contains-duplicate)
2. [Valid Anagram](#2-valid-anagram)
3. [Two Sum](#3-two-sum)
4. [Group Anagrams](#4-group-anagrams)
5. [Top K Frequent Elements](#5-top-k-frequent-elements)
6. [Encode and Decode Strings](#6-encode-and-decode-strings)
7. [Product of Array Except Self](#7-product-of-array-except-self)
8. [Valid Sudoku](#8-valid-sudoku)
9. [Longest Consecutive Sequence](#9-longest-consecutive-sequence)

**[Two Pointers](#two-pointers)**

10. [Valid Palindrome](#10-valid-palindrome)
11. [Two Sum II - Input Array Is Sorted](#11-two-sum-ii---input-array-is-sorted)
12. [3Sum](#12-3sum)
13. [Container With Most Water](#13-container-with-most-water)
14. [Trapping Rain Water](#14-trapping-rain-water)

**[Sliding Window](#sliding-window)**

15. [Best Time to Buy and Sell Stock](#15-best-time-to-buy-and-sell-stock)
16. [Longest Substring Without Repeating Characters](#16-longest-substring-without-repeating-characters)
17. [Longest Repeating Character Replacement](#17-longest-repeating-character-replacement)
18. [Permutation in String](#18-permutation-in-string)
19. [Minimum Window Substring](#19-minimum-window-substring)
20. [Sliding Window Maximum](#20-sliding-window-maximum)

**[Stack](#stack)**

21. [Valid Parentheses](#21-valid-parentheses)
22. [Min Stack](#22-min-stack)
23. [Evaluate Reverse Polish Notation](#23-evaluate-reverse-polish-notation)
24. [Generate Parentheses](#24-generate-parentheses)
25. [Daily Temperatures](#25-daily-temperatures)
26. [Car Fleet](#26-car-fleet)
27. [Largest Rectangle in Histogram](#27-largest-rectangle-in-histogram)

**[Binary Search](#binary-search)**

28. [Binary Search](#28-binary-search)
29. [Search a 2D Matrix](#29-search-a-2d-matrix)
30. [Koko Eating Bananas](#30-koko-eating-bananas)
31. [Find Minimum in Rotated Sorted Array](#31-find-minimum-in-rotated-sorted-array)
32. [Search in Rotated Sorted Array](#32-search-in-rotated-sorted-array)
33. [Time Based Key-Value Store](#33-time-based-key-value-store)
34. [Median of Two Sorted Arrays](#34-median-of-two-sorted-arrays)

**[Linked List](#linked-list)**

35. [Reverse Linked List](#35-reverse-linked-list)
36. [Merge Two Sorted Lists](#36-merge-two-sorted-lists)
37. [Reorder List](#37-reorder-list)
38. [Remove Nth Node From End of List](#38-remove-nth-node-from-end-of-list)
39. [Copy List with Random Pointer](#39-copy-list-with-random-pointer)
40. [Add Two Numbers](#40-add-two-numbers)
41. [Linked List Cycle Detection](#41-linked-list-cycle-detection)
42. [Find the Duplicate Number](#42-find-the-duplicate-number)
43. [LRU Cache](#43-lru-cache)
44. [Merge k Sorted Lists](#44-merge-k-sorted-lists)
45. [Reverse Nodes in k-Group](#45-reverse-nodes-in-k-group)

**[Trees](#trees)**

46. [Invert Binary Tree](#46-invert-binary-tree)
47. [Maximum Depth of Binary Tree](#47-maximum-depth-of-binary-tree)
48. [Diameter of Binary Tree](#48-diameter-of-binary-tree)
49. [Balanced Binary Tree](#49-balanced-binary-tree)
50. [Same Tree](#50-same-tree)
51. [Subtree of Another Tree](#51-subtree-of-another-tree)
52. [Lowest Common Ancestor of a Binary Search Tree](#52-lowest-common-ancestor-of-a-binary-search-tree)
53. [Binary Tree Level Order Traversal](#53-binary-tree-level-order-traversal)
54. [Binary Tree Right Side View](#54-binary-tree-right-side-view)
55. [Count Good Nodes in Binary Tree](#55-count-good-nodes-in-binary-tree)
56. [Validate Binary Search Tree](#56-validate-binary-search-tree)
57. [Kth Smallest Element in a BST](#57-kth-smallest-element-in-a-bst)
58. [Construct Binary Tree from Preorder and Inorder Traversal](#58-construct-binary-tree-from-preorder-and-inorder-traversal)
59. [Binary Tree Maximum Path Sum](#59-binary-tree-maximum-path-sum)
60. [Serialize and Deserialize Binary Tree](#60-serialize-and-deserialize-binary-tree)

**[Tries](#tries)**

61. [Implement Trie (Prefix Tree)](#61-implement-trie-prefix-tree)
62. [Design Add and Search Words Data Structure](#62-design-add-and-search-words-data-structure)
63. [Word Search II](#63-word-search-ii)

**[Heap / Priority Queue](#heap--priority-queue)**

64. [Kth Largest Element in a Stream](#64-kth-largest-element-in-a-stream)
65. [Last Stone Weight](#65-last-stone-weight)
66. [K Closest Points to Origin](#66-k-closest-points-to-origin)
67. [Kth Largest Element in an Array](#67-kth-largest-element-in-an-array)
68. [Task Scheduler](#68-task-scheduler)
69. [Design Twitter](#69-design-twitter)
70. [Find Median from Data Stream](#70-find-median-from-data-stream)

**[Backtracking](#backtracking)**

71. [Subsets](#71-subsets)
72. [Combination Sum](#72-combination-sum)
73. [Permutations](#73-permutations)
74. [Subsets II](#74-subsets-ii)
75. [Combination Sum II](#75-combination-sum-ii)
76. [Word Search](#76-word-search)
77. [Palindrome Partitioning](#77-palindrome-partitioning)
78. [Letter Combinations of a Phone Number](#78-letter-combinations-of-a-phone-number)
79. [N-Queens](#79-n-queens)

**[Graphs](#graphs)**

80. [Number of Islands](#80-number-of-islands)
81. [Clone Graph](#81-clone-graph)
82. [Max Area of Island](#82-max-area-of-island)
83. [Pacific Atlantic Water Flow](#83-pacific-atlantic-water-flow)
84. [Surrounded Regions](#84-surrounded-regions)
85. [Rotting Oranges](#85-rotting-oranges)
86. [Walls and Gates](#86-walls-and-gates)
87. [Course Schedule](#87-course-schedule)
88. [Course Schedule II](#88-course-schedule-ii)
89. [Redundant Connection](#89-redundant-connection)
90. [Number of Connected Components in an Undirected Graph](#90-number-of-connected-components-in-an-undirected-graph)
91. [Graph Valid Tree](#91-graph-valid-tree)
92. [Word Ladder](#92-word-ladder)

**[Advanced Graphs](#advanced-graphs)**

93. [Reconstruct Itinerary](#93-reconstruct-itinerary)
94. [Min Cost to Connect All Points](#94-min-cost-to-connect-all-points)
95. [Network Delay Time](#95-network-delay-time)
96. [Swim in Rising Water](#96-swim-in-rising-water)
97. [Path With Minimum Effort](#97-path-with-minimum-effort)
98. [Cheapest Flights Within K Stops](#98-cheapest-flights-within-k-stops)

**[1-D Dynamic Programming](#1-d-dynamic-programming)**

99. [Climbing Stairs](#99-climbing-stairs)
100. [Min Cost Climbing Stairs](#100-min-cost-climbing-stairs)
101. [House Robber](#101-house-robber)
102. [House Robber II](#102-house-robber-ii)
103. [Longest Palindromic Substring](#103-longest-palindromic-substring)
104. [Palindromic Substrings](#104-palindromic-substrings)
105. [Decode Ways](#105-decode-ways)
106. [Coin Change](#106-coin-change)
107. [Maximum Product Subarray](#107-maximum-product-subarray)
108. [Word Break](#108-word-break)
109. [Longest Increasing Subsequence](#109-longest-increasing-subsequence)
110. [Partition Equal Subset Sum](#110-partition-equal-subset-sum)

**[2-D Dynamic Programming](#2-d-dynamic-programming)**

111. [Unique Paths](#111-unique-paths)
112. [Longest Common Subsequence](#112-longest-common-subsequence)
113. [Best Time to Buy and Sell Stock with Cooldown](#113-best-time-to-buy-and-sell-stock-with-cooldown)
114. [Coin Change II](#114-coin-change-ii)
115. [Target Sum](#115-target-sum)
116. [Interleaving String](#116-interleaving-string)
117. [Longest Increasing Path in a Matrix](#117-longest-increasing-path-in-a-matrix)
118. [Distinct Subsequences](#118-distinct-subsequences)
119. [Edit Distance](#119-edit-distance)
120. [Burst Balloons](#120-burst-balloons)
121. [Regular Expression Matching](#121-regular-expression-matching)

**[Greedy](#greedy)**

122. [Maximum Subarray](#122-maximum-subarray)
123. [Jump Game](#123-jump-game)
124. [Jump Game II](#124-jump-game-ii)
125. [Gas Station](#125-gas-station)
126. [Hand of Straights](#126-hand-of-straights)
127. [Merge Triplets to Form Target Triplet](#127-merge-triplets-to-form-target-triplet)
128. [Partition Labels](#128-partition-labels)
129. [Valid Parenthesis String](#129-valid-parenthesis-string)

**[Intervals](#intervals)**

130. [Insert Interval](#130-insert-interval)
131. [Merge Intervals](#131-merge-intervals)
132. [Non-overlapping Intervals](#132-non-overlapping-intervals)
133. [Meeting Rooms](#133-meeting-rooms)
134. [Meeting Rooms II](#134-meeting-rooms-ii)
135. [Minimum Interval to Include Each Query](#135-minimum-interval-to-include-each-query)

**[Math & Geometry](#math--geometry)**

136. [Rotate Image](#136-rotate-image)
137. [Spiral Matrix](#137-spiral-matrix)
138. [Set Matrix Zeroes](#138-set-matrix-zeroes)
139. [Happy Number](#139-happy-number)
140. [Plus One](#140-plus-one)
141. [Pow(x, n)](#141-powx-n)
142. [Multiply Strings](#142-multiply-strings)
143. [Detect Squares](#143-detect-squares)

**[Bit Manipulation](#bit-manipulation)**

144. [Single Number](#144-single-number)
145. [Number of 1 Bits](#145-number-of-1-bits)
146. [Counting Bits](#146-counting-bits)
147. [Reverse Bits](#147-reverse-bits)
148. [Missing Number](#148-missing-number)
149. [Sum of Two Integers](#149-sum-of-two-integers)
150. [Reverse Integer](#150-reverse-integer)

---

# Arrays & Hashing

## 1. Contains Duplicate

[Back to Index](#index)

**Problem:** Given an integer array `nums`, return `true` if any value appears at least twice, otherwise return `false`.

```java
import java.util.*;

class Solution {
    public boolean containsDuplicate(int[] nums) {
        Set<Integer> seen = new HashSet<>();
        for (int n : nums) {
            if (!seen.add(n)) return true; // add() returns false if already present
        }
        return false;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.containsDuplicate(new int[]{1, 2, 3, 1})); // true
        System.out.println(s.containsDuplicate(new int[]{1, 2, 3, 4})); // false
    }
}
```

**Explanation:** A `HashSet` tracks values seen so far. `add` returns `false` when the value already exists, which means a duplicate. Time is O(n) and space is O(n).

## 2. Valid Anagram

[Back to Index](#index)

**Problem:** Given strings `s` and `t`, return `true` if `t` is an anagram of `s`.

```java
class Solution {
    public boolean isAnagram(String s, String t) {
        if (s.length() != t.length()) return false;
        int[] count = new int[26];
        for (int i = 0; i < s.length(); i++) {
            count[s.charAt(i) - 'a']++;
            count[t.charAt(i) - 'a']--;
        }
        for (int c : count) {
            if (c != 0) return false;
        }
        return true;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.isAnagram("anagram", "nagaram")); // true
        System.out.println(s.isAnagram("rat", "car"));         // false
    }
}
```

**Explanation:** Increment counts for characters in `s` and decrement for characters in `t`. If the two strings are anagrams, every count ends at zero. Time is O(n) and space is O(1) since the alphabet is fixed at 26 letters.

## 3. Two Sum

[Back to Index](#index)

**Problem:** Given `nums` and a `target`, return indices of the two numbers that add up to `target`.

```java
import java.util.*;

class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> indexOf = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];
            if (indexOf.containsKey(complement)) {
                return new int[]{indexOf.get(complement), i};
            }
            indexOf.put(nums[i], i);
        }
        return new int[]{};
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(Arrays.toString(s.twoSum(new int[]{2, 7, 11, 15}, 9))); // [0, 1]
        System.out.println(Arrays.toString(s.twoSum(new int[]{3, 2, 4}, 6)));      // [1, 2]
    }
}
```

**Explanation:** For each number, compute the complement needed to reach the target and check whether it was already seen. The map stores value to index. Time is O(n) and space is O(n).

## 4. Group Anagrams

[Back to Index](#index)

**Problem:** Given an array of strings, group the anagrams together.

```java
import java.util.*;

class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        Map<String, List<String>> groups = new HashMap<>();
        for (String str : strs) {
            char[] chars = str.toCharArray();
            Arrays.sort(chars);
            String key = new String(chars);
            groups.computeIfAbsent(key, k -> new ArrayList<>()).add(str);
        }
        return new ArrayList<>(groups.values());
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.groupAnagrams(new String[]{"eat", "tea", "tan", "ate", "nat", "bat"}));
        // [[bat], [nat, tan], [ate, eat, tea]] (order of groups may vary)
    }
}
```

**Explanation:** Anagrams have identical sorted characters, so the sorted string works as a key. Time is O(n * k log k) where k is the maximum string length, and space is O(n * k).

## 5. Top K Frequent Elements

[Back to Index](#index)

**Problem:** Given `nums` and `k`, return the `k` most frequent elements.

```java
import java.util.*;

class Solution {
    public int[] topKFrequent(int[] nums, int k) {
        Map<Integer, Integer> freq = new HashMap<>();
        for (int n : nums) freq.merge(n, 1, Integer::sum);

        // Bucket i holds numbers that appear exactly i times
        List<Integer>[] buckets = new List[nums.length + 1];
        for (Map.Entry<Integer, Integer> e : freq.entrySet()) {
            int count = e.getValue();
            if (buckets[count] == null) buckets[count] = new ArrayList<>();
            buckets[count].add(e.getKey());
        }

        int[] result = new int[k];
        int idx = 0;
        for (int i = buckets.length - 1; i >= 0 && idx < k; i--) {
            if (buckets[i] == null) continue;
            for (int num : buckets[i]) {
                result[idx++] = num;
                if (idx == k) break;
            }
        }
        return result;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(Arrays.toString(s.topKFrequent(new int[]{1, 1, 1, 2, 2, 3}, 2))); // [1, 2]
        System.out.println(Arrays.toString(s.topKFrequent(new int[]{1}, 1)));                // [1]
    }
}
```

**Explanation:** Count frequencies, then use bucket sort, where the index is the frequency. Walking buckets from high to low frequency collects the top k. Time is O(n) and space is O(n).

## 6. Encode and Decode Strings

[Back to Index](#index)

**Problem:** Design an algorithm to encode a list of strings into one string and decode it back, so that it works for any characters.

```java
import java.util.*;

class Codec {
    // Format each string as "<length>#<string>"
    public String encode(List<String> strs) {
        StringBuilder sb = new StringBuilder();
        for (String s : strs) {
            sb.append(s.length()).append('#').append(s);
        }
        return sb.toString();
    }

    public List<String> decode(String str) {
        List<String> result = new ArrayList<>();
        int i = 0;
        while (i < str.length()) {
            int hash = str.indexOf('#', i);
            int len = Integer.parseInt(str.substring(i, hash));
            result.add(str.substring(hash + 1, hash + 1 + len));
            i = hash + 1 + len;
        }
        return result;
    }

    public static void main(String[] args) {
        Codec codec = new Codec();
        List<String> input = Arrays.asList("neet", "code", "love", "you");
        String encoded = codec.encode(input);
        System.out.println(encoded);               // 4#neet4#code4#love3#you
        System.out.println(codec.decode(encoded)); // [neet, code, love, you]
    }
}
```

**Explanation:** Prefixing each string with its length lets the decoder know exactly how many characters to read, so delimiters inside the strings do not cause problems. Time is O(total characters) and space is O(total characters).

## 7. Product of Array Except Self

[Back to Index](#index)

**Problem:** Return an array where each element equals the product of all other elements, without using division.

```java
import java.util.*;

class Solution {
    public int[] productExceptSelf(int[] nums) {
        int n = nums.length;
        int[] result = new int[n];

        // Pass 1: result[i] = product of everything to the left of i
        result[0] = 1;
        for (int i = 1; i < n; i++) {
            result[i] = result[i - 1] * nums[i - 1];
        }

        // Pass 2: multiply by product of everything to the right of i
        int right = 1;
        for (int i = n - 1; i >= 0; i--) {
            result[i] *= right;
            right *= nums[i];
        }
        return result;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(Arrays.toString(s.productExceptSelf(new int[]{1, 2, 3, 4})));  // [24, 12, 8, 6]
        System.out.println(Arrays.toString(s.productExceptSelf(new int[]{-1, 1, 0, -3, 3}))); // [0, 0, 9, 0, 0]
    }
}
```

**Explanation:** Prefix products fill the result in a left-to-right pass, and suffix products are multiplied in during a right-to-left pass with a running variable. Time is O(n) and extra space is O(1), not counting the output array.

## 8. Valid Sudoku

[Back to Index](#index)

**Problem:** Determine whether a 9x9 Sudoku board is valid. Only the filled cells need to be validated. Digits `1-9` must appear at most once per row, column, and 3x3 box.

```java
import java.util.*;

class Solution {
    public boolean isValidSudoku(char[][] board) {
        Set<String> seen = new HashSet<>();
        for (int r = 0; r < 9; r++) {
            for (int c = 0; c < 9; c++) {
                char val = board[r][c];
                if (val == '.') continue;
                int box = (r / 3) * 3 + (c / 3);
                // Each string encodes a unique (value, position-group) pair
                if (!seen.add(val + " in row " + r)) return false;
                if (!seen.add(val + " in col " + c)) return false;
                if (!seen.add(val + " in box " + box)) return false;
            }
        }
        return true;
    }

    public static void main(String[] args) {
        char[][] board = {
            {'5','3','.','.','7','.','.','.','.'},
            {'6','.','.','1','9','5','.','.','.'},
            {'.','9','8','.','.','.','.','6','.'},
            {'8','.','.','.','6','.','.','.','3'},
            {'4','.','.','8','.','3','.','.','1'},
            {'7','.','.','.','2','.','.','.','6'},
            {'.','6','.','.','.','.','2','8','.'},
            {'.','.','.','4','1','9','.','.','5'},
            {'.','.','.','.','8','.','.','7','9'}
        };
        Solution s = new Solution();
        System.out.println(s.isValidSudoku(board)); // true

        board[0][2] = '5'; // duplicate 5 in row 0 and box 0
        System.out.println(s.isValidSudoku(board)); // false
    }
}
```

**Explanation:** A single `HashSet` stores strings describing each digit's presence in a row, column, or box. If any string is already present, the board is invalid. The board is always 9x9, so time and space are both O(1) in practice.

## 9. Longest Consecutive Sequence

[Back to Index](#index)

**Problem:** Given an unsorted array, return the length of the longest consecutive sequence of integers. The solution must run in O(n) time.

```java
import java.util.*;

class Solution {
    public int longestConsecutive(int[] nums) {
        Set<Integer> set = new HashSet<>();
        for (int n : nums) set.add(n);

        int best = 0;
        for (int num : set) {
            // Only start counting from the beginning of a sequence
            if (!set.contains(num - 1)) {
                int length = 1;
                while (set.contains(num + length)) length++;
                best = Math.max(best, length);
            }
        }
        return best;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.longestConsecutive(new int[]{100, 4, 200, 1, 3, 2})); // 4
        System.out.println(s.longestConsecutive(new int[]{0, 3, 7, 2, 5, 8, 4, 6, 0, 1})); // 9
    }
}
```

**Explanation:** Putting numbers in a set allows O(1) lookups. Each sequence is only walked from its smallest element (the one where `num - 1` is absent), so every number is visited a constant number of times. Time is O(n) and space is O(n).

---

# Two Pointers

## 10. Valid Palindrome

[Back to Index](#index)

**Problem:** Return `true` if a string is a palindrome after converting to lowercase and ignoring non-alphanumeric characters.

```java
class Solution {
    public boolean isPalindrome(String s) {
        int left = 0, right = s.length() - 1;
        while (left < right) {
            while (left < right && !Character.isLetterOrDigit(s.charAt(left))) left++;
            while (left < right && !Character.isLetterOrDigit(s.charAt(right))) right--;
            if (Character.toLowerCase(s.charAt(left)) != Character.toLowerCase(s.charAt(right))) {
                return false;
            }
            left++;
            right--;
        }
        return true;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.isPalindrome("A man, a plan, a canal: Panama")); // true
        System.out.println(s.isPalindrome("race a car"));                     // false
    }
}
```

**Explanation:** Two pointers move inward from both ends, skipping characters that are not letters or digits. Mismatched characters mean the string is not a palindrome. Time is O(n) and space is O(1).

## 11. Two Sum II - Input Array Is Sorted

[Back to Index](#index)

**Problem:** Given a sorted array `numbers` and a `target`, return the 1-indexed positions of two numbers that add up to `target`.

```java
import java.util.*;

class Solution {
    public int[] twoSum(int[] numbers, int target) {
        int left = 0, right = numbers.length - 1;
        while (left < right) {
            int sum = numbers[left] + numbers[right];
            if (sum == target) return new int[]{left + 1, right + 1};
            if (sum < target) left++;
            else right--;
        }
        return new int[]{};
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(Arrays.toString(s.twoSum(new int[]{2, 7, 11, 15}, 9)));  // [1, 2]
        System.out.println(Arrays.toString(s.twoSum(new int[]{2, 3, 4}, 6)));       // [1, 3]
    }
}
```

**Explanation:** Because the array is sorted, moving the left pointer up increases the sum and moving the right pointer down decreases it. This converges on the target in one pass. Time is O(n) and space is O(1).

## 12. 3Sum

[Back to Index](#index)

**Problem:** Return all unique triplets `[a, b, c]` in `nums` such that `a + b + c == 0`.

```java
import java.util.*;

class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        Arrays.sort(nums);
        List<List<Integer>> result = new ArrayList<>();

        for (int i = 0; i < nums.length - 2; i++) {
            if (i > 0 && nums[i] == nums[i - 1]) continue; // skip duplicate first elements

            int left = i + 1, right = nums.length - 1;
            while (left < right) {
                int sum = nums[i] + nums[left] + nums[right];
                if (sum < 0) {
                    left++;
                } else if (sum > 0) {
                    right--;
                } else {
                    result.add(Arrays.asList(nums[i], nums[left], nums[right]));
                    left++;
                    right--;
                    while (left < right && nums[left] == nums[left - 1]) left++;   // skip duplicates
                    while (left < right && nums[right] == nums[right + 1]) right--;
                }
            }
        }
        return result;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.threeSum(new int[]{-1, 0, 1, 2, -1, -4})); // [[-1, -1, 2], [-1, 0, 1]]
        System.out.println(s.threeSum(new int[]{0, 1, 1}));             // []
        System.out.println(s.threeSum(new int[]{0, 0, 0}));             // [[0, 0, 0]]
    }
}
```

**Explanation:** Sorting lets us fix one number and use two pointers on the rest, like Two Sum II. Duplicate values are skipped at every level so each unique triplet appears once. Time is O(n^2) and space is O(1) beyond the output (ignoring sort overhead).

## 13. Container With Most Water

[Back to Index](#index)

**Problem:** Given heights of vertical lines, find two lines that together with the x-axis form a container holding the most water.

```java
class Solution {
    public int maxArea(int[] height) {
        int left = 0, right = height.length - 1;
        int best = 0;
        while (left < right) {
            int width = right - left;
            int h = Math.min(height[left], height[right]);
            best = Math.max(best, width * h);
            // Move the shorter line, since it is the limiting factor
            if (height[left] < height[right]) left++;
            else right--;
        }
        return best;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.maxArea(new int[]{1, 8, 6, 2, 5, 4, 8, 3, 7})); // 49
        System.out.println(s.maxArea(new int[]{1, 1}));                      // 1
    }
}
```

**Explanation:** Start with the widest container. Moving the taller line inward can only shrink the width while the height stays capped by the shorter line, so we always move the shorter line. Time is O(n) and space is O(1).

## 14. Trapping Rain Water

[Back to Index](#index)

**Problem:** Given an elevation map, compute how much rain water can be trapped after raining.

```java
class Solution {
    public int trap(int[] height) {
        int left = 0, right = height.length - 1;
        int leftMax = 0, rightMax = 0;
        int water = 0;

        while (left < right) {
            if (height[left] < height[right]) {
                // The left side is the limit, so its water level is known
                leftMax = Math.max(leftMax, height[left]);
                water += leftMax - height[left];
                left++;
            } else {
                rightMax = Math.max(rightMax, height[right]);
                water += rightMax - height[right];
                right--;
            }
        }
        return water;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.trap(new int[]{0, 1, 0, 2, 1, 0, 1, 3, 2, 1, 2, 1})); // 6
        System.out.println(s.trap(new int[]{4, 2, 0, 3, 2, 5}));                   // 9
    }
}
```

**Explanation:** Water at each index is limited by the smaller of the tallest bars on its left and right. Processing from whichever side is currently lower means that side's max is already the binding constraint, so one pass with two pointers is enough. Time is O(n) and space is O(1).

---



# Sliding Window

## 15. Best Time to Buy and Sell Stock

[Back to Index](#index)

**Problem:** Given an array `prices` where `prices[i]` is the price of a given stock on the `i`th day, find the maximum profit you can achieve from a single buy and sell transaction. If no profit can be achieved, return `0`.

```java
class Solution {
    public int maxProfit(int[] prices) {
        int minPrice = Integer.MAX_VALUE;
        int maxProfit = 0;
        for (int price : prices) {
            if (price < minPrice) {
                minPrice = price;
            } else if (price - minPrice > maxProfit) {
                maxProfit = price - minPrice;
            }
        }
        return maxProfit;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[] prices = {7, 1, 5, 3, 6, 4};
        System.out.println(s.maxProfit(prices)); // Expected: 5
    }
}
```

**Explanation:** Track the minimum purchase price seen so far and calculate profit at each day, updating the maximum profit. Time is O(n) and space is O(1).

## 16. Longest Substring Without Repeating Characters

[Back to Index](#index)

**Problem:** Given a string `s`, find the length of the longest substring without duplicate characters.

```java
import java.util.HashMap;
import java.util.Map;

class Solution {
    public int lengthOfLongestSubstring(String s) {
        Map<Character, Integer> lastSeen = new HashMap<>();
        int maxLen = 0, left = 0;
        for (int right = 0; right < s.length(); right++) {
            char c = s.charAt(right);
            if (lastSeen.containsKey(c)) {
                left = Math.max(left, lastSeen.get(c) + 1);
            }
            lastSeen.put(c, right);
            maxLen = Math.max(maxLen, right - left + 1);
        }
        return maxLen;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.lengthOfLongestSubstring("abcabcbb")); // Expected: 3
    }
}
```

**Explanation:** Use a sliding window with a hash map storing the most recent index of each character, advancing the left boundary when duplicates are encountered. Time is O(n) and space is O(min(m, n)) where m is the character set size.

## 17. Longest Repeating Character Replacement

[Back to Index](#index)

**Problem:** Given a string `s` and an integer `k`, return the length of the longest substring containing the same letter you can achieve after choosing at most `k` characters and replacing them with any other uppercase English character.

```java
class Solution {
    public int characterReplacement(String s, int k) {
        int[] count = new int[26];
        int maxCount = 0, left = 0, maxLen = 0;
        for (int right = 0; right < s.length(); right++) {
            maxCount = Math.max(maxCount, ++count[s.charAt(right) - 'A']);
            while ((right - left + 1) - maxCount > k) {
                count[s.charAt(left) - 'A']--;
                left++;
            }
            maxLen = Math.max(maxLen, right - left + 1);
        }
        return maxLen;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.characterReplacement("AABABBA", 1)); // Expected: 4
    }
}
```

**Explanation:** Maintain a sliding window and track the count of the most frequent character; if the window size minus the max frequency exceeds `k`, shrink the window from the left. Time is O(n) and space is O(1).

## 18. Permutation in String

[Back to Index](#index)

**Problem:** Given two strings `s1` and `s2`, return `true` if `s2` contains a permutation of `s1`, or `false` otherwise.

```java
import java.util.Arrays;

class Solution {
    public boolean checkInclusion(String s1, String s2) {
        int n1 = s1.length(), n2 = s2.length();
        if (n1 > n2) return false;
        int[] count1 = new int[26];
        int[] count2 = new int[26];
        for (int i = 0; i < n1; i++) {
            count1[s1.charAt(i) - 'a']++;
            count2[s2.charAt(i) - 'a']++;
        }
        if (Arrays.equals(count1, count2)) return true;
        for (int i = n1; i < n2; i++) {
            count2[s2.charAt(i) - 'a']++;
            count2[s2.charAt(i - n1) - 'a']--;
            if (Arrays.equals(count1, count2)) return true;
        }
        return false;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.checkInclusion("ab", "eidbaooo")); // Expected: true
    }
}
```

**Explanation:** Slide a fixed-size window of length `s1.length()` across `s2` and compare character frequency arrays. Time is O(n2) and space is O(1).

## 19. Minimum Window Substring

[Back to Index](#index)

**Problem:** Given two strings `s` and `t`, return the minimum window substring of `s` such that every character in `t` (including duplicates) is included in the window. If no such substring exists, return `""`.

```java
import java.util.HashMap;
import java.util.Map;

class Solution {
    public String minWindow(String s, String t) {
        if (s.isEmpty() || t.isEmpty()) return "";
        Map<Character, Integer> target = new HashMap<>();
        for (char c : t.toCharArray()) {
            target.put(c, target.getOrDefault(c, 0) + 1);
        }
        Map<Character, Integer> window = new HashMap<>();
        int have = 0, need = target.size();
        int minLen = Integer.MAX_VALUE, start = 0;
        int left = 0;

        for (int right = 0; right < s.length(); right++) {
            char c = s.charAt(right);
            window.put(c, window.getOrDefault(c, 0) + 1);
            if (target.containsKey(c) && window.get(c).intValue() == target.get(c).intValue()) {
                have++;
            }
            while (have == need) {
                if (right - left + 1 < minLen) {
                    minLen = right - left + 1;
                    start = left;
                }
                char lc = s.charAt(left);
                window.put(lc, window.get(lc) - 1);
                if (target.containsKey(lc) && window.get(lc) < target.get(lc)) {
                    have--;
                }
                left++;
            }
        }
        return minLen == Integer.MAX_VALUE ? "" : s.substring(start, start + minLen);
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.minWindow("ADOBECODEBANC", "ABC")); // Expected: "BANC"
    }
}
```

**Explanation:** Expand a sliding window until all characters of `t` are covered, then contract from the left to find the minimal valid window. Time is O(m + n) and space is O(m + n).

## 20. Sliding Window Maximum

[Back to Index](#index)

**Problem:** Given an array of integers `nums` and a sliding window of size `k` moving from left to right, return the max sliding window.

```java
import java.util.ArrayDeque;
import java.util.Arrays;
import java.util.Deque;

class Solution {
    public int[] maxSlidingWindow(int[] nums, int k) {
        if (nums == null || k <= 0) return new int[0];
        int n = nums.length;
        int[] result = new int[n - k + 1];
        Deque<Integer> deque = new ArrayDeque<>();

        for (int i = 0; i < n; i++) {
            if (!deque.isEmpty() && deque.peekFirst() < i - k + 1) {
                deque.pollFirst();
            }
            while (!deque.isEmpty() && nums[deque.peekLast()] < nums[i]) {
                deque.pollLast();
            }
            deque.offerLast(i);
            if (i >= k - 1) {
                result[i - k + 1] = nums[deque.peekFirst()];
            }
        }
        return result;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[] nums = {1, 3, -1, -3, 5, 3, 6, 7};
        System.out.println(Arrays.toString(s.maxSlidingWindow(nums, 3))); // Expected: [3, 3, 5, 5, 6, 7]
    }
}
```

**Explanation:** Use a monotonic decreasing deque to store indices of potential maxima within the current window of size `k`. Time is O(n) and space is O(k).


---

# Stack

## 21. Valid Parentheses

[Back to Index](#index)

**Problem:** Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

```java
import java.util.ArrayDeque;
import java.util.Deque;

class Solution {
    public boolean isValid(String s) {
        Deque<Character> stack = new ArrayDeque<>();
        for (char c : s.toCharArray()) {
            if (c == '(') stack.push(')');
            else if (c == '{') stack.push('}');
            else if (c == '[') stack.push(']');
            else if (stack.isEmpty() || stack.pop() != c) return false;
        }
        return stack.isEmpty();
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.isValid("()[]{}")); // Expected: true
        System.out.println(s.isValid("(]"));     // Expected: false
    }
}
```

**Explanation:** Push expected closing brackets onto a stack when opening brackets appear, and verify that actual closing brackets match the stack top. Time is O(n) and space is O(n).

## 22. Min Stack

[Back to Index](#index)

**Problem:** Design a stack that supports `push`, `pop`, `top`, and retrieving the minimum element in constant time.

```java
import java.util.ArrayDeque;
import java.util.Deque;

class MinStack {
    private Deque<Integer> stack = new ArrayDeque<>();
    private Deque<Integer> minStack = new ArrayDeque<>();

    public MinStack() {}

    public void push(int val) {
        stack.push(val);
        if (minStack.isEmpty() || val <= minStack.peek()) {
            minStack.push(val);
        }
    }

    public void pop() {
        if (stack.peek().equals(minStack.peek())) {
            minStack.pop();
        }
        stack.pop();
    }

    public int top() {
        return stack.peek();
    }

    public int getMin() {
        return minStack.peek();
    }
}

class Solution {
    public static void main(String[] args) {
        MinStack minStack = new MinStack();
        minStack.push(-2);
        minStack.push(0);
        minStack.push(-3);
        System.out.println(minStack.getMin()); // Expected: -3
        minStack.pop();
        System.out.println(minStack.top());    // Expected: 0
        System.out.println(minStack.getMin()); // Expected: -2
    }
}
```

**Explanation:** Use an auxiliary stack to keep track of the minimum value seen so far for each element in the primary stack. Time is O(1) for all operations and space is O(n).

## 23. Evaluate Reverse Polish Notation

[Back to Index](#index)

**Problem:** Evaluate the value of an arithmetic expression in Reverse Polish Notation given an array of string tokens representing valid operators (`+`, `-`, `*`, `/`) and integers.

```java
import java.util.ArrayDeque;
import java.util.Deque;

class Solution {
    public int evalRPN(String[] tokens) {
        Deque<Integer> stack = new ArrayDeque<>();
        for (String token : tokens) {
            switch (token) {
                case "+":
                    stack.push(stack.pop() + stack.pop());
                    break;
                case "-": {
                    int b = stack.pop();
                    int a = stack.pop();
                    stack.push(a - b);
                    break;
                }
                case "*":
                    stack.push(stack.pop() * stack.pop());
                    break;
                case "/": {
                    int b = stack.pop();
                    int a = stack.pop();
                    stack.push(a / b);
                    break;
                }
                default:
                    stack.push(Integer.parseInt(token));
                    break;
            }
        }
        return stack.pop();
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        String[] tokens = {"2", "1", "+", "3", "*"};
        System.out.println(s.evalRPN(tokens)); // Expected: 9
    }
}
```

**Explanation:** Use a stack to hold operands, popping the top two operands to apply each operator and pushing the result back. Time is O(n) and space is O(n).

## 24. Generate Parentheses

[Back to Index](#index)

**Problem:** Given `n` pairs of parentheses, write a function to generate all combinations of well-formed parentheses.

```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public List<String> generateParenthesis(int n) {
        List<String> result = new ArrayList<>();
        backtrack(result, new StringBuilder(), 0, 0, n);
        return result;
    }

    private void backtrack(List<String> result, StringBuilder current, int open, int close, int max) {
        if (current.length() == max * 2) {
            result.add(current.toString());
            return;
        }
        if (open < max) {
            current.append('(');
            backtrack(result, current, open + 1, close, max);
            current.deleteCharAt(current.length() - 1);
        }
        if (close < open) {
            current.append(')');
            backtrack(result, current, open, close + 1, max);
            current.deleteCharAt(current.length() - 1);
        }
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.generateParenthesis(3)); // Expected: [((())), (()()), (())(), ()(()), ()()()]
    }
}
```

**Explanation:** Use backtracking to recursively place opening parentheses while `open < n` and closing parentheses while `close < open`. Time is O(4^n / sqrt(n)) and space is O(n).

## 25. Daily Temperatures

[Back to Index](#index)

**Problem:** Given an array of integers `temperatures` representing daily temperatures, return an array `answer` such that `answer[i]` is the number of days you have to wait after the `i`th day to get a warmer temperature. If there is no future day for which this is possible, keep `answer[i] == 0`.

```java
import java.util.ArrayDeque;
import java.util.Arrays;
import java.util.Deque;

class Solution {
    public int[] dailyTemperatures(int[] temperatures) {
        int n = temperatures.length;
        int[] answer = new int[n];
        Deque<Integer> stack = new ArrayDeque<>();

        for (int i = 0; i < n; i++) {
            while (!stack.isEmpty() && temperatures[i] > temperatures[stack.peek()]) {
                int prevIndex = stack.pop();
                answer[prevIndex] = i - prevIndex;
            }
            stack.push(i);
        }
        return answer;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[] temps = {73, 74, 75, 71, 69, 72, 76, 73};
        System.out.println(Arrays.toString(s.dailyTemperatures(temps))); // Expected: [1, 1, 4, 2, 1, 1, 0, 0]
    }
}
```

**Explanation:** Maintain a monotonic decreasing stack of day indices, popping previous days when a warmer day is encountered to calculate waiting distances. Time is O(n) and space is O(n).

## 26. Car Fleet

[Back to Index](#index)

**Problem:** There are `n` cars at given `position` and `speed` traveling along a one-lane road toward a destination `target`. A car can never pass another car ahead of it. Return the number of car fleets that arrive at the destination.

```java
import java.util.Arrays;

class Solution {
    public int carFleet(int target, int[] position, int[] speed) {
        int n = position.length;
        double[][] cars = new double[n][2];
        for (int i = 0; i < n; i++) {
            cars[i][0] = position[i];
            cars[i][1] = (double) (target - position[i]) / speed[i];
        }
        Arrays.sort(cars, (a, b) -> Double.compare(b[0], a[0]));

        int fleets = 0;
        double maxTime = 0.0;
        for (double[] car : cars) {
            if (car[1] > maxTime) {
                fleets++;
                maxTime = car[1];
            }
        }
        return fleets;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int target = 12;
        int[] position = {10, 8, 0, 5, 3};
        int[] speed = {2, 4, 1, 1, 3};
        System.out.println(s.carFleet(target, position, speed)); // Expected: 3
    }
}
```

**Explanation:** Sort cars by initial position descending and calculate arrival time to target; a car behind that arrives faster joins the fleet ahead. Time is O(n log n) and space is O(n).

## 27. Largest Rectangle in Histogram

[Back to Index](#index)

**Problem:** Given an array of integers `heights` representing the histogram's bar height where the width of each bar is `1`, return the area of the largest rectangle in the histogram.

```java
import java.util.ArrayDeque;
import java.util.Deque;

class Solution {
    public int largestRectangleArea(int[] heights) {
        int n = heights.length;
        Deque<Integer> stack = new ArrayDeque<>();
        int maxArea = 0;

        for (int i = 0; i <= n; i++) {
            int currentHeight = (i == n) ? 0 : heights[i];
            while (!stack.isEmpty() && currentHeight < heights[stack.peek()]) {
                int height = heights[stack.pop()];
                int width = stack.isEmpty() ? i : i - stack.peek() - 1;
                maxArea = Math.max(maxArea, height * width);
            }
            stack.push(i);
        }
        return maxArea;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[] heights = {2, 1, 5, 6, 2, 3};
        System.out.println(s.largestRectangleArea(heights)); // Expected: 10
    }
}
```

**Explanation:** Use a monotonic increasing stack to track bar indices; when a shorter bar is encountered, calculate rectangle areas for bars in the stack using the popped bar's height. Time is O(n) and space is O(n).

---

# Binary Search

## 28. Binary Search

[Back to Index](#index)

**Problem:** Given an array of integers `nums` which is sorted in ascending order, and an integer `target`, write a function to search `target` in `nums`. If `target` exists, return its index; otherwise, return `-1`.

```java
class Solution {
    public int search(int[] nums, int target) {
        int left = 0, right = nums.length - 1;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] == target) {
                return mid;
            } else if (nums[mid] < target) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
        return -1;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[] nums = {-1, 0, 3, 5, 9, 12};
        System.out.println(s.search(nums, 9)); // Expected: 4
        System.out.println(s.search(nums, 2)); // Expected: -1
    }
}
```

**Explanation:** Maintain `left` and `right` pointers and halve the search space at each step by comparing `target` with the element at `mid`. Time is O(log n) and space is O(1).

## 29. Search a 2D Matrix

[Back to Index](#index)

**Problem:** You are given an `m x n` integer matrix `matrix` with each row sorted in non-decreasing order and the first integer of each row greater than the last integer of the previous row. Given an integer `target`, return `true` if `target` is in `matrix` or `false` otherwise in $O(\log(m \cdot n))$ time.

```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int m = matrix.length;
        int n = matrix[0].length;
        int left = 0, right = m * n - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;
            int r = mid / n;
            int c = mid % n;
            if (matrix[r][c] == target) {
                return true;
            } else if (matrix[r][c] < target) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
        return false;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[][] matrix = {
            {1, 3, 5, 7},
            {10, 11, 16, 20},
            {23, 30, 34, 60}
        };
        System.out.println(s.searchMatrix(matrix, 3));  // Expected: true
        System.out.println(s.searchMatrix(matrix, 13)); // Expected: false
    }
}
```

**Explanation:** Treat the 2D matrix as a flat 1D sorted array of length $m \times n$. Use standard binary search with coordinate mapping $r = \text{mid} / n$ and $c = \text{mid} \pmod n$. Time is O(log(m * n)) and space is O(1).

## 30. Koko Eating Bananas

[Back to Index](#index)

**Problem:** Koko loves to eat bananas. There are `n` piles of bananas, the $i$-th pile has `piles[i]` bananas. Guards will return in `h` hours. Return the minimum integer `k` such that she can eat all the bananas within `h` hours.

```java
class Solution {
    public int minEatingSpeed(int[] piles, int h) {
        int left = 1;
        int right = 0;
        for (int pile : piles) {
            right = Math.max(right, pile);
        }

        int result = right;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            long hoursNeeded = 0;
            for (int pile : piles) {
                hoursNeeded += (pile + mid - 1L) / mid;
            }

            if (hoursNeeded <= h) {
                result = mid;
                right = mid - 1;
            } else {
                left = mid + 1;
            }
        }
        return result;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[] piles1 = {3, 6, 7, 11};
        System.out.println(s.minEatingSpeed(piles1, 8)); // Expected: 4
        int[] piles2 = {30, 11, 23, 4, 20};
        System.out.println(s.minEatingSpeed(piles2, 5)); // Expected: 30
    }
}
```

**Explanation:** Binary search the answer in the range $[1, \max(\text{piles})]$. For a given speed `mid`, calculate total hours using ceiling division `(pile + mid - 1) / mid`. If valid, try a smaller speed. Time is O(n * log(max(piles))) and space is O(1).

## 31. Find Minimum in Rotated Sorted Array

[Back to Index](#index)

**Problem:** Suppose an array of length `n` sorted in ascending order is rotated between `1` and `n` times. Given the sorted rotated array `nums` of unique elements, return the minimum element of this array.

```java
class Solution {
    public int findMin(int[] nums) {
        int left = 0, right = nums.length - 1;

        while (left < right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] > nums[right]) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }
        return nums[left];
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[] nums1 = {3, 4, 5, 1, 2};
        System.out.println(s.findMin(nums1)); // Expected: 1
        int[] nums2 = {4, 5, 6, 7, 0, 1, 2};
        System.out.println(s.findMin(nums2)); // Expected: 0
        int[] nums3 = {11, 13, 15, 17};
        System.out.println(s.findMin(nums3)); // Expected: 11
    }
}
```

**Explanation:** Compare `nums[mid]` with `nums[right]`. If `nums[mid] > nums[right]`, the minimum lies in the right portion (`left = mid + 1`). Otherwise, the minimum lies at or to the left of `mid` (`right = mid`). Time is O(log n) and space is O(1).

## 32. Search in Rotated Sorted Array

[Back to Index](#index)

**Problem:** Given the array `nums` after the possible rotation and an integer `target`, return the index of `target` if it is in `nums`, or `-1` if it is not in `nums`. You must write an algorithm with $O(\log n)$ runtime complexity.

```java
class Solution {
    public int search(int[] nums, int target) {
        int left = 0, right = nums.length - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] == target) {
                return mid;
            }

            // Check if the left half is sorted
            if (nums[left] <= nums[mid]) {
                if (nums[left] <= target && target < nums[mid]) {
                    right = mid - 1;
                } else {
                    left = mid + 1;
                }
            } else { // Right half is sorted
                if (nums[mid] < target && target <= nums[right]) {
                    left = mid + 1;
                } else {
                    right = mid - 1;
                }
            }
        }
        return -1;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[] nums = {4, 5, 6, 7, 0, 1, 2};
        System.out.println(s.search(nums, 0)); // Expected: 4
        System.out.println(s.search(nums, 3)); // Expected: -1
    }
}
```

**Explanation:** In any rotated sorted array, dividing at `mid` always leaves at least one sorted half. Determine which half is sorted and check if `target` falls in its range to prune the search space. Time is O(log n) and space is O(1).

## 33. Time Based Key-Value Store

[Back to Index](#index)

**Problem:** Design a time-based key-value data structure that can store multiple values for the same key at different timestamps and retrieve the key's value at a certain timestamp.

```java
import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

class Solution {
    static class TimeMap {
        static class Node {
            String value;
            int timestamp;
            Node(String value, int timestamp) {
                this.value = value;
                this.timestamp = timestamp;
            }
        }

        private Map<String, List<Node>> map;

        public TimeMap() {
            map = new HashMap<>();
        }

        public void set(String key, String value, int timestamp) {
            map.computeIfAbsent(key, k -> new ArrayList<>()).add(new Node(value, timestamp));
        }

        public String get(String key, int timestamp) {
            if (!map.containsKey(key)) {
                return "";
            }
            List<Node> list = map.get(key);
            int left = 0, right = list.size() - 1;
            String result = "";

            while (left <= right) {
                int mid = left + (right - left) / 2;
                if (list.get(mid).timestamp <= timestamp) {
                    result = list.get(mid).value;
                    left = mid + 1;
                } else {
                    right = mid - 1;
                }
            }
            return result;
        }
    }

    public static void main(String[] args) {
        TimeMap timeMap = new TimeMap();
        timeMap.set("foo", "bar", 1);
        System.out.println(timeMap.get("foo", 1)); // Expected: bar
        System.out.println(timeMap.get("foo", 3)); // Expected: bar
        timeMap.set("foo", "bar2", 4);
        System.out.println(timeMap.get("foo", 4)); // Expected: bar2
        System.out.println(timeMap.get("foo", 5)); // Expected: bar2
        System.out.println(timeMap.get("foo", 0)); // Expected: ""
    }
}
```

**Explanation:** Store a list of timestamped entries for each key. Since timestamps are monotonically increasing, use binary search to locate the largest timestamp less than or equal to the query timestamp. Time is O(1) for `set`, O(log n) for `get`, and space is O(m) total storage.

## 34. Median of Two Sorted Arrays

[Back to Index](#index)

**Problem:** Given two sorted arrays `nums1` and `nums2` of size `m` and `n` respectively, return the median of the two sorted arrays in $O(\log(m+n))$ runtime complexity.

```java
class Solution {
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        if (nums1.length > nums2.length) {
            return findMedianSortedArrays(nums2, nums1);
        }

        int m = nums1.length, n = nums2.length;
        int left = 0, right = m;
        int halfLen = (m + n + 1) / 2;

        while (left <= right) {
            int i = left + (right - left) / 2;
            int j = halfLen - i;

            int nums1LeftMax = (i == 0) ? Integer.MIN_VALUE : nums1[i - 1];
            int nums1RightMin = (i == m) ? Integer.MAX_VALUE : nums1[i];
            int nums2LeftMax = (j == 0) ? Integer.MIN_VALUE : nums2[j - 1];
            int nums2RightMin = (j == n) ? Integer.MAX_VALUE : nums2[j];

            if (nums1LeftMax <= nums2RightMin && nums2LeftMax <= nums1RightMin) {
                if ((m + n) % 2 == 1) {
                    return Math.max(nums1LeftMax, nums2LeftMax);
                } else {
                    return (Math.max(nums1LeftMax, nums2LeftMax) + Math.min(nums1RightMin, nums2RightMin)) / 2.0;
                }
            } else if (nums1LeftMax > nums2RightMin) {
                right = i - 1;
            } else {
                left = i + 1;
            }
        }
        return 0.0;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[] nums1 = {1, 3};
        int[] nums2 = {2};
        System.out.println(s.findMedianSortedArrays(nums1, nums2)); // Expected: 2.0

        int[] nums3 = {1, 2};
        int[] nums4 = {3, 4};
        System.out.println(s.findMedianSortedArrays(nums3, nums4)); // Expected: 2.5
    }
}
```

**Explanation:** Binary search the partition of the smaller array so that the combined left half contains half of all elements and every element on the left is $\le$ every element on the right. Time is O(log(min(m, n))) and space is O(1).


---

# Linked List

## 35. Reverse Linked List

[Back to Index](#index)

**Problem:** Given the `head` of a singly linked list, reverse the list, and return the reversed list.

```java
class Solution {
    static class ListNode {
        int val;
        ListNode next;
        ListNode(int val) { this.val = val; }
        ListNode(int val, ListNode next) { this.val = val; this.next = next; }
    }

    public ListNode reverseList(ListNode head) {
        ListNode prev = null;
        ListNode curr = head;
        while (curr != null) {
            ListNode nextTemp = curr.next;
            curr.next = prev;
            prev = curr;
            curr = nextTemp;
        }
        return prev;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        ListNode head = new ListNode(1, new ListNode(2, new ListNode(3, new ListNode(4, new ListNode(5)))));
        ListNode rev = s.reverseList(head);
        while (rev != null) {
            System.out.print(rev.val + (rev.next != null ? "->" : ""));
            rev = rev.next;
        }
        System.out.println(); // Expected: 5->4->3->2->1
    }
}
```

**Explanation:** Maintain three pointers `prev`, `curr`, and `nextTemp` to iteratively reverse the link direction for each node in a single pass. Time is O(n) and space is O(1).

## 36. Merge Two Sorted Lists

[Back to Index](#index)

**Problem:** You are given the heads of two sorted linked lists `list1` and `list2`. Merge the two lists into one sorted list by splicing together the nodes of the first two lists and return its head.

```java
class Solution {
    static class ListNode {
        int val;
        ListNode next;
        ListNode(int val) { this.val = val; }
        ListNode(int val, ListNode next) { this.val = val; this.next = next; }
    }

    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode dummy = new ListNode(0);
        ListNode tail = dummy;

        while (list1 != null && list2 != null) {
            if (list1.val <= list2.val) {
                tail.next = list1;
                list1 = list1.next;
            } else {
                tail.next = list2;
                list2 = list2.next;
            }
            tail = tail.next;
        }

        tail.next = (list1 != null) ? list1 : list2;
        return dummy.next;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        ListNode l1 = new ListNode(1, new ListNode(2, new ListNode(4)));
        ListNode l2 = new ListNode(1, new ListNode(3, new ListNode(4)));
        ListNode merged = s.mergeTwoLists(l1, l2);
        while (merged != null) {
            System.out.print(merged.val + (merged.next != null ? "->" : ""));
            merged = merged.next;
        }
        System.out.println(); // Expected: 1->1->2->3->4->4
    }
}
```

**Explanation:** Use a dummy node and a tail pointer. Repeatedly attach the node with the smaller value from either list until one is exhausted, then append the remaining list. Time is O(n + m) and space is O(1).

## 37. Reorder List

[Back to Index](#index)

**Problem:** You are given the head of a singly linked-list $L_0 \to L_1 \to \dots \to L_{n-1} \to L_n$. Reorder the list to be: $L_0 \to L_n \to L_1 \to L_{n-1} \to L_2 \to L_{n-2} \to \dots$ without modifying node values.

```java
class Solution {
    static class ListNode {
        int val;
        ListNode next;
        ListNode(int val) { this.val = val; }
        ListNode(int val, ListNode next) { this.val = val; this.next = next; }
    }

    public void reorderList(ListNode head) {
        if (head == null || head.next == null) return;

        // 1. Find the middle of the list
        ListNode slow = head, fast = head;
        while (fast.next != null && fast.next.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }

        // 2. Reverse the second half
        ListNode prev = null, curr = slow.next;
        slow.next = null;
        while (curr != null) {
            ListNode nextTemp = curr.next;
            curr.next = prev;
            prev = curr;
            curr = nextTemp;
        }

        // 3. Merge first half and reversed second half
        ListNode first = head, second = prev;
        while (second != null) {
            ListNode tmp1 = first.next;
            ListNode tmp2 = second.next;

            first.next = second;
            second.next = tmp1;

            first = tmp1;
            second = tmp2;
        }
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        ListNode head = new ListNode(1, new ListNode(2, new ListNode(3, new ListNode(4))));
        s.reorderList(head);
        while (head != null) {
            System.out.print(head.val + (head.next != null ? "->" : ""));
            head = head.next;
        }
        System.out.println(); // Expected: 1->4->2->3
    }
}
```

**Explanation:** Split the list into two halves using slow and fast pointers, reverse the second half, and interleave the nodes of the two halves. Time is O(n) and space is O(1).

## 38. Remove Nth Node From End of List

[Back to Index](#index)

**Problem:** Given the `head` of a linked list, remove the $n$-th node from the end of the list and return its head.

```java
class Solution {
    static class ListNode {
        int val;
        ListNode next;
        ListNode(int val) { this.val = val; }
        ListNode(int val, ListNode next) { this.val = val; this.next = next; }
    }

    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode dummy = new ListNode(0, head);
        ListNode fast = dummy;
        ListNode slow = dummy;

        for (int i = 0; i < n; i++) {
            fast = fast.next;
        }

        while (fast.next != null) {
            fast = fast.next;
            slow = slow.next;
        }

        slow.next = slow.next.next;
        return dummy.next;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        ListNode head = new ListNode(1, new ListNode(2, new ListNode(3, new ListNode(4, new ListNode(5)))));
        ListNode res = s.removeNthFromEnd(head, 2);
        while (res != null) {
            System.out.print(res.val + (res.next != null ? "->" : ""));
            res = res.next;
        }
        System.out.println(); // Expected: 1->2->3->5
    }
}
```

**Explanation:** Advance a `fast` pointer $n$ steps ahead from a dummy node. Then advance both `fast` and `slow` together until `fast` reaches the end; `slow` will be directly before the target node to delete. Time is O(n) and space is O(1).

## 39. Copy List with Random Pointer

[Back to Index](#index)

**Problem:** A linked list of length `n` is given such that each node contains an additional `random` pointer, which could point to any node in the list, or `null`. Construct a deep copy of the list.

```java
import java.util.HashMap;
import java.util.Map;

class Solution {
    static class Node {
        int val;
        Node next;
        Node random;
        Node(int val) {
            this.val = val;
            this.next = null;
            this.random = null;
        }
    }

    public Node copyRandomList(Node head) {
        if (head == null) return null;

        Map<Node, Node> map = new HashMap<>();

        Node curr = head;
        while (curr != null) {
            map.put(curr, new Node(curr.val));
            curr = curr.next;
        }

        curr = head;
        while (curr != null) {
            map.get(curr).next = map.get(curr.next);
            map.get(curr).random = map.get(curr.random);
            curr = curr.next;
        }

        return map.get(head);
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        Node n1 = new Node(7);
        Node n2 = new Node(13);
        Node n3 = new Node(11);
        n1.next = n2;
        n2.next = n3;
        n2.random = n1;
        n3.random = n2;

        Node copy = s.copyRandomList(n1);
        System.out.println(copy.val + " next: " + copy.next.val); // Expected: 7 next: 13
        System.out.println(copy.next.val + " random: " + copy.next.random.val); // Expected: 13 random: 7
    }
}
```

**Explanation:** Use a hash map mapping original nodes to cloned copies. Populate nodes in a first pass, then hook up `next` and `random` pointers in a second pass. Time is O(n) and space is O(n).

## 40. Add Two Numbers

[Back to Index](#index)

**Problem:** You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

```java
class Solution {
    static class ListNode {
        int val;
        ListNode next;
        ListNode(int val) { this.val = val; }
        ListNode(int val, ListNode next) { this.val = val; this.next = next; }
    }

    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode dummy = new ListNode(0);
        ListNode curr = dummy;
        int carry = 0;

        while (l1 != null || l2 != null || carry != 0) {
            int sum = carry;
            if (l1 != null) {
                sum += l1.val;
                l1 = l1.next;
            }
            if (l2 != null) {
                sum += l2.val;
                l2 = l2.next;
            }

            carry = sum / 10;
            curr.next = new ListNode(sum % 10);
            curr = curr.next;
        }

        return dummy.next;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        ListNode l1 = new ListNode(2, new ListNode(4, new ListNode(3)));
        ListNode l2 = new ListNode(5, new ListNode(6, new ListNode(4)));
        ListNode res = s.addTwoNumbers(l1, l2);
        while (res != null) {
            System.out.print(res.val + (res.next != null ? "->" : ""));
            res = res.next;
        }
        System.out.println(); // Expected: 7->0->8
    }
}
```

**Explanation:** Iterate through both lists node by node, computing `sum = carry + l1.val + l2.val`, creating new nodes with `sum % 10`, and carrying forward `sum / 10`. Time is O(max(n, m)) and space is O(max(n, m)).

## 41. Linked List Cycle Detection

[Back to Index](#index)

**Problem:** Given `head`, the head of a linked list, determine if the linked list has a cycle in it.

```java
class Solution {
    static class ListNode {
        int val;
        ListNode next;
        ListNode(int val) { this.val = val; }
    }

    public boolean hasCycle(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;

        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
            if (slow == fast) {
                return true;
            }
        }
        return false;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        ListNode n1 = new ListNode(3);
        ListNode n2 = new ListNode(2);
        ListNode n3 = new ListNode(0);
        ListNode n4 = new ListNode(-4);
        n1.next = n2;
        n2.next = n3;
        n3.next = n4;
        n4.next = n2; // cycle pointing to n2

        System.out.println(s.hasCycle(n1)); // Expected: true

        ListNode n5 = new ListNode(1);
        System.out.println(s.hasCycle(n5)); // Expected: false
    }
}
```

**Explanation:** Floyd's Tortoise and Hare algorithm uses two pointers moving at speeds of 1 and 2 nodes per step. If a cycle exists, `fast` will inevitably lap and meet `slow`. Time is O(n) and space is O(1).

## 42. Find the Duplicate Number

[Back to Index](#index)

**Problem:** Given an array of integers `nums` containing $n + 1$ integers where each integer is in the range $[1, n]$ inclusive, return the duplicate number without modifying the array and using only constant extra space.

```java
class Solution {
    public int findDuplicate(int[] nums) {
        int slow = nums[0];
        int fast = nums[0];

        // Phase 1: Detect cycle
        do {
            slow = nums[slow];
            fast = nums[nums[fast]];
        } while (slow != fast);

        // Phase 2: Find cycle entrance
        slow = nums[0];
        while (slow != fast) {
            slow = nums[slow];
            fast = nums[fast];
        }

        return slow;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[] nums1 = {1, 3, 4, 2, 2};
        System.out.println(s.findDuplicate(nums1)); // Expected: 2

        int[] nums2 = {3, 1, 3, 4, 2};
        System.out.println(s.findDuplicate(nums2)); // Expected: 3
    }
}
```

**Explanation:** Treat the array as a functional directed graph $i \to \text{nums}[i]$. Since values are in $[1, n]$ with $n+1$ values, a cycle exists. Use Floyd's cycle detection to find the intersection, then advance pointers at equal speed from index 0 and intersection to locate the duplicate. Time is O(n) and space is O(1).

## 43. LRU Cache

[Back to Index](#index)

**Problem:** Design a data structure that follows the constraints of a Least Recently Used (LRU) cache supporting `get` and `put` in $O(1)$ average time complexity.

```java
import java.util.HashMap;
import java.util.Map;

class Solution {
    static class LRUCache {
        static class Node {
            int key, val;
            Node prev, next;
            Node(int key, int val) {
                this.key = key;
                this.val = val;
            }
        }

        private final int capacity;
        private final Map<Integer, Node> cache;
        private final Node head;
        private final Node tail;

        public LRUCache(int capacity) {
            this.capacity = capacity;
            this.cache = new HashMap<>();
            this.head = new Node(0, 0);
            this.tail = new Node(0, 0);
            head.next = tail;
            tail.prev = head;
        }

        private void remove(Node node) {
            node.prev.next = node.next;
            node.next.prev = node.prev;
        }

        private void insert(Node node) {
            node.next = head.next;
            node.prev = head;
            head.next.prev = node;
            head.next = node;
        }

        public int get(int key) {
            if (!cache.containsKey(key)) {
                return -1;
            }
            Node node = cache.get(key);
            remove(node);
            insert(node);
            return node.val;
        }

        public void put(int key, int value) {
            if (cache.containsKey(key)) {
                remove(cache.get(key));
            }
            Node node = new Node(key, value);
            insert(node);
            cache.put(key, node);

            if (cache.size() > capacity) {
                Node lru = tail.prev;
                remove(lru);
                cache.remove(lru.key);
            }
        }
    }

    public static void main(String[] args) {
        LRUCache lRUCache = new LRUCache(2);
        lRUCache.put(1, 1);
        lRUCache.put(2, 2);
        System.out.println(lRUCache.get(1)); // Expected: 1
        lRUCache.put(3, 3);                 // evicts key 2
        System.out.println(lRUCache.get(2)); // Expected: -1
        lRUCache.put(4, 4);                 // evicts key 1
        System.out.println(lRUCache.get(1)); // Expected: -1
        System.out.println(lRUCache.get(3)); // Expected: 3
        System.out.println(lRUCache.get(4)); // Expected: 4
    }
}
```

**Explanation:** A hash map provides $O(1)$ key lookup to doubly linked list nodes. The doubly linked list maintains usage order by moving accessed nodes to the head and evicting from the tail in $O(1)$ time. Time is O(1) for both `get` and `put`, and space is O(capacity).

## 44. Merge k Sorted Lists

[Back to Index](#index)

**Problem:** You are given an array of `k` linked-lists `lists`, each linked-list is sorted in ascending order. Merge all the linked-lists into one sorted linked-list and return it.

```java
import java.util.PriorityQueue;

class Solution {
    static class ListNode {
        int val;
        ListNode next;
        ListNode(int val) { this.val = val; }
        ListNode(int val, ListNode next) { this.val = val; this.next = next; }
    }

    public ListNode mergeKLists(ListNode[] lists) {
        if (lists == null || lists.length == 0) return null;

        PriorityQueue<ListNode> minHeap = new PriorityQueue<>((a, b) -> Integer.compare(a.val, b.val));
        for (ListNode node : lists) {
            if (node != null) {
                minHeap.offer(node);
            }
        }

        ListNode dummy = new ListNode(0);
        ListNode curr = dummy;

        while (!minHeap.isEmpty()) {
            ListNode smallest = minHeap.poll();
            curr.next = smallest;
            curr = curr.next;

            if (smallest.next != null) {
                minHeap.offer(smallest.next);
            }
        }

        return dummy.next;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        ListNode l1 = new ListNode(1, new ListNode(4, new ListNode(5)));
        ListNode l2 = new ListNode(1, new ListNode(3, new ListNode(4)));
        ListNode l3 = new ListNode(2, new ListNode(6));

        ListNode[] lists = {l1, l2, l3};
        ListNode res = s.mergeKLists(lists);
        while (res != null) {
            System.out.print(res.val + (res.next != null ? "->" : ""));
            res = res.next;
        }
        System.out.println(); // Expected: 1->1->2->3->4->4->5->6
    }
}
```

**Explanation:** Initialize a min-heap with the head node of each of the $k$ lists. Continuously extract the minimum node, append it to the result list, and push its next node into the heap. Time is O(N log k) where N is total nodes and k is number of lists, and space is O(k).

## 45. Reverse Nodes in k-Group

[Back to Index](#index)

**Problem:** Given the `head` of a linked list, reverse the nodes of the list `k` at a time, and return the modified list. If the number of nodes is not a multiple of `k` then left-out nodes at the end should remain as-is.

```java
class Solution {
    static class ListNode {
        int val;
        ListNode next;
        ListNode(int val) { this.val = val; }
        ListNode(int val, ListNode next) { this.val = val; this.next = next; }
    }

    public ListNode reverseKGroup(ListNode head, int k) {
        ListNode dummy = new ListNode(0, head);
        ListNode groupPrev = dummy;

        while (true) {
            ListNode kth = getKth(groupPrev, k);
            if (kth == null) {
                break;
            }
            ListNode groupNext = kth.next;

            // Reverse current group
            ListNode prev = groupNext;
            ListNode curr = groupPrev.next;
            while (curr != groupNext) {
                ListNode tmp = curr.next;
                curr.next = prev;
                prev = curr;
                curr = tmp;
            }

            ListNode tmp = groupPrev.next;
            groupPrev.next = kth;
            groupPrev = tmp;
        }

        return dummy.next;
    }

    private ListNode getKth(ListNode curr, int k) {
        while (curr != null && k > 0) {
            curr = curr.next;
            k--;
        }
        return curr;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        ListNode head = new ListNode(1, new ListNode(2, new ListNode(3, new ListNode(4, new ListNode(5)))));
        ListNode res = s.reverseKGroup(head, 2);
        while (res != null) {
            System.out.print(res.val + (res.next != null ? "->" : ""));
            res = res.next;
        }
        System.out.println(); // Expected: 2->1->4->3->5

        ListNode head2 = new ListNode(1, new ListNode(2, new ListNode(3, new ListNode(4, new ListNode(5)))));
        ListNode res2 = s.reverseKGroup(head2, 3);
        while (res2 != null) {
            System.out.print(res2.val + (res2.next != null ? "->" : ""));
            res2 = res2.next;
        }
        System.out.println(); // Expected: 3->2->1->4->5
    }
}
```

**Explanation:** For each group of $k$ nodes, find the $k$-th node. If fewer than $k$ nodes remain, terminate. Otherwise, reverse the $k$ nodes in-place, connect the previous group's tail to the new head, and advance pointer `groupPrev`. Time is O(n) and space is O(1).

---

# Trees

## 46. Invert Binary Tree

[Back to Index](#index)

**Problem:** Given the root of a binary tree, invert the tree (mirror all left and right subtrees), and return its root.

```java
import java.util.*;

class Solution {
    static class TreeNode {
        int val;
        TreeNode left, right;
        TreeNode(int val) { this.val = val; }
        TreeNode(int val, TreeNode left, TreeNode right) {
            this.val = val;
            this.left = left;
            this.right = right;
        }
    }

    public TreeNode invertTree(TreeNode root) {
        if (root == null) {
            return null;
        }
        TreeNode temp = root.left;
        root.left = invertTree(root.right);
        root.right = invertTree(temp);
        return root;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        // Tree: [4, 2, 7, 1, 3, 6, 9]
        TreeNode root = new TreeNode(4,
            new TreeNode(2, new TreeNode(1), new TreeNode(3)),
            new TreeNode(7, new TreeNode(6), new TreeNode(9))
        );
        TreeNode inverted = s.invertTree(root);
        System.out.println(inverted.val + " left:" + inverted.left.val + " right:" + inverted.right.val); // Output: 4 left:7 right:2 (expected: 4 left:7 right:2)
    }
}
```

**Explanation:** Recursively invert the left and right subtrees, then swap the left and right child pointers for the current node. Time is O(n) and space is O(h) where h is the tree height.

## 47. Maximum Depth of Binary Tree

[Back to Index](#index)

**Problem:** Given the root of a binary tree, return its maximum depth, defined as the number of nodes along the longest path from the root node down to the farthest leaf node.

```java
import java.util.*;

class Solution {
    static class TreeNode {
        int val;
        TreeNode left, right;
        TreeNode(int val) { this.val = val; }
        TreeNode(int val, TreeNode left, TreeNode right) {
            this.val = val;
            this.left = left;
            this.right = right;
        }
    }

    public int maxDepth(TreeNode root) {
        if (root == null) {
            return 0;
        }
        return 1 + Math.max(maxDepth(root.left), maxDepth(root.right));
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        // Tree: [3, 9, 20, null, null, 15, 7]
        TreeNode root = new TreeNode(3,
            new TreeNode(9),
            new TreeNode(20, new TreeNode(15), new TreeNode(7))
        );
        System.out.println(s.maxDepth(root)); // Output: 3 (expected: 3)
    }
}
```

**Explanation:** Use a depth-first search (DFS) post-order traversal to compute the depth of each subtree. The maximum depth of the current subtree is 1 plus the maximum depth of its left and right children. Time is O(n) and space is O(h) where h is the tree height.

## 48. Diameter of Binary Tree

[Back to Index](#index)

**Problem:** Given the root of a binary tree, return the length of the diameter of the tree, which is the length of the longest path between any two nodes in a tree (measured in number of edges).

```java
import java.util.*;

class Solution {
    static class TreeNode {
        int val;
        TreeNode left, right;
        TreeNode(int val) { this.val = val; }
        TreeNode(int val, TreeNode left, TreeNode right) {
            this.val = val;
            this.left = left;
            this.right = right;
        }
    }

    private int maxDiameter = 0;

    public int diameterOfBinaryTree(TreeNode root) {
        maxDiameter = 0;
        maxDepth(root);
        return maxDiameter;
    }

    private int maxDepth(TreeNode node) {
        if (node == null) {
            return 0;
        }
        int left = maxDepth(node.left);
        int right = maxDepth(node.right);
        maxDiameter = Math.max(maxDiameter, left + right);
        return 1 + Math.max(left, right);
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        // Tree: [1, 2, 3, 4, 5]
        TreeNode root = new TreeNode(1,
            new TreeNode(2, new TreeNode(4), new TreeNode(5)),
            new TreeNode(3)
        );
        System.out.println(s.diameterOfBinaryTree(root)); // Output: 3 (expected: 3)
    }
}
```

**Explanation:** At each node, the longest path that has this node as its highest point is the sum of the maximum depths of its left and right subtrees. We maintain a global maximum diameter while recursively computing subtree heights. Time is O(n) and space is O(h) where h is the tree height.

## 49. Balanced Binary Tree

[Back to Index](#index)

**Problem:** Given a binary tree, determine if it is height-balanced, meaning the depth of the two subtrees of every node never differs by more than one.

```java
import java.util.*;

class Solution {
    static class TreeNode {
        int val;
        TreeNode left, right;
        TreeNode(int val) { this.val = val; }
        TreeNode(int val, TreeNode left, TreeNode right) {
            this.val = val;
            this.left = left;
            this.right = right;
        }
    }

    public boolean isBalanced(TreeNode root) {
        return checkHeight(root) != -1;
    }

    private int checkHeight(TreeNode node) {
        if (node == null) {
            return 0;
        }
        int leftHeight = checkHeight(node.left);
        if (leftHeight == -1) return -1;

        int rightHeight = checkHeight(node.right);
        if (rightHeight == -1) return -1;

        if (Math.abs(leftHeight - rightHeight) > 1) {
            return -1;
        }
        return 1 + Math.max(leftHeight, rightHeight);
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        // Balanced Tree: [3, 9, 20, null, null, 15, 7]
        TreeNode root1 = new TreeNode(3,
            new TreeNode(9),
            new TreeNode(20, new TreeNode(15), new TreeNode(7))
        );
        System.out.println(s.isBalanced(root1)); // Output: true (expected: true)

        // Unbalanced Tree: [1, 2, 2, 3, 3, null, null, 4, 4]
        TreeNode root2 = new TreeNode(1,
            new TreeNode(2,
                new TreeNode(3, new TreeNode(4), new TreeNode(4)),
                new TreeNode(3)
            ),
            new TreeNode(2)
        );
        System.out.println(s.isBalanced(root2)); // Output: false (expected: false)
    }
}
```

**Explanation:** Use a bottom-up DFS approach returning the height of the current subtree if balanced, or -1 if unbalanced. If any subtree is unbalanced, the failure propagates immediately without redundant calculations. Time is O(n) and space is O(h) where h is the tree height.

## 50. Same Tree

[Back to Index](#index)

**Problem:** Given the roots of two binary trees `p` and `q`, write a function to check if they are the same (structurally identical and all corresponding nodes have the same values).

```java
import java.util.*;

class Solution {
    static class TreeNode {
        int val;
        TreeNode left, right;
        TreeNode(int val) { this.val = val; }
        TreeNode(int val, TreeNode left, TreeNode right) {
            this.val = val;
            this.left = left;
            this.right = right;
        }
    }

    public boolean isSameTree(TreeNode p, TreeNode q) {
        if (p == null && q == null) {
            return true;
        }
        if (p == null || q == null || p.val != q.val) {
            return false;
        }
        return isSameTree(p.left, q.left) && isSameTree(p.right, q.right);
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        TreeNode t1 = new TreeNode(1, new TreeNode(2), new TreeNode(3));
        TreeNode t2 = new TreeNode(1, new TreeNode(2), new TreeNode(3));
        TreeNode t3 = new TreeNode(1, new TreeNode(2), null);

        System.out.println(s.isSameTree(t1, t2)); // Output: true (expected: true)
        System.out.println(s.isSameTree(t1, t3)); // Output: false (expected: false)
    }
}
```

**Explanation:** Recursively compare both trees. If both nodes are null, they match; if only one is null or their values differ, they do not match; otherwise, check both their left subtrees and right subtrees. Time is O(min(n, m)) and space is O(min(h1, h2)) where h1 and h2 are the heights of the two trees.

## 51. Subtree of Another Tree

[Back to Index](#index)

**Problem:** Given the roots of two binary trees `root` and `subRoot`, return `true` if there is a subtree of `root` with the same structure and node values as `subRoot`, and `false` otherwise.

```java
import java.util.*;

class Solution {
    static class TreeNode {
        int val;
        TreeNode left, right;
        TreeNode(int val) { this.val = val; }
        TreeNode(int val, TreeNode left, TreeNode right) {
            this.val = val;
            this.left = left;
            this.right = right;
        }
    }

    public boolean isSubtree(TreeNode root, TreeNode subRoot) {
        if (root == null) {
            return false;
        }
        if (isSameTree(root, subRoot)) {
            return true;
        }
        return isSubtree(root.left, subRoot) || isSubtree(root.right, subRoot);
    }

    private boolean isSameTree(TreeNode p, TreeNode q) {
        if (p == null && q == null) return true;
        if (p == null || q == null || p.val != q.val) return false;
        return isSameTree(p.left, q.left) && isSameTree(p.right, q.right);
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        TreeNode root = new TreeNode(3,
            new TreeNode(4, new TreeNode(1), new TreeNode(2)),
            new TreeNode(5)
        );
        TreeNode subRoot = new TreeNode(4, new TreeNode(1), new TreeNode(2));
        System.out.println(s.isSubtree(root, subRoot)); // Output: true (expected: true)
    }
}
```

**Explanation:** Traverse each node in `root` using DFS; at each node, verify if the subtree rooted there matches `subRoot` completely using an `isSameTree` helper. Time is O(m * n) where m and n are node counts of the two trees, and space is O(h) where h is the tree height.

## 52. Lowest Common Ancestor of a Binary Search Tree

[Back to Index](#index)

**Problem:** Given a binary search tree (BST) and two nodes `p` and `q`, find the lowest common ancestor (LCA) of `p` and `q`.

```java
import java.util.*;

class Solution {
    static class TreeNode {
        int val;
        TreeNode left, right;
        TreeNode(int val) { this.val = val; }
        TreeNode(int val, TreeNode left, TreeNode right) {
            this.val = val;
            this.left = left;
            this.right = right;
        }
    }

    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        TreeNode curr = root;
        while (curr != null) {
            if (p.val < curr.val && q.val < curr.val) {
                curr = curr.left;
            } else if (p.val > curr.val && q.val > curr.val) {
                curr = curr.right;
            } else {
                return curr;
            }
        }
        return null;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        TreeNode node0 = new TreeNode(0);
        TreeNode node3 = new TreeNode(3);
        TreeNode node5 = new TreeNode(5);
        TreeNode node4 = new TreeNode(4, node3, node5);
        TreeNode node2 = new TreeNode(2, node0, node4);
        TreeNode node7 = new TreeNode(7);
        TreeNode node9 = new TreeNode(9);
        TreeNode node8 = new TreeNode(8, node7, node9);
        TreeNode root = new TreeNode(6, node2, node8);

        TreeNode lca1 = s.lowestCommonAncestor(root, node2, node8);
        System.out.println(lca1.val); // Output: 6 (expected: 6)

        TreeNode lca2 = s.lowestCommonAncestor(root, node2, node4);
        System.out.println(lca2.val); // Output: 2 (expected: 2)
    }
}
```

**Explanation:** In a BST, if both `p` and `q` are strictly smaller than the current node, the LCA must reside in the left subtree. If both are strictly greater, it must reside in the right subtree. Otherwise, the current node is the split point and hence the LCA. Time is O(h) and space is O(1) iterative where h is the tree height.

## 53. Binary Tree Level Order Traversal

[Back to Index](#index)

**Problem:** Given the root of a binary tree, return the level order traversal of its nodes' values (i.e., from left to right, level by level).

```java
import java.util.*;

class Solution {
    static class TreeNode {
        int val;
        TreeNode left, right;
        TreeNode(int val) { this.val = val; }
        TreeNode(int val, TreeNode left, TreeNode right) {
            this.val = val;
            this.left = left;
            this.right = right;
        }
    }

    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> result = new ArrayList<>();
        if (root == null) {
            return result;
        }

        Queue<TreeNode> queue = new LinkedList<>();
        queue.offer(root);

        while (!queue.isEmpty()) {
            int levelSize = queue.size();
            List<Integer> currentLevel = new ArrayList<>(levelSize);
            for (int i = 0; i < levelSize; i++) {
                TreeNode curr = queue.poll();
                currentLevel.add(curr.val);
                if (curr.left != null) queue.offer(curr.left);
                if (curr.right != null) queue.offer(curr.right);
            }
            result.add(currentLevel);
        }
        return result;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        TreeNode root = new TreeNode(3,
            new TreeNode(9),
            new TreeNode(20, new TreeNode(15), new TreeNode(7))
        );
        System.out.println(s.levelOrder(root)); // Output: [[3], [9, 20], [15, 7]] (expected: [[3], [9, 20], [15, 7]])
    }
}
```

**Explanation:** Use breadth-first search (BFS) with a queue. For each level, determine the current queue size, poll all nodes at that level to construct the level's value list, and push their children into the queue. Time is O(n) and space is O(n).

## 54. Binary Tree Right Side View

[Back to Index](#index)

**Problem:** Given the root of a binary tree, imagine yourself standing on the right side of it; return the values of the nodes you can see ordered from top to bottom.

```java
import java.util.*;

class Solution {
    static class TreeNode {
        int val;
        TreeNode left, right;
        TreeNode(int val) { this.val = val; }
        TreeNode(int val, TreeNode left, TreeNode right) {
            this.val = val;
            this.left = left;
            this.right = right;
        }
    }

    public List<Integer> rightSideView(TreeNode root) {
        List<Integer> result = new ArrayList<>();
        if (root == null) {
            return result;
        }

        Queue<TreeNode> queue = new LinkedList<>();
        queue.offer(root);

        while (!queue.isEmpty()) {
            int size = queue.size();
            for (int i = 0; i < size; i++) {
                TreeNode node = queue.poll();
                if (i == size - 1) {
                    result.add(node.val);
                }
                if (node.left != null) queue.offer(node.left);
                if (node.right != null) queue.offer(node.right);
            }
        }
        return result;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        // Tree: [1, 2, 3, null, 5, null, 4]
        TreeNode root = new TreeNode(1,
            new TreeNode(2, null, new TreeNode(5)),
            new TreeNode(3, null, new TreeNode(4))
        );
        System.out.println(s.rightSideView(root)); // Output: [1, 3, 4] (expected: [1, 3, 4])
    }
}
```

**Explanation:** Perform a level-order traversal (BFS). At each level, the last node processed in that level's queue iteration corresponds to the rightmost visible node. Add its value to the result list. Time is O(n) and space is O(n).

## 55. Count Good Nodes in Binary Tree

[Back to Index](#index)

**Problem:** Given a binary tree root, a node X in the tree is named good if in the path from the root to X there are no nodes with a value greater than X. Return the number of good nodes in the binary tree.

```java
import java.util.*;

class Solution {
    static class TreeNode {
        int val;
        TreeNode left, right;
        TreeNode(int val) { this.val = val; }
        TreeNode(int val, TreeNode left, TreeNode right) {
            this.val = val;
            this.left = left;
            this.right = right;
        }
    }

    public int goodNodes(TreeNode root) {
        return dfs(root, root.val);
    }

    private int dfs(TreeNode node, int maxVal) {
        if (node == null) {
            return 0;
        }
        int count = 0;
        if (node.val >= maxVal) {
            count = 1;
            maxVal = node.val;
        }
        count += dfs(node.left, maxVal);
        count += dfs(node.right, maxVal);
        return count;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        // Tree: [3, 1, 4, 3, null, 1, 5]
        TreeNode root = new TreeNode(3,
            new TreeNode(1, new TreeNode(3), null),
            new TreeNode(4, new TreeNode(1), new TreeNode(5))
        );
        System.out.println(s.goodNodes(root)); // Output: 4 (expected: 4)
    }
}
```

**Explanation:** Perform a preorder DFS traversal passing along the maximum node value encountered along the path from the root. If the current node value is at least this maximum, it is a good node; update the maximum and recurse on left and right children. Time is O(n) and space is O(h) where h is the tree height.

## 56. Validate Binary Search Tree

[Back to Index](#index)

**Problem:** Given the root of a binary tree, determine if it is a valid binary search tree (BST). A valid BST requires that all nodes in the left subtree have values strictly less than the node's value, and all nodes in the right subtree have values strictly greater than the node's value, recursively for all subtrees.

```java
import java.util.*;

class Solution {
    static class TreeNode {
        int val;
        TreeNode left, right;
        TreeNode(int val) { this.val = val; }
        TreeNode(int val, TreeNode left, TreeNode right) {
            this.val = val;
            this.left = left;
            this.right = right;
        }
    }

    public boolean isValidBST(TreeNode root) {
        return validate(root, null, null);
    }

    private boolean validate(TreeNode node, Long min, Long max) {
        if (node == null) {
            return true;
        }
        if ((min != null && node.val <= min) || (max != null && node.val >= max)) {
            return false;
        }
        return validate(node.left, min, (long) node.val) && validate(node.right, (long) node.val, max);
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        TreeNode validRoot = new TreeNode(2, new TreeNode(1), new TreeNode(3));
        System.out.println(s.isValidBST(validRoot)); // Output: true (expected: true)

        TreeNode invalidRoot = new TreeNode(5,
            new TreeNode(1),
            new TreeNode(4, new TreeNode(3), new TreeNode(6))
        );
        System.out.println(s.isValidBST(invalidRoot)); // Output: false (expected: false)
    }
}
```

**Explanation:** Recursively validate each node by enforcing strictly open boundaries `(min, max)`. When traversing left, the current node becomes the upper bound; when traversing right, it becomes the lower bound. Using `Long` bounds prevents integer overflow issues. Time is O(n) and space is O(h) where h is the tree height.

## 57. Kth Smallest Element in a BST

[Back to Index](#index)

**Problem:** Given the root of a binary search tree, and an integer `k`, return the `k`th smallest value (1-indexed) of all the values of the nodes in the tree.

```java
import java.util.*;

class Solution {
    static class TreeNode {
        int val;
        TreeNode left, right;
        TreeNode(int val) { this.val = val; }
        TreeNode(int val, TreeNode left, TreeNode right) {
            this.val = val;
            this.left = left;
            this.right = right;
        }
    }

    private int count = 0;
    private int result = -1;

    public int kthSmallest(TreeNode root, int k) {
        count = 0;
        result = -1;
        inorder(root, k);
        return result;
    }

    private void inorder(TreeNode node, int k) {
        if (node == null || count >= k) {
            return;
        }
        inorder(node.left, k);
        count++;
        if (count == k) {
            result = node.val;
            return;
        }
        inorder(node.right, k);
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        // Tree: [3, 1, 4, null, 2], k = 1
        TreeNode root = new TreeNode(3,
            new TreeNode(1, null, new TreeNode(2)),
            new TreeNode(4)
        );
        System.out.println(s.kthSmallest(root, 1)); // Output: 1 (expected: 1)
    }
}
```

**Explanation:** An in-order traversal of a binary search tree visits nodes in ascending sorted order. By maintaining a counter of nodes visited in-order, we can stop the traversal and record the value once we reach the `k`th node. Time is O(h + k) and space is O(h) where h is the tree height.

## 58. Construct Binary Tree from Preorder and Inorder Traversal

[Back to Index](#index)

**Problem:** Given two integer arrays `preorder` and `inorder` where `preorder` is the preorder traversal of a binary tree and `inorder` is the inorder traversal of the same tree, construct and return the binary tree.

```java
import java.util.*;

class Solution {
    static class TreeNode {
        int val;
        TreeNode left, right;
        TreeNode(int val) { this.val = val; }
        TreeNode(int val, TreeNode left, TreeNode right) {
            this.val = val;
            this.left = left;
            this.right = right;
        }
    }

    private int preorderIndex = 0;
    private Map<Integer, Integer> inorderIndexMap;

    public TreeNode buildTree(int[] preorder, int[] inorder) {
        preorderIndex = 0;
        inorderIndexMap = new HashMap<>();
        for (int i = 0; i < inorder.length; i++) {
            inorderIndexMap.put(inorder[i], i);
        }
        return build(preorder, 0, inorder.length - 1);
    }

    private TreeNode build(int[] preorder, int left, int right) {
        if (left > right) {
            return null;
        }
        int rootVal = preorder[preorderIndex++];
        TreeNode root = new TreeNode(rootVal);
        int mid = inorderIndexMap.get(rootVal);

        root.left = build(preorder, left, mid - 1);
        root.right = build(preorder, mid + 1, right);
        return root;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[] preorder = {3, 9, 20, 15, 7};
        int[] inorder = {9, 3, 15, 20, 7};
        TreeNode root = s.buildTree(preorder, inorder);
        System.out.println(root.val + " left:" + root.left.val + " right:" + root.right.val); // Output: 3 left:9 right:20 (expected: 3 left:9 right:20)
    }
}
```

**Explanation:** In preorder traversal, the first unused element is always the current subtree's root. Locating this root in the inorder traversal (using an O(1) hash map lookup) splits the elements into the left subtree and right subtree, which are recursively constructed. Time is O(n) and space is O(n).

## 59. Binary Tree Maximum Path Sum

[Back to Index](#index)

**Problem:** A path in a binary tree is a sequence of nodes where each pair of adjacent nodes has an edge connecting them. Return the maximum path sum of any non-empty path in the tree.

```java
import java.util.*;

class Solution {
    static class TreeNode {
        int val;
        TreeNode left, right;
        TreeNode(int val) { this.val = val; }
        TreeNode(int val, TreeNode left, TreeNode right) {
            this.val = val;
            this.left = left;
            this.right = right;
        }
    }

    private int maxSum = Integer.MIN_VALUE;

    public int maxPathSum(TreeNode root) {
        maxSum = Integer.MIN_VALUE;
        gainFromSubtree(root);
        return maxSum;
    }

    private int gainFromSubtree(TreeNode node) {
        if (node == null) {
            return 0;
        }
        // Discard negative paths by taking max with 0
        int leftGain = Math.max(0, gainFromSubtree(node.left));
        int rightGain = Math.max(0, gainFromSubtree(node.right));

        // Path passing through this node as highest point
        int priceNewPath = node.val + leftGain + rightGain;
        maxSum = Math.max(maxSum, priceNewPath);

        // For parent node, return max single branch gain
        return node.val + Math.max(leftGain, rightGain);
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        // Tree: [-10, 9, 20, null, null, 15, 7]
        TreeNode root = new TreeNode(-10,
            new TreeNode(9),
            new TreeNode(20, new TreeNode(15), new TreeNode(7))
        );
        System.out.println(s.maxPathSum(root)); // Output: 42 (expected: 42)
    }
}
```

**Explanation:** For each node, compute the maximum gain that the left and right subtrees can contribute (clamping negative gains to 0). A full path turning at the current node has sum `node.val + leftGain + rightGain`, which updates the global maximum. The function returns `node.val + max(leftGain, rightGain)` to continue extending the path to the parent. Time is O(n) and space is O(h) where h is the tree height.

## 60. Serialize and Deserialize Binary Tree

[Back to Index](#index)

**Problem:** Design an algorithm to serialize a binary tree into a string and deserialize that string back into the original binary tree structure.

```java
import java.util.*;

class Solution {
    static class TreeNode {
        int val;
        TreeNode left, right;
        TreeNode(int val) { this.val = val; }
        TreeNode(int val, TreeNode left, TreeNode right) {
            this.val = val;
            this.left = left;
            this.right = right;
        }
    }

    // Encodes a tree to a single string.
    public String serialize(TreeNode root) {
        StringBuilder sb = new StringBuilder();
        serializeHelper(root, sb);
        return sb.toString();
    }

    private void serializeHelper(TreeNode node, StringBuilder sb) {
        if (node == null) {
            sb.append("N,");
            return;
        }
        sb.append(node.val).append(",");
        serializeHelper(node.left, sb);
        serializeHelper(node.right, sb);
    }

    // Decodes your encoded data to tree.
    public TreeNode deserialize(String data) {
        Queue<String> nodes = new LinkedList<>(Arrays.asList(data.split(",")));
        return deserializeHelper(nodes);
    }

    private TreeNode deserializeHelper(Queue<String> nodes) {
        String val = nodes.poll();
        if (val == null || val.equals("N")) {
            return null;
        }
        TreeNode node = new TreeNode(Integer.parseInt(val));
        node.left = deserializeHelper(nodes);
        node.right = deserializeHelper(nodes);
        return node;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        // Tree: [1, 2, 3, null, null, 4, 5]
        TreeNode root = new TreeNode(1,
            new TreeNode(2),
            new TreeNode(3, new TreeNode(4), new TreeNode(5))
        );
        String serialized = s.serialize(root);
        System.out.println("Serialized: " + serialized); // Output: Serialized: 1,2,N,N,3,4,N,N,5,N,N,
        TreeNode deserialized = s.deserialize(serialized);
        System.out.println("Deserialized root: " + deserialized.val + " left:" + deserialized.left.val + " right:" + deserialized.right.val); // Output: Deserialized root: 1 left:2 right:3 (expected: Deserialized root: 1 left:2 right:3)
    }
}
```

**Explanation:** Serialize the tree using preorder traversal, writing comma-separated values and using `"N"` to represent null children. Deserialize by splitting the string into a queue of tokens and recursively reconstructing the tree in preorder fashion. Time is O(n) and space is O(n).

---

# Tries

## 61. Implement Trie (Prefix Tree)

[Back to Index](#index)

**Problem:** Implement a trie (prefix tree) data structure with `insert`, `search`, and `startsWith` methods for lowercase English letters.

```java
class Solution {
    static class Trie {
        private final TrieNode root;

        private static class TrieNode {
            TrieNode[] children = new TrieNode[26];
            boolean isEndOfWord = false;
        }

        public Trie() {
            root = new TrieNode();
        }

        public void insert(String word) {
            TrieNode node = root;
            for (char c : word.toCharArray()) {
                int index = c - 'a';
                if (node.children[index] == null) {
                    node.children[index] = new TrieNode();
                }
                node = node.children[index];
            }
            node.isEndOfWord = true;
        }

        public boolean search(String word) {
            TrieNode node = findNode(word);
            return node != null && node.isEndOfWord;
        }

        public boolean startsWith(String prefix) {
            return findNode(prefix) != null;
        }

        private TrieNode findNode(String prefix) {
            TrieNode node = root;
            for (char c : prefix.toCharArray()) {
                int index = c - 'a';
                if (node.children[index] == null) {
                    return null;
                }
                node = node.children[index];
            }
            return node;
        }
    }

    public static void main(String[] args) {
        Trie trie = new Trie();
        trie.insert("apple");
        System.out.println(trie.search("apple"));   // true
        System.out.println(trie.search("app"));     // false
        System.out.println(trie.startsWith("app")); // true
        trie.insert("app");
        System.out.println(trie.search("app"));     // true
    }
}
```

**Explanation:** Each tree node holds an array of 26 pointers for letters 'a' through 'z' and a boolean flag indicating if the node marks the end of a word. Traversing character-by-character allows exact match checks and prefix checks. Time is O(L) for all operations where L is the length of the string, and space is O(N * L) where N is the total number of words inserted.

## 62. Design Add and Search Words Data Structure

[Back to Index](#index)

**Problem:** Design a data structure that supports adding new words and finding if a string matches any previously added string, supporting the wildcard character `.` which matches any letter.

```java
class Solution {
    static class WordDictionary {
        private static class TrieNode {
            TrieNode[] children = new TrieNode[26];
            boolean isEndOfWord = false;
        }

        private final TrieNode root;

        public WordDictionary() {
            root = new TrieNode();
        }

        public void addWord(String word) {
            TrieNode node = root;
            for (char c : word.toCharArray()) {
                int index = c - 'a';
                if (node.children[index] == null) {
                    node.children[index] = new TrieNode();
                }
                node = node.children[index];
            }
            node.isEndOfWord = true;
        }

        public boolean search(String word) {
            return searchInNode(word, 0, root);
        }

        private boolean searchInNode(String word, int index, TrieNode curr) {
            if (curr == null) {
                return false;
            }
            if (index == word.length()) {
                return curr.isEndOfWord;
            }

            char c = word.charAt(index);
            if (c == '.') {
                for (TrieNode child : curr.children) {
                    if (child != null && searchInNode(word, index + 1, child)) {
                        return true;
                    }
                }
                return false;
            } else {
                int childIndex = c - 'a';
                return searchInNode(word, index + 1, curr.children[childIndex]);
            }
        }
    }

    public static void main(String[] args) {
        WordDictionary wd = new WordDictionary();
        wd.addWord("bad");
        wd.addWord("dad");
        wd.addWord("mad");
        System.out.println(wd.search("pad")); // false
        System.out.println(wd.search("bad")); // true
        System.out.println(wd.search(".ad")); // true
        System.out.println(wd.search("b..")); // true
    }
}
```

**Explanation:** A trie stores the words. Standard insertion traverses direct child references. When searching, encountering a regular character follows that single branch; encountering a `.` wildcard branches recursively across all non-null child nodes. Time is O(L) for `addWord` and O(26^L) worst-case for `search` with all dots, and space is O(N * L) for storing words.

## 63. Word Search II

[Back to Index](#index)

**Problem:** Given an `m x n` board of characters and a list of strings `words`, return all words on the board where words must be constructed from letters of sequentially adjacent cells (horizontally or vertically neighboring).

```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    private static class TrieNode {
        TrieNode[] children = new TrieNode[26];
        String word = null; // Stores word directly at leaf to avoid string building
    }

    public List<String> findWords(char[][] board, String[] words) {
        TrieNode root = new TrieNode();
        for (String w : words) {
            TrieNode node = root;
            for (char c : w.toCharArray()) {
                int index = c - 'a';
                if (node.children[index] == null) {
                    node.children[index] = new TrieNode();
                }
                node = node.children[index];
            }
            node.word = w;
        }

        List<String> result = new ArrayList<>();
        int rows = board.length, cols = board[0].length;

        for (int r = 0; r < rows; r++) {
            for (int c = 0; c < cols; c++) {
                dfs(board, r, c, root, result);
            }
        }

        return result;
    }

    private void dfs(char[][] board, int r, int c, TrieNode node, List<String> result) {
        if (r < 0 || r >= board.length || c < 0 || c >= board[0].length) {
            return;
        }

        char ch = board[r][c];
        if (ch == '#' || node.children[ch - 'a'] == null) {
            return;
        }

        node = node.children[ch - 'a'];
        if (node.word != null) {
            result.add(node.word);
            node.word = null; // Deduplicate so the word is added only once
        }

        board[r][c] = '#'; // Mark cell as visited

        dfs(board, r + 1, c, node, result);
        dfs(board, r - 1, c, node, result);
        dfs(board, r, c + 1, node, result);
        dfs(board, r, c - 1, node, result);

        board[r][c] = ch; // Backtrack
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        char[][] board = {
            {'o', 'a', 'a', 'n'},
            {'e', 't', 'a', 'e'},
            {'i', 'h', 'k', 'r'},
            {'i', 'f', 'l', 'v'}
        };
        String[] words = {"oath", "pea", "eat", "rain"};
        System.out.println(s.findWords(board, words)); // [oath, eat]
    }
}
```

**Explanation:** Building a trie from the target words allows prefix pruning during DFS exploration of the grid. Storing the word string directly at terminal nodes avoids string reconstructions and allows O(1) deduplication by setting `node.word = null` once found. Time is O(M * N * 4 * 3^(L - 1)) where M and N are grid dimensions and L is the maximum word length, and space is O(W * L) for the trie.

---

# Heap / Priority Queue

## 64. Kth Largest Element in a Stream

[Back to Index](#index)

**Problem:** Design a class to find the `k`th largest element in a stream.

```java
import java.util.PriorityQueue;

class Solution {
    static class KthLargest {
        private final PriorityQueue<Integer> minHeap;
        private final int k;

        public KthLargest(int k, int[] nums) {
            this.k = k;
            this.minHeap = new PriorityQueue<>(k);
            for (int num : nums) {
                add(num);
            }
        }

        public int add(int val) {
            minHeap.offer(val);
            if (minHeap.size() > k) {
                minHeap.poll();
            }
            return minHeap.peek();
        }
    }

    public static void main(String[] args) {
        KthLargest kthLargest = new KthLargest(3, new int[]{4, 5, 8, 2});
        System.out.println(kthLargest.add(3));  // 4
        System.out.println(kthLargest.add(5));  // 5
        System.out.println(kthLargest.add(10)); // 5
        System.out.println(kthLargest.add(9));  // 8
        System.out.println(kthLargest.add(4));  // 8
    }
}
```

**Explanation:** Maintain a min-heap bounded at size `k`. The root of the min-heap always holds the smallest among the top `k` elements seen so far, which is precisely the `k`th largest element. Time is O(N log k) for initialization and O(log k) per `add` call, and space is O(k).

## 65. Last Stone Weight

[Back to Index](#index)

**Problem:** You are given an array of integers `stones` where `stones[i]` is the weight of the `i`th stone. Each turn, the two heaviest stones `x` and `y` (`x <= y`) are smashed together. If `x == y`, both stones are destroyed. If `x != y`, stone `x` is destroyed and stone `y` has new weight `y - x`. Return the weight of the last remaining stone, or 0 if none remain.

```java
import java.util.Collections;
import java.util.PriorityQueue;

class Solution {
    public int lastStoneWeight(int[] stones) {
        PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder());
        for (int stone : stones) {
            maxHeap.offer(stone);
        }

        while (maxHeap.size() > 1) {
            int y = maxHeap.poll();
            int x = maxHeap.poll();
            if (y != x) {
                maxHeap.offer(y - x);
            }
        }

        return maxHeap.isEmpty() ? 0 : maxHeap.peek();
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.lastStoneWeight(new int[]{2, 7, 4, 1, 8, 1})); // 1
        System.out.println(s.lastStoneWeight(new int[]{1}));                // 1
    }
}
```

**Explanation:** A max-heap keeps stones sorted so the two heaviest stones can be retrieved in O(log N) time each round. After smashing, if there is a remainder, it is pushed back into the heap until at most one stone is left. Time is O(N log N) and space is O(N).

## 66. K Closest Points to Origin

[Back to Index](#index)

**Problem:** Given an array of points where `points[i] = [xi, yi]` represents a point on the X-Y plane and an integer `k`, return the `k` closest points to the origin `(0, 0)`.

```java
import java.util.Arrays;
import java.util.PriorityQueue;

class Solution {
    public int[][] kClosest(int[][] points, int k) {
        // Max-heap storing points by Euclidean distance squared descending
        PriorityQueue<int[]> maxHeap = new PriorityQueue<>(
            (a, b) -> Integer.compare(b[0] * b[0] + b[1] * b[1], a[0] * a[0] + a[1] * a[1])
        );

        for (int[] point : points) {
            maxHeap.offer(point);
            if (maxHeap.size() > k) {
                maxHeap.poll();
            }
        }

        int[][] result = new int[k][2];
        for (int i = 0; i < k; i++) {
            result[i] = maxHeap.poll();
        }
        return result;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[][] pts1 = {{1, 3}, {-2, 2}};
        System.out.println(Arrays.deepToString(s.kClosest(pts1, 1))); // [[-2, 2]]

        int[][] pts2 = {{3, 3}, {5, -1}, {-2, 4}};
        System.out.println(Arrays.deepToString(s.kClosest(pts2, 2))); // [[3, 3], [-2, 4]]
    }
}
```

**Explanation:** A max-heap of capacity `k` tracks the `k` points closest to the origin. If the heap size exceeds `k`, the farthest point among the current `k + 1` elements is removed from the root. Time is O(N log k) and space is O(k).

## 67. Kth Largest Element in an Array

[Back to Index](#index)

**Problem:** Given an integer array `nums` and an integer `k`, return the `k`th largest element in the array without sorting.

```java
import java.util.PriorityQueue;

class Solution {
    public int findKthLargest(int[] nums, int k) {
        PriorityQueue<Integer> minHeap = new PriorityQueue<>(k);

        for (int num : nums) {
            minHeap.offer(num);
            if (minHeap.size() > k) {
                minHeap.poll();
            }
        }

        return minHeap.peek();
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.findKthLargest(new int[]{3, 2, 1, 5, 6, 4}, 2));          // 5
        System.out.println(s.findKthLargest(new int[]{3, 2, 3, 1, 2, 4, 5, 5, 6}, 4)); // 4
    }
}
```

**Explanation:** Maintaining a min-heap of size `k` ensures that after examining all numbers, the root contains the smallest of the `k` largest values, which is the `k`th largest overall. Time is O(N log k) and space is O(k).


## 68. Task Scheduler

[Back to Index](#index)

**Problem:** Given a characters array `tasks` representing tasks a CPU needs to do and an integer cooldown period `n` between two identical tasks, return the minimum number of CPU intervals needed to finish all tasks.

```java
class Solution {
    public int leastInterval(char[] tasks, int n) {
        int[] freq = new int[26];
        int maxFreq = 0;
        for (char c : tasks) {
            freq[c - 'A']++;
            maxFreq = Math.max(maxFreq, freq[c - 'A']);
        }

        int countMaxFreq = 0;
        for (int f : freq) {
            if (f == maxFreq) {
                countMaxFreq++;
            }
        }

        // Formula for slots needed based on the most frequent task(s)
        int intervals = (maxFreq - 1) * (n + 1) + countMaxFreq;
        return Math.max(tasks.length, intervals);
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.leastInterval(new char[]{'A', 'A', 'A', 'B', 'B', 'B'}, 2)); // 8
        System.out.println(s.leastInterval(new char[]{'A', 'A', 'A', 'B', 'B', 'B'}, 0)); // 6
        System.out.println(s.leastInterval(new char[]{'A', 'A', 'A', 'A', 'A', 'A', 'B', 'C', 'D', 'E', 'F', 'G'}, 2)); // 16
    }
}
```

**Explanation:** The schedule length is bottlenecked by the task(s) with the maximum frequency `maxFreq`. Placing them requires `maxFreq - 1` blocks of size `n + 1`, followed by the final instances of all tasks tied for `maxFreq`. If the total number of tasks exceeds this idle-filled frame, no idle time is needed and the answer is `tasks.length`. Time is O(N) where N is the number of tasks, and space is O(1) for the 26-element array.

## 69. Design Twitter

[Back to Index](#index)

**Problem:** Design a simplified Twitter service supporting posting tweets, following/unfollowing users, and retrieving the 10 most recent tweets in a user's news feed.

```java
import java.util.*;

class Solution {
    static class Twitter {
        private static int timestamp = 0;

        private static class Tweet {
            int id;
            int time;
            Tweet next;

            Tweet(int id, int time) {
                this.id = id;
                this.time = time;
                this.next = null;
            }
        }

        private static class User {
            int id;
            Set<Integer> followed;
            Tweet tweetHead;

            User(int id) {
                this.id = id;
                this.followed = new HashSet<>();
                follow(id); // Follow self so self's tweets appear in feed
                this.tweetHead = null;
            }

            void follow(int id) {
                followed.add(id);
            }

            void unfollow(int id) {
                if (id != this.id) { // Cannot unfollow self
                    followed.remove(id);
                }
            }

            void post(int id) {
                Tweet tweet = new Tweet(id, timestamp++);
                tweet.next = tweetHead;
                tweetHead = tweet;
            }
        }

        private final Map<Integer, User> userMap;

        public Twitter() {
            userMap = new HashMap<>();
        }

        public void postTweet(int userId, int tweetId) {
            userMap.computeIfAbsent(userId, User::new).post(tweetId);
        }

        public List<Integer> getNewsFeed(int userId) {
            List<Integer> feed = new ArrayList<>();
            if (!userMap.containsKey(userId)) {
                return feed;
            }

            Set<Integer> followed = userMap.get(userId).followed;
            // Max-heap comparing tweets by global timestamp
            PriorityQueue<Tweet> maxHeap = new PriorityQueue<>((a, b) -> Integer.compare(b.time, a.time));

            for (int followeeId : followed) {
                User followee = userMap.get(followeeId);
                if (followee != null && followee.tweetHead != null) {
                    maxHeap.offer(followee.tweetHead);
                }
            }

            int count = 0;
            while (!maxHeap.isEmpty() && count < 10) {
                Tweet top = maxHeap.poll();
                feed.add(top.id);
                count++;
                if (top.next != null) {
                    maxHeap.offer(top.next);
                }
            }

            return feed;
        }

        public void follow(int followerId, int followeeId) {
            userMap.computeIfAbsent(followerId, User::new);
            userMap.computeIfAbsent(followeeId, User::new);
            userMap.get(followerId).follow(followeeId);
        }

        public void unfollow(int followerId, int followeeId) {
            if (userMap.containsKey(followerId) && followerId != followeeId) {
                userMap.get(followerId).unfollow(followeeId);
            }
        }
    }

    public static void main(String[] args) {
        Twitter twitter = new Twitter();
        twitter.postTweet(1, 5);
        System.out.println(twitter.getNewsFeed(1)); // [5]
        twitter.follow(1, 2);
        twitter.postTweet(2, 6);
        System.out.println(twitter.getNewsFeed(1)); // [6, 5]
        twitter.unfollow(1, 2);
        System.out.println(twitter.getNewsFeed(1)); // [5]
    }
}
```

**Explanation:** Each user maintains a singly-linked list of their tweets (latest first) and a set of followees. Generating the news feed merges the linked lists of all followees using a max-heap of size at most the number of followees, pulling up to 10 most recent tweets. Time is O(1) for `postTweet`, `follow`, and `unfollow`, and O(K log K) for `getNewsFeed` where K is the number of followed users. Space is O(U + T) where U is total users and T is total tweets.

## 70. Find Median from Data Stream

[Back to Index](#index)

**Problem:** Design a data structure that supports adding integer numbers from a data stream and finding the median of all elements seen so far.

```java
import java.util.Collections;
import java.util.PriorityQueue;

class Solution {
    static class MedianFinder {
        // Max-heap stores the smaller half of numbers
        private final PriorityQueue<Integer> small;
        // Min-heap stores the larger half of numbers
        private final PriorityQueue<Integer> large;

        public MedianFinder() {
            small = new PriorityQueue<>(Collections.reverseOrder());
            large = new PriorityQueue<>();
        }

        public void addNum(int num) {
            small.offer(num);
            large.offer(small.poll());

            // Balance heaps so small.size() == large.size() or small.size() == large.size() + 1
            if (large.size() > small.size()) {
                small.offer(large.poll());
            }
        }

        public double findMedian() {
            if (small.size() > large.size()) {
                return small.peek();
            }
            return (small.peek() + large.peek()) / 2.0;
        }
    }

    public static void main(String[] args) {
        MedianFinder mf = new MedianFinder();
        mf.addNum(1);
        mf.addNum(2);
        System.out.println(mf.findMedian()); // 1.5
        mf.addNum(3);
        System.out.println(mf.findMedian()); // 2.0
    }
}
```

**Explanation:** Two heaps maintain the stream partitioned into two equal (or balanced by 1) halves. The max-heap holds the smaller half, while the min-heap holds the larger half. The median is either the top of the max-heap (if odd count) or the average of both heap roots (if even count). Time is O(log N) for `addNum` and O(1) for `findMedian`, and space is O(N).

---

# Backtracking

## 71. Subsets

[Back to Index](#index)

**Problem:** Given an integer array `nums` of unique elements, return all possible subsets (the power set) without duplicate subsets.

```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> result = new ArrayList<>();
        backtrack(nums, 0, new ArrayList<>(), result);
        return result;
    }

    private void backtrack(int[] nums, int start, List<Integer> current, List<List<Integer>> result) {
        result.add(new ArrayList<>(current));

        for (int i = start; i < nums.length; i++) {
            current.add(nums[i]);
            backtrack(nums, i + 1, current, result);
            current.remove(current.size() - 1);
        }
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.subsets(new int[]{1, 2, 3})); 
        // [[], [1], [1, 2], [1, 2, 3], [1, 3], [2], [2, 3], [3]]
    }
}
```

**Explanation:** At each decision point, include the current number in the subset, recursively explore further elements starting at index `i + 1`, and then backtrack by removing the element. Each unique combination visited is copied into the result. Time is O(N * 2^N) and space is O(N) recursion stack space.

## 72. Combination Sum

[Back to Index](#index)

**Problem:** Given an array of distinct integers `candidates` and a target integer `target`, return all unique combinations of `candidates` where the chosen numbers sum to `target`. Each number may be used an unlimited number of times.

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

class Solution {
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        List<List<Integer>> result = new ArrayList<>();
        Arrays.sort(candidates);
        backtrack(candidates, target, 0, new ArrayList<>(), result);
        return result;
    }

    private void backtrack(int[] candidates, int remain, int start, List<Integer> current, List<List<Integer>> result) {
        if (remain == 0) {
            result.add(new ArrayList<>(current));
            return;
        }

        for (int i = start; i < candidates.length; i++) {
            if (candidates[i] > remain) {
                break; // Array is sorted, so subsequent candidates are even larger
            }
            current.add(candidates[i]);
            // Stay at index i since the same element can be reused
            backtrack(candidates, remain - candidates[i], i, current, result);
            current.remove(current.size() - 1);
        }
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.combinationSum(new int[]{2, 3, 6, 7}, 7)); // [[2, 2, 3], [7]]
        System.out.println(s.combinationSum(new int[]{2, 3, 5}, 8));    // [[2, 2, 2, 2], [2, 3, 3], [3, 5]]
    }
}
```

**Explanation:** Sort candidates first to enable early pruning when candidate value exceeds the remaining target. Passing the same index `i` into the recursive call allows unlimited reuse of the candidate while preventing duplicate permutations. Time is O(2^(target / min_candidate)) and space is O(target / min_candidate) for recursion depth.

## 73. Permutations

[Back to Index](#index)

**Problem:** Given an array `nums` of distinct integers, return all the possible permutations.

```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> result = new ArrayList<>();
        boolean[] used = new boolean[nums.length];
        backtrack(nums, used, new ArrayList<>(), result);
        return result;
    }

    private void backtrack(int[] nums, boolean[] used, List<Integer> current, List<List<Integer>> result) {
        if (current.size() == nums.length) {
            result.add(new ArrayList<>(current));
            return;
        }

        for (int i = 0; i < nums.length; i++) {
            if (used[i]) {
                continue;
            }
            used[i] = true;
            current.add(nums[i]);
            backtrack(nums, used, current, result);
            current.remove(current.size() - 1);
            used[i] = false;
        }
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.permute(new int[]{1, 2, 3})); 
        // [[1, 2, 3], [1, 3, 2], [2, 1, 3], [2, 3, 1], [3, 1, 2], [3, 2, 1]]
    }
}
```

**Explanation:** Use a boolean `used` array to track which elements are already part of the current permutation. Try every unused number at each step, recurse until all numbers are chosen, and then backtrack. Time is O(N * N!) and space is O(N) recursion stack.

## 74. Subsets II

[Back to Index](#index)

**Problem:** Given an integer array `nums` that may contain duplicates, return all possible subsets (the power set) without duplicate subsets.

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

class Solution {
    public List<List<Integer>> subsetsWithDup(int[] nums) {
        List<List<Integer>> result = new ArrayList<>();
        Arrays.sort(nums);
        backtrack(nums, 0, new ArrayList<>(), result);
        return result;
    }

    private void backtrack(int[] nums, int start, List<Integer> current, List<List<Integer>> result) {
        result.add(new ArrayList<>(current));

        for (int i = start; i < nums.length; i++) {
            // Skip duplicate values at the same recursive level
            if (i > start && nums[i] == nums[i - 1]) {
                continue;
            }
            current.add(nums[i]);
            backtrack(nums, i + 1, current, result);
            current.remove(current.size() - 1);
        }
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.subsetsWithDup(new int[]{1, 2, 2})); 
        // [[], [1], [1, 2], [1, 2, 2], [2], [2, 2]]
    }
}
```

**Explanation:** Sorting groups identical numbers adjacent to each other. Whenever `i > start` and `nums[i] == nums[i - 1]`, skipping the element prevents generating identical subsets at the same tree depth while still allowing duplicate numbers to appear across deeper recursive calls. Time is O(N * 2^N) and space is O(N) recursion stack.


## 75. Combination Sum II

[Back to Index](#index)

**Problem:** Given a collection of candidate numbers `candidates` and a target number `target`, find all unique combinations in `candidates` where the candidate numbers sum to `target`. Each number in `candidates` may only be used once in the combination, and the solution must not contain duplicate combinations.

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

class Solution {
    public List<List<Integer>> combinationSum2(int[] candidates, int target) {
        List<List<Integer>> result = new ArrayList<>();
        Arrays.sort(candidates);
        backtrack(candidates, target, 0, new ArrayList<>(), result);
        return result;
    }

    private void backtrack(int[] candidates, int remain, int start, List<Integer> current, List<List<Integer>> result) {
        if (remain == 0) {
            result.add(new ArrayList<>(current));
            return;
        }

        for (int i = start; i < candidates.length; i++) {
            if (candidates[i] > remain) {
                break; // Candidates are sorted; remaining items will also exceed
            }
            // Skip duplicate candidate at same decision level
            if (i > start && candidates[i] == candidates[i - 1]) {
                continue;
            }
            current.add(candidates[i]);
            backtrack(candidates, remain - candidates[i], i + 1, current, result);
            current.remove(current.size() - 1);
        }
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.combinationSum2(new int[]{10, 1, 2, 7, 6, 1, 5}, 8)); 
        // [[1, 1, 6], [1, 2, 5], [1, 7], [2, 6]]
        System.out.println(s.combinationSum2(new int[]{2, 5, 2, 1, 2}, 5)); 
        // [[1, 2, 2], [5]]
    }
}
```

**Explanation:** Sorting groups identical numbers and allows early pruning when candidate value exceeds the remaining target. Passing `i + 1` ensures each candidate index is used at most once, and skipping `candidates[i] == candidates[i - 1]` for `i > start` eliminates identical combination branches. Time is O(2^N) and space is O(N) recursion stack.

## 76. Word Search

[Back to Index](#index)

**Problem:** Given an `m x n` grid of characters `board` and a string `word`, return `true` if `word` exists in the grid constructed from sequentially adjacent cells without reusing any cell.

```java
class Solution {
    public boolean exist(char[][] board, String word) {
        int rows = board.length;
        int cols = board[0].length;

        for (int r = 0; r < rows; r++) {
            for (int c = 0; c < cols; c++) {
                if (dfs(board, word, r, c, 0)) {
                    return true;
                }
            }
        }
        return false;
    }

    private boolean dfs(char[][] board, String word, int r, int c, int index) {
        if (index == word.length()) {
            return true;
        }
        if (r < 0 || r >= board.length || c < 0 || c >= board[0].length || board[r][c] != word.charAt(index)) {
            return false;
        }

        char temp = board[r][c];
        board[r][c] = '#'; // Mark cell as visited

        boolean found = dfs(board, word, r + 1, c, index + 1)
                     || dfs(board, word, r - 1, c, index + 1)
                     || dfs(board, word, r, c + 1, index + 1)
                     || dfs(board, word, r, c - 1, index + 1);

        board[r][c] = temp; // Backtrack
        return found;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        char[][] board = {
            {'A', 'B', 'C', 'E'},
            {'S', 'F', 'C', 'S'},
            {'A', 'D', 'E', 'E'}
        };
        System.out.println(s.exist(board, "ABCCED")); // true
        System.out.println(s.exist(board, "SEE"));    // true
        System.out.println(s.exist(board, "ABCB"));   // false
    }
}
```

**Explanation:** Depth-first search traverses from each cell matching the first letter. In-place modification (`'#'`) avoids extra memory for visited tracking and gets restored on backtrack. Time is O(M * N * 3^L) where L is the length of `word` (3 branches because we never move backward to the cell we just came from), and space is O(L) for the recursion stack.

## 77. Palindrome Partitioning

[Back to Index](#index)

**Problem:** Given a string `s`, partition `s` such that every substring of the partition is a palindrome. Return all possible palindrome partitionings of `s`.

```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public List<List<String>> partition(String s) {
        List<List<String>> result = new ArrayList<>();
        backtrack(s, 0, new ArrayList<>(), result);
        return result;
    }

    private void backtrack(String s, int start, List<String> current, List<List<String>> result) {
        if (start == s.length()) {
            result.add(new ArrayList<>(current));
            return;
        }

        for (int end = start; end < s.length(); end++) {
            if (isPalindrome(s, start, end)) {
                current.add(s.substring(start, end + 1));
                backtrack(s, end + 1, current, result);
                current.remove(current.size() - 1);
            }
        }
    }

    private boolean isPalindrome(String s, int left, int right) {
        while (left < right) {
            if (s.charAt(left++) != s.charAt(right--)) {
                return false;
            }
        }
        return true;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.partition("aab")); // [[a, a, b], [aa, b]]
        System.out.println(s.partition("a"));   // [[a]]
    }
}
```

**Explanation:** At each index `start`, examine every prefix substring `s[start...end]`. If it is a palindrome, add it to the path and recursively partition the remainder `s[end + 1...]`, backtracking afterwards. Time is O(N * 2^N) and space is O(N) recursion stack.

## 78. Letter Combinations of a Phone Number

[Back to Index](#index)

**Problem:** Given a string containing digits from `2-9` inclusive, return all possible letter combinations that the number could represent based on classic telephone keypad buttons.

```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    private static final String[] KEYPAD = {
        "",     // 0
        "",     // 1
        "abc",  // 2
        "def",  // 3
        "ghi",  // 4
        "jkl",  // 5
        "mno",  // 6
        "pqrs", // 7
        "tuv",  // 8
        "wxyz"  // 9
    };

    public List<String> letterCombinations(String digits) {
        List<String> result = new ArrayList<>();
        if (digits == null || digits.isEmpty()) {
            return result;
        }
        backtrack(digits, 0, new StringBuilder(), result);
        return result;
    }

    private void backtrack(String digits, int index, StringBuilder current, List<String> result) {
        if (index == digits.length()) {
            result.add(current.toString());
            return;
        }

        String letters = KEYPAD[digits.charAt(index) - '0'];
        for (char c : letters.toCharArray()) {
            current.append(c);
            backtrack(digits, index + 1, current, result);
            current.deleteCharAt(current.length() - 1);
        }
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.letterCombinations("23")); // [ad, ae, af, bd, be, bf, cd, ce, cf]
        System.out.println(s.letterCombinations(""));   // []
        System.out.println(s.letterCombinations("2"));  // [a, b, c]
    }
}
```

**Explanation:** Digits are mapped to character sets via a lookup array. A recursive DFS explores each possible letter for the current digit, advancing index by 1 until the combination reaches the input length. Time is O(4^N * N) where N is the length of digits (since keys 7 and 9 have 4 letters), and space is O(N) recursion stack.

## 79. N-Queens

[Back to Index](#index)

**Problem:** Place `n` queens on an `n x n` chessboard such that no two queens attack each other, returning all distinct board configurations.

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.HashSet;
import java.util.List;
import java.util.Set;

class Solution {
    public List<List<String>> solveNQueens(int n) {
        List<List<String>> result = new ArrayList<>();
        char[][] board = new char[n][n];
        for (char[] row : board) {
            Arrays.fill(row, '.');
        }

        Set<Integer> cols = new HashSet<>();
        Set<Integer> posDiag = new HashSet<>(); // r + c
        Set<Integer> negDiag = new HashSet<>(); // r - c

        backtrack(0, n, board, cols, posDiag, negDiag, result);
        return result;
    }

    private void backtrack(int r, int n, char[][] board,
                           Set<Integer> cols, Set<Integer> posDiag, Set<Integer> negDiag,
                           List<List<String>> result) {
        if (r == n) {
            List<String> configuration = new ArrayList<>();
            for (char[] row : board) {
                configuration.add(new String(row));
            }
            result.add(configuration);
            return;
        }

        for (int c = 0; c < n; c++) {
            if (cols.contains(c) || posDiag.contains(r + c) || negDiag.contains(r - c)) {
                continue;
            }

            board[r][c] = 'Q';
            cols.add(c);
            posDiag.add(r + c);
            negDiag.add(r - c);

            backtrack(r + 1, n, board, cols, posDiag, negDiag, result);

            board[r][c] = '.';
            cols.remove(c);
            posDiag.remove(r + c);
            negDiag.remove(r - c);
        }
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        List<List<String>> res = s.solveNQueens(4);
        System.out.println("Solutions count: " + res.size());
        for (List<String> board : res) {
            System.out.println(board);
        }
    }
}
```

**Explanation:** Place queens row by row. Conflicting placements are pruned in O(1) time using hash sets for columns (`c`), positive diagonals (`r + c`), and negative diagonals (`r - c`). Once row reaches `n`, a valid placement is formatted and stored. Time is O(N!) and space is O(N) for sets and board recursion.

---

# Graphs

## 80. Number of Islands

[Back to Index](#index)

**Problem:** Given an `m x n` 2D binary grid `grid` which represents a map of `'1'`s (land) and `'0'`s (water), return the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically.

```java
import java.util.*;

class Solution {
    public int numIslands(char[][] grid) {
        if (grid == null || grid.length == 0) return 0;
        int m = grid.length, n = grid[0].length;
        int count = 0;

        for (int r = 0; r < m; r++) {
            for (int c = 0; c < n; c++) {
                if (grid[r][c] == '1') {
                    count++;
                    dfs(grid, r, c);
                }
            }
        }
        return count;
    }

    private void dfs(char[][] grid, int r, int c) {
        if (r < 0 || r >= grid.length || c < 0 || c >= grid[0].length || grid[r][c] != '1') {
            return;
        }
        grid[r][c] = '0'; // mark visited
        dfs(grid, r + 1, c);
        dfs(grid, r - 1, c);
        dfs(grid, r, c + 1);
        dfs(grid, r, c - 1);
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        char[][] grid = {
            {'1', '1', '1', '1', '0'},
            {'1', '1', '0', '1', '0'},
            {'1', '1', '0', '0', '0'},
            {'0', '0', '0', '0', '0'}
        };
        System.out.println(s.numIslands(grid)); // Expected: 1
    }
}
```

**Explanation:** Traverse the grid and launch a depth-first search (DFS) whenever an unvisited land cell `'1'` is found, incrementing the island counter and sinking connected land cells by flipping them to `'0'`. Time is O(m * n) and space is O(m * n) for the recursion stack in the worst case.

## 81. Clone Graph

[Back to Index](#index)

**Problem:** Given a reference of a node in a connected undirected graph, return a deep copy (clone) of the graph. Each node in the graph contains a value (`val`) and a list of its neighbors (`List<Node>`).

```java
import java.util.*;

class Solution {
    static class Node {
        public int val;
        public List<Node> neighbors;
        public Node() {
            val = 0;
            neighbors = new ArrayList<>();
        }
        public Node(int _val) {
            val = _val;
            neighbors = new ArrayList<>();
        }
        public Node(int _val, ArrayList<Node> _neighbors) {
            val = _val;
            neighbors = _neighbors;
        }
    }

    private Map<Node, Node> visited = new HashMap<>();

    public Node cloneGraph(Node node) {
        if (node == null) return null;
        if (visited.containsKey(node)) {
            return visited.get(node);
        }

        Node cloneNode = new Node(node.val);
        visited.put(node, cloneNode);

        for (Node neighbor : node.neighbors) {
            cloneNode.neighbors.add(cloneGraph(neighbor));
        }

        return cloneNode;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        Node node1 = new Node(1);
        Node node2 = new Node(2);
        Node node3 = new Node(3);
        Node node4 = new Node(4);
        node1.neighbors.add(node2);
        node1.neighbors.add(node4);
        node2.neighbors.add(node1);
        node2.neighbors.add(node3);
        node3.neighbors.add(node2);
        node3.neighbors.add(node4);
        node4.neighbors.add(node1);
        node4.neighbors.add(node3);

        Node cloned = s.cloneGraph(node1);
        System.out.println(cloned.val + " with " + cloned.neighbors.size() + " neighbors"); // Expected: 1 with 2 neighbors
    }
}
```

**Explanation:** Use depth-first search along with a hash map mapping each original node to its cloned copy to prevent infinite loops from graph cycles and reconstruct neighbor connections recursively. Time is O(V + E) and space is O(V) for the hash map and call stack.

## 82. Max Area of Island

[Back to Index](#index)

**Problem:** Given an `m x n` binary matrix `grid`, an island is a group of `1`'s (representing land) connected 4-directionally. Return the maximum area of an island in `grid`. If there is no island, return `0`.

```java
import java.util.*;

class Solution {
    public int maxAreaOfIsland(int[][] grid) {
        if (grid == null || grid.length == 0) return 0;
        int m = grid.length, n = grid[0].length;
        int maxArea = 0;

        for (int r = 0; r < m; r++) {
            for (int c = 0; c < n; c++) {
                if (grid[r][c] == 1) {
                    maxArea = Math.max(maxArea, dfs(grid, r, c));
                }
            }
        }
        return maxArea;
    }

    private int dfs(int[][] grid, int r, int c) {
        if (r < 0 || r >= grid.length || c < 0 || c >= grid[0].length || grid[r][c] != 1) {
            return 0;
        }
        grid[r][c] = 0; // mark visited
        return 1 + dfs(grid, r + 1, c) + dfs(grid, r - 1, c) + dfs(grid, r, c + 1) + dfs(grid, r, c - 1);
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[][] grid = {
            {0, 0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0},
            {0, 0, 0, 0, 0, 0, 0, 1, 1, 1, 0, 0, 0},
            {0, 1, 1, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0},
            {0, 1, 0, 0, 1, 1, 0, 0, 1, 0, 1, 0, 0},
            {0, 1, 0, 0, 1, 1, 0, 0, 1, 1, 1, 0, 0},
            {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0},
            {0, 0, 0, 0, 0, 0, 0, 1, 1, 1, 0, 0, 0},
            {0, 0, 0, 0, 0, 0, 0, 1, 1, 0, 0, 0, 0}
        };
        System.out.println(s.maxAreaOfIsland(grid)); // Expected: 6
    }
}
```

**Explanation:** Iterate through each cell and perform DFS on discovering land (`1`), computing the island's area by recursively summing connected land tiles while resetting visited cells to `0`. Time is O(m * n) and space is O(m * n) for the recursion stack.

## 83. Pacific Atlantic Water Flow

[Back to Index](#index)

**Problem:** Given an `m x n` matrix of non-negative integers `heights` representing the height of each unit cell in a continent, water can flow from any cell adjacent to the Pacific Ocean (top and left borders) into the Pacific, and adjacent to the Atlantic Ocean (bottom and right borders) into the Atlantic. Water flows to neighboring cells directly north, south, east, and west if the neighboring cell's height is less than or equal to the current cell's height. Return a list of grid coordinates `[r, c]` where water can flow to both oceans.

```java
import java.util.*;

class Solution {
    public List<List<Integer>> pacificAtlantic(int[][] heights) {
        List<List<Integer>> result = new ArrayList<>();
        if (heights == null || heights.length == 0 || heights[0].length == 0) return result;

        int m = heights.length, n = heights[0].length;
        boolean[][] pacific = new boolean[m][n];
        boolean[][] atlantic = new boolean[m][n];

        for (int r = 0; r < m; r++) {
            dfs(heights, pacific, r, 0, heights[r][0]);
            dfs(heights, atlantic, r, n - 1, heights[r][n - 1]);
        }
        for (int c = 0; c < n; c++) {
            dfs(heights, pacific, 0, c, heights[0][c]);
            dfs(heights, atlantic, m - 1, c, heights[m - 1][c]);
        }

        for (int r = 0; r < m; r++) {
            for (int c = 0; c < n; c++) {
                if (pacific[r][c] && atlantic[r][c]) {
                    result.add(Arrays.asList(r, c));
                }
            }
        }
        return result;
    }

    private void dfs(int[][] heights, boolean[][] ocean, int r, int c, int prevHeight) {
        if (r < 0 || r >= heights.length || c < 0 || c >= heights[0].length) return;
        if (ocean[r][c] || heights[r][c] < prevHeight) return;

        ocean[r][c] = true;
        int[][] dirs = {{1, 0}, {-1, 0}, {0, 1}, {0, -1}};
        for (int[] d : dirs) {
            dfs(heights, ocean, r + d[0], c + d[1], heights[r][c]);
        }
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[][] heights = {
            {1, 2, 2, 3, 5},
            {3, 2, 3, 4, 4},
            {2, 4, 5, 3, 1},
            {6, 7, 1, 4, 5},
            {5, 1, 1, 2, 4}
        };
        System.out.println(s.pacificAtlantic(heights));
        // Expected: [[0, 4], [1, 3], [1, 4], [2, 2], [3, 0], [3, 1], [4, 0]]
    }
}
```

**Explanation:** Instead of checking water flow from every cell to oceans, reverse the flow and use DFS starting from the Pacific and Atlantic borders inward toward cells of equal or greater height. Coordinates reachable from both oceans form the result. Time is O(m * n) and space is O(m * n).

## 84. Surrounded Regions

[Back to Index](#index)

**Problem:** Given an `m x n` matrix `board` containing `'X'` and `'O'`, capture all regions that are 4-directionally surrounded by `'X'`. A region is captured by flipping all `'O'`s into `'X'`s in that surrounded region. Any `'O'` connected to the boundary is not captured.

```java
import java.util.*;

class Solution {
    public void solve(char[][] board) {
        if (board == null || board.length == 0 || board[0].length == 0) return;
        int m = board.length, n = board[0].length;

        for (int r = 0; r < m; r++) {
            if (board[r][0] == 'O') dfs(board, r, 0);
            if (board[r][n - 1] == 'O') dfs(board, r, n - 1);
        }
        for (int c = 0; c < n; c++) {
            if (board[0][c] == 'O') dfs(board, 0, c);
            if (board[m - 1][c] == 'O') dfs(board, m - 1, c);
        }

        for (int r = 0; r < m; r++) {
            for (int c = 0; c < n; c++) {
                if (board[r][c] == 'O') {
                    board[r][c] = 'X';
                } else if (board[r][c] == 'T') {
                    board[r][c] = 'O';
                }
            }
        }
    }

    private void dfs(char[][] board, int r, int c) {
        if (r < 0 || r >= board.length || c < 0 || c >= board[0].length || board[r][c] != 'O') {
            return;
        }
        board[r][c] = 'T'; // Mark connected border region as temporary safe
        dfs(board, r + 1, c);
        dfs(board, r - 1, c);
        dfs(board, r, c + 1);
        dfs(board, r, c - 1);
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        char[][] board = {
            {'X', 'X', 'X', 'X'},
            {'X', 'O', 'O', 'X'},
            {'X', 'X', 'O', 'X'},
            {'X', 'O', 'X', 'X'}
        };
        s.solve(board);
        System.out.println(Arrays.deepToString(board));
        // Expected: [[X, X, X, X], [X, X, X, X], [X, X, X, X], [X, O, X, X]]
    }
}
```

**Explanation:** Run DFS starting from all boundary `'O'` cells to mark non-surrounded regions with a temporary symbol `'T'`. Then traverse the grid, changing all remaining `'O'`s to `'X'` and converting `'T'`s back to `'O'`. Time is O(m * n) and space is O(m * n).

## 85. Rotting Oranges

[Back to Index](#index)

**Problem:** You are given an `m x n` grid where each cell can have one of three values: `0` representing an empty cell, `1` representing a fresh orange, or `2` representing a rotten orange. Every minute, any fresh orange 4-directionally adjacent to a rotten orange becomes rotten. Return the minimum number of minutes that must elapse until no cell has a fresh orange, or `-1` if impossible.

```java
import java.util.*;

class Solution {
    public int orangesRotting(int[][] grid) {
        if (grid == null || grid.length == 0) return 0;
        int m = grid.length, n = grid[0].length;
        Queue<int[]> queue = new LinkedList<>();
        int freshCount = 0;

        for (int r = 0; r < m; r++) {
            for (int c = 0; c < n; c++) {
                if (grid[r][c] == 2) {
                    queue.offer(new int[]{r, c});
                } else if (grid[r][c] == 1) {
                    freshCount++;
                }
            }
        }

        if (freshCount == 0) return 0;
        int minutes = 0;
        int[][] dirs = {{1, 0}, {-1, 0}, {0, 1}, {0, -1}};

        while (!queue.isEmpty() && freshCount > 0) {
            int size = queue.size();
            for (int i = 0; i < size; i++) {
                int[] curr = queue.poll();
                int r = curr[0], c = curr[1];
                for (int[] d : dirs) {
                    int nr = r + d[0], nc = c + d[1];
                    if (nr >= 0 && nr < m && nc >= 0 && nc < n && grid[nr][nc] == 1) {
                        grid[nr][nc] = 2;
                        freshCount--;
                        queue.offer(new int[]{nr, nc});
                    }
                }
            }
            minutes++;
        }

        return freshCount == 0 ? minutes : -1;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[][] grid = {
            {2, 1, 1},
            {1, 1, 0},
            {0, 1, 1}
        };
        System.out.println(s.orangesRotting(grid)); // Expected: 4
    }
}
```

**Explanation:** Multi-source breadth-first search (BFS) starting with all initially rotten oranges in a queue. Each level of the BFS corresponds to one minute of rotting spreading to adjacent fresh oranges. Time is O(m * n) and space is O(m * n).

## 86. Walls and Gates

[Back to Index](#index)

**Problem:** You are given an `m x n` grid initialized with `-1` (a wall or obstacle), `0` (a gate), and `2147483647` / `INF` (an empty room). Fill each empty room with the distance to its nearest gate. If it is impossible to reach a gate, leave it as `INF`.

```java
import java.util.*;

class Solution {
    public void wallsAndGates(int[][] rooms) {
        if (rooms == null || rooms.length == 0) return;
        int m = rooms.length, n = rooms[0].length;
        Queue<int[]> queue = new LinkedList<>();

        for (int r = 0; r < m; r++) {
            for (int c = 0; c < n; c++) {
                if (rooms[r][c] == 0) {
                    queue.offer(new int[]{r, c});
                }
            }
        }

        int[][] dirs = {{1, 0}, {-1, 0}, {0, 1}, {0, -1}};
        while (!queue.isEmpty()) {
            int[] curr = queue.poll();
            int r = curr[0], c = curr[1];

            for (int[] d : dirs) {
                int nr = r + d[0], nc = c + d[1];
                if (nr >= 0 && nr < m && nc >= 0 && nc < n && rooms[nr][nc] == 2147483647) {
                    rooms[nr][nc] = rooms[r][c] + 1;
                    queue.offer(new int[]{nr, nc});
                }
            }
        }
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int INF = 2147483647;
        int[][] rooms = {
            {INF,  -1,  0, INF},
            {INF, INF, INF,  -1},
            {INF,  -1, INF,  -1},
            {  0,  -1, INF, INF}
        };
        s.wallsAndGates(rooms);
        System.out.println(Arrays.deepToString(rooms));
        // Expected: [[3, -1, 0, 1], [2, 2, 1, -1], [1, -1, 2, -1], [0, -1, 3, 4]]
    }
}
```

**Explanation:** Initialize a multi-source BFS queue with all gate locations (`0`). Expand outward layer by layer, updating empty rooms (`INF`) with their shortest distance from any gate upon first visitation. Time is O(m * n) and space is O(m * n).


## 87. Course Schedule

[Back to Index](#index)

**Problem:** There are a total of `numCourses` courses you have to take, labeled from `0` to `numCourses - 1`. You are given an array `prerequisites` where `prerequisites[i] = [a, b]` indicates that you must take course `b` first if you want to take course `a`. Return `true` if you can finish all courses, or `false` otherwise.

```java
import java.util.*;

class Solution {
    public boolean canFinish(int numCourses, int[][] prerequisites) {
        List<List<Integer>> adj = new ArrayList<>();
        int[] inDegree = new int[numCourses];
        for (int i = 0; i < numCourses; i++) {
            adj.add(new ArrayList<>());
        }

        for (int[] pre : prerequisites) {
            adj.get(pre[1]).add(pre[0]);
            inDegree[pre[0]]++;
        }

        Queue<Integer> queue = new LinkedList<>();
        for (int i = 0; i < numCourses; i++) {
            if (inDegree[i] == 0) {
                queue.offer(i);
            }
        }

        int count = 0;
        while (!queue.isEmpty()) {
            int course = queue.poll();
            count++;

            for (int next : adj.get(course)) {
                inDegree[next]--;
                if (inDegree[next] == 0) {
                    queue.offer(next);
                }
            }
        }

        return count == numCourses;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int numCourses = 2;
        int[][] prerequisites = {{1, 0}};
        System.out.println(s.canFinish(numCourses, prerequisites)); // Expected: true
    }
}
```

**Explanation:** Kahn's algorithm for topological sorting: compute in-degrees for each course, push 0 in-degree courses into a BFS queue, and decrement neighbor in-degrees as nodes are processed. If all courses are processed, no cycle exists. Time is O(V + E) and space is O(V + E).

## 88. Course Schedule II

[Back to Index](#index)

**Problem:** There are a total of `numCourses` courses labeled from `0` to `numCourses - 1`. Given `prerequisites` where `prerequisites[i] = [a, b]`, return the ordering of courses you should take to finish all courses. If impossible, return an empty array.

```java
import java.util.*;

class Solution {
    public int[] findOrder(int numCourses, int[][] prerequisites) {
        List<List<Integer>> adj = new ArrayList<>();
        int[] inDegree = new int[numCourses];
        for (int i = 0; i < numCourses; i++) {
            adj.add(new ArrayList<>());
        }

        for (int[] pre : prerequisites) {
            adj.get(pre[1]).add(pre[0]);
            inDegree[pre[0]]++;
        }

        Queue<Integer> queue = new LinkedList<>();
        for (int i = 0; i < numCourses; i++) {
            if (inDegree[i] == 0) {
                queue.offer(i);
            }
        }

        int[] order = new int[numCourses];
        int idx = 0;
        while (!queue.isEmpty()) {
            int course = queue.poll();
            order[idx++] = course;

            for (int next : adj.get(course)) {
                inDegree[next]--;
                if (inDegree[next] == 0) {
                    queue.offer(next);
                }
            }
        }

        return idx == numCourses ? order : new int[0];
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int numCourses = 4;
        int[][] prerequisites = {{1, 0}, {2, 0}, {3, 1}, {3, 2}};
        System.out.println(Arrays.toString(s.findOrder(numCourses, prerequisites)));
        // Expected: [0, 1, 2, 3] (or [0, 2, 1, 3])
    }
}
```

**Explanation:** Extend Kahn's algorithm by appending each course with zero in-degree to an ordering array as it is dequeued. If the total number of processed courses equals `numCourses`, return the topological order; otherwise, return an empty array due to a cycle. Time is O(V + E) and space is O(V + E).

## 89. Redundant Connection

[Back to Index](#index)

**Problem:** A graph is given as a tree of `n` nodes labeled from `1` to `n`, with one additional edge added. Return an edge that can be removed so that the resulting graph is a tree of `n` nodes. If there are multiple answers, return the answer that occurs last in the input.

```java
import java.util.*;

class Solution {
    public int[] findRedundantConnection(int[][] edges) {
        int n = edges.length;
        int[] parent = new int[n + 1];
        for (int i = 1; i <= n; i++) {
            parent[i] = i;
        }

        for (int[] edge : edges) {
            int root1 = find(parent, edge[0]);
            int root2 = find(parent, edge[1]);

            if (root1 == root2) {
                return edge;
            }
            parent[root1] = root2;
        }

        return new int[0];
    }

    private int find(int[] parent, int node) {
        if (parent[node] != node) {
            parent[node] = find(parent, parent[node]); // Path compression
        }
        return parent[node];
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[][] edges = {{1, 2}, {1, 3}, {2, 3}};
        System.out.println(Arrays.toString(s.findRedundantConnection(edges))); // Expected: [2, 3]
    }
}
```

**Explanation:** Disjoint Set Union (Union-Find) with path compression: iterate through each edge, finding the roots of both endpoints. If both nodes already share the same root, adding this edge forms a cycle, so this edge is the redundant connection. Time is O(n * α(n)) ≈ O(n) and space is O(n).

## 90. Number of Connected Components in an Undirected Graph

[Back to Index](#index)

**Problem:** You have a graph of `n` nodes labeled from `0` to `n - 1`. You are given an integer `n` and an array `edges` where `edges[i] = [a, b]` indicates an edge between `a` and `b`. Return the number of connected components in the graph.

```java
import java.util.*;

class Solution {
    public int countComponents(int n, int[][] edges) {
        int[] parent = new int[n];
        for (int i = 0; i < n; i++) {
            parent[i] = i;
        }

        int components = n;
        for (int[] edge : edges) {
            int root1 = find(parent, edge[0]);
            int root2 = find(parent, edge[1]);

            if (root1 != root2) {
                parent[root1] = root2;
                components--;
            }
        }

        return components;
    }

    private int find(int[] parent, int node) {
        if (parent[node] != node) {
            parent[node] = find(parent, parent[node]);
        }
        return parent[node];
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int n = 5;
        int[][] edges = {{0, 1}, {1, 2}, {3, 4}};
        System.out.println(s.countComponents(n, edges)); // Expected: 2
    }
}
```

**Explanation:** Union-Find initialized with `n` individual components. For each edge, merge the sets of the two vertices; if they were in different components, decrement the component count by 1. Time is O(V + E * α(V)) and space is O(V).

## 91. Graph Valid Tree

[Back to Index](#index)

**Problem:** Given `n` nodes labeled from `0` to `n - 1` and a list of undirected edges, determine whether these edges make up a valid tree.

```java
import java.util.*;

class Solution {
    public boolean validTree(int n, int[][] edges) {
        if (edges.length != n - 1) return false;

        int[] parent = new int[n];
        for (int i = 0; i < n; i++) {
            parent[i] = i;
        }

        for (int[] edge : edges) {
            int root1 = find(parent, edge[0]);
            int root2 = find(parent, edge[1]);

            if (root1 == root2) {
                return false; // Cycle detected
            }
            parent[root1] = root2;
        }

        return true;
    }

    private int find(int[] parent, int node) {
        if (parent[node] != node) {
            parent[node] = find(parent, parent[node]);
        }
        return parent[node];
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int n = 5;
        int[][] edges = {{0, 1}, {0, 2}, {0, 3}, {1, 4}};
        System.out.println(s.validTree(n, edges)); // Expected: true
    }
}
```

**Explanation:** A graph of `n` nodes is a valid tree if and only if it has exactly `n - 1` edges and contains no cycles. Use Union-Find to detect cycles; if any edge connects two nodes already having the same root, a cycle exists. Time is O(V + E * α(V)) and space is O(V).

## 92. Word Ladder

[Back to Index](#index)

**Problem:** A transformation sequence from `beginWord` to `endWord` using a dictionary `wordList` changes one letter at a time, where each intermediate word must exist in `wordList`. Return the number of words in the shortest transformation sequence from `beginWord` to `endWord`, or `0` if no such sequence exists.

```java
import java.util.*;

class Solution {
    public int ladderLength(String beginWord, String endWord, List<String> wordList) {
        Set<String> wordSet = new HashSet<>(wordList);
        if (!wordSet.contains(endWord)) return 0;

        Queue<String> queue = new LinkedList<>();
        queue.offer(beginWord);
        int level = 1;

        while (!queue.isEmpty()) {
            int size = queue.size();
            for (int i = 0; i < size; i++) {
                String word = queue.poll();
                char[] chars = word.toCharArray();

                for (int j = 0; j < chars.length; j++) {
                    char orig = chars[j];
                    for (char c = 'a'; c <= 'z'; c++) {
                        if (c == orig) continue;
                        chars[j] = c;
                        String nextWord = new String(chars);

                        if (nextWord.equals(endWord)) {
                            return level + 1;
                        }

                        if (wordSet.contains(nextWord)) {
                            queue.offer(nextWord);
                            wordSet.remove(nextWord); // Mark visited
                        }
                    }
                    chars[j] = orig;
                }
            }
            level++;
        }

        return 0;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        String beginWord = "hit";
        String endWord = "cog";
        List<String> wordList = Arrays.asList("hot", "dot", "dog", "lot", "log", "cog");
        System.out.println(s.ladderLength(beginWord, endWord, wordList)); // Expected: 5
    }
}
```

**Explanation:** Breadth-first search treats each valid word as a node and single-letter transformations as edges. Using a hash set for fast lookups, each position is replaced with letters `'a'` to `'z'`; removing visited words from the set ensures optimal shortest path discovery. Time is O(M^2 * N) where M is word length and N is dictionary size, and space is O(M * N).


---

# Advanced Graphs

## 93. Reconstruct Itinerary

[Back to Index](#index)

**Problem:** Given a list of airline tickets represented by pairs of departure and arrival airports `[from, to]`, reconstruct the itinerary in order starting from `"JFK"`. If there are multiple valid itineraries, return the itinerary with the smallest lexical order.

```java
import java.util.*;

class Solution {
    private Map<String, PriorityQueue<String>> graph = new HashMap<>();
    private LinkedList<String> itinerary = new LinkedList<>();

    public List<String> findItinerary(List<List<String>> tickets) {
        for (List<String> ticket : tickets) {
            graph.computeIfAbsent(ticket.get(0), k -> new PriorityQueue<>()).offer(ticket.get(1));
        }

        dfs("JFK");
        return itinerary;
    }

    private void dfs(String airport) {
        PriorityQueue<String> destinations = graph.get(airport);
        while (destinations != null && !destinations.isEmpty()) {
            dfs(destinations.poll());
        }
        itinerary.addFirst(airport); // Post-order insertion for Eulerian path
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        List<List<String>> tickets = Arrays.asList(
            Arrays.asList("MUC", "LHR"),
            Arrays.asList("JFK", "MUC"),
            Arrays.asList("SFO", "SJC"),
            Arrays.asList("LHR", "SFO")
        );
        System.out.println(s.findItinerary(tickets));
        // Expected: [JFK, MUC, LHR, SFO, SJC]
    }
}
```

**Explanation:** Hierholzer's algorithm for finding an Eulerian path: construct a graph where outgoing airports are stored in a min-heap (PriorityQueue) for lexicographical order. Traverse with DFS, polling destinations, and add airports to the front of the list in post-order. Time is O(E * log E) and space is O(V + E).

## 94. Min Cost to Connect All Points

[Back to Index](#index)

**Problem:** You are given an array `points` representing 2D integer coordinates `[xi, yi]`. The cost of connecting two points is the Manhattan distance: `|xi - xj| + |yi - yj|`. Return the minimum cost to make all points connected.

```java
import java.util.*;

class Solution {
    public int minCostConnectPoints(int[][] points) {
        int n = points.length;
        int minCost = 0;
        boolean[] inMST = new boolean[n];
        int[] minDist = new int[n];
        Arrays.fill(minDist, Integer.MAX_VALUE);
        minDist[0] = 0;

        for (int i = 0; i < n; i++) {
            int curr = -1;
            for (int j = 0; j < n; j++) {
                if (!inMST[j] && (curr == -1 || minDist[j] < minDist[curr])) {
                    curr = j;
                }
            }

            inMST[curr] = true;
            minCost += minDist[curr];

            for (int next = 0; next < n; next++) {
                if (!inMST[next]) {
                    int dist = Math.abs(points[curr][0] - points[next][0]) +
                               Math.abs(points[curr][1] - points[next][1]);
                    if (dist < minDist[next]) {
                        minDist[next] = dist;
                    }
                }
            }
        }

        return minCost;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[][] points = {{0, 0}, {2, 2}, {3, 10}, {5, 2}, {7, 0}};
        System.out.println(s.minCostConnectPoints(points)); // Expected: 20
    }
}
```

**Explanation:** Prim's algorithm for Minimum Spanning Tree (MST) on a dense complete graph. Maintain the minimum distance from the current MST to each remaining point, greedily choosing the lowest cost vertex to include and relaxing distances to all unvisited vertices. Time is O(V^2) and space is O(V).

## 95. Network Delay Time

[Back to Index](#index)

**Problem:** You are given a network of `n` nodes labeled from `1` to `n` and a list of travel times `times[i] = (ui, vi, wi)`. From a starting node `k`, return the minimum time needed for all `n` nodes to receive the signal, or `-1` if impossible.

```java
import java.util.*;

class Solution {
    public int networkDelayTime(int[][] times, int n, int k) {
        Map<Integer, List<int[]>> graph = new HashMap<>();
        for (int[] time : times) {
            graph.computeIfAbsent(time[0], key -> new ArrayList<>()).add(new int[]{time[1], time[2]});
        }

        PriorityQueue<int[]> pq = new PriorityQueue<>(Comparator.comparingInt(a -> a[0]));
        pq.offer(new int[]{0, k}); // {dist, node}

        int[] dist = new int[n + 1];
        Arrays.fill(dist, Integer.MAX_VALUE);
        dist[k] = 0;

        while (!pq.isEmpty()) {
            int[] curr = pq.poll();
            int d = curr[0], u = curr[1];

            if (d > dist[u]) continue;

            if (graph.containsKey(u)) {
                for (int[] edge : graph.get(u)) {
                    int v = edge[0], weight = edge[1];
                    if (dist[u] + weight < dist[v]) {
                        dist[v] = dist[u] + weight;
                        pq.offer(new int[]{dist[v], v});
                    }
                }
            }
        }

        int maxTime = 0;
        for (int i = 1; i <= n; i++) {
            if (dist[i] == Integer.MAX_VALUE) return -1;
            maxTime = Math.max(maxTime, dist[i]);
        }

        return maxTime;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[][] times = {{2, 1, 1}, {2, 3, 1}, {3, 4, 1}};
        int n = 4, k = 2;
        System.out.println(s.networkDelayTime(times, n, k)); // Expected: 2
    }
}
```

**Explanation:** Dijkstra's shortest path algorithm using a min-priority queue to determine the minimum time to reach each node from source `k`. The final answer is the maximum shortest time among all nodes, or `-1` if any node remains unreachable. Time is O(E * log V) and space is O(V + E).

## 96. Swim in Rising Water

[Back to Index](#index)

**Problem:** You are given an `n x n` integer grid where `grid[i][j]` represents elevation. At time `t`, water depth everywhere is `t`, allowing swimming between adjacent cells if both elevations are at most `t`. Return the least time required to swim from `(0, 0)` to `(n - 1, n - 1)`.

```java
import java.util.*;

class Solution {
    public int swimInWater(int[][] grid) {
        int n = grid.length;
        boolean[][] visited = new boolean[n][n];
        PriorityQueue<int[]> pq = new PriorityQueue<>(Comparator.comparingInt(a -> a[0]));

        pq.offer(new int[]{grid[0][0], 0, 0});
        visited[0][0] = true;

        int[][] dirs = {{1, 0}, {-1, 0}, {0, 1}, {0, -1}};

        while (!pq.isEmpty()) {
            int[] curr = pq.poll();
            int time = curr[0], r = curr[1], c = curr[2];

            if (r == n - 1 && c == n - 1) {
                return time;
            }

            for (int[] d : dirs) {
                int nr = r + d[0], nc = c + d[1];
                if (nr >= 0 && nr < n && nc >= 0 && nc < n && !visited[nr][nc]) {
                    visited[nr][nc] = true;
                    pq.offer(new int[]{Math.max(time, grid[nr][nc]), nr, nc});
                }
            }
        }

        return 0;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[][] grid = {
            {0, 2},
            {1, 3}
        };
        System.out.println(s.swimInWater(grid)); // Expected: 3
    }
}
```

**Explanation:** Modified Dijkstra's algorithm where the cost of a path is defined as the maximum elevation encountered along the path. A priority queue greedily expands the path having the minimum peak elevation so far until reaching `(n - 1, n - 1)`. Time is O(n^2 * log n) and space is O(n^2).

## 97. Path With Minimum Effort

[Back to Index](#index)

**Problem:** Given a 2D array `heights` of size `rows x columns`, a route's effort from `(0, 0)` to `(rows - 1, columns - 1)` is the maximum absolute difference in heights between two consecutive cells of the route. Return the minimum effort required.

```java
import java.util.*;

class Solution {
    public int minimumEffortPath(int[][] heights) {
        int m = heights.length, n = heights[0].length;
        int[][] dist = new int[m][n];
        for (int[] row : dist) {
            Arrays.fill(row, Integer.MAX_VALUE);
        }

        PriorityQueue<int[]> pq = new PriorityQueue<>(Comparator.comparingInt(a -> a[0]));
        pq.offer(new int[]{0, 0, 0}); // {effort, r, c}
        dist[0][0] = 0;

        int[][] dirs = {{1, 0}, {-1, 0}, {0, 1}, {0, -1}};

        while (!pq.isEmpty()) {
            int[] curr = pq.poll();
            int effort = curr[0], r = curr[1], c = curr[2];

            if (r == m - 1 && c == n - 1) {
                return effort;
            }

            if (effort > dist[r][c]) continue;

            for (int[] d : dirs) {
                int nr = r + d[0], nc = c + d[1];
                if (nr >= 0 && nr < m && nc >= 0 && nc < n) {
                    int nextEffort = Math.max(effort, Math.abs(heights[nr][nc] - heights[r][c]));
                    if (nextEffort < dist[nr][nc]) {
                        dist[nr][nc] = nextEffort;
                        pq.offer(new int[]{nextEffort, nr, nc});
                    }
                }
            }
        }

        return 0;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[][] heights = {
            {1, 2, 2},
            {3, 8, 2},
            {5, 3, 5}
        };
        System.out.println(s.minimumEffortPath(heights)); // Expected: 2
    }
}
```

**Explanation:** Dijkstra's algorithm tracking the minimum possible maximum step elevation difference to reach each cell. Using a priority queue ordered by effort, pop the cell with least effort and relax neighbor distances with `max(currentEffort, |heightDifference|)`. Time is O(m * n * log(m * n)) and space is O(m * n).

## 98. Cheapest Flights Within K Stops

[Back to Index](#index)

**Problem:** There are `n` cities connected by flights `flights[i] = [fromi, toi, pricei]`. Return the cheapest price from `src` to `dst` with at most `k` stops, or `-1` if no such route exists.

```java
import java.util.*;

class Solution {
    public int findCheapestPrice(int n, int[][] flights, int src, int dst, int k) {
        int[] prices = new int[n];
        Arrays.fill(prices, Integer.MAX_VALUE);
        prices[src] = 0;

        for (int i = 0; i <= k; i++) {
            int[] temp = Arrays.copyOf(prices, n);
            for (int[] flight : flights) {
                int u = flight[0], v = flight[1], price = flight[2];
                if (prices[u] != Integer.MAX_VALUE && prices[u] + price < temp[v]) {
                    temp[v] = prices[u] + price;
                }
            }
            prices = temp;
        }

        return prices[dst] == Integer.MAX_VALUE ? -1 : prices[dst];
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int n = 4;
        int[][] flights = {
            {0, 1, 100},
            {1, 2, 100},
            {2, 0, 100},
            {1, 3, 600},
            {2, 3, 200}
        };
        int src = 0, dst = 3, k = 1;
        System.out.println(s.findCheapestPrice(n, flights, src, dst, k)); // Expected: 700
    }
}
```

**Explanation:** Bellman-Ford algorithm executed for `k + 1` iterations (allowing at most `k` intermediate stops). In each iteration, update distances using a copy of the previous round's prices to ensure edges are relaxed using paths of length at most `i`. Time is O(k * E) and space is O(V).

---

# 1-D Dynamic Programming

## 99. Climbing Stairs

[Back to Index](#index)

**Problem:** You are climbing a staircase that takes `n` steps to reach the top. Each time you can climb either 1 or 2 steps. Return the number of distinct ways to climb to the top.

```java
class Solution {
    public int climbStairs(int n) {
        if (n <= 2) return n;
        int prev2 = 1, prev1 = 2;
        for (int i = 3; i <= n; i++) {
            int curr = prev1 + prev2;
            prev2 = prev1;
            prev1 = curr;
        }
        return prev1;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.climbStairs(2)); // Expected: 2
        System.out.println(s.climbStairs(3)); // Expected: 3
        System.out.println(s.climbStairs(5)); // Expected: 8
    }
}
```

**Explanation:** The number of ways to reach step `i` is the sum of ways to reach step `i - 1` and step `i - 2` (Fibonacci recurrence), maintained with two variables for constant space. Time is O(n) and space is O(1).

## 100. Min Cost Climbing Stairs

[Back to Index](#index)

**Problem:** Given an integer array `cost` where `cost[i]` is the cost of the `i`-th step on a staircase, you can start from step 0 or step 1. Once you pay the cost, you can take one or two steps. Return the minimum cost to reach the top floor.

```java
class Solution {
    public int minCostClimbingStairs(int[] cost) {
        int prev2 = 0, prev1 = 0;
        for (int c : cost) {
            int curr = c + Math.min(prev1, prev2);
            prev2 = prev1;
            prev1 = curr;
        }
        return Math.min(prev1, prev2);
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.minCostClimbingStairs(new int[]{10, 15, 20})); // Expected: 15
        System.out.println(s.minCostClimbingStairs(new int[]{1, 100, 1, 1, 1, 100, 1, 1, 100, 1})); // Expected: 6
    }
}
```

**Explanation:** The minimum cost to step onto step `i` is `cost[i] + min(dp[i-1], dp[i-2])`, and the top floor can be reached from either of the last two steps. Time is O(n) and space is O(1).

## 101. House Robber

[Back to Index](#index)

**Problem:** Given an integer array `nums` representing the amount of money in each house along a street, return the maximum amount of money you can rob tonight without alerting the police (adjacent houses cannot be robbed together).

```java
class Solution {
    public int rob(int[] nums) {
        int rob1 = 0, rob2 = 0;
        for (int num : nums) {
            int curr = Math.max(rob2, rob1 + num);
            rob1 = rob2;
            rob2 = curr;
        }
        return rob2;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.rob(new int[]{1, 2, 3, 1})); // Expected: 4
        System.out.println(s.rob(new int[]{2, 7, 9, 3, 1})); // Expected: 12
    }
}
```

**Explanation:** At each house, choose either to skip it (carrying forward the previous maximum) or rob it (adding its value to the maximum up to two houses prior), tracking the two states with rolling variables. Time is O(n) and space is O(1).

## 102. House Robber II

[Back to Index](#index)

**Problem:** Given an integer array `nums` representing the amount of money in houses arranged in a circle (the first and last houses are adjacent), return the maximum amount of money you can rob without robbing two adjacent houses.

```java
class Solution {
    public int rob(int[] nums) {
        if (nums.length == 1) return nums[0];
        return Math.max(robRange(nums, 0, nums.length - 2),
                        robRange(nums, 1, nums.length - 1));
    }

    private int robRange(int[] nums, int start, int end) {
        int rob1 = 0, rob2 = 0;
        for (int i = start; i <= end; i++) {
            int curr = Math.max(rob2, rob1 + nums[i]);
            rob1 = rob2;
            rob2 = curr;
        }
        return rob2;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.rob(new int[]{2, 3, 2})); // Expected: 3
        System.out.println(s.rob(new int[]{1, 2, 3, 1})); // Expected: 4
        System.out.println(s.rob(new int[]{1, 2, 3})); // Expected: 3
    }
}
```

**Explanation:** Since the first and last houses cannot both be robbed, solve two separate House Robber instances (excluding the last house, and excluding the first house) and take the maximum. Time is O(n) and space is O(1).

## 103. Longest Palindromic Substring

[Back to Index](#index)

**Problem:** Given a string `s`, return the longest palindromic substring in `s`.

```java
class Solution {
    public String longestPalindrome(String s) {
        if (s == null || s.length() < 1) return "";
        int start = 0, end = 0;
        for (int i = 0; i < s.length(); i++) {
            int len1 = expandAroundCenter(s, i, i);
            int len2 = expandAroundCenter(s, i, i + 1);
            int len = Math.max(len1, len2);
            if (len > end - start + 1) {
                start = i - (len - 1) / 2;
                end = i + len / 2;
            }
        }
        return s.substring(start, end + 1);
    }

    private int expandAroundCenter(String s, int left, int right) {
        while (left >= 0 && right < s.length() && s.charAt(left) == s.charAt(right)) {
            left--;
            right++;
        }
        return right - left - 1;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.longestPalindrome("babad")); // Expected: "bab" or "aba"
        System.out.println(s.longestPalindrome("cbbd"));  // Expected: "bb"
    }
}
```

**Explanation:** Expand outward from every single character (odd-length palindromes) and between every adjacent pair (even-length palindromes) while tracking the longest palindrome bounds. Time is O(n^2) and space is O(1).

## 104. Palindromic Substrings

[Back to Index](#index)

**Problem:** Given a string `s`, return the number of palindromic substrings in it.

```java
class Solution {
    public int countSubstrings(String s) {
        int count = 0;
        for (int i = 0; i < s.length(); i++) {
            count += countPalindromes(s, i, i);     // Odd-length centers
            count += countPalindromes(s, i, i + 1); // Even-length centers
        }
        return count;
    }

    private int countPalindromes(String s, int left, int right) {
        int count = 0;
        while (left >= 0 && right < s.length() && s.charAt(left) == s.charAt(right)) {
            count++;
            left--;
            right++;
        }
        return count;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.countSubstrings("abc")); // Expected: 3
        System.out.println(s.countSubstrings("aaa")); // Expected: 6
    }
}
```

**Explanation:** Expand outward around all possible centers (each index and each gap between indices), incrementing the count for each valid palindrome found. Time is O(n^2) and space is O(1).

## 105. Decode Ways

[Back to Index](#index)

**Problem:** A message containing letters from A-Z can be encoded into numbers using the mapping 'A' -> "1", 'B' -> "2", ..., 'Z' -> "26". Given a string `s` of digits, return the number of ways to decode it.

```java
class Solution {
    public int numDecodings(String s) {
        if (s == null || s.length() == 0 || s.charAt(0) == '0') return 0;
        int n = s.length();
        int prev2 = 1, prev1 = 1;
        for (int i = 1; i < n; i++) {
            int curr = 0;
            int singleDigit = s.charAt(i) - '0';
            int twoDigits = Integer.parseInt(s.substring(i - 1, i + 1));
            if (singleDigit >= 1) {
                curr += prev1;
            }
            if (twoDigits >= 10 && twoDigits <= 26) {
                curr += prev2;
            }
            prev2 = prev1;
            prev1 = curr;
        }
        return prev1;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.numDecodings("12"));  // Expected: 2
        System.out.println(s.numDecodings("226")); // Expected: 3
        System.out.println(s.numDecodings("06"));  // Expected: 0
    }
}
```

**Explanation:** Each position adds valid single-digit decodings (1-9) from `dp[i-1]` and valid two-digit decodings (10-26) from `dp[i-2]`, tracking values using two rolling variables. Time is O(n) and space is O(1).

## 106. Coin Change

[Back to Index](#index)

**Problem:** Given an integer array `coins` representing coin denominations and an integer `amount`, return the fewest number of coins needed to make up that amount, or -1 if it cannot be made up.

```java
import java.util.Arrays;

class Solution {
    public int coinChange(int[] coins, int amount) {
        int max = amount + 1;
        int[] dp = new int[amount + 1];
        Arrays.fill(dp, max);
        dp[0] = 0;

        for (int i = 1; i <= amount; i++) {
            for (int coin : coins) {
                if (coin <= i) {
                    dp[i] = Math.min(dp[i], dp[i - coin] + 1);
                }
            }
        }
        return dp[amount] > amount ? -1 : dp[amount];
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.coinChange(new int[]{1, 2, 5}, 11)); // Expected: 3
        System.out.println(s.coinChange(new int[]{2}, 3));         // Expected: -1
        System.out.println(s.coinChange(new int[]{1}, 0));         // Expected: 0
    }
}
```

**Explanation:** Use bottom-up dynamic programming where `dp[i]` stores the minimum coins required to make amount `i`, transitioning via `dp[i] = min(dp[i], dp[i - coin] + 1)`. Time is O(amount * len(coins)) and space is O(amount).

## 107. Maximum Product Subarray

[Back to Index](#index)

**Problem:** Given an integer array `nums`, find a contiguous non-empty subarray that has the largest product and return that product.

```java
class Solution {
    public int maxProduct(int[] nums) {
        int maxProd = nums[0];
        int minProd = nums[0];
        int result = nums[0];

        for (int i = 1; i < nums.length; i++) {
            int num = nums[i];
            if (num < 0) {
                int temp = maxProd;
                maxProd = minProd;
                minProd = temp;
            }
            maxProd = Math.max(num, maxProd * num);
            minProd = Math.min(num, minProd * num);
            result = Math.max(result, maxProd);
        }
        return result;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.maxProduct(new int[]{2, 3, -2, 4}));  // Expected: 6
        System.out.println(s.maxProduct(new int[]{-2, 0, -1}));    // Expected: 0
        System.out.println(s.maxProduct(new int[]{-2, 3, -4}));    // Expected: 24
    }
}
```

**Explanation:** Maintain running maximum and minimum products ending at each index because multiplying a negative number by a negative minimum can produce a new maximum. Time is O(n) and space is O(1).

## 108. Word Break

[Back to Index](#index)

**Problem:** Given a string `s` and a dictionary of strings `wordDict`, return true if `s` can be segmented into a space-separated sequence of one or more dictionary words.

```java
import java.util.Arrays;
import java.util.HashSet;
import java.util.List;
import java.util.Set;

class Solution {
    public boolean wordBreak(String s, List<String> wordDict) {
        Set<String> dict = new HashSet<>(wordDict);
        int n = s.length();
        boolean[] dp = new boolean[n + 1];
        dp[0] = true;

        for (int i = 1; i <= n; i++) {
            for (int j = 0; j < i; j++) {
                if (dp[j] && dict.contains(s.substring(j, i))) {
                    dp[i] = true;
                    break;
                }
            }
        }
        return dp[n];
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.wordBreak("leetcode", Arrays.asList("leet", "code")));                         // Expected: true
        System.out.println(s.wordBreak("applepenapple", Arrays.asList("apple", "pen")));                   // Expected: true
        System.out.println(s.wordBreak("catsandog", Arrays.asList("cats", "dog", "sand", "and", "cat"))); // Expected: false
    }
}
```

**Explanation:** Define `dp[i]` as whether the prefix of length `i` can be segmented into words, setting `dp[i] = true` if some partition point `j` has `dp[j] == true` and substring `s[j...i-1]` in the set. Time is O(n^3) and space is O(n + total dictionary length).

## 109. Longest Increasing Subsequence

[Back to Index](#index)

**Problem:** Given an integer array `nums`, return the length of the longest strictly increasing subsequence.

```java
class Solution {
    public int lengthOfLIS(int[] nums) {
        int[] tails = new int[nums.length];
        int size = 0;
        for (int num : nums) {
            int i = 0, j = size;
            while (i < j) {
                int mid = (i + j) / 2;
                if (tails[mid] < num) {
                    i = mid + 1;
                } else {
                    j = mid;
                }
            }
            tails[i] = num;
            if (i == size) size++;
        }
        return size;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.lengthOfLIS(new int[]{10, 9, 2, 5, 3, 7, 101, 18})); // Expected: 4
        System.out.println(s.lengthOfLIS(new int[]{0, 1, 0, 3, 2, 3}));           // Expected: 4
        System.out.println(s.lengthOfLIS(new int[]{7, 7, 7, 7, 7, 7, 7}));        // Expected: 1
    }
}
```

**Explanation:** Maintain a `tails` array where `tails[i]` stores the smallest tail of all increasing subsequences of length `i + 1`, updating elements via binary search (patience sorting). Time is O(n log n) and space is O(n).

## 110. Partition Equal Subset Sum

[Back to Index](#index)

**Problem:** Given an integer array `nums`, return true if the array can be partitioned into two subsets such that the sum of elements in both subsets is equal.

```java
class Solution {
    public boolean canPartition(int[] nums) {
        int totalSum = 0;
        for (int num : nums) totalSum += num;
        if (totalSum % 2 != 0) return false;

        int target = totalSum / 2;
        boolean[] dp = new boolean[target + 1];
        dp[0] = true;

        for (int num : nums) {
            for (int j = target; j >= num; j--) {
                dp[j] = dp[j] || dp[j - num];
            }
        }
        return dp[target];
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.canPartition(new int[]{1, 5, 11, 5})); // Expected: true
        System.out.println(s.canPartition(new int[]{1, 2, 3, 5}));  // Expected: false
    }
}
```

**Explanation:** Formulates as a 0/1 knapsack problem seeking a subset summing to `totalSum / 2`, solved with a 1D boolean array traversed backwards to ensure each number is used at most once. Time is O(n * target) and space is O(target), where target = sum / 2.

---

# 2-D Dynamic Programming

## 111. Unique Paths

[Back to Index](#index)

**Problem:** Given the integers `m` and `n` representing the dimensions of an `m x n` grid, return the number of possible unique paths from the top-left corner `(0, 0)` to the bottom-right corner `(m - 1, n - 1)`. The robot can only move either down or right at any point in time.

```java
import java.util.Arrays;

class Solution {
    public int uniquePaths(int m, int n) {
        int[] dp = new int[n];
        Arrays.fill(dp, 1);
        for (int i = 1; i < m; i++) {
            for (int j = 1; j < n; j++) {
                dp[j] += dp[j - 1];
            }
        }
        return dp[n - 1];
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.uniquePaths(3, 7)); // Expected: 28
        System.out.println(s.uniquePaths(3, 2)); // Expected: 3
    }
}
```

**Explanation:** Compute unique paths using a 1D dynamic programming array where each cell `dp[j]` represents the number of ways to reach column `j`, updated by adding paths from the cell above (`dp[j]`) and the cell to the left (`dp[j - 1]`). Time is O(m * n) and space is O(n).

## 112. Longest Common Subsequence

[Back to Index](#index)

**Problem:** Given two strings `text1` and `text2`, return the length of their longest common subsequence. If there is no common subsequence, return `0`.

```java
class Solution {
    public int longestCommonSubsequence(String text1, String text2) {
        int m = text1.length();
        int n = text2.length();
        int[][] dp = new int[m + 1][n + 1];

        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                if (text1.charAt(i - 1) == text2.charAt(j - 1)) {
                    dp[i][j] = 1 + dp[i - 1][j - 1];
                } else {
                    dp[i][j] = Math.max(dp[i - 1][j], dp[i][j - 1]);
                }
            }
        }

        return dp[m][n];
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.longestCommonSubsequence("abcde", "ace")); // Expected: 3
        System.out.println(s.longestCommonSubsequence("abc", "def"));   // Expected: 0
    }
}
```

**Explanation:** Use 2D dynamic programming where `dp[i][j]` represents the LCS length of prefixes `text1[0..i-1]` and `text2[0..j-1]`. If characters match, extend the diagonal value by 1; otherwise, take the maximum of excluding the current character from either string. Time is O(m * n) and space is O(m * n).

## 113. Best Time to Buy and Sell Stock with Cooldown

[Back to Index](#index)

**Problem:** You are given an array `prices` where `prices[i]` is the price of a given stock on the `i`-th day. Find the maximum profit you can achieve with unlimited transactions, with the condition that after selling your stock, you cannot buy stock on the next day (cooldown of 1 day).

```java
class Solution {
    public int maxProfit(int[] prices) {
        if (prices == null || prices.length == 0) return 0;

        int held = -prices[0];
        int sold = 0;
        int rest = 0;

        for (int i = 1; i < prices.length; i++) {
            int prevSold = sold;
            sold = held + prices[i];
            held = Math.max(held, rest - prices[i]);
            rest = Math.max(rest, prevSold);
        }

        return Math.max(sold, rest);
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[] prices = {1, 2, 3, 0, 2};
        System.out.println(s.maxProfit(prices)); // Expected: 3
    }
}
```

**Explanation:** Maintain three state variables tracking maximum profit: `held` (holding a stock), `sold` (just sold, triggering cooldown next day), and `rest` (cooldown or holding cash). Transitions occur day-by-day in constant space. Time is O(n) and space is O(1).

## 114. Coin Change II

[Back to Index](#index)

**Problem:** You are given an integer array `coins` representing coins of different denominations and an integer `amount` representing a total amount of money. Return the number of combinations that make up that amount. You may assume you have an infinite number of each kind of coin.

```java
class Solution {
    public int change(int amount, int[] coins) {
        int[] dp = new int[amount + 1];
        dp[0] = 1;

        for (int coin : coins) {
            for (int i = coin; i <= amount; i++) {
                dp[i] += dp[i - coin];
            }
        }

        return dp[amount];
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[] coins = {1, 2, 5};
        System.out.println(s.change(5, coins)); // Expected: 4
    }
}
```

**Explanation:** Solve using unbounded knapsack dynamic programming where the outer loop iterates over coin denominations to ensure combinations (not permutations) are counted, adding ways to make `i - coin` to `dp[i]`. Time is O(n * amount) and space is O(amount).

## 115. Target Sum

[Back to Index](#index)

**Problem:** You are given an integer array `nums` and an integer `target`. Build an expression using `+` and `-` before each integer in `nums` and evaluate it. Return the number of different expressions that evaluate to `target`.

```java
class Solution {
    public int findTargetSumWays(int[] nums, int target) {
        int totalSum = 0;
        for (int num : nums) {
            totalSum += num;
        }

        if (totalSum < Math.abs(target) || (totalSum + target) % 2 != 0) {
            return 0;
        }

        int subsetSum = (totalSum + target) / 2;
        int[] dp = new int[subsetSum + 1];
        dp[0] = 1;

        for (int num : nums) {
            for (int j = subsetSum; j >= num; j--) {
                dp[j] += dp[j - num];
            }
        }

        return dp[subsetSum];
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[] nums = {1, 1, 1, 1, 1};
        System.out.println(s.findTargetSumWays(nums, 3)); // Expected: 5
    }
}
```

**Explanation:** Transform the problem into finding a subset of numbers whose sum equals `(totalSum + target) / 2`, then count valid subsets using 0/1 knapsack dynamic programming iterating backwards to avoid reusing elements. Time is O(n * S) where S is (totalSum + target) / 2 and space is O(S).

## 116. Interleaving String

[Back to Index](#index)

**Problem:** Given strings `s1`, `s2`, and `s3`, determine whether `s3` is formed by an interleaving of `s1` and `s2`.

```java
class Solution {
    public boolean isInterleave(String s1, String s2, String s3) {
        int m = s1.length();
        int n = s2.length();
        if (m + n != s3.length()) {
            return false;
        }

        boolean[][] dp = new boolean[m + 1][n + 1];
        dp[0][0] = true;

        for (int i = 1; i <= m; i++) {
            dp[i][0] = dp[i - 1][0] && s1.charAt(i - 1) == s3.charAt(i - 1);
        }

        for (int j = 1; j <= n; j++) {
            dp[0][j] = dp[0][j - 1] && s2.charAt(j - 1) == s3.charAt(j - 1);
        }

        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                char c = s3.charAt(i + j - 1);
                dp[i][j] = (dp[i - 1][j] && s1.charAt(i - 1) == c) ||
                           (dp[i][j - 1] && s2.charAt(j - 1) == c);
            }
        }

        return dp[m][n];
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.isInterleave("aabcc", "dbbca", "aadbbcbcac")); // Expected: true
        System.out.println(s.isInterleave("aabcc", "dbbca", "aadbbbaccc")); // Expected: false
    }
}
```

**Explanation:** Use 2D dynamic programming where `dp[i][j]` indicates whether `s3[0..i+j-1]` can be formed by interleaving prefixes `s1[0..i-1]` and `s2[0..j-1]`, transitioning from valid subproblems when characters match. Time is O(m * n) and space is O(m * n).

## 117. Longest Increasing Path in a Matrix

[Back to Index](#index)

**Problem:** Given an `m x n` integers matrix, return the length of the longest increasing path in matrix. From each cell, you can move in four directions (up, down, left, right), but not diagonally or outside the boundary.

```java
class Solution {
    private int[][] memo;
    private int[][] dirs = {{0, 1}, {0, -1}, {1, 0}, {-1, 0}};

    public int longestIncreasingPath(int[][] matrix) {
        if (matrix == null || matrix.length == 0 || matrix[0].length == 0) return 0;
        int m = matrix.length;
        int n = matrix[0].length;
        memo = new int[m][n];

        int maxPath = 0;
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                maxPath = Math.max(maxPath, dfs(matrix, i, j));
            }
        }
        return maxPath;
    }

    private int dfs(int[][] matrix, int r, int c) {
        if (memo[r][c] != 0) return memo[r][c];

        int max = 1;
        for (int[] dir : dirs) {
            int nr = r + dir[0];
            int nc = c + dir[1];
            if (nr >= 0 && nr < matrix.length && nc >= 0 && nc < matrix[0].length && matrix[nr][nc] > matrix[r][c]) {
                max = Math.max(max, 1 + dfs(matrix, nr, nc));
            }
        }

        memo[r][c] = max;
        return max;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[][] matrix = {
            {9, 9, 4},
            {6, 6, 8},
            {2, 1, 1}
        };
        System.out.println(s.longestIncreasingPath(matrix)); // Expected: 4
    }
}
```

**Explanation:** Model the matrix as a directed acyclic graph (DAG) where edges point to strictly greater neighbors, and find the longest path using DFS with memoization on each cell. Time is O(m * n) and space is O(m * n).

## 118. Distinct Subsequences

[Back to Index](#index)

**Problem:** Given two strings `s` and `t`, return the number of distinct subsequences of `s` which equals `t`.

```java
class Solution {
    public int numDistinct(String s, String t) {
        int m = s.length();
        int n = t.length();
        int[][] dp = new int[m + 1][n + 1];

        for (int i = 0; i <= m; i++) {
            dp[i][0] = 1;
        }

        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                if (s.charAt(i - 1) == t.charAt(j - 1)) {
                    dp[i][j] = dp[i - 1][j - 1] + dp[i - 1][j];
                } else {
                    dp[i][j] = dp[i - 1][j];
                }
            }
        }

        return dp[m][n];
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.numDistinct("rabbbit", "rabbit")); // Expected: 3
        System.out.println(s.numDistinct("babgbag", "bag"));    // Expected: 5
    }
}
```

**Explanation:** Use 2D dynamic programming where `dp[i][j]` is the count of distinct subsequences of `s[0..i-1]` matching `t[0..j-1]`. If characters match, add occurrences using the character (`dp[i - 1][j - 1]`) and omitting it (`dp[i - 1][j]`); otherwise, only omit it. Time is O(m * n) and space is O(m * n).

## 119. Edit Distance

[Back to Index](#index)

**Problem:** Given two strings `word1` and `word2`, return the minimum number of operations required to convert `word1` to `word2`. Permitted operations are inserting, deleting, or replacing a character.

```java
class Solution {
    public int minDistance(String word1, String word2) {
        int m = word1.length();
        int n = word2.length();
        int[][] dp = new int[m + 1][n + 1];

        for (int i = 0; i <= m; i++) {
            dp[i][0] = i;
        }
        for (int j = 0; j <= n; j++) {
            dp[0][j] = j;
        }

        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                if (word1.charAt(i - 1) == word2.charAt(j - 1)) {
                    dp[i][j] = dp[i - 1][j - 1];
                } else {
                    dp[i][j] = 1 + Math.min(dp[i - 1][j - 1],
                                   Math.min(dp[i - 1][j],
                                            dp[i][j - 1]));
                }
            }
        }

        return dp[m][n];
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.minDistance("horse", "ros"));            // Expected: 3
        System.out.println(s.minDistance("intention", "execution")); // Expected: 5
    }
}
```

**Explanation:** Compute minimum operations using 2D dynamic programming where `dp[i][j]` represents the edit distance between `word1[0..i-1]` and `word2[0..j-1]`. If characters match, cost is zero; otherwise, take 1 plus the minimum of insert, delete, or replace operations. Time is O(m * n) and space is O(m * n).

## 120. Burst Balloons

[Back to Index](#index)

**Problem:** You are given `n` balloons, indexed from `0` to `n - 1`, where each balloon is painted with a number on it represented by an array `nums`. If you burst the `i`-th balloon, you get `nums[i - 1] * nums[i] * nums[i + 1]` coins. If `i - 1` or `i + 1` goes out of bounds, treat it as a balloon with value `1`. Return the maximum coins you can collect by bursting the balloons wisely.

```java
class Solution {
    public int maxCoins(int[] nums) {
        int n = nums.length;
        int[] vals = new int[n + 2];
        vals[0] = 1;
        vals[n + 1] = 1;
        for (int i = 0; i < n; i++) {
            vals[i + 1] = nums[i];
        }

        int[][] dp = new int[n + 2][n + 2];

        for (int len = 1; len <= n; len++) {
            for (int left = 1; left <= n - len + 1; left++) {
                int right = left + len - 1;
                for (int k = left; k <= right; k++) {
                    int coins = vals[left - 1] * vals[k] * vals[right + 1]
                              + dp[left][k - 1]
                              + dp[k + 1][right];
                    dp[left][right] = Math.max(dp[left][right], coins);
                }
            }
        }

        return dp[1][n];
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[] nums = {3, 1, 5, 8};
        System.out.println(s.maxCoins(nums)); // Expected: 167
    }
}
```

**Explanation:** Pad the array with 1 at both boundaries and use interval dynamic programming, where `dp[left][right]` stores the maximum coins obtained by bursting all balloons in `[left, right]`. We choose each balloon `k` as the last balloon to burst in the range, decoupling the left and right subproblems. Time is O(n^3) and space is O(n^2).

## 121. Regular Expression Matching

[Back to Index](#index)

**Problem:** Given an input string `s` and a pattern `p`, implement regular expression matching with support for `'.'` (which matches any single character) and `'*'` (which matches zero or more of the preceding element). The matching must cover the entire input string.

```java
class Solution {
    public boolean isMatch(String s, String p) {
        int m = s.length();
        int n = p.length();
        boolean[][] dp = new boolean[m + 1][n + 1];
        dp[0][0] = true;

        for (int j = 1; j <= n; j++) {
            if (p.charAt(j - 1) == '*' && j >= 2) {
                dp[0][j] = dp[0][j - 2];
            }
        }

        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                char pc = p.charAt(j - 1);
                if (pc == '*') {
                    dp[i][j] = dp[i][j - 2];
                    char prevChar = p.charAt(j - 2);
                    if (prevChar == '.' || prevChar == s.charAt(i - 1)) {
                        dp[i][j] = dp[i][j] || dp[i - 1][j];
                    }
                } else if (pc == '.' || pc == s.charAt(i - 1)) {
                    dp[i][j] = dp[i - 1][j - 1];
                }
            }
        }

        return dp[m][n];
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.isMatch("aa", "a"));    // Expected: false
        System.out.println(s.isMatch("aa", "a*"));   // Expected: true
        System.out.println(s.isMatch("ab", ".*"));   // Expected: true
    }
}
```

**Explanation:** Use 2D dynamic programming where `dp[i][j]` represents whether `s[0..i-1]` matches `p[0..j-1]`. If the current pattern character is `'*'`, branch into zero matches of the preceding element or one/more matches if the preceding character matches the current character of `s`. Time is O(m * n) and space is O(m * n).

---

# Greedy

## 122. Maximum Subarray

[Back to Index](#index)

**Problem:** Given an integer array `nums`, find the subarray with the largest sum, and return *its sum*.

```java
class Solution {
    public int maxSubArray(int[] nums) {
        int maxSum = nums[0];
        int curSum = 0;

        for (int n : nums) {
            curSum = Math.max(curSum, 0) + n;
            maxSum = Math.max(maxSum, curSum);
        }

        return maxSum;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[] nums = {-2, 1, -3, 4, -1, 2, 1, -5, 4};
        System.out.println(s.maxSubArray(nums)); // Expected: 6
    }
}
```

**Explanation:** Use Kadane's algorithm. Maintain a running sum `curSum` and reset it to `0` whenever it drops below zero, updating `maxSum` at each element. Time is O(n) and space is O(1).

## 123. Jump Game

[Back to Index](#index)

**Problem:** Given an integer array `nums` where each element represents your maximum jumping length from that position, return `true` if you can reach the last index starting from index `0`, or `false` otherwise.

```java
class Solution {
    public boolean canJump(int[] nums) {
        int goal = nums.length - 1;

        for (int i = nums.length - 2; i >= 0; i--) {
            if (i + nums[i] >= goal) {
                goal = i;
            }
        }

        return goal == 0;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.canJump(new int[]{2, 3, 1, 1, 4})); // Expected: true
        System.out.println(s.canJump(new int[]{3, 2, 1, 0, 4})); // Expected: false
    }
}
```

**Explanation:** Work backwards greedily from the last index. If index `i` can reach the current `goal` (`i + nums[i] >= goal`), update `goal` to `i`. If the goal reaches `0`, the destination is reachable. Time is O(n) and space is O(1).

## 124. Jump Game II

[Back to Index](#index)

**Problem:** Given a 0-indexed array of integers `nums` of length `n`, return the minimum number of jumps to reach index `n - 1`. You can assume that you can always reach the last index.

```java
class Solution {
    public int jump(int[] nums) {
        int jumps = 0;
        int curEnd = 0;
        int farthest = 0;

        for (int i = 0; i < nums.length - 1; i++) {
            farthest = Math.max(farthest, i + nums[i]);
            if (i == curEnd) {
                jumps++;
                curEnd = farthest;
            }
        }

        return jumps;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.jump(new int[]{2, 3, 1, 1, 4})); // Expected: 2
        System.out.println(s.jump(new int[]{2, 3, 0, 1, 4})); // Expected: 2
    }
}
```

**Explanation:** Use a greedy BFS level-by-level approach. At each step, record the farthest index reachable. When the current jump window boundary `curEnd` is reached, increment `jumps` and extend the boundary to `farthest`. Time is O(n) and space is O(1).

## 125. Gas Station

[Back to Index](#index)

**Problem:** There are `n` gas stations along a circular route where station `i` has `gas[i]` fuel and costs `cost[i]` to travel to station `i + 1`. Return the starting station index to complete the full circuit clockwise once, or `-1` if impossible.

```java
class Solution {
    public int canCompleteCircuit(int[] gas, int[] cost) {
        int totalGas = 0;
        int totalCost = 0;
        for (int i = 0; i < gas.length; i++) {
            totalGas += gas[i];
            totalCost += cost[i];
        }

        if (totalGas < totalCost) {
            return -1;
        }

        int startIndex = 0;
        int currentTank = 0;
        for (int i = 0; i < gas.length; i++) {
            currentTank += gas[i] - cost[i];
            if (currentTank < 0) {
                startIndex = i + 1;
                currentTank = 0;
            }
        }

        return startIndex;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[] gas = {1, 2, 3, 4, 5};
        int[] cost = {3, 4, 5, 1, 2};
        System.out.println(s.canCompleteCircuit(gas, cost)); // Expected: 3
    }
}
```

**Explanation:** If total gas is less than total cost, completing the circuit is impossible. Otherwise, a unique valid start station is guaranteed to exist: iterate through stations and if current tank drops below 0, reset start to `i + 1` and tank to `0`. Time is O(n) and space is O(1).

## 126. Hand of Straights

[Back to Index](#index)

**Problem:** Given an integer array `hand` and an integer `groupSize`, return `true` if the hand can be rearranged into groups of `groupSize` consecutive cards, or `false` otherwise.

```java
import java.util.TreeMap;

class Solution {
    public boolean isNStraightHand(int[] hand, int groupSize) {
        if (hand.length % groupSize != 0) {
            return false;
        }

        TreeMap<Integer, Integer> count = new TreeMap<>();
        for (int card : hand) {
            count.put(card, count.getOrDefault(card, 0) + 1);
        }

        for (int card : count.keySet()) {
            int freq = count.get(card);
            if (freq > 0) {
                for (int i = 0; i < groupSize; i++) {
                    int nextCard = card + i;
                    if (count.getOrDefault(nextCard, 0) < freq) {
                        return false;
                    }
                    count.put(nextCard, count.get(nextCard) - freq);
                }
            }
        }

        return true;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[] hand = {1, 2, 3, 6, 2, 3, 4, 7, 8};
        System.out.println(s.isNStraightHand(hand, 3)); // Expected: true
        System.out.println(s.isNStraightHand(new int[]{1, 2, 3, 4, 5}, 4)); // Expected: false
    }
}
```

**Explanation:** Count card frequencies in a `TreeMap` to process keys in sorted order. For each smallest available card with frequency `f`, deduct `f` copies from each card in `[card, card + groupSize - 1]`. Time is O(n log k) where `k` is the number of distinct cards, and space is O(k).

## 127. Merge Triplets to Form Target Triplet

[Back to Index](#index)

**Problem:** Given a 2D integer array `triplets` and an integer array `target = [x, y, z]`, return `true` if you can obtain `target` by repeatedly taking component-wise maximums of selected triplets, or `false` otherwise.

```java
class Solution {
    public boolean mergeTriplets(int[][] triplets, int[] target) {
        boolean match0 = false;
        boolean match1 = false;
        boolean match2 = false;

        for (int[] t : triplets) {
            if (t[0] <= target[0] && t[1] <= target[1] && t[2] <= target[2]) {
                if (t[0] == target[0]) match0 = true;
                if (t[1] == target[1]) match1 = true;
                if (t[2] == target[2]) match2 = true;
            }
        }

        return match0 && match1 && match2;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[][] triplets = {{2, 5, 3}, {1, 8, 4}, {1, 7, 5}};
        int[] target = {2, 7, 5};
        System.out.println(s.mergeTriplets(triplets, target)); // Expected: true
    }
}
```

**Explanation:** Ignore any triplet containing a value exceeding the corresponding target component, as taking a max with it would invalidate that coordinate. Among valid triplets, verify whether triplets exist matching each individual target element. Time is O(n) and space is O(1).

## 128. Partition Labels

[Back to Index](#index)

**Problem:** Given a string `s`, partition it into as many parts as possible so that each letter appears in at most one part, and return a list of integers representing the size of these parts.

```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public List<Integer> partitionLabels(String s) {
        int[] lastIndex = new int[26];
        for (int i = 0; i < s.length(); i++) {
            lastIndex[s.charAt(i) - 'a'] = i;
        }

        List<Integer> result = new ArrayList<>();
        int start = 0;
        int end = 0;

        for (int i = 0; i < s.length(); i++) {
            end = Math.max(end, lastIndex[s.charAt(i) - 'a']);
            if (i == end) {
                result.add(end - start + 1);
                start = i + 1;
            }
        }

        return result;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        String str = "ababcbacadefegdehijhklij";
        System.out.println(s.partitionLabels(str)); // Expected: [9, 7, 8]
    }
}
```

**Explanation:** Precompute the last occurrence of each character. Traverse the string and expand the current partition's boundary `end` to include the last occurrence of each encountered character; when index `i` reaches `end`, close the partition. Time is O(n) and space is O(1) auxiliary space (26 characters).

## 129. Valid Parenthesis String

[Back to Index](#index)

**Problem:** Given a string `s` containing only `'('`, `')'`, and `'*'`, return `true` if `s` is valid. `'*'` can be treated as a single `'('`, a single `')'`, or an empty string `""`.

```java
class Solution {
    public boolean checkValidString(String s) {
        int cmin = 0;
        int cmax = 0;

        for (char c : s.toCharArray()) {
            if (c == '(') {
                cmin++;
                cmax++;
            } else if (c == ')') {
                cmin--;
                cmax--;
            } else { // '*' can be '(', ')', or ''
                cmin--;
                cmax++;
            }

            if (cmax < 0) {
                return false;
            }
            cmin = Math.max(cmin, 0);
        }

        return cmin == 0;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.checkValidString("()"));   // Expected: true
        System.out.println(s.checkValidString("(*)"));  // Expected: true
        System.out.println(s.checkValidString("(*))")); // Expected: true
        System.out.println(s.checkValidString(")("));   // Expected: false
    }
}
```

**Explanation:** Maintain the range `[cmin, cmax]` of possible open parentheses count. `cmin` decreases with `')'` or `'*'` (bounded by 0), and `cmax` increases with `'('` or `'*'`. If `cmax < 0`, more closing parentheses exist than can be balanced; string is valid if `cmin == 0` at the end. Time is O(n) and space is O(1).

---

# Intervals

## 130. Insert Interval

[Back to Index](#index)

**Problem:** Given an array of non-overlapping intervals `intervals` sorted by start time, insert `newInterval` into `intervals` such that the result remains sorted and non-overlapping (merging overlapping intervals as needed).

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

class Solution {
    public int[][] insert(int[][] intervals, int[] newInterval) {
        List<int[]> result = new ArrayList<>();
        int i = 0;
        int n = intervals.length;

        // Add all intervals that come before newInterval
        while (i < n && intervals[i][1] < newInterval[0]) {
            result.add(intervals[i]);
            i++;
        }

        // Merge all overlapping intervals with newInterval
        while (i < n && intervals[i][0] <= newInterval[1]) {
            newInterval[0] = Math.min(newInterval[0], intervals[i][0]);
            newInterval[1] = Math.max(newInterval[1], intervals[i][1]);
            i++;
        }
        result.add(newInterval);

        // Add all intervals that come after newInterval
        while (i < n) {
            result.add(intervals[i]);
            i++;
        }

        return result.toArray(new int[result.size()][]);
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[][] intervals = {{1, 3}, {6, 9}};
        int[] newInterval = {2, 5};
        System.out.println(Arrays.deepToString(s.insert(intervals, newInterval))); // Expected: [[1, 5], [6, 9]]
    }
}
```

**Explanation:** Process the intervals in three linear passes: add intervals that end before `newInterval` starts, merge all intervals overlapping `newInterval` by expanding its bounds, add `newInterval`, then append all remaining intervals. Time is O(n) and space is O(n) for the output list.

## 131. Merge Intervals

[Back to Index](#index)

**Problem:** Given an array of `intervals` where `intervals[i] = [start_i, end_i]`, merge all overlapping intervals, and return an array of non-overlapping intervals that cover all intervals in the input.

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

class Solution {
    public int[][] merge(int[][] intervals) {
        if (intervals.length <= 1) {
            return intervals;
        }

        Arrays.sort(intervals, (a, b) -> Integer.compare(a[0], b[0]));

        List<int[]> merged = new ArrayList<>();
        int[] current = intervals[0];
        merged.add(current);

        for (int i = 1; i < intervals.length; i++) {
            if (intervals[i][0] <= current[1]) {
                current[1] = Math.max(current[1], intervals[i][1]);
            } else {
                current = intervals[i];
                merged.add(current);
            }
        }

        return merged.toArray(new int[merged.size()][]);
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[][] intervals = {{1, 3}, {2, 6}, {8, 10}, {15, 18}};
        System.out.println(Arrays.deepToString(s.merge(intervals))); // Expected: [[1, 6], [8, 10], [15, 18]]
    }
}
```

**Explanation:** Sort intervals by start time. Iterate through the intervals: if the next interval begins before or when the current interval ends, merge them by extending the end time; otherwise, append it as a new interval. Time is O(n log n) due to sorting, and space is O(n) for the result.

## 132. Non-overlapping Intervals

[Back to Index](#index)

**Problem:** Given an array of intervals `intervals` where `intervals[i] = [start_i, end_i]`, return the minimum number of intervals to remove to make the remainder non-overlapping.

```java
import java.util.Arrays;

class Solution {
    public int eraseOverlapIntervals(int[][] intervals) {
        if (intervals.length == 0) {
            return 0;
        }

        Arrays.sort(intervals, (a, b) -> Integer.compare(a[1], b[1]));

        int removed = 0;
        int prevEnd = intervals[0][1];

        for (int i = 1; i < intervals.length; i++) {
            if (intervals[i][0] < prevEnd) {
                removed++;
            } else {
                prevEnd = intervals[i][1];
            }
        }

        return removed;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[][] intervals = {{1, 2}, {2, 3}, {3, 4}, {1, 3}};
        System.out.println(s.eraseOverlapIntervals(intervals)); // Expected: 1
    }
}
```

**Explanation:** Greedy interval scheduling: sort intervals by their end times. Greedily keep the interval that finishes earliest to leave maximum room for subsequent intervals; increment the removal count whenever an overlap occurs. Time is O(n log n) and space is O(log n) auxiliary for sorting.

## 133. Meeting Rooms

[Back to Index](#index)

**Problem:** Given an array of meeting time intervals `intervals` where `intervals[i] = [start_i, end_i]`, determine if a person could attend all meetings without overlap.

```java
import java.util.Arrays;

class Solution {
    public boolean canAttendMeetings(int[][] intervals) {
        Arrays.sort(intervals, (a, b) -> Integer.compare(a[0], b[0]));

        for (int i = 1; i < intervals.length; i++) {
            if (intervals[i][0] < intervals[i - 1][1]) {
                return false;
            }
        }

        return true;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[][] intervals = {{0, 30}, {5, 10}, {15, 20}};
        System.out.println(s.canAttendMeetings(intervals)); // Expected: false

        int[][] intervals2 = {{7, 10}, {2, 4}};
        System.out.println(s.canAttendMeetings(intervals2)); // Expected: true
    }
}
```

**Explanation:** Sort meetings by start time and check if any meeting begins before the previous meeting concludes. If an overlap is found, return `false`; otherwise, return `true`. Time is O(n log n) and space is O(log n) auxiliary for sorting.

## 134. Meeting Rooms II

[Back to Index](#index)

**Problem:** Given an array of meeting time intervals `intervals` where `intervals[i] = [start_i, end_i]`, return the minimum number of conference rooms required.

```java
import java.util.Arrays;
import java.util.PriorityQueue;

class Solution {
    public int minMeetingRooms(int[][] intervals) {
        if (intervals.length == 0) {
            return 0;
        }

        Arrays.sort(intervals, (a, b) -> Integer.compare(a[0], b[0]));
        PriorityQueue<Integer> minHeap = new PriorityQueue<>();

        minHeap.add(intervals[0][1]);

        for (int i = 1; i < intervals.length; i++) {
            if (intervals[i][0] >= minHeap.peek()) {
                minHeap.poll();
            }
            minHeap.add(intervals[i][1]);
        }

        return minHeap.size();
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[][] intervals = {{0, 30}, {5, 10}, {15, 20}};
        System.out.println(s.minMeetingRooms(intervals)); // Expected: 2

        int[][] intervals2 = {{7, 10}, {2, 4}};
        System.out.println(s.minMeetingRooms(intervals2)); // Expected: 1
    }
}
```

**Explanation:** Sort meetings by start time and use a min-heap to track the end times of active meetings. If the next meeting starts after the earliest ending meeting finishes, reuse that room by polling from the heap; then push the new end time. The heap size represents the required rooms. Time is O(n log n) and space is O(n).

## 135. Minimum Interval to Include Each Query

[Back to Index](#index)

**Problem:** Given a 2D integer array `intervals` where `intervals[i] = [left_i, right_i]` and an integer array `queries`, find the minimum size of an interval containing `queries[j]` for each query, or `-1` if none exists. The size of an interval is `right_i - left_i + 1`.

```java
import java.util.Arrays;
import java.util.PriorityQueue;

class Solution {
    public int[] minInterval(int[][] intervals, int[] queries) {
        Arrays.sort(intervals, (a, b) -> Integer.compare(a[0], b[0]));

        int m = queries.length;
        int[][] sortedQueries = new int[m][2];
        for (int i = 0; i < m; i++) {
            sortedQueries[i][0] = queries[i];
            sortedQueries[i][1] = i;
        }
        Arrays.sort(sortedQueries, (a, b) -> Integer.compare(a[0], b[0]));

        // Min-heap storing int[]{intervalLength, intervalEnd} ordered by length
        PriorityQueue<int[]> minHeap = new PriorityQueue<>((a, b) -> Integer.compare(a[0], b[0]));

        int[] result = new int[m];
        int i = 0;
        int n = intervals.length;

        for (int[] q : sortedQueries) {
            int qVal = q[0];
            int qIdx = q[1];

            while (i < n && intervals[i][0] <= qVal) {
                int len = intervals[i][1] - intervals[i][0] + 1;
                minHeap.offer(new int[]{len, intervals[i][1]});
                i++;
            }

            while (!minHeap.isEmpty() && minHeap.peek()[1] < qVal) {
                minHeap.poll();
            }

            result[qIdx] = minHeap.isEmpty() ? -1 : minHeap.peek()[0];
        }

        return result;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[][] intervals = {{1, 4}, {2, 4}, {3, 6}, {4, 4}};
        int[] queries = {2, 3, 4, 5};
        System.out.println(Arrays.toString(s.minInterval(intervals, queries))); // Expected: [3, 3, 1, 4]
    }
}
```

**Explanation:** Sort intervals by start and queries in ascending order (preserving original indices). For each query, push all intervals starting before or at the query point into a min-heap keyed by length, discard intervals that end before the query, and query the top of the heap. Time is O(n log n + q log q) and space is O(n + q).

---

# Math & Geometry

## 136. Rotate Image

[Back to Index](#index)

**Problem:** Given an `n x n` 2D matrix representing an image, rotate the image by 90 degrees clockwise in-place.

```java
import java.util.Arrays;

class Solution {
    public void rotate(int[][] matrix) {
        int n = matrix.length;
        // Transpose matrix
        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                int temp = matrix[i][j];
                matrix[i][j] = matrix[j][i];
                matrix[j][i] = temp;
            }
        }
        // Reverse each row
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n / 2; j++) {
                int temp = matrix[i][j];
                matrix[i][j] = matrix[i][n - 1 - j];
                matrix[i][n - 1 - j] = temp;
            }
        }
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };
        s.rotate(matrix);
        System.out.println(Arrays.deepToString(matrix)); // [[7, 4, 1], [8, 5, 2], [9, 6, 3]]
    }
}
```

**Explanation:** Transpose the matrix across its main diagonal, then reverse each row horizontally to produce a 90-degree clockwise rotation in-place. Time is O(n^2) and space is O(1).

## 137. Spiral Matrix

[Back to Index](#index)

**Problem:** Given an `m x n` matrix, return all elements of the matrix in spiral order.

```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        List<Integer> res = new ArrayList<>();
        if (matrix == null || matrix.length == 0) return res;

        int top = 0, bottom = matrix.length - 1;
        int left = 0, right = matrix[0].length - 1;

        while (top <= bottom && left <= right) {
            // Traverse from left to right along top row
            for (int col = left; col <= right; col++) {
                res.add(matrix[top][col]);
            }
            top++;

            // Traverse downwards along right column
            for (int row = top; row <= bottom; row++) {
                res.add(matrix[row][right]);
            }
            right--;

            // Traverse from right to left along bottom row
            if (top <= bottom) {
                for (int col = right; col >= left; col--) {
                    res.add(matrix[bottom][col]);
                }
                bottom--;
            }

            // Traverse upwards along left column
            if (left <= right) {
                for (int row = bottom; row >= top; row--) {
                    res.add(matrix[row][left]);
                }
                left++;
            }
        }

        return res;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };
        System.out.println(s.spiralOrder(matrix)); // [1, 2, 3, 6, 9, 8, 7, 4, 5]
    }
}
```

**Explanation:** Maintain four boundary pointers (top, bottom, left, right) and cycle through traversing the edges inwards until all boundaries cross. Time is O(m * n) and space is O(1) auxiliary.

## 138. Set Matrix Zeroes

[Back to Index](#index)

**Problem:** Given an `m x n` integer matrix, if an element is 0, set its entire row and column to 0's in-place.

```java
import java.util.Arrays;

class Solution {
    public void setZeroes(int[][] matrix) {
        int m = matrix.length, n = matrix[0].length;
        boolean firstRowZero = false, firstColZero = false;

        // Check if first column has any zero
        for (int i = 0; i < m; i++) {
            if (matrix[i][0] == 0) {
                firstColZero = true;
                break;
            }
        }

        // Check if first row has any zero
        for (int j = 0; j < n; j++) {
            if (matrix[0][j] == 0) {
                firstRowZero = true;
                break;
            }
        }

        // Use first row and column as markers
        for (int i = 1; i < m; i++) {
            for (int j = 1; j < n; j++) {
                if (matrix[i][j] == 0) {
                    matrix[i][0] = 0;
                    matrix[0][j] = 0;
                }
            }
        }

        // Zero out cells based on markers
        for (int i = 1; i < m; i++) {
            for (int j = 1; j < n; j++) {
                if (matrix[i][0] == 0 || matrix[0][j] == 0) {
                    matrix[i][j] = 0;
                }
            }
        }

        // Zero out first row if needed
        if (firstRowZero) {
            for (int j = 0; j < n; j++) {
                matrix[0][j] = 0;
            }
        }

        // Zero out first col if needed
        if (firstColZero) {
            for (int i = 0; i < m; i++) {
                matrix[i][0] = 0;
            }
        }
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        int[][] matrix = {
            {1, 1, 1},
            {1, 0, 1},
            {1, 1, 1}
        };
        s.setZeroes(matrix);
        System.out.println(Arrays.deepToString(matrix)); // [[1, 0, 1], [0, 0, 0], [1, 0, 1]]
    }
}
```

**Explanation:** Use the first row and column of the matrix as state markers for the rest of the cells, with separate boolean flags for the first row and first column themselves. Time is O(m * n) and space is O(1).

## 139. Happy Number

[Back to Index](#index)

**Problem:** Determine if a number `n` is happy, where a happy number eventually reaches 1 when repeatedly replaced by the sum of the squares of its digits.

```java
class Solution {
    public boolean isHappy(int n) {
        int slow = n;
        int fast = getNext(n);

        while (fast != 1 && slow != fast) {
            slow = getNext(slow);
            fast = getNext(getNext(fast));
        }

        return fast == 1;
    }

    private int getNext(int n) {
        int sum = 0;
        while (n > 0) {
            int digit = n % 10;
            sum += digit * digit;
            n /= 10;
        }
        return sum;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.isHappy(19)); // true
        System.out.println(s.isHappy(2));  // false
    }
}
```

**Explanation:** Detect cycles in the sequence of digit-square sums using Floyd's Tortoise and Hare cycle detection algorithm until reaching 1 or detecting a loop. Time is O(log n) and space is O(1).

## 140. Plus One

[Back to Index](#index)

**Problem:** Given a large integer represented as an integer array `digits`, increment the large integer by one and return the resulting array of digits.

```java
import java.util.Arrays;

class Solution {
    public int[] plusOne(int[] digits) {
        for (int i = digits.length - 1; i >= 0; i--) {
            if (digits[i] < 9) {
                digits[i]++;
                return digits;
            }
            digits[i] = 0;
        }

        // If all digits were 9, e.g., 999 -> 1000
        int[] res = new int[digits.length + 1];
        res[0] = 1;
        return res;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(Arrays.toString(s.plusOne(new int[]{1, 2, 3}))); // [1, 2, 4]
        System.out.println(Arrays.toString(s.plusOne(new int[]{9, 9, 9}))); // [1, 0, 0, 0]
    }
}
```

**Explanation:** Iterate from the least significant digit backwards, incrementing and returning immediately if a digit is less than 9; if all digits are 9, prepend 1 to a new array of zeros. Time is O(n) and space is O(1) auxiliary (or O(n) when allocating a new array).

## 141. Pow(x, n)

[Back to Index](#index)

**Problem:** Implement `pow(x, n)`, which calculates `x` raised to the power `n` ($x^n$).

```java
class Solution {
    public double myPow(double x, int n) {
        long exp = n;
        if (exp < 0) {
            x = 1.0 / x;
            exp = -exp;
        }

        double res = 1.0;
        double currentProduct = x;

        while (exp > 0) {
            if ((exp & 1) == 1) {
                res *= currentProduct;
            }
            currentProduct *= currentProduct;
            exp >>= 1;
        }

        return res;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.myPow(2.0, 10));  // 1024.0
        System.out.println(s.myPow(2.1, 3));   // 9.261000000000001
        System.out.println(s.myPow(2.0, -2));  // 0.25
    }
}
```

**Explanation:** Use binary exponentiation (fast power) by squaring the base and halving the exponent at each step, using `long` to prevent overflow when negating `Integer.MIN_VALUE`. Time is O(log n) and space is O(1).

## 142. Multiply Strings

[Back to Index](#index)

**Problem:** Given two non-negative integers `num1` and `num2` represented as strings, return the product of `num1` and `num2`, also represented as a string.

```java
class Solution {
    public String multiply(String num1, String num2) {
        if ("0".equals(num1) || "0".equals(num2)) {
            return "0";
        }

        int m = num1.length(), n = num2.length();
        int[] pos = new int[m + n];

        for (int i = m - 1; i >= 0; i--) {
            int d1 = num1.charAt(i) - '0';
            for (int j = n - 1; j >= 0; j--) {
                int d2 = num2.charAt(j) - '0';
                int mul = d1 * d2;
                int p1 = i + j, p2 = i + j + 1;
                int sum = mul + pos[p2];

                pos[p2] = sum % 10;
                pos[p1] += sum / 10;
            }
        }

        StringBuilder sb = new StringBuilder();
        for (int p : pos) {
            if (!(sb.length() == 0 && p == 0)) {
                sb.append(p);
            }
        }

        return sb.length() == 0 ? "0" : sb.toString();
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.multiply("2", "3"));       // 6
        System.out.println(s.multiply("123", "456"));   // 56088
    }
}
```

**Explanation:** Simulate grade-school manual multiplication by multiplying digits pair by pair and placing products at positions `i + j` and `i + j + 1` in an array, then converting to string without leading zeros. Time is O(m * n) and space is O(m + n).

## 143. Detect Squares

[Back to Index](#index)

**Problem:** Design a data structure that maintains a stream of 2D points and counts the number of ways to form axis-aligned squares with a given query point as one of the four corners.

```java
import java.util.ArrayList;
import java.util.List;

class DetectSquares {
    private int[][] counts;
    private List<int[]> points;

    public DetectSquares() {
        counts = new int[1001][1001];
        points = new ArrayList<>();
    }

    public void add(int[] point) {
        counts[point[0]][point[1]]++;
        points.add(point);
    }

    public int count(int[] point) {
        int px = point[0], py = point[1];
        int total = 0;

        for (int[] p : points) {
            int x = p[0], y = p[1];
            // Must be diagonally opposite: non-zero equal side lengths
            if (px == x || py == y || Math.abs(px - x) != Math.abs(py - y)) {
                continue;
            }
            // Check existence of the other two corners: (px, y) and (x, py)
            total += counts[px][y] * counts[x][py];
        }

        return total;
    }

    public static void main(String[] args) {
        DetectSquares s = new DetectSquares();
        s.add(new int[]{3, 10});
        s.add(new int[]{11, 2});
        s.add(new int[]{3, 2});
        System.out.println(s.count(new int[]{11, 10})); // 1
        System.out.println(s.count(new int[]{14, 8}));  // 0
        s.add(new int[]{11, 2});
        System.out.println(s.count(new int[]{11, 10})); // 2
    }
}
```

**Explanation:** Store point frequencies in a 2D coordinate grid and iterate over potential diagonally opposite corners from added points, multiplying frequencies of the complementary corners `(px, y)` and `(x, py)`. Time is O(1) for `add` and O(N) for `count` where N is the number of points added, and space is O(N).

---

# Bit Manipulation

## 144. Single Number

[Back to Index](#index)

**Problem:** Given a non-empty array of integers `nums`, every element appears twice except for one. Find that single one in linear time and constant extra space.

```java
class Solution {
    public int singleNumber(int[] nums) {
        int res = 0;
        for (int num : nums) {
            res ^= num;
        }
        return res;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.singleNumber(new int[]{2, 2, 1}));       // 1
        System.out.println(s.singleNumber(new int[]{4, 1, 2, 1, 2})); // 4
    }
}
```

**Explanation:** XOR all numbers in the array together; identical pairs cancel out ($x \oplus x = 0$), leaving only the single unique number ($0 \oplus x = x$). Time is O(n) and space is O(1).

## 145. Number of 1 Bits

[Back to Index](#index)

**Problem:** Given a positive integer `n`, return the number of set bits (1s) in its binary representation (Hamming weight).

```java
class Solution {
    public int hammingWeight(int n) {
        int count = 0;
        while (n != 0) {
            n &= (n - 1);
            count++;
        }
        return count;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.hammingWeight(11));  // 3
        System.out.println(s.hammingWeight(128)); // 1
        System.out.println(s.hammingWeight(2147483645)); // 30
    }
}
```

**Explanation:** Use Brian Kernighan's algorithm where `n &= (n - 1)` removes the lowest set bit in each iteration until `n` becomes 0. Time is O(k) where k is the number of 1-bits ($\le 32$, so O(1)) and space is O(1).

## 146. Counting Bits

[Back to Index](#index)

**Problem:** Given an integer `n`, return an array `ans` of length `n + 1` such that for each `i` (`0 <= i <= n`), `ans[i]` is the number of 1's in the binary representation of `i`.

```java
import java.util.Arrays;

class Solution {
    public int[] countBits(int n) {
        int[] ans = new int[n + 1];
        for (int i = 1; i <= n; i++) {
            ans[i] = ans[i >> 1] + (i & 1);
        }
        return ans;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(Arrays.toString(s.countBits(2))); // [0, 1, 1]
        System.out.println(Arrays.toString(s.countBits(5))); // [0, 1, 1, 2, 1, 2]
    }
}
```

**Explanation:** Apply dynamic programming where the number of set bits in `i` equals the number of set bits in `i >> 1` plus `1` if `i` is odd (`i & 1`). Time is O(n) and space is O(1) auxiliary (excluding the returned array).

## 147. Reverse Bits

[Back to Index](#index)

**Problem:** Reverse the bits of a given 32-bit unsigned integer.

```java
class Solution {
    public int reverseBits(int n) {
        int res = 0;
        for (int i = 0; i < 32; i++) {
            res = (res << 1) | (n & 1);
            n >>>= 1;
        }
        return res;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.reverseBits(43261596)); // 964176192
    }
}
```

**Explanation:** Iterate 32 times, shifting `res` left and appending the lowest bit of `n`, then logically shifting `n` to the right with `>>>= 1`. Time is O(1) and space is O(1).

## 148. Missing Number

[Back to Index](#index)

**Problem:** Given an array `nums` containing `n` distinct numbers in the range `[0, n]`, return the only number in the range that is missing from the array.

```java
class Solution {
    public int missingNumber(int[] nums) {
        int res = nums.length;
        for (int i = 0; i < nums.length; i++) {
            res ^= i ^ nums[i];
        }
        return res;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.missingNumber(new int[]{3, 0, 1}));                   // 2
        System.out.println(s.missingNumber(new int[]{0, 1}));                      // 2
        System.out.println(s.missingNumber(new int[]{9, 6, 4, 2, 3, 5, 7, 0, 1})); // 8
    }
}
```

**Explanation:** XOR all values from `0` to `n` with all elements present in the array; duplicate values cancel out to 0, leaving the missing number. Time is O(n) and space is O(1).

## 149. Sum of Two Integers

[Back to Index](#index)

**Problem:** Given two integers `a` and `b`, return the sum of the two integers without using the operators `+` and `-`.

```java
class Solution {
    public int getSum(int a, int b) {
        while (b != 0) {
            int carry = (a & b) << 1;
            a = a ^ b;
            b = carry;
        }
        return a;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.getSum(1, 2));   // 3
        System.out.println(s.getSum(2, 3));   // 5
        System.out.println(s.getSum(-2, 3));  // 1
    }
}
```

**Explanation:** Simulate half-adder addition using XOR (`a ^ b`) to compute the sum without carry and AND shifted left (`(a & b) << 1`) to calculate the carry, iterating until the carry is zero. Time is O(1) and space is O(1).

## 150. Reverse Integer

[Back to Index](#index)

**Problem:** Given a signed 32-bit integer `x`, return `x` with its digits reversed. If reversing `x` causes the value to go outside the signed 32-bit integer range `[-2^31, 2^31 - 1]`, return 0.

```java
class Solution {
    public int reverse(int x) {
        int res = 0;
        while (x != 0) {
            int pop = x % 10;
            x /= 10;

            // Check for potential overflow before multiplying by 10
            if (res > Integer.MAX_VALUE / 10 || (res == Integer.MAX_VALUE / 10 && pop > 7)) {
                return 0;
            }
            if (res < Integer.MIN_VALUE / 10 || (res == Integer.MIN_VALUE / 10 && pop < -8)) {
                return 0;
            }

            res = res * 10 + pop;
        }
        return res;
    }

    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.reverse(123));         // 321
        System.out.println(s.reverse(-123));        // -321
        System.out.println(s.reverse(120));         // 21
        System.out.println(s.reverse(1534236469));  // 0
    }
}
```

**Explanation:** Extract digits from the end of `x` and append them to `res`, checking against 32-bit integer boundaries before multiplying by 10 to prevent arithmetic overflow. Time is O(log10(|x|)) and space is O(1).
