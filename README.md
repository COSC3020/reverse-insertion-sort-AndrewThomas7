# Reverse Insertion Sort

Consider the code for insertion sort we covered in class:

```javascript
function insertionSort(arr) {
  for(var i = 1; i < arr.length; i++) {
    var val = arr[i];
    var j;
    for(j = i; j > 0 && arr[j-1] > val; j--) {
      arr[j] = arr[j-1];
    }
    arr[j] = val;
  }
  return arr;
}
```

Change this function such that it works from the end of the array rather than
the beginning, `insertionSortReverse()` -- only the direction of
iterating over the elements is reversed, the array is still sorted the same way
(ascending). Add your code in `code.js`. Test your new function; I've provided
some basic testing code that uses [jsverify](https://jsverify.github.io/) in
`code.test.js`.

“I certify that I have listed all sources used to complete this exercise, including the use
of any Large Language Models. All of the work is my own, except where stated
otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is
suspected, charges may be filed against me without prior notice.”-Andrew Thomas


## Average-Case Time Complexity of Insertion Sort

In the lectures, we covered that insertion sort has best-case time complexity of
$\Theta(n)$ and worst-case time complexity of $\Theta(n^2)$. What is the
average-case time complexity ($\Theta$)?

Hint: Think about what happens in each iteration of the loop, and how often the
loop is executed. Keep in mind that for asymptotic analysis we don't care about
constant factors.

Describe your reasoning and the conclusion you've come to. Your reasoning is
most important -- you can easily find the answer, but you need to demonstrate
that you've understood the concept. Add your answer to this markdown file.

## Code Analysis

#### The If Statment:

``` javascript
function ReverseinsertionSort(arr) {
  if(arr.length<1){
    return arr
  }
  ...
}
```
The if statment is a of a constant time. We know this because it just does one check and then moves on or exits. 

$O(1) \uparrow$

#### First For-loop:

```Javascript
function ReverseinsertionSort(arr) {
...
  for (var i = arr.length-1; i >=0; i--) {
    var val = arr[i];
    var j;
    ...
  }
```
The first for-loop starts at the last element of the vector and then counts down to the first element. Thus we have a sequence of the form:

$T(n)=n,n-1,n-2,n....0.$

This sequence yields a time complexity of $n$ because we iterate over the list exactly once. Also note that the operations done on the inside of the for loop are of constant time.

$O(n) \uparrow$


#### The Last loop:

```Javascript
 for (j = i; j <arr.length-1 && arr[j +1] < val; j++) {
      arr[j] = arr[j + 1];
    }
    arr[j] = val;
```

Here we only run the loop until it is less than the last elements index, because we are comparing the item in front of the one we are indexed on. i.e if j=4, we compare with j=5. However as we loop through the first for-loop the value for j changes and we eventually go through the entire list again in the second loop. Thus resulting in a time complexity of $n$ again.

O(n) $\uparrow$

In conclusion this gives us $1+n*n=n^2  \implies T(n) \in \theta(n^2)$
Here we only run the loop until it is less than the last element because we are comparing the item in front of the one we are indexed on. I.e if j=4, we compare with j=5. However as we loop through the first loop the value for j changes and we eventually go through the entire list again, resulting in a time complexity of n again.

In conclusion this gives us $1+n*n=n^2  \implies T(n) \in \theta(n^2)$

