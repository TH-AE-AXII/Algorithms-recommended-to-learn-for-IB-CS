# 

# IB Problems, Standard Algorithms, and ADT Structure in JAVA

## By Thach Dang, IBO Victim of 2024 

# Table Of Contents {#table-of-contents}

[**Table Of Contents	1**](#table-of-contents)

[**Resources:	1**](#resources:)

[JETS: Java Examination Tool Subset	1](#jets:-java-examination-tool-subset)

[IB Pseudocode	1](#ib-pseudocode)

[Pseudocode Coding Bat (very specific, use more as a learning tool)	1](#pseudocode-coding-bat-\(very-specific,-use-more-as-a-learning-tool\))

[**1\. Array Rotation	2**](#1.-array-rotation)

[**2\. Find Middle Element of a Linked List	2**](#2.-find-middle-element-of-a-linked-list)

[**3\. Implement a Stack	2**](#3.-implement-a-stack)

[**4\. Implement a Queue Using Two Stacks	3**](#4.-implement-a-queue-using-two-stacks)

[**5\. Check Balanced Parentheses Using Stack	4**](#5.-check-balanced-parentheses-using-stack)

[**6\. Reverse a Queue	4**](#6.-reverse-a-queue)

[**7\. Merge Two Sorted Arrays	5**](#7.-merge-two-sorted-arrays)

[**8\. Remove Duplicates from a Linked List	5**](#8.-remove-duplicates-from-a-linked-list)

[**9\. Implement a Circular Queue	6**](#9.-implement-a-circular-queue)

[**10\. Find Intersection of Two Arrays	7**](#10.-find-intersection-of-two-arrays)

[**11\. Quick Sort	8**](#11.-quick-sort)

[**12\. Binary Search	10**](#12.-binary-search)

[**13\. Bubble Sort	10**](#13.-bubble-sort)

[**14\. Selection Sort	11**](#14.-selection-sort)

[**15\. 2D Arrays	12**](#15.-2d-arrays)

[**16\. Rotate NxN 2D Array by k steps	13**](#16.-rotate-nxn-2d-array-by-k-steps)

[**17\. Binary Trees	14**](#17.-binary-trees)

[**18\. Inorder Tree Traversal	15**](#18.-inorder-tree-traversal)

[**19\. Post Order Traversal	15**](#19.-post-order-traversal)

[**20\. Preorder Tree Traversal	16**](#20.-preorder-tree-traversal)

[**21\. Linked Lists Operations	16**](#21.-linked-lists-operations)

[**22\. Error Handling	19**](#22.-error-handling)

[**23\. ArrayList Operations	19**](#23.-arraylist-operations)

# Resources: {#resources:}

## [JETS](https://drive.google.com/file/d/140_RgYw2nGVJvXp91UgSfkMKvSWFIaob/view?usp=drive_link): Java Examination Tool Subset {#jets:-java-examination-tool-subset}

## [IB Pseudocode](https://drive.google.com/file/d/1r6CTsiJ8eXWZzPUebREUHkDDNW6KiFrN/view) {#ib-pseudocode}

## [Pseudocode Coding Bat](https://graded-cs-resources.github.io/CodingBatPseudo/) (very specific, use more as a learning tool) {#pseudocode-coding-bat-(very-specific,-use-more-as-a-learning-tool)}

# 1\. Array Rotation {#1.-array-rotation}

Question: Write Java Code, *Rotate*,  to rotate an array A of n elements to the right by k steps, where k is a non-negative integer.

| public void rotate(int\[\] array, int k) {    int n \= array.length;    k \= k % n;    int\[\] tempArray \= new int\[n\];    for (int i \= 0; i \< n; i++) {        int newPosition \= (i \+ k) % n;        tempArray\[newPosition\] \= array\[i\];    }    for (int i \= 0; i \< n; i++) {        array\[i\] \= tempArray\[i\];    }} |
| :---- |

# 2\. Find Middle Element of a Linked List {#2.-find-middle-element-of-a-linked-list}

Question: Write Java Code to find the middle element of a singly linked list. If the list has an even number of elements, return the second middle element.

| public class ListNode {    int val;    ListNode next;    ListNode(int x) { val \= x; }}public int findMiddleElement(ListNode head) {    ListNode slow \= head, fast \= head;    while (fast \!= null && fast.next \!= null) {        slow \= slow.next;        fast \= fast.next.next;    }    return slow.val;} |
| :---- |

# 3\. Implement a Stack {#3.-implement-a-stack}

Question: Write Java Code for implementing a stack with operations push, pop, and peek. Use an array as the underlying data structure.

| public class Stack {    private int\[\] data;    private int top;    public Stack(int size) {        data \= new int\[size\];        top \= \-1;    }    public void push(int element) {        data\[++top\] \= element;    }    public int pop() {        if (isEmpty())            throw new IllegalStateException("Stack is empty");        return data\[top--\];    }    public boolean isEmpty() {        return top \== \-1;    }} |
| :---- |

# 4\. Implement a Queue Using Two Stacks {#4.-implement-a-queue-using-two-stacks}

Question: Write Java Code to implement a queue using two stacks. The queue should support enqueue and dequeue operations.

| import java.util.Stack;public class QueueUsingStacks {    private Stack\<Integer\> inStack \= new Stack\<\>();    private Stack\<Integer\> outStack \= new Stack\<\>();    public void enqueue(int element) {        inStack.push(element);    }    public int dequeue() {        if (outStack.isEmpty()) {            while (\!inStack.isEmpty()) {                outStack.push(inStack.pop());            }        }        return outStack.pop();    }} |
| :---- |

# 5\. Check Balanced Parentheses Using Stack {#5.-check-balanced-parentheses-using-stack}

Question: Write Java Code method *Balanced* that uses a stack S to check if an input string P of parentheses (characters '(' and ')') is balanced. A string is balanced if all opening parentheses have a corresponding closing parenthesis in the correct order. Return true if it is balanced, false otherwise.

| public boolean isBalanced(String s) {    Stack\<Character\> stack \= new Stack\<\>();    for (char c : s.toCharArray()) {        if (c \== '(') {            stack.push(c);        } else if (c \== ')') {            if (stack.isEmpty()) {                return false;            }            stack.pop();        }    }    return stack.isEmpty();} |
| :---- |

# 6\. Reverse a Queue {#6.-reverse-a-queue}

Question: Write Java Code to reverse the elements of a queue using only standard queue operations. You may use a stack as temporary storage. (enqueue, dequeue, and isEmpty).

| import java.util.LinkedList;import java.util.Queue;import java.util.Stack;Public void reverseQueue(Queue\<Integer\> queue) {    Stack\<Integer\> stack \= new Stack\<\>();    while (\!queue.isEmpty()) {        stack.push(queue.poll());    }    while (\!stack.isEmpty()) {        queue.offer(stack.pop());    }} |
| :---- |

# 7\. Merge Two Sorted Arrays {#7.-merge-two-sorted-arrays}

Question: Write Java Code to merge two sorted arrays of integers, A and B, into a new sorted array C.

| public int\[\] mergeSortedArrays(int\[\] A, int\[\] B) {    int\[\] C \= new int\[A.length \+ B.length\];    int i \= 0, j \= 0, k \= 0;    while (i \< A.length && j \< B.length) {        if (A\[i\] \< B\[j\]) {            C\[k++\] \= A\[i++\];        } else {            C\[k++\] \= B\[j++\];        }    }    while (i \< A.length) {        C\[k++\] \= A\[i++\];    }    while (j \< B.length) {        C\[k++\] \= B\[j++\];    }    return C;} |
| :---- |

# 8\. Remove Duplicates from a Linked List {#8.-remove-duplicates-from-a-linked-list}

Question: Write Java Code method, RemoveDup, to remove duplicate values from an unsorted linked list. You may use another Queue as temporary storage.

| public void removeDuplicates(ListNode head) {    Set\<Integer\> seen \= new HashSet\<\>();    ListNode current \= head, prev \= null;    while (current \!= null) {        if (\!seen.add(current.val)) {            prev.next \= current.next;        } else {            prev \= current;        }        current \= current.next;    }} |
| :---- |

# 9\. Implement a Circular Queue {#9.-implement-a-circular-queue}

Question: Write Java Code for implementing a circular queue with operations enqueue, dequeue, and isFull. Use an array as the underlying data structure.

| public class CircularQueue {    private int\[\] data;    private int head \= 0, tail \= 0, size \= 0, capacity;    public CircularQueue(int capacity) {        this.capacity \= capacity;        data \= new int\[capacity\];    }    public boolean enqueue(int element) {        if (isFull()) {            return false;        }        data\[tail\] \= element;        tail \= (tail \+ 1) % capacity;        size++;        return true;    }    public int dequeue() {        if (isEmpty()) {            throw new IllegalStateException("Queue is empty");        }        int result \= data\[head\];        head \= (head \+ 1) % capacity;        size--;        return result;    }    public boolean isFull() {        return size \== capacity;    }    public boolean isEmpty() {        return size \== 0;    }} |
| :---- |

# 10\. Find Intersection of Two Arrays {#10.-find-intersection-of-two-arrays}

Question: Write Java Code to find the intersection of two arrays A and B, where the intersection is a collection of elements that are common to both arrays. Avoid using built-in collection methods for the intersection.

public class ArrayIntersection {  
    public int\[\] findIntersection(int\[\] A, int\[\] B) {  
        // Sort both arrays using QuickSort  
        QuickSort.sort(A);  
        QuickSort.sort(B);

        // Initialize pointers for both arrays  
        int pointerA \= 0, pointerB \= 0;  
        int\[\] temp \= new int\[Math.min(A.length, B.length)\];  
        int index \= 0;

        // Use two-pointer technique to find common elements  
        while (pointerA \< A.length && pointerB \< B.length) {  
            if (A\[pointerA\] \< B\[pointerB\]) {  
                pointerA++;  
            } else if (A\[pointerA\] \> B\[pointerB\]) {  
                pointerB++;  
            } else {  
                // Found a common element  
                if (index \== 0 || temp\[index \- 1\] \!= A\[pointerA\]) { // Check to avoid duplicates  
                    temp\[index++\] \= A\[pointerA\];  
                }  
                pointerA++;  
                pointerB++;  
            }  
        }

        // Copy the found elements to the final result array  
        int\[\] result \= new int\[index\];  
        System.arraycopy(temp, 0, result, 0, index);  
        return result;  
    }

    public void main(String\[\] args) {  
        int\[\] A \= {4, 9, 5, 7, 5};  
        int\[\] B \= {9, 4, 9, 8, 4, 6};  
        int\[\] intersection \= findIntersection(A, B);

        System.out.println("Intersection of the two arrays is:");  
        for (int num : intersection) {  
            System.out.print(num \+ " ");  
        }  
    }  
}

# 11\. Quick Sort {#11.-quick-sort}

| public class QuickSort {    public void sort(int\[\] array) {        quickSort(array, 0, array.length \- 1);    }    private void quickSort(int\[\] array, int low, int high) {        if (low \< high) {            int partitionIndex \= partition(array, low, high);            quickSort(array, low, partitionIndex \- 1);  // Recursively sort elements before partition            quickSort(array, partitionIndex \+ 1, high); // Recursively sort elements after partition        }    }    private int partition(int\[\] array, int low, int high) {        int pivot \= array\[high\];          int i \= (low \- 1); // Index of smaller element        for (int j \= low; j \< high; j++) {            // If current element is smaller than or equal to pivot            if (array\[j\] \<= pivot) {                i++;                // Swap array\[i\] and array\[j\]                int temp \= array\[i\];                array\[i\] \= array\[j\];                array\[j\] \= temp;            }        }        // Swap array\[i+1\] and array\[high\] (or pivot)        int temp \= array\[i \+ 1\];        array\[i \+ 1\] \= array\[high\];        array\[high\] \= temp;        return i \+ 1;    }} 12\. Binary Search Question: Write Java Code for Binary Search |
| :---- |

|     // Performs binary search on a sorted array to find the index of a target value.    // @param array The sorted array.    // @param target The value to search for.    // @return The index of the target if found, otherwise \-1.         public int search(int\[\] array, int target) {        int left \= 0;        int right \= array.length \- 1;        while (left \<= right) {            int mid \= left \+ (right \- left) / 2;            if (array\[mid\] \== target) {                return mid; // Target found            } else if (array\[mid\] \< target) {                left \= mid \+ 1; // Continue search in the right half            } else {                right \= mid \- 1; // Continue search in the left half            }        }        return \-1; // Target not found    } |
| :---- |
|  |

# 13\. Bubble Sort {#13.-bubble-sort}

Question: Write Java Code for Bubble Sort

| // Sorts an array using the bubble sort algorithm.// @param array The array to be sorted. public void sort(int\[\] array) {        boolean swapped;        int n \= array.length;        do {            swapped \= false;            for (int i \= 1; i \< n; i++) {                if (array\[i \- 1\] \> array\[i\]) {                    // Swap elements at index i-1 and i                    int temp \= array\[i \- 1\];                    array\[i \- 1\] \= array\[i\];                    array\[i\] \= temp;                    swapped \= true;                }            }            n--; // Decrement n since the last element is now sorted        } while (swapped);    } |
| :---- |
|  |

# 14\. Selection Sort {#14.-selection-sort}

Question: Write Java Code for Selection Sort

| // Sorts an array using the selection sort algorithm.// @param array The array to be sorted.     public void sort(int\[\] array) {        int n \= array.length;        for (int i \= 0; i \< n \- 1; i++) {            // Find the minimum element in the unsorted part of the array            int minIndex \= i;            for (int j \= i \+ 1; j \< n; j++) {                if (array\[j\] \< array\[minIndex\]) {                    minIndex \= j;                }            }            // Swap the found minimum element with the first element of the unsorted part            int temp \= array\[minIndex\];            array\[minIndex\] \= array\[i\];            array\[i\] \= temp;        }    } |
| :---- |

# 15\. 2D Arrays {#15.-2d-arrays}

| public class Array2DAccess {    public void main(String\[\] args) {        // 1\. Creating and initializing a 2D array        int\[\]\[\] matrix \= {            {1, 2, 3},            {4, 5, 6},            {7, 8, 9}        };        // 2\. Accessing elements        int element \= matrix\[1\]\[2\]; // Access element at second row and third column (6)        System.out.println("Accessed element: " \+ element);        // 3\. Modifying elements        matrix\[2\]\[0\] \= 10; // Change element at third row and first column from 7 to 10        // 4\. Printing all elements using nested loops        System.out.println("Updated matrix:");        printMatrix(matrix);        // 5\. Using enhanced for loop to iterate over 2D array        System.out.println("Iterating with enhanced for-loop:");        printMatrixWithEnhancedFor(matrix);    }    private void printMatrix(int\[\]\[\] matrix) {        for (int i \= 0; i \< matrix.length; i++) {            for (int j \= 0; j \< matrix\[i\].length; j++) {                System.out.print(matrix\[i\]\[j\] \+ " ");            }            System.out.println();        }    }    private void printMatrixWithEnhancedFor(int\[\]\[\] matrix) {        for (int\[\] row : matrix) {            for (int element : row) {                System.out.print(element \+ " ");            }            System.out.println();        }    }} |
| :---- |

# 16\. Rotate NxN 2D Array by k steps {#16.-rotate-nxn-2d-array-by-k-steps}

| public class MatrixRotation {    public void rotateMatrix(int\[\]\[\] matrix, int k) {        int n \= matrix.length;        k \= k % 4;  // Only need to consider rotations that are not full circles                for (int r \= 0; r \< k; r++) {            // Perform a single 90-degree rotation clockwise            for (int i \= 0; i \< n / 2; i++) {                for (int j \= i; j \< n \- i \- 1; j++) {                    int temp \= matrix\[i\]\[j\];                    matrix\[i\]\[j\] \= matrix\[n \- 1 \- j\]\[i\];                    matrix\[n \- 1 \- j\]\[i\] \= matrix\[n \- 1 \- i\]\[n \- 1 \- j\];                    matrix\[n \- 1 \- i\]\[n \- 1 \- j\] \= matrix\[j\]\[n \- 1 \- i\];                    matrix\[j\]\[n \- 1 \- i\] \= temp;                }            }        }    }    public void printMatrix(int\[\]\[\] matrix) {        for (int\[\] row : matrix) {            for (int val : row) {                System.out.print(val \+ " ");            }            System.out.println();        }    }    public void main(String\[\] args) {        int\[\]\[\] matrix \= {             {1, 2, 3},             {4, 5, 6},             {7, 8, 9}         };                int k \= 1;  // Number of 90-degree clockwise rotations        rotateMatrix(matrix, k);        printMatrix(matrix);    }} |
| :---- |

# 17\. Binary Trees {#17.-binary-trees}

| public class TreeNode {    int value;    TreeNode left;    TreeNode right;    TreeNode(int value) {        this.value \= value;        this.left \= null;        this.right \= null;    }} |
| :---- |

| public class BinaryTree {    // Method to perform recursive inorder traversal    public void inorderTraversal(TreeNode root) {        if (root \== null) {            return;        }        inorderTraversal(root.left);       // Visit left subtree        System.out.print(root.value \+ " "); // Visit node itself        inorderTraversal(root.right);      // Visit right subtree    }    public void main(String\[\] args) {        // Creating a simple binary tree        TreeNode root \= new TreeNode(1);        root.left \= new TreeNode(2);        root.right \= new TreeNode(3);        root.left.left \= new TreeNode(4);        root.left.right \= new TreeNode(5);        BinaryTree tree \= new BinaryTree();        System.out.println("Inorder Traversal:");        tree.inorderTraversal(root);    }} |
| :---- |

# 18\. Inorder Tree Traversal  {#18.-inorder-tree-traversal}

| import java.util.Stack;public void inorderTraversalIterative(TreeNode root) {    if (root \== null) return;    Stack\<TreeNode\> stack \= new Stack\<\>();    TreeNode current \= root;    while (current \!= null || \!stack.isEmpty()) {        // Reach the left most Node of the current Node        while (current \!= null) {            stack.push(current);            current \= current.left;        }        // Current must be null at this point        current \= stack.pop();        System.out.print(current.value \+ " "); // Visit the node        current \= current.right; // Move to the right subtree    }} |
| :---- |

# 19\. Post Order Traversal  {#19.-post-order-traversal}

| import java.util.Stack;public void postorderTraversalIterative(TreeNode root) {    if (root \== null) return;    Stack\<TreeNode\> stack1 \= new Stack\<\>();    Stack\<TreeNode\> stack2 \= new Stack\<\>();    stack1.push(root);    while (\!stack1.isEmpty()) {        TreeNode currentNode \= stack1.pop();        stack2.push(currentNode);        if (currentNode.left \!= null) {            stack1.push(currentNode.left);        }        if (currentNode.right \!= null) {            stack1.push(currentNode.right);        }    }    while (\!stack2.isEmpty()) {        TreeNode node \= stack2.pop();        System.out.print(node.value \+ " ");    }} 20\. Preorder Tree Traversal |
| :---- |

| import java.util.Stack;public void preorderTraversalIterative(TreeNode root) {    if (root \== null) return;    Stack\<TreeNode\> stack \= new Stack\<\>();    stack.push(root);    while (\!stack.isEmpty()) {        TreeNode currentNode \= stack.pop();        System.out.print(currentNode.value \+ " "); // Visit the node        // Push right child first so that left child is processed first        if (currentNode.right \!= null) {            stack.push(currentNode.right);        }        if (currentNode.left \!= null) {            stack.push(currentNode.left);        }    }} |
| :---- |

# 21\. Linked Lists Operations {#21.-linked-lists-operations}

| public class Node {    int data;    Node next;    Node(int data) {        this.data \= data;        this.next \= null;    }}public class LinkedList {    Node head; // head of the list    // Method to insert a new node at the front of the list    public void insertAtFront(int data) {        Node newNode \= new Node(data);        newNode.next \= head;        head \= newNode;    }    // Method to insert a new node at the end of the list    public void insertAtEnd(int data) {        Node newNode \= new Node(data);        if (head \== null) {            head \= newNode;            return;        }        Node last \= head;        while (last.next \!= null) {            last \= last.next;        }        last.next \= newNode;    }    // Method to delete a node by key    public void deleteByKey(int key) {        Node temp \= head, prev \= null;        // If head node itself holds the key to be deleted        if (temp \!= null && temp.data \== key) {            head \= temp.next; // Changed head            return;        }        // Search for the key to be deleted, keep track of the previous node        while (temp \!= null && temp.data \!= key) {            prev \= temp;            temp \= temp.next;        }        // If key was not present in linked list        if (temp \== null) return;        // Unlink the node from linked list        prev.next \= temp.next;    }    // Method to print the linked list    public void printList() {        Node tNode \= head;        while (tNode \!= null) {            System.out.print(tNode.data \+ " \-\> ");            tNode \= tNode.next;        }        System.out.println("NULL");    }    public void main(String\[\] args) {        LinkedList list \= new LinkedList();        list.insertAtEnd(1);        list.insertAtEnd(2);        list.insertAtEnd(3);        list.insertAtFront(0);        list.insertAtFront(-1);        System.out.println("Created Linked list is:");        list.printList();        list.deleteByKey(1);        System.out.println("Linked List after Deletion of 1:");        list.printList();    }} |
| :---- |

# 22\. Error Handling {#22.-error-handling}

| public class ExceptionHandlingDemo {    public static void main(String\[\] args) {        try {            int\[\] numbers \= {1, 2, 3};            // This will throw an ArrayIndexOutOfBoundsException            System.out.println(numbers\[10\]);        } catch (ArrayIndexOutOfBoundsException e) {            System.out.println("An exception occurred: " \+ e.getMessage());        } finally {            System.out.println("The 'try catch' is finished.");        }    }}  |
| :---- |

Explanation:  
**ArithmeticException catch block**: Specifically handles division by zero.  
**ArrayIndexOutOfBoundsException** **catch block**: Specifically handles errors related to array indexing.  
**Exception** **catch block**: A general catch block that can handle any exception not caught by the preceding specific blocks.  
**finally** **block**: Executes after the try-catch blocks regardless of whether an exception occurred.

# 23\. ArrayList Operations  {#23.-arraylist-operations}

| import java.util.ArrayList;import java.util.List;public class ArrayListOperations {    public static void main(String\[\] args) {        // Create an ArrayList to store Integer elements        List\<Integer\> numbers \= new ArrayList\<\>();        // Adding elements        numbers.add(10);        numbers.add(20);        numbers.add(30);        System.out.println("Initial ArrayList: " \+ numbers);        // Accessing elements        System.out.println("Element at index 1: " \+ numbers.get(1));        // Adding an element at a specific index        numbers.add(1, 15);  // Insert 15 at index 1        System.out.println("ArrayList after adding an element at index 1: " \+ numbers);        // Removing elements        numbers.remove(Integer.valueOf(20));  // Remove element 20        System.out.println("ArrayList after removing the element 20: " \+ numbers);        numbers.remove(2);  // Remove element at index 2 (30 in this case)        System.out.println("ArrayList after removing element at index 2: " \+ numbers);        // Iterating over ArrayList using for-each loop        System.out.print("Current ArrayList: ");        for (Integer number : numbers) {            System.out.print(number \+ " ");        }        System.out.println();        // Checking if ArrayList is empty        if (numbers.isEmpty()) {            System.out.println("ArrayList is empty");        } else {            System.out.println("ArrayList is not empty");        }        // Finding the size of the ArrayList        System.out.println("Size of ArrayList: " \+ numbers.size());        // Clear all elements from ArrayList        numbers.clear();        System.out.println("ArrayList after clear operation: " \+ numbers);    }} |
| :---- |

