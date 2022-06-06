---
layout: post
title: Random Shuffling an Array
date: 2020-10-08
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Algorithm
tags:
- algorithm
- programming
- random-shuffle
meta:
_edit_last: '21980982'
---
Sorting an array in any language is quite trivial as most of them have built in libraries to perform the task quite
  efficiently. However, most languages lack the ability to Shuffle an Array(Make a random sort). One trivial way to
  implement that would be to repeatedly take successive permutations of a sorted array, but the computations would get
  costly for even a relatively small sized array. There is an <strong>O(n)</strong> solution to the problem which
  doesn't even require the original array to be in any particular order.

The solution involves  iterating over the array and swap a number with the current iterating position, where the
  candidate for exchange is located at a higher index. We may also keep the number at its current position. The exact
  candidate is of course selected at random(after all it's a Random Shuffle). That is all there is to it. Every possible
  permutation has equal chance of being obtained which can be proven by trivial mathematics.

Suppose we have an Array of length <strong>n</strong>(0 based). Consider placing a number at the 0th index, we can
  see that any number has 1/n chance of being placed at the 0th index. Now consider the 1st index. We have two different
  case for a number to be placed here: It wasn't placed at the 0th index and can be placed here or it was already placed
  in the 0th index hence it has no chance to get placed here. Therefore, probability of a number taking 1st index is
  <strong>(n-1)/n * 1/(n-1) = 1/n</strong>. Similarly, if we proceed to the 2nd index, probability of a number not
  getting placed at 0th and 1st and then placed here is <strong>(n-1)/n*(n-2)/(n-1) * 1/(n-2) =  1/n</strong>. It can be
  observed that, every number is equally likely to get placed at any index and hence the shuffling algorithm isn't
  biased.
  
A sample code in Java is given below, which can be readily adapted to any language.
{% highlight java %}
public static void RandomShuffleArray(int[] numbers)
{
  int temp, index,i;
  for (i = 0; i < numbers.length; i++)
  {
    index=(int) (Math.random() * (numbers.length - i)) + i;
    temp=numbers[i];
    numbers[i]=numbers[index];
    numbers[index]=temp;
  }
} {% endhighlight %}

Obtaining a random number can be tricky at
  times depending on the language. For example, in JavaScript,  the
  built in
  random number generator always returns a floating value within 0 to 1. However, it can be readily modified to obtain the
  desired range of random numbers.