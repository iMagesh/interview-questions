## Basic Algorithm Questions

- **Name some of the sorting algorithms**

  - Selection Sort
  - Bubble Sort
  - Insertion Sort
  - Merge Sort
  - Quick Sort
  - Heap Sort
  - Counting Sort
  - Radix Sort
  - Bucket Sort

- **Name some of the search algorithms**

  - Binary Search
  - Exponential Search
  - Jump Search
  - Linear Search

- **Name some of the graph algorithms**

  - Breadth First Search (BFS)
  - Depth First Search (DFS)
  - Dijkstra's Algorithm
  - Floyd Warshall Algorithm

- **What are greedy algorithms?**

  - greedy algorithm picks the best immediate choice and never reconsiders its choices. In terms of optimizing a solution, this simply means that the greedy solution will try and find local optimum solutions - which can be many - and might miss out on a global optimum solution.

  - Imagine you are going for hiking and your goal is to reach the highest peak possible. You already have the map before you start, but there are thousands of possible paths shown on the map. You are too lazy and simply don’t have the time to evaluate each of them. Screw the map! You started hiking with a simple strategy – be greedy and short-sighted. Just take paths that slope upwards the most. This seems like a good strategy for hiking. But is it always the best ?

  - After the trip ended and your whole body is sore and tired, you look at the hiking map for the first time. Oh my god! There’s a muddy river that I should’ve crossed, instead of keep walking upwards. This means that a greedy algorithm picks the best immediate choice and never reconsiders its choices. In terms of optimizing a solution, this simply means that the greedy solution will try and find local optimum solutions - which can be many - and might miss out on a global optimum solution.

- **Name some of the Divide and Conquer Algorithms**

  - **Binary Search** is a searching algorithm. In each step, the algorithm compares the input element x with the value of the middle element in array. If the values match, return the index of middle. Otherwise, if x is less than the middle element, then the algorithm recurs for left side of middle element, else recurs for right side of middle element.

  - **Quicksort** is a sorting algorithm. The algorithm picks a pivot element, rearranges the array elements in such a way that all elements smaller than the picked pivot element move to left side of pivot, and all greater elements move to right side. Finally, the algorithm recursively sorts the subarrays on left and right of pivot element.

  - **Merge Sort** is also a sorting algorithm. The algorithm divides the array in two halves, recursively sorts them and finally merges the two sorted halves.

  - **Closest Pair of Points** The problem is to find the closest pair of points in a set of points in x-y plane. The problem can be solved in O(n^2) time by calculating distances of every pair of points and comparing the distances to find the minimum. The Divide and Conquer algorithm solves the problem in O(nLogn) time.

  - **Strassen’s Algorithm** is an efficient algorithm to multiply two matrices. A simple method to multiply two matrices need 3 nested loops and is O(n^3). Strassen’s algorithm multiplies two matrices in O(n^2.8974) time.

  - **Cooley–Tukey Fast Fourier Transform (FFT)** algorithm is the most common algorithm for FFT. It is a divide and conquer algorithm which works in O(nlogn) time.

  - The Karatsuba algorithm was the first multiplication algorithm asymptotically faster than the quadratic “grade school” algorithm. It reduces the multiplication of two n-digit numbers to at most to n^1.585(which is approximation of log of 3 in base 2) single digit products. It is therefore faster than the classical algorithm, which requires n^2 single-digit products.

- **How does insertion sort work?**

  - Insertion sort takes elements of the array sequentially, and maintains a sorted subarray to the left of the current point. It does this by taking an element, finding its correct position in the sorted array, and shifting all following elements by 1, leaving a space for the element to be inserted.

- **Heap Sort**

  - Heapsort starts by building a max heap. A binary max heap is a nearly complete binary tree in which each parent node is larger or equal to its children. The heap is stored in the same memory in which the original array elements are. Once the heap is formed, it completely replaces the array. After that, we take and remove the first element, restore the heap property, thus reducing the heap size by 1, after which we place the max element at the end of that memory. This is repeated until we empty out the heap, resulting in the smallest element being in the first place, and the following elements being sequentially larger.

- **Quick Sort**

  - Quicksort is performed by taking the first (leftmost) element of the array as a pivot point. We then compare it to each following element. When we find one that is smaller, we move it to the left. The moving is performed quickly by swapping that element with the first element after the pivot point, and then swapping the pivot point with the element after it. After going through the whole array, we take all points on the left of the pivot and call quicksort on that subarray, and we do the same to all points on the right of the pivot. The recursion is performed until we reach subarrays of 0-1 elements in length.

- **Merge Sort**

  - Merge sort recursively halves the given array. Once the subarrays reach trivial length, merging begins. Merging takes the smallest element between two adjacent subarrays and repeats that step until all elements are taken, resulting in a sorted subarray. The process is repeated on pairs of adjacent subarrays until we arrive at the starting array, but sorted.

- **What is a Binary Search Tree?**

  - The binary search tree is a special type of data structure which has the following properties.

    - Nodes which are less than root will be in the left subtree.
    - Nodes which are greater than root (i.e., contains more value) will be right subtree.
    - A binary search tree should not have duplicate nodes.
    - Both sides subtree (i.e., left and right) also should be a binary search tree.


    ![alt btree](./images/btree.png)

- **Write an algorithm to insert a node in the Binary search tree?**

  Insert node operation is a smooth operation. You need to compare it with the root node and traverse left (if smaller) or right (if greater) according to the value of the node to be inserted.

  **Algorithm:**

  - Make the root node as the current node
  - If the node to be inserted < root
    - If it has left child, then traverse left
    - If it does not have left child, insert node here
  - If the node to be inserted > root
    - If it has the right child, traverse right
    - If it does not have the right child, insert node here.

- **Explain how the encryption algorithm works?**

  - Encryption is the technique of converting plaintext into a secret code format it is also called as "Ciphertext." To convert the text, the algorithm uses a string of bits called as "keys" for calculations. The larger the key, the higher the number of potential patterns for Encryption. Most of the algorithm use codes fixed blocks of input that have a length of about 64 to 128 bits, while some uses stream method for encryption.

- **What are Divide and Conquer algorithms? Describe how they work. Can you give any common examples of the types of problems where this approach might be used?**

  - Divide and Conquer algorithms are a paradigm for solving problems that involve several basic steps. First, we divide the problem into smaller pieces and work to solve each of them independently. Once we’ve solved all of the pieces, we take all of the resulting smaller solutions and combine them into a single integrated comprehensive solution.

  - This process can be performed recursively; that is, each “sub problem” can itself be subdivided into even smaller parts if necessary.. This recursive division of the problem is performed until each individual problem is small enough to become relatively trivial to solve.

  - Some common examples of problems that lend themselves well to this approach are binary search, sorting algorithms (e.g., Merge Sort, Quicksort), optimization of computationally complex mathematical operations (Exponentiation, FFT, Strassen’s algorithm), and others.

- **Given a big string of characters, how to efficiently find the first unique character in it?**

  - The efficient solution is to use character as an index in a count array. Traverse the given string and store index of first occurrence of every character, also store count of occurrences. Then traverse the count array and find the smallest index with count as 1. See find the first unique character for more details.
  - [Code solution](https://www.geeksforgeeks.org/given-a-string-find-its-first-non-repeating-character/)

- **Given a linked list which is sorted, how will you insert in sorted way**

  - Given a sorted linked list and a value to insert, write a function to insert the value in a sorted way.
  - [2, 5, 7, 10, 15]
  - Output after adding 9 => [2, 5, 7, 9, 10, 15]
  - [Code solution](https://www.geeksforgeeks.org/given-a-linked-list-which-is-sorted-how-will-you-insert-in-sorted-way/)

- **Algorithm to swap two valubes a and b**

```
function swap(a,b){
  temp = a
  a = b
  b = temp
  return [a,b]
}
```
