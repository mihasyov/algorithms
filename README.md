# Algorithms

## Table of contents

    1. [Two Sum](https://github.com/mihasyov/algorithms#Two-Sum)
    2. [Reverse Integer](https://github.com/mihasyov/algorithms#Reverse-Integer)
    3. [Palindrome Number](https://github.com/mihasyov/algorithms#Palindrome-Number)
    4. [Roman To Integer](https://github.com/mihasyov/algorithms#Roman-To-Integer)
    5. [Longest Common Prefix](https://github.com/mihasyov/algorithms#Longest-Common-Prefix)
    6. [Valid Parentheses](https://github.com/mihasyov/algorithms#Valid-Parentheses)
    7. [Merge Two Sorted Lists](https://github.com/mihasyov/algorithms#Merge-Two-Sorted-Lists)
    8. [Remove Duplicates from Sorted Array](https://github.com/mihasyov/algorithms#Remove-Duplicates-from-Sorted-Array)
    9. [Remove Element](https://github.com/mihasyov/algorithms#Remove-Element)
    10. [Implement strStr](https://github.com/mihasyov/algorithms#Implement-strStr)
    11. [Search Insert Position](https://github.com/mihasyov/algorithms#Search-Insert-Position)
    12. [Maximum Subarray](https://github.com/mihasyov/algorithms#Maximum-Subarray)
    13. [Length of Last Word](https://github.com/mihasyov/algorithms#Length-of-Last-Word)
    14. [Plus One](https://github.com/mihasyov/algorithms#Plus-One)
    15. [Climbing Stairs](https://github.com/mihasyov/algorithms#Climbing-Stairs)
    16. [Merge Sorted Array](https://github.com/mihasyov/algorithms#Merge-Sorted-Array)
    17. [Pascal's Triangle](https://github.com/mihasyov/algorithms#Pascal's-Triangle)
    18. [Pascal's Triangle II](https://github.com/mihasyov/algorithms#Pascal's-Triangle-II)
    19. [Best Time to Buy and Sell Stock](https://github.com/mihasyov/algorithms#Best-Time-to-Buy-and-Sell-Stock)
    20. [Best Time to Buy and Sell Stock II](https://github.com/mihasyov/algorithms#Best-Time-to-Buy-and-Sell-Stock-II)
    21. [Valid Palindrome](https://github.com/mihasyov/algorithms#Valid-Palindrome)
    22. [Single Number](https://github.com/mihasyov/algorithms#Single-Number)
    23. [Two Sum II](https://github.com/mihasyov/algorithms#Two-Sum-II)
    24. [Majority Element](https://github.com/mihasyov/algorithms#Majority-Element)
    25. [Factorial Trailing Zeroes](https://github.com/mihasyov/algorithms#Factorial-Trailing-Zeroes)

## **Two Sum**

Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

Example 1:

```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Output: Because nums[0] + nums[1] == 9, we return [0, 1].
```

Example 2:

```
Input: nums = [3,2,4], target = 6
Output: [1,2]
```

Example 3:

```
Input: nums = [3,3], target = 6
Output: [0,1]
```

Constraints:

```
2 <= nums.length <= 104
-109 <= nums[i] <= 109
-109 <= target <= 109
Only one valid answer exists.
```

Follow-up: Can you come up with an algorithm that is less than O(n2) time complexity?

**Solution:**

```javascript
const twoSum = (nums, target) => {
  const map = new Map();

  for (let i = 0; i < nums.length; i++) {
    if (map.has(target - nums[i])) return [map.get(target - nums[i]), i];

    map.set(nums[i], i);
  }

  return null;
};
```

## **Reverse Integer**

Given a signed 32-bit integer x, return x with its digits reversed. If reversing x causes the value to go outside the signed 32-bit integer range [-231, 231 - 1], then return 0.

Assume the environment does not allow you to store 64-bit integers (signed or unsigned).

Example 1:

```
Input: x = 123
Output: 321
```

Example 2:

```
Input: x = -123
Output: -321
```

Example 3:

```
Input: x = 120
Output: 21
```

Example 4:

```
Input: x = 0
Output: 0
```

**Solution:**

```javascript
const reverse = (num) => {
  if (num > -10 && num < 10) return num;

  const absNumber = Math.abs(num);

  let numReversed = +absNumber.toString().split("").reverse().join("");

  numReversed = num < 0 ? -numReversed : numReversed;

  if (numReversed >= VALUES.max || numReversed <= VALUES.min) return 0;

  return numReversed;
};
```

## **Palindrome Number**

Given an integer x, return true if x is palindrome integer.

An integer is a palindrome when it reads the same backward as forward. For example, 121 is palindrome while 123 is not.

Example 1:

```
Input: x = 121
Output: true
```

Example 2:

```
Input: x = -121
Output: false
Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.
```

Example 3:

```
Input: x = 10
Output: false
Explanation: Reads 01 from right to left. Therefore it is not a palindrome.
```

Example 4:

```
Input: x = -101
Output: false
```

Constraints:

```
-231 <= x <= 231 - 1
```

Follow up: Could you solve it without converting the integer to a string?

**Solution:**

```javascript
const isPalindrome = (x) => {
  if (x < 0) return false;
  if (x < 9) return true;

  x = x.toString();

  let i = 0;
  let j = x.length - 1;

  while (i < j) {
    if (x[i] !== x[j]) {
      return false;
    } else {
      i++;
      j--;
    }
  }
  return true;
};
```

## **Roman To Integer**

Roman numerals are represented by seven different symbols: I, V, X, L, C, D and M.

Symbol Value
I 1
V 5
X 10
L 50
C 100
D 500
M 1000
For example, 2 is written as II in Roman numeral, just two one's added together. 12 is written as XII, which is simply X + II. The number 27 is written as XXVII, which is XX + V + II.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not IIII. Instead, the number four is written as IV. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as IX. There are six instances where subtraction is used:

I can be placed before V (5) and X (10) to make 4 and 9.
X can be placed before L (50) and C (100) to make 40 and 90.
C can be placed before D (500) and M (1000) to make 400 and 900.
Given a roman numeral, convert it to an integer.

Example 1:

```
Input: s = "III"
Output: 3
```

Example 2:

```
Input: s = "IV"
Output: 4
```

Example 3:

```
Input: s = "IX"
Output: 9
```

Example 4:

```
Input: s = "LVIII"
Output: 58
Explanation: L = 50, V= 5, III = 3.
```

Example 5:

```
Input: s = "MCMXCIV"
Output: 1994
Explanation: M = 1000, CM = 900, XC = 90 and IV = 4.
```

Constraints:

```
1 <= s.length <= 15
s contains only the characters ('I', 'V', 'X', 'L', 'C', 'D', 'M').
It is guaranteed that s is a valid roman numeral in the range [1, 3999].
```

**Solution:**

```javascript
const ROMAN = {
  I: 1,
  V: 5,
  X: 10,
  L: 50,
  C: 100,
  D: 500,
  M: 1000,
};

const romanTOInteger = (roman) => {
  let value = 0;

  for (let i = 0; i < roman.length; i++) {
    if (ROMAN[roman[i]] < ROMAN[roman[i + 1]]) {
      value -= ROMAN[roman[i]];
    } else {
      value += ROMAN[roman[i]];
    }
  }

  return value;
};
```

## **Longest Common Prefix**

Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

Example 1:

```
Input: strs = ["flower","flow","flight"]
Output: "fl"
```

Example 2:

```
Input: strs = ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
```

Constraints:

```
1 <= strs.length <= 200
0 <= strs[i].length <= 200
strs[i] consists of only lower-case English letters.
```

**Solution:**

```javascript
const longestCommonPrefix_1 = (strs) => {
  if (strs == null || strs.length <= 0) return "";

  let sorted = strs.sort((a, b) => a.length - b.length);
  let shortestStr = sorted[0];

  while (!strs.every((str) => str.startsWith(shortestStr))) {
    if (shortestStr.length === 0) return;

    shortestStr = shortestStr.slice(0, -1);
  }

  return shortestStr;
};

const longestCommonPrefix_2 = (strs) => {
  if (strs.length === 0) return "";

  let prefix = strs[0];

  for (let i = 0; i < prefix.length; i++) {
    if (strs.some((str) => str[i] !== prefix[i])) return prefix.slice(0, i);
  }

  return prefix;
};
```

## **Valid Parentheses**

Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.

Example 1:

```
Input: s = "()"
Output: true
```

Example 2:

```
Input: s = "()[]{}"
Output: true
```

Example 3:

```
Input: s = "(]"
Output: false
```

Example 4:

```
Input: s = "([)]"
Output: false
```

Example 5:

```
Input: s = "{[]}"
Output: true
```

Constraints:

```
1 <= s.length <= 104
s consists of parentheses only '()[]{}'.
```

**Solution:**

```javascript
const isValid = (str) => {
  if (!str || str.length === 0) return "No string";
  const stack = [];

  for (bracket of str) {
    switch (bracket) {
      case "[":
        stack.push("]");
        break;

      case "{":
        stack.push("}");
        break;

      case "(":
        stack.push(")");
        break;

      default:
        if (bracket !== stack.pop()) return false;
    }
  }

  return stack.length === 0;
};
```

## **Merge Two Sorted Lists**

Merge two sorted linked lists and return it as a sorted list. The list should be made by splicing together the nodes of the first two lists.

Example 1:

```
Input: l1 = [1,2,4], l2 = [1,3,4]
Output: [1,1,2,3,4,4]
```

Example 2:

```
Input: l1 = [], l2 = []
Output: []
```

Example 3:

```
Input: l1 = [], l2 = [0]
Output: [0]
```

Constraints:

```
The number of nodes in both lists is in the range [0, 50].
-100 <= Node.val <= 100
Both l1 and l2 are sorted in non-decreasing order.
```

**Solution:**

```javascript
const mergeLists = (l1, l2) => {
  let mergedHead = { next: null };
  let crt = mergedHead;

  while (l1 && l2) {
    if (l1.value > l2.value) {
      crt.next = l2;
      l2 = l2.next;
    } else {
      crt.next = l1;
      l1 = l1.next;
    }
    crt = crt.next;
  }
  crt.next = l1 || l2;
  return mergedHead.next;
};

const newMergeLists = (l1, l2) => {
  if (!l1 || !l2) return l1 || l2;

  if (l1.value < l2.value) {
    l1.next = newMergeLists(l1.next, l2);
    return l1;
  }
  l2.next = newMergeLists(l1, l2.next);
  return l2;
};
```

## **Remove Duplicates from Sorted Array**

Given a sorted array nums, remove the duplicates in-place such that each element appears only once and returns the new length.

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.

Clarification:

Confused why the returned value is an integer but your answer is an array?

Note that the input array is passed in by reference, which means a modification to the input array will be known to the caller as well.

Internally you can think of this:

// nums is passed in by reference. (i.e., without making a copy)

```
int len = removeDuplicates(nums);
```

// any modification to nums in your function would be known by the caller.
// using the length returned by your function, it prints the first len elements.

```
for (int i = 0; i < len; i++) {
print(nums[i]);
}
```

Example 1:

```
Input: nums = [1,1,2]
Output: 2, nums = [1,2]
Explanation: Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively. It doesn't matter what you leave beyond the returned length.
```

Example 2:

```
Input: nums = [0,0,1,1,1,2,2,3,3,4]
Output: 5, nums = [0,1,2,3,4]
Explanation: Your function should return length = 5, with the first five elements of nums being modified to 0, 1, 2, 3, and 4 respectively. It doesn't matter what values are set beyond the returned length.
```

Constraints:

```
0 <= nums.length <= 3 \* 104
-104 <= nums[i] <= 104
nums is sorted in ascending order.
```

**Solution:**

```javascript
const removeDuplicates = (nums) => {
  if (nums.length <= 1) return nums.length;

  let i = 0;
  for (let j = 1; j < nums.length; j++) {
    if (nums[j] !== nums[i]) nums[++i] = nums[j];
  }

  return {
    length: ++i,
    uniqueArr: nums.slice(0, i),
  };
};
```

## **Remove Element**

Given an array nums and a value val, remove all instances of that value in-place and return the new length.

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.

The order of elements can be changed. It doesn't matter what you leave beyond the new length.

Clarification:

Confused why the returned value is an integer but your answer is an array?

Note that the input array is passed in by reference, which means a modification to the input array will be known to the caller as well.

Internally you can think of this:

// nums is passed in by reference. (i.e., without making a copy)

```
int len = removeElement(nums, val);
```

// any modification to nums in your function would be known by the caller.
// using the length returned by your function, it prints the first len elements.

```
for (int i = 0; i < len; i++) {
print(nums[i]);
}
```

Example 1:

```
Input: nums = [3,2,2,3], val = 3
Output: 2, nums = [2,2]
Explanation: Your function should return length = 2, with the first two elements of nums being 2.
It doesn't matter what you leave beyond the returned length. For example if you return 2 with nums = [2,2,3,3] or nums = [2,2,0,0], your answer will be accepted.
```

Example 2:

```
Input: nums = [0,1,2,2,3,0,4,2], val = 2
Output: 5, nums = [0,1,4,0,3]
Explanation: Your function should return length = 5, with the first five elements of nums containing 0, 1, 3, 0, and 4. Note that the order of those five elements can be arbitrary. It doesn't matter what values are set beyond the returned length.
```

Constraints:

```
0 <= nums.length <= 100
0 <= nums[i] <= 50
0 <= val <= 100
```

**Solution:**

```javascript
const removeEl = (nums, val) => {
  for (let i = 0; i < nums.length; i++) {
    if (nums[i] == val) nums.splice(i--, 1);
  }

  return {
    length: nums.length,
    filteredArr: nums,
  };
};

const removeElem = (nums, val) => {
  while (nums.indexOf(val) >= 0) {
    nums.splice(nums.indexOf(val), 1);
  }

  return {
    length: nums.length,
    filteredArr: nums,
  };
};
```

## **Implement strStr**

Return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

Clarification:

What should we return when needle is an empty string? This is a great question to ask during an interview.

For the purpose of this problem, we will return 0 when needle is an empty string. This is consistent to C's strstr() and Java's indexOf().

Example 1:

```
Input: haystack = "hello", needle = "ll"
Output: 2
```

Example 2:

```
Input: haystack = "aaaaa", needle = "bba"
Output: -1
```

Example 3:

```
Input: haystack = "", needle = ""
Output: 0
```

Constraints:

```
0 <= haystack.length, needle.length <= 5 \* 104
haystack and needle consist of only lower-case English characters.
```

**Solution:**

```javascript
const strStr = (str, needle) => {
  if (str === needle || needle === "") return 0;
  if (str.length < needle.length) return -1;

  for (let i = 0; i < str.length; i++) {
    if (str[i] === needle[0]) {
      let temp = str.substr(i, needle.length);
      if (temp === needle) return i;
    }
  }
  return -1;
};
```

## **Search Insert Position**

Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You must write an algorithm with O(log n) runtime complexity.

Example 1:

```
Input: nums = [1,3,5,6], target = 5
Output: 2

```

Example 2:

```

Input: nums = [1,3,5,6], target = 2
Output: 1

```

Example 3:

```

Input: nums = [1,3,5,6], target = 7
Output: 4

```

Example 4:

```

Input: nums = [1,3,5,6], target = 0
Output: 0

```

Example 5:

```

Input: nums = [1], target = 0
Output: 0

```

Constraints:

```

1 <= nums.length <= 104
-104 <= nums[i] <= 104
nums contains distinct values sorted in ascending order.
-104 <= target <= 104

```

**Solution:**

```javascript
const searchPosition = (nums, target) => {
  if (!nums.length) return 0;
  let left = 0;
  let right = nums.length - 1;

  while (left < right) {
    let mid = left + Math.floor((right - left) / 2);
    if (nums[mid] === target) return mid;
    if (nums[mid] > target) right = mid - 1;
    if (nums[mid] < target) left = mid + 1;
  }
  return nums[left] < target ? left + 1 : left;
};
```

## **Maximum Subarray**

Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

Example 1:

```
Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.
```

Example 2:

```
Input: nums = [1]
Output: 1
```

Example 3:

```
Input: nums = [5,4,-1,7,8]
Output: 23
```

Constraints:

```
1 <= nums.length <= 3 \* 104
-105 <= nums[i] <= 105
```

Follow up: If you have figured out the O(n) solution, try coding another solution using the divide and conquer approach, which is more subtle.

**Solution:**

```javascript
const maxSubArr_1 = (arr) => {
  let maxSum = 0;
  let partialSum = 0;

  for (let item of arr) {
    partialSum += item;
    maxSum = Math.max(maxSum, partialSum);
    if (partialSum < 0) partialSum = 0;
  }
  return maxSum;
};

const maxSubArr_2 = (arr) => {
  for (let i = 1; i < arr.length; i++) {
    arr[i] = Math.max(arr[i], arr[i] + arr[i - 1]);
  }
  return Math.max(...arr);
};

const maxSubArr_3 = (arr) => {
  let prev = 0;
  let maxSum = -Number.MAX_VALUE;

  for (let i = 0; i < arr.length; i++) {
    prev = Math.max(arr[i], arr[i] + prev);
    maxSum = Math.max(prev, maxSum);
  }
  return maxSum;
};

const maxSubArr_4 = (arr) => {
  let tmp = [];
  for (let i = 0; i < arr.length; i++) {
    if (i == 0) {
      tmp.push(arr[i]);
    } else {
      tmp[i] = Math.max(arr[i], tmp[i - 1] + arr[i]);
    }
  }
  return Math.max(...tmp);
};
```

## **Length of Last Word**

Given a string s consists of some words separated by spaces, return the length of the last word in the string. If the last word does not exist, return 0.

A word is a maximal substring consisting of non-space characters only.

Example 1:

```
Input: s = "Hello World"
Output: 5
```

Example 2:

```
Input: s = " "
Output: 0
```

Constraints:

```
1 <= s.length <= 104
s consists of only English letters and spaces ' '.
```

**Solution:**

```javascript
const lengthOfLastWord_1 = (str) => {
  if (!str.length) return 0;
  let length = 0;
  for (let i = str.length - 1; i >= 0; i--) {
    if (str[i] == " " && length !== 0) {
      return length;
    } else if (str[i] !== " ") {
      length++;
      if (i == 0) return length;
    }
  }
};

const lengthOfLastWord_2 = (str) => {
  return str.trim().split(" ").pop().length;
};

const lengthOfLastWord_3 = (str) => {
  str = str.trim();
  return str.substr(str.lastIndexOf(" ") + 1).length;
};
```

## **Plus One**

Given a non-empty array of decimal digits representing a non-negative integer, increment one to the integer.

The digits are stored such that the most significant digit is at the head of the list, and each element in the array contains a single digit.

You may assume the integer does not contain any leading zero, except the number 0 itself.

Example 1:

```
Input: digits = [1,2,3]
Output: [1,2,4]
Explanation: The array represents the integer 123.
```

Example 2:

```
Input: digits = [4,3,2,1]
Output: [4,3,2,2]
Explanation: The array represents the integer 4321.
```

Example 3:

```
Input: digits = [0]
Output: [1]
```

Constraints:

```
1 <= digits.length <= 100
0 <= digits[i] <= 9
```

**Solution:**

```javascript
const plusOne = (arr) => {
  for (let i = arr.length - 1; i >= 0; i--) {
    if (++arr[i] > 9) arr[i] = 0;
    else return arr;
  }
  return [1, ...arr];
};
```

## **Climbing Stairs**

You are climbing a staircase. It takes n steps to reach the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

Example 1:

```
Input: n = 2
Output: 2
Explanation: There are two ways to climb to the top.
1. 1 step + 1 step
2. 2 steps
```

Example 2:

```
Input: n = 3
Output: 3
Explanation: There are three ways to climb to the top.

1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step
```

Constraints:

```
1 <= n <= 45
```

**Solution:**

```javascript
const climbStair = (n) => {
  if (n == 0) return 0;
  if (n == 1) return 1;
  if (n == 2) return 2;

  let twoStepbefore = 1;
  let oneStepbefore = 2;
  let steps = 0;
  for (let i = 2; i < n; i++) {
    steps = oneStepbefore + twoStepbefore;
    twoStepbefore = oneStepbefore;
    oneStepbefore = steps;
  }

  return steps;
};
```

## **Merge Sorted Array**

You are given two integer arrays nums1 and nums2, sorted in non-decreasing order, and two integers m and n, representing the number of elements in nums1 and nums2 respectively.

Merge nums1 and nums2 into a single array sorted in non-decreasing order.

The final sorted array should not be returned by the function, but instead be stored inside the array nums1. To accommodate this, nums1 has a length of m + n, where the first m elements denote the elements that should be merged, and the last n elements are set to 0 and should be ignored. nums2 has a length of n.

Example 1:

```
Input: nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3
Output: [1,2,2,3,5,6]
Explanation: The arrays we are merging are [1,2,3] and [2,5,6].
The result of the merge is [1,2,2,3,5,6] with the underlined elements coming from nums1.
```

Example 2:

```
Input: nums1 = [1], m = 1, nums2 = [], n = 0
Output: [1]
Explanation: The arrays we are merging are [1] and [].
The result of the merge is [1].
```

Example 3:

```
Input: nums1 = [0], m = 0, nums2 = [1], n = 1
Output: [1]
Explanation: The arrays we are merging are [] and [1].
The result of the merge is [1].
Note that because m = 0, there are no elements in nums1. The 0 is only there to ensure the merge result can fit in nums1.
```

Constraints:

```
nums1.length == m + n
nums2.length == n
0 <= m, n <= 200
1 <= m + n <= 200
-109 <= nums1[i], nums2[j] <= 109
```

Follow up: Can you come up with an algorithm that runs in O(m + n) time?

**Solution:**

```javascript
const mergeArrs = (arr1, arr2) => {
  let tail1 = arr1.length - 1;
  let tail2 = arr2.length - 1;
  let mergedArrLength = arr1.length + arr2.length - 1;

  while (tail1 >= 0 && tail2 >= 0) {
    arr[mergedArrLength--] =
      arr1[tail1] > arr2[tail2] ? arr1[tail1--] : arr2[tail2--];
  }

  while (tail2 >= 0) {
    arr1[mergedArrLength--] = arr2[tail2--];
  }
  return arr1;
};
```

## **Pascal's Triangle**

Given an integer numRows, return the first numRows of Pascal's triangle.

In Pascal's triangle, each number is the sum of the two numbers directly above it.

Example 1:

```
Input: numRows = 5
Output: [[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]
```

Example 2:

```
Input: numRows = 1
Output: [[1]]
```

Constraints:

```
1 <= numRows <= 30
```

**Solution:**

```javascript
const generate_1 = (rowsNum) => {
  if (!rowsNum || rowsNum <= 0) return [];
  const pascalTriangle = [];
  for (let i = 0; i < rowsNum; i++) {
    pascalTriangle[i] = [];
    for (let j = 0; j <= i; j++) {
      if (j === 0 || j === i) {
        pascalTriangle[i][j] = 1;
      } else {
        pascalTriangle[i][j] =
          pascalTriangle[i - 1][j] + pascalTriangle[i - 1][j - 1];
      }
    }
  }
  return pascalTriangle;
};

const generate_2 = (rowsNum) => {
  if (!rowsNum || rowsNum <= 0) return [];
  const pascal = [[1]];
  for (let i = 1; i < rowsNum; i++) {
    const prevRow = pascal[pascal.length - 1];
    const shiftLeft = [...prevRow, 0];
    const shiftRight = [0, ...prevRow];
    const currentRow = shiftLeft.map((num, i) => num + shiftRight[i]);
    pascal.push(currentRow);
  }
  return pascal;
};
```

## **Pascal's Triangle II**

Given an integer rowIndex, return the rowIndexth (0-indexed) row of the Pascal's triangle.

In Pascal's triangle, each number is the sum of the two numbers directly above it.

Example 1:

```
Input: rowIndex = 3
Output: [1,3,3,1]
```

Example 2:

```
Input: rowIndex = 0
Output: [1]
```

Example 3:

```
Input: rowIndex = 1
Output: [1,1]
```

Constraints:

```
0 <= rowIndex <= 33
```

Follow up: Could you optimize your algorithm to use only O(rowIndex) extra space?

**Solution:**

```javascript
const getRow = (rowIndex) => {
  const arr = [1];
  if (rowIndex === 0) return arr;
  let pre = 1;
  for (let i = 0; i < rowIndex; i++) {
    pre = (pre * (rowIndex - i)) / (i + 1);
    arr.push(pre);
  }
  return arr;
};
```

## **Best Time to Buy and Sell Stock**

You are given an array prices where prices[i] is the price of a given stock on the ith day.

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.

Example 1:

```
Input: prices = [7,1,5,3,6,4]
Output: 5
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.
```

Example 2:

```
Input: prices = [7,6,4,3,1]
Output: 0
Explanation: In this case, no transactions are done and the max profit = 0.
```

Constraints:

```
1 <= prices.length <= 105
0 <= prices[i] <= 104
```

**Solution:**

```javascript
const maxProfit_1 = (stocks) => {
  let currentProfit = 0;
  let maxProfit = 0;

  for (let i = 1; i < stocks.length; i++) {
    currentProfit = Math.max(0, (currentProfit += stocks[i] - stocks[i - 1]));
    maxProfit = Math.max(currentProfit, maxProfit);
  }
  return maxProfit;
};

const maxProfit_2 = (stocks) => {
  let buyPrice = Number.MAX_SAFE_INTEGER;
  let max = 0;
  for (let i = 0; i < stocks.length; i++) {
    buyPrice = Math.min(buyPrice, stocks[i]);
    max = Math.max(max, stocks[i] - buyPrice);
  }
  return max;
};
```

## **Best Time to Buy and Sell Stock II**

You are given an array prices where prices[i] is the price of a given stock on the ith day.

Find the maximum profit you can achieve. You may complete as many transactions as you like (i.e., buy one and sell one share of the stock multiple times).

Note: You may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).

Example 1:

```
Input: prices = [7,1,5,3,6,4]
Output: 7
Explanation: Buy on day 2 (price = 1) and sell on day 3 (price = 5), profit = 5-1 = 4.
Then buy on day 4 (price = 3) and sell on day 5 (price = 6), profit = 6-3 = 3.
```

Example 2:

```
Input: prices = [1,2,3,4,5]
Output: 4
Explanation: Buy on day 1 (price = 1) and sell on day 5 (price = 5), profit = 5-1 = 4.
Note that you cannot buy on day 1, buy on day 2 and sell them later, as you are engaging multiple transactions at the same time. You must sell before buying again.
```

Example 3:

```
Input: prices = [7,6,4,3,1]
Output: 0
Explanation: In this case, no transaction is done, i.e., max profit = 0.
```

Constraints:

```
1 <= prices.length <= 3 \* 104
0 <= prices[i] <= 104
```

**Solution:**

```javascript
const maxMultipleProfit_1 = (stocks) => {
  let lastBuy = -stocks[0];
  let lastSold = 0;

  let currentBuy, currentSold;

  for (let i = 0; i < stocks.length; i++) {
    currentBuy = Math.max(lastBuy, lastSold - stocks[i]);
    currentSold = Math.max(lastSold, lastBuy + stocks[i]);

    lastBuy = currentBuy;
    lastSold = currentSold;
  }
  return lastSold;
};

const maxMultipleProfit_2 = (stocks) => {
  let profit = 0;
  for (let i = 1; i < stocks.length; i++) {
    profit += Math.max(0, stocks[i] - stocks[i - 1]);
  }
  return profit;
};
```

## **Valid Palindrome**

Given a string s, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

Example 1:

```
Input: s = "A man, a plan, a canal: Panama"
Output: true
Explanation: "amanaplanacanalpanama" is a palindrome.
```

Example 2:

```
Input: s = "race a car"
Output: false
Explanation: "raceacar" is not a palindrome.
```

Constraints:

```
1 <= s.length <= 2 \* 105
s consists only of printable ASCII characters.
```

**Solution:**

```javascript
const isAlphaNumeric = (char) => {
  return /[a-z]|\d/i.test(char);
};
const isPalindrome = (str) => {
  if (str.length == 0) return false;

  let start = 0;
  let end = str.length - 1;

  while (start < end) {
    if (!isAlphaNumeric(str[start])) {
      start++;
      continue;
    }
    if (!isAlphaNumeric(str[end])) {
      end--;
      continue;
    }

    if (str[start++].toLowerCase() === str[end--].toLowerCase()) {
      continue;
    } else {
      return false;
    }
  }
  return true;
};
```

## **Single Number**

Given a non-empty array of integers nums, every element appears twice except for one. Find that single one.

You must implement a solution with a linear runtime complexity and use only constant extra space.

Example 1:

```
Input: nums = [2,2,1]
Output: 1
```

Example 2:

```
Input: nums = [4,1,2,1,2]
Output: 4
```

Example 3:

```
Input: nums = [1]
Output: 1
```

Constraints:

```
1 <= nums.length <= 3 _ 104
-3 _ 104 <= nums[i] <= 3 \* 104
Each element in the array appears twice except for one element which appears only once.
```

**Solution:**

```javascript
const singleNumber = (nums) => {
  return nums.reduce((prev, current) => prev ^ current, 0);
};
```

## **Two Sum II**

Given an array of integers numbers that is already sorted in non-decreasing order, find two numbers such that they add up to a specific target number.

Return the indices of the two numbers (1-indexed) as an integer array answer of size 2, where 1 <= answer[0] < answer[1] <= numbers.length.

The tests are generated such that there is exactly one solution. You may not use the same element twice.

Example 1:

```
Input: numbers = [2,7,11,15], target = 9
Output: [1,2]
Explanation: The sum of 2 and 7 is 9. Therefore index1 = 1, index2 = 2.
```

Example 2:

```
Input: numbers = [2,3,4], target = 6
Output: [1,3]
```

Example 3:

```
Input: numbers = [-1,0], target = -1
Output: [1,2]
```

Constraints:

```
2 <= numbers.length <= 3 \* 104
-1000 <= numbers[i] <= 1000
numbers is sorted in non-decreasing order.
-1000 <= target <= 1000
```

The tests are generated such that there is exactly one solution.

**Solution:**

```javascript
const twoSum2 = (nums, target) => {
  let i = 0;
  let j = nums.length - 1;
  let sum = nums[i] + nums[j];

  while (sum !== target) {
    if (i > j) return [];
    nums[i] + nums[j] > target ? j-- : i++;
    sum = nums[i] + nums[j];
  }

  return [i + 1, j + 1];
};
```

## **Majority Element**

Given an array nums of size n, return the majority element.

The majority element is the element that appears more than ⌊n / 2⌋ times. You may assume that the majority element always exists in the array.

Example 1:

```
Input: nums = [3,2,3]
Output: 3
```

Example 2:

```
Input: nums = [2,2,1,1,1,2,2]
Output: 2
```

Constraints:

```
n == nums.length
1 <= n <= 5 \* 104
-231 <= nums[i] <= 231 - 1
```

Follow-up: Could you solve the problem in linear time and in O(1) space?

**Solution:**

```javascript
const findMajorityEl_1 = (nums) => {
  nums.sort();
  const mid = Math.ceil(nums.length / 2);

  if (nums[mid] == nums[mid + 1] || nums[mid] == nums[mid - 1])
    return nums[mid];
  return null;
};

const findMajorityEl_2 = (nums) => {
  let cur = 0;
  let counter = 0;
  for (let num of nums) {
    if (counter === 0) {
      cur = num;
      counter;
    } else if (cur === x) {
      counter++;
    } else {
      counter--;
    }
  }
  return cur;
};
```

## **Factorial Trailing Zeroes**

Given an integer n, return the number of trailing zeroes in n!.

Follow up: Could you write a solution that works in logarithmic time complexity?

Example 1:

```
Input: n = 3
Output: 0
Explanation: 3! = 6, no trailing zero.
```

Example 2:

```
Input: n = 5
Output: 1
Explanation: 5! = 120, one trailing zero.
```

Example 3:

```
Input: n = 0
Output: 0
```

Constraints:

```
0 <= n <= 104
```

**Solution:**

```javascript
const trailingZeroes = (n) => {
  let numZeroes = 0;
  for (let i = 5; i <= n; i *= 5) {
    numZeroes += Math.floor(n / i);
  }
  return numZeroes;
};

const trailingZeroes2 = (n) => {
  let result = 0;
  while (n > 0) {
    n = n / 5;
    result += n;
  }
  return Math.floor(result);
};
```
