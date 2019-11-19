# Sorting

Why do you need to learn sorting algorithm? Because when the inputs get larger, it starts costing companies a lot of money and this is something built-in sort method cannot solve. We need custom sorted methods based on the data so that they can lower their costs and operations process that the computer needs to do.

Why do company need sorted data? Because they need to preprocess the data to make sure that it is meaningful. If it is random data that is not sorted, it is really hard to access.

The quirk of sorting algorithm:

1. In JS, the built-in sort method sort number by converting it into string
2. The time and space complexity of sort cannot be guaranteed as it is implementation dependent, on different engines / browsers.

The goal of learning sorting algorithm is not to implement them from scratch, but to understand the difference between sorting algorithm and what is the trade-off between them \(the time as well as space complexity\). So that we can make the right decision what sorting algorithm to use for a particular data set.

Elementary Sort

1. Bubble Sort: O\(n^2\) for time complexity and O\(1\) for space complexity
2. Selection Sort: O\(n^2\) for time complexity and O\(1\) for space complexity
3. Insertion Sort: O\(n^2\) for time complexity and O\(1\) for space complexity

Complex Sort 

1. Merge Sort: O\(n log\(n\)\) for time complexity and O\(n\) for space complexity
2. Quick Sort: O\(n log\(n\)\) for time complexity and space complexity. With picking the wrong pivot \(pick the largest and smallest where you are not splitting the list into half\), the time complexity is O\(n^2\)

What is O\(n log\(n\)\)?

Merge Sort and Quick Sort are the most used sorting algorithm, use technique, such as divide and conquer as well as recursion - to divide the problem down to do work on each subset and then combining the solutions. So this will give log\(n\). For the first part, you will still have n and that n comes from the fact that we're still comparing everything in order to sort it. But, it is better than O\(n^2\) because we are not comparing everything with everything.

Quick Sort uses something called a pivoting technique to break the main list into smaller lists and these smaller lists use the pivoting technique until they are sorted.

Some sorting algorithms are stable by nature like Insertion Sort, Merge Sort, Bubble Sort, etc. And some sorting algorithms are not, like Heap Sort, Quick Sort, etc. Stable means that if you have equivalent elements that is, let's say 6 and 6 or a name that is the same, it will keep the original order in the array. And this can sometimes be important depending on the type of data.

When should you use algorithm sort?

1. Insertion sort is when your input is small or items are mostly sorted.
2. Bubble sort and selection sort is not used because they are not very efficient
3. Merge Sort and Quick Sort is the most algorithm. Merge Sort advantage over Quick Sort is with worst case scenario - O\(n log\(n\)\) vs O\(n^2\) time complexity, but lose out on space complexity O\(n\) vs O\(n log\(n\)\)

In general, for [different data set](%20https://www.toptal.com/developers/sorting-algorithms), a particular sorting algorithm works best:

1. Random Data - Heap and Quick Sort is the best
2. Nearly Sorted - Insertion
3. Reverse Data - Heap and Shell sort
4. Few unique - Quick Sort

Can you beat O\(n log\(n\)\)?

You can improve this time complexity if you don't make comparisons, like Counting Sort and Radix Sort \(non-comparison sort\). Non-comparison sort makes use the way that numbers and data is stored on our computers in zeros and ones and take advantage of that fact to sort things.

The one thing to note here is that these type of non-comparison sort only work with numbers specifically integers in a restricted range. It wouldn't work on any type of data. It only works on numbers because of the way numbers are stored in memory.

{% hint style="success" %}
Mozilla uses merge sort for sorting. Chrome and V8 use quick sort and insertion sort for smaller array
{% endhint %}

| Quick Sort | Merge Sort |
| :--- | :--- |
| Better space complexity | Consistent time complexity |
| \*Be careful of worst scenario | Stable Algorithm |

In summary, you should be able to decide which sorting algorithm to use based on the speed, space complexity, stability, input characteristic \(whether they are random or already sorted\) and how large the input is.

