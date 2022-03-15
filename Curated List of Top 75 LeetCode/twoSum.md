# twoSum

## 문제

Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

Example 1:

```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
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

## 풀이

```
const twoSum = (nums, target) => {
  for(let i=0; i<nums.length; i++) {
    for(let j=i+1; j<nums.length; j++) {
      if(nums[i]+nums[j] === target) return [i, j];
    }
  }
};
```

## 설명

i 인덱스에서 앞에 있는 인덱스들(각각의 j)을 한번씩 돌면서 더한 값이 target과 동일할 때 [i, j]를 return 한다.

- 전에도 동일하게 풀었었군..! [전에 풀이한 방법 보러가기](https://habitual-history.tistory.com/entry/codekata-1)

```
Runtime: 160 ms, faster than 32.04% of JavaScript online submissions for Two Sum.
Memory Usage: 42.7 MB, less than 37.47% of JavaScript online submissions for Two Sum.
```
