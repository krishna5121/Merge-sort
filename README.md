# Merge Sort in Swift

This project contains an implementation of the Merge Sort algorithm in Swift. Merge Sort is a classic divide-and-conquer algorithm that sorts an array by recursively dividing it into two halves, sorting each half, and merging them back together.

## Algorithm Explanation

Merge Sort works by dividing the array into halves, recursively sorting each half, and then merging the sorted halves into a complete sorted array.

### Steps:
1. **Divide**: Split the array into two halves.
2. **Conquer**: Recursively sort each half.
3. **Combine**: Merge the sorted halves to produce a single sorted array.

### Flowchart

# Merge Sort in Swift

This project provides an implementation of the Merge Sort algorithm in Swift. Merge Sort is a divide-and-conquer algorithm that sorts an array by recursively dividing it into two halves, sorting each half, and merging them back together.

## Explanation of Each Step

### Step 1: Check if the Array Length is 1 or Less
- **Base Case Check**: We use `guard` to check if the array contains more than one element. If not, the array is already sorted, and it is returned immediately.

### Step 2: Divide the Array into Two Halves
- **Splitting**: The array is divided into two halves using the midpoint:
  - `middleIndex = array.count / 2`
  - `leftArray` contains the first half: `Array(array[0..<middleIndex])`.
  - `rightArray` contains the second half: `Array(array[middleIndex..<array.count])`.

### Step 3: Recursively Sort Each Half
- **Recursive Calls**: The `mergeSort` function is called recursively on `leftArray` and `rightArray`.
- **Divide Further**: The recursion continues to split the array until each subarray contains a single element.

### Step 4: Merge the Sorted Halves
- **Merging Function**: The `merge` function is used to merge two sorted arrays (`leftSorted` and `rightSorted`).
- **Combine Results**: The merged sorted arrays are returned as a single sorted array.

### Step 5: Merge Two Sorted Arrays
- **Initialize**: An empty array `sortedArray` is initialized to store the merged result.
- **Two-Pointer Technique**: Two indices, `leftIndex` and `rightIndex`, are used to traverse the `left` and `right` arrays.

### Steps 6 and 7: Compare and Merge
- **Compare Elements**: Compare elements from both arrays: `left[leftIndex]` and `right[rightIndex]`.
- **Append Smaller Element**: Append the smaller element to `sortedArray`, and move the pointer of the array from which the element was taken.
- **Remaining Elements**: Append any remaining elements from the `left` and `right` arrays once one is exhausted.

## Swift Implementation

Below is the flowchart illustrating the recursive flow of the Merge Sort algorithm:

![Merge Sort Flowchart](image-file-name.png)
![Uploading Screenshot 2024-07-26 at 5.54.52 PM.png…]()


## Swift Implementation

Here is the Swift code implementing Merge Sort:

```swift
func mergeSort(_ array: [Int]) -> [Int] {
    // Step 1: Check if the array length is 1 or less
    guard array.count > 1 else { return array }

    // Step 2: Divide the array into two halves
    let middleIndex = array.count / 2
    let leftArray = Array(array[0..<middleIndex])
    let rightArray = Array(array[middleIndex..<array.count])

    // Step 3: Recursively sort each half
    let leftSorted = mergeSort(leftArray)
    let rightSorted = mergeSort(rightArray)

    // Step 4: Merge the sorted halves
    return merge(leftSorted, rightSorted)
}

func merge(_ left: [Int], _ right: [Int]) -> [Int] {
    var sortedArray = [Int]()
    var leftIndex = 0
    var rightIndex = 0

    // Step 5: Merge the two sorted arrays
    while leftIndex < left.count && rightIndex < right.count {
        if left[leftIndex] < right[rightIndex] {
            sortedArray.append(left[leftIndex])
            leftIndex += 1
        } else {
            sortedArray.append(right[rightIndex])
            rightIndex += 1
        }
    }

    // Step 6: Append any remaining elements from the left array
    while leftIndex < left.count {
        sortedArray.append(left[leftIndex])
        leftIndex += 1
    }

    // Step 7: Append any remaining elements from the right array
    while rightIndex < right.count {
        sortedArray.append(right[rightIndex])
        rightIndex += 1
    }

    return sortedArray
}

// Example usage
let array = [3, 1, 2, 4, 6, 5]
let sortedArray = mergeSort(array)
print(sortedArray)  // Output: [1, 2, 3, 4, 5, 6]
```

