# Two Sum Problem

## Question
Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

## Difficulty Level
- [x] Easy
- [ ] Medium
- [ ] Hard

## Company
Multiple companies (Google, Amazon, Microsoft, Facebook)

## Category
Data Structures - Arrays

## Video Link
[Two Sum Problem Explained - YouTube Video](#)

## Answer
This is a classic problem that can be solved efficiently using a hash map (dictionary) to store previously seen numbers and their indices.

### Approach 1: Brute Force (Not Recommended)
Check every pair of numbers to see if they sum to the target.

### Approach 2: Hash Map (Optimal)
1. Create a hash map to store numbers we've seen and their indices
2. For each number in the array:
   - Calculate what number we need to reach the target: `complement = target - current_number`
   - Check if this complement exists in our hash map
   - If yes, return the indices
   - If no, add the current number and its index to the hash map

### Key Points:
- Single pass through the array
- O(1) lookup time with hash map
- Space-time tradeoff for better performance

## Code Example
```python
def two_sum(nums, target):
    """
    Find two numbers in array that sum to target

    Args:
        nums: List of integers
        target: Target sum

    Returns:
        List of two indices
    """
    # Hash map to store number -> index mapping
    seen = {}

    for i, num in enumerate(nums):
        complement = target - num

        # Check if complement exists in our seen numbers
        if complement in seen:
            return [seen[complement], i]

        # Store current number and its index
        seen[num] = i

    # This shouldn't happen given the problem constraints
    return []

# Example usage
nums = [2, 7, 11, 15]
target = 9
result = two_sum(nums, target)
print(result)  # Output: [0, 1] because nums[0] + nums[1] = 2 + 7 = 9
```

## Time Complexity
- **Time**: O(n) - Single pass through the array
- **Space**: O(n) - Hash map can store up to n elements

## Follow-up Questions
1. What if no solution exists? (Handle edge case)
2. What if multiple solutions exist? (Return any one or all)
3. What if the array is sorted? (Two-pointer approach)
4. What if we can't use extra space? (Brute force O(n²))
5. What if there are duplicate numbers?

## Interview Tips
- **Start with brute force**: Mention the O(n²) solution first, then optimize
- **Clarify constraints**: Ask about duplicates, multiple solutions, etc.
- **Explain the trade-off**: Time vs space complexity
- **Test with examples**: Walk through your solution with given examples
- **Consider edge cases**: Empty array, single element, no solution

## Alternative Solutions

### Approach 3: Two Pointers (if array is sorted)
```python
def two_sum_sorted(nums, target):
    """
    Two-pointer approach for sorted array
    """
    left, right = 0, len(nums) - 1

    while left < right:
        current_sum = nums[left] + nums[right]

        if current_sum == target:
            return [left, right]
        elif current_sum < target:
            left += 1
        else:
            right -= 1

    return []
```

**Note**: This approach only works if the array is sorted and modifies the problem slightly since we need original indices.

## Related Questions
- [Three Sum](../three-sum.md)
- [Two Sum II - Input Array is Sorted](./two-sum-sorted.md)
- [Two Sum Less Than K](./two-sum-less-than-k.md)

---
*Last updated: December 2024*
*Video: [Two Sum Explanation](https://youtube.com/example)*
