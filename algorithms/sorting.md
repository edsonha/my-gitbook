# Sorting

Why do you need to learn sorting algorithm? Because when the inputs get larger, it starts costing companies a lot of money and this is something built-in sort method cannot solve. We need custom sorted methods based on the data so that they can lower their costs and operations process that the computer needs to do.

Why do company need sorted data? Because they need to preprocess the data to make sure that it is meaningful. If it is random data that is not sorted, it is really hard to access.

The quirk of sorting algorithm:

1. In JS, the built-in sort method sort number by converting it into string
2. The time and space complexity of sort cannot be guaranteed as it is implementation dependent, on different engines / browsers.

The goal of learning sorting algorithm is not to implement them from scratch, but to understand the difference between sorting algorithm and what is the trade-off between them \(the time as well as space complexity\). So that we can make the right decision what sorting algorithm to use for a particular data set.

In general, for [different data set](%20https://www.toptal.com/developers/sorting-algorithms), a particular sorting algorithm works best:

1. Random Data - Heap and Quick Sort is the best
2. Nearly Sorted - Insertion
3. Reverse Data - Heap and Shell sort
4. Few unique - Quick Sort

Elementary Sort

1. Bubble Sort: O\(n^2\) for time complexity and O\(1\) for space complexity
2. Selection Sort: O\(n^2\) for time complexity and O\(1\) for space complexity
3. Insertion Sort: O\(n^2\) for time complexity and O\(1\) for space complexity

Complex Sort 

1. Merge Sort: O\(n log\(n\)\) for time complexity and O\(n\) for space complexity
2. Quick Sort

What is O\(n log\(n\)\)?

Merge Sort and Quick Sort use technique, such as divide and conquer as well as recursion - to divide the problem down to do work on each subset and then combining the solutions. So this will give log\(n\). For the first part, you will still have n and that n comes from the fact that we're still comparing everything in order to sort it. But, it is better than O\(n^2\) because we are not comparing everything with everything.

Some sorting algorithms are stable by nature like Insertion Sort, Merge Sort, Bubble Sort, etc. And some sorting algorithms are not, like Heap Sort, Quick Sort, etc. Stable means that if you have equivalent elements that is, let's say 6 and 6 or a name that is the same, it will keep the original order in the array. And this can sometimes be important depending on the type of data.

