# Array Problem-Solving Patterns

## 1. Two Pointers
### What it is:
A technique using two variables ("pointers") to traverse an array. These pointers can move in the same direction, opposite directions, or based on specific conditions.

### When to use:
- When comparing elements from different parts of the array
- When searching for pairs with certain conditions
- When processing array elements simultaneously

### Algorithm:
1. Initialize two pointers (typically start and end, or slow and fast)
2. Move pointers based on conditions:
   - Same direction: 
      - fast moves k steps when slow moves 1 step
      - fast moves 1 step and slow replaces with fast's position when condition is met [TUF example](https://takeuforward.org/data-structure/remove-duplicates-in-place-from-sorted-array/).
   - Opposite direction: start moves right, end moves left
   - Based on conditions: move according to target comparison
3. Process elements at pointer positions
4. Continue until pointers meet or other termination condition

### Example Problem: Find pair with sum X in sorted array
```
Algorithm:
1. Set left = 0, right = array.length - 1
2. While left < right:
   a. If array[left] + array[right] == X: Found pair
   b. If sum < X: left++
   c. If sum > X: right--
```

## 2. Prefix Sum
### What it is:
A technique to precompute cumulative sums up to each index, enabling quick range sum queries.

### Algorithm:
1. Create prefix array of same size as input
2. First element: prefix[0] = array[0]
3. For i from 1 to n-1:
   prefix[i] = prefix[i-1] + array[i]
4. Any range sum from i to j:
   - If i == 0: prefix[j]
   - Else: prefix[j] - prefix[i-1]

### Common Pattern for Subarray Sum Problems:
```
Algorithm:
1. Initialize sum = 0, count = 0
2. Create hashmap with (0,1) entry
3. For each number in array:
   a. Add number to sum
   b. If (sum - target) exists in map:
      - Add its frequency to count
   c. Add sum to map or increment its frequency
```

## 3. Three Pointers
### What it is:
Extension of two pointers using three variables to process elements in specific order.

### Algorithm:
1. Initialize three pointers:
   - first = start index
   - middle = start index
   - last = end index
2. Move middle pointer as main traversal
3. Perform operations based on relationships:
   - Compare elements at all three positions
   - Swap elements between positions
   - Update pointers based on conditions
4. Continue until middle crosses last

### Example Problem: Sort array of 0s, 1s, and 2s
```
Algorithm:
1. Set low = 0, mid = 0, high = n-1
2. While mid <= high:
   a. If element is 0: swap with low, low++, mid++
   b. If element is 1: mid++
   c. If element is 2: swap with high, high--
```

## 4. Majority Element
### What it is:
A pattern to find the element that appears more than half the time in an array.

### Algorithm:
1. Use a variable to track the count of a potential majority element
2. Increment the count if the current element matches the candidate
3. Decrement the count if it doesn’t match. If the count becomes zero, update the candidate
4. Verify the candidate by counting its occurrences

### Example Problem: Find majority element in array
```
Algorithm:
1. Initialize candidate = None, count = 0
2. For each element in array:
   a. If count == 0: candidate = element
   b. If element == candidate: count++
   c. Else: count--
3. Verify candidate by counting occurrences
```

## 5. Using HashSet
### What it is:
A HashSet is a collection that stores unique values. It’s useful for checking if an element exists or for removing duplicates.

### Algorithm:
1. Initialize an empty HashSet
2. For each element in array:
   a. If element exists in HashSet: duplicate found
   b. Else: add element to HashSet
3. Use HashSet for membership checks or to remove duplicates

### Example Problem: Find duplicates in array
```
Algorithm:
1. Initialize HashSet
2. For each element:
   a. If element exists in HashSet: duplicate found
   b. Else: add element to HashSet
```

## 6. Matrix Patterns
### a. Set Matrix Zeroes
#### What it is:
If an element in a matrix is 0, set its entire row and column to 0.

#### Algorithm:
1. Use the first row and first column to mark which rows and columns need to be zeroed
2. Traverse the matrix and update values accordingly

### b. Transpose a Matrix
#### What it is:
Transposing a matrix means swapping its rows with columns. For example, the element at (i, j) becomes (j, i).

#### Algorithm:
1. Iterate through matrix elements
2. Swap elements at (i, j) with (j, i)

These patterns are foundational and will help you solve many array-related problems efficiently. Practice implementing them in any programming language to solidify your understanding!
