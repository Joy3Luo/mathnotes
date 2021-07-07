---
layout: post
title: Programming - Amazon OA practice test
date: 2021-07-06 5:18 +0800
tags: [Programming]
toc:  true
---

<!-- Global site tag (gtag.js) - Google Analytics -->
  <script async src="https://www.googletagmanager.com/gtag/js?id=G-TG0XJZG53F"></script>
  <script>
    window.dataLayer = window.dataLayer || [];
    function gtag(){dataLayer.push(arguments);}
    gtag('js', new Date());

    gtag('config', 'G-TG0XJZG53F');
  </script>

<font color= blue> You are required to fix all syntactical errors in the given code. You can click on *Compile & Run* anytime to check the compilation/execution status of the program. You can use *System.out.printin* to debug your code. The submitted code should be logically/syntactically correct and pass al testcases. Do not write the *main()* function as it is not required.


Code Approach: For this question, you will need to correct the given implementation. We de net expect you to modify the approach or incorporate any additional library methods. </font>

### Q1
The function/method ***findIndex*** accept three arguments - *size*, *list* and *key*, an integer representing the size ofthe list; a list of integers and an integer representing the value to search from the given list, respectively. The functior/method ***findIndex*** is supposed to return the index ofthe *key* value if *key* found in the list else return '-1'

The functior/method compiles successfully but fails to return the desired result for some test cases. Your task isto fix the code so that it passes all the test cases.

```javascript
import java.util.*;
import java.lang.*;
import java.io.*;
class Solution
{
  int findIndex(int size, int [] list, int key)
  {
    for(int i=0;i<size;i++)
    {
      if(list(i) == key)
      {
        return i;
      }
    }
    return -1;
  }
}
```  

Answer:
```javascript
import java.util.*;
import java.lang.*;
import java.io.*;
class Solution
{
  int findIndex(int size, int [] list, int key)
  {
    for(int i=0;i<size;i++)
    {
      if(list[i] == key)
      {
        return i;
      }
    }
    return -1;
  }
}
```  

> if(list(i) == key) -> if(list[i] == key)

### Q2
The function/method ***evenMultiplication*** accept two arguments - *size*, and *list*, an integer representing the size of the list and a list of integers. The function/method ***evenMultiplication*** is supposed to return an integer representing the multipicated value of all even number is present.

The function/method compiles successfully but falls to return the desired result for some test cases. Your tasks to fix the code so that it passes all the test cases,

```javascript
import java.util.*;
import java.lang.*;
import java.io.*;
class Solution
{
  int evenMultiplication(int size, int[] list)
  {
    int evenMulti=1;
    for (int i=0; i<size;)
    {
      if(list[i] % 2 == 0)
      {
        evenMulti*=list[i++];
      }
    }
    return evenMulti;
  }
}
```  

Answer:
```javascript
import java.util.*;
import java.lang.*;
import java.io.*;
class Solution
{
  int evenMultiplication(int size, int[] list)
  {
    int evenMulti=1;
    for (int i=0; i<size, i++)
    {
      if(list[i] % 2 == 0)
      {
        evenMulti*=list[i];
      }
    }
    return evenMulti;
  }
}
```

### Q3
The function/method ***oddSum*** accept three arguments - *start* *end*, and *list*, an integer representing the starting index of the range; an integer representing the ending index of the range and a list of integers, respectively. The function/method ***oddSum*** is supposed to return the sum of the odd numbers in the given range from the list.

The functior/method compiles successfully but fails to return the desired result for some test cases. Your task isto fix the code so that it passes all the test cases.

```javascript
import java.util.*;
import java.lang.*;
import java.io.*
class Solution
{
  int oddSum(int start, int end, int[] list)
  {
    int sum =0;
    int i =start;
    while(i<=end)
    {
      if(list[t] % 2 != 0)
      {
        sum+=list[i++];
      }
      i++;
    }
    return sum;
  }
}
```

Answer:
```javascript
import java.util.*;
import java.lang.*;
import java.io.*
class Solution
{
  int oddSum(int start, int end, int[] list)
  {
    int sum =0;
    int i =start;
    while(i<=end)
    {
      if(list[i] % 2 != 0)
      {
        sum+=list[i];
      }
      i++;
    }
    return sum;
  }
}
```

### Q4
A binary search tree (BST) is defined as a binary tree in which each node satisfies the property such that ts value is larger than the value of every node in its left subtree, and less than or equal to the value of every node in its right subtree. The distance between two values in a binary search tree is the minimum number of edges traversed to reach from one value to the other.

The function/method ***searchBST*** accepts two arguments - *root*, a node representing the root node ofthe tre; and *key*, an integer representing the value to be searched, respectively tis supposed to return '1' if keys found inthe binary search tree. Otherwise, it returns '0.'

Your tasks to implement the function/method ***searchBST*** so that it passes all the test cases.

The following class is used to represent a node of the Binary search tree and is already implemented inthe default code (Do not write this definition again in your code):

```javascript
class Node
{
  int key;
  Node left, right;
  public Node(int item)
  {
    key = item;
    left = right = null;
  }
}
```

```javascript
class Solution
{
  int searchBST(NodeBst root, int key)
  {
    if(root == null)
      return 0;
    if(root.kry == key)
      return 1;
    if (key <= root.key)
      return searchBST(root.right, key);
    else {
      return searchBST(root.left, key);
    }
  }
}
```

Answer:
```javascript
class Solution
{
  int searchBST(NodeBst root, int key)
  {
    if(root == null)
      return 0;
    if(root.kry == key)
      return 1;
    if (key <= root.key)
      return searchBST(root.left, key);
    else {
      return searchBST(root.right, key);
    }
  }
}
```

### Q5
The function/method ***searchKeyIndex*** accepts two arguments list_head, a node representing the head node of the linked-list; and *key*, an integer
representing the key value that must be searched inthe linked-list. It is supposed to return a list of integers representing the index values of the key in the linked list if the key value is present in the linked-ist. Otherwise, It returns a list of length of 1 with content '-1'.

Your taskis to implement the function/method ***searchKeyIndex*** to search a value in the linkedist so that it passes all the test cases.

The following lass is used to represent a node of the Linked List and is already implemented in the default code (Do not write this definition again in your code):

```javascript
class NodeLinkedList
{
  int key;
  NodeLinkedList left, right;
  public NodeLinkedList(int item)
  {
    key = item;
    left = right = null;
  }
}
```

```javascript
import java.util.*;
import java.lang.*;
import java.io.*
class Solution
{
  List<Integer> searchKeyIndex(NodeLinkedList list_head, int key)
  {
    List<Integer> res = new ArrayList<>();
    int flag =0;
    int index = -1;
    NodeLinkedList current = list_head;

    while(current.next !=null)
    {
      index++;
      if(current.value == key)
      {
        res.add(index);
        flag = 1;
      }
      else {
        current = current.next;
      }

    if(flag == 1)
      return res;
    else {
      res.add(-1);
      return res;
    }
    }
  }
}
```
Answer:
```javascript
import java.util.*;
import java.lang.*;
import java.io.*
class Solution
{
  List<Integer> searchKeyIndext(NodeLinkedList list_head, int key)
  {
    List<Integer> res = new ArrayList<>();
    int flag =0;
    int index = 0;
    NodeLinkedList current = list_head;

    while(current.nxt !=null)
    {
      if(current.value == key)
      {
        res.add(index);
        flag = 1;
        current = current.next;
      }
      else {
        current = current.next;
      }
      index++;
    }

    if(flag == 1)
      return res;
    else {
      res.add(-1);
      return res;
    }
  }
}
```

### Q6
The function ***calculateGeneralHCF*** accepts two arguments - *len* and *arr*, an integer representing the length of the array and alist of integers, respectively. It is supposed to calculate and return the maximum element inthe input array.

Another function ***calculateHCF(int a, int b)*** returns the HCF of two input numbers a and b.

Your taskisto use calculateHCF(int a, int b) function and complete the code in ***calculateHCF(int len, int *arr)*** so that it passes all test cases.

```javascript
class Solution
{
  int calculateHCF(int a, int b)
  {
    if(a ==0)
      return b;
    return calculateHCF(b % a,a);
  }
  int calculateGeneralHCF(int len, int[] arr)
  {
    // WRITE YOUR CODE HERE
  }
}
```

Answer:
```javascript
class Solution
{
  int calculateHCF(int a, int b)
  {
    if(a ==0)
      return b;
    return calculateHCF(b % a,a);
  }
  int calculateGeneralHCF(int len, int[] arr)
  {
    int overallHCF = 1;
    for(int i = 0; i<arr.length; i++){
      for(int j =0; j<arr.length; j++){
        int currentHCF = calculateHCF(arr[i], arr[j]);
        overallHCF = calculateHCF(currentMax, overallMax);
      }
    }
    return overallMax;
  }
}
```



### Q7
The function ***calculateGeneralMax*** accepts two arguments - *len* and *arr*, an integer representing the length of the array and a list of integers, respectively. Its supposed to calculate and return the maximum element in the input array.

Another function ***calculateMax(int a, int b)*** returns the maximum element of two input numbers aand b.

Your task is to use ***calculateMax(int a, int b)*** function and complete the code in ***calculateGeneralMax(int len, int *arr)*** so that it passes all test cases.

```javascript
class Solution
{
  int calculateMax(int a, int b)
  {
    if(a > b)
      return a;
    else {
      return b;
    }
  }

  int calculateGeneralMax(int len, int[] arr)
  {
    //WRITE YOUR CODE HERE
  }
}
```

Answer:
```javascript
class Solution
{
  int calculateMax(int a, int b)
  {
    if(a > b)
      return a;
    else {
      return b;
    }

  int calculateGeneralMax(int len, int[] arr)
  {
    int overallMax = arr[0];
    for(int i = 0; i<arr.length; i++){
      for(int j =0; j<arr.length; j++){
        int currentMax = calculateMax(arr[i], arr[j]);
        overallMax = calculateMax(currentMax, overallMax);
      }
    }
    return overallMax;
  }
}
```
