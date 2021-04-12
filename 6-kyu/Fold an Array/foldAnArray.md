#Fold an array

In this kata you have to write a method that folds a given array of integers by the middle x-times.

An example says more than thousand words:

````Fold 1-times:
[1,2,3,4,5] -> [6,6,3]

A little visualization (NOT for the algorithm but for the idea of folding):

Step 1         Step 2        Step 3       Step 4       Step5
5/           5|         5\          
4/            4|          4\      
1 2 3 4 5      1 2 3/         1 2 3|       1 2 3\       6 6 3
----*----      ----*          ----*        ----*        ----*


Fold 2-times:
[1,2,3,4,5] -> [9,6]
````


As you see, if the count of numbers is odd, the middle number will stay. Otherwise the fold-point is between the middle-numbers, so all numbers would be added in a way.

The array will always contain numbers and will never be null. The parameter runs will always be a positive integer greater than 0 and says how many runs of folding your method has to do.

If an array with one element is folded, it stays as the same array.

The input array should not be modified!

Have fun coding it and please don't forget to vote and rank this kata! :-)

I have created other katas. Have a look if you like coding and challenges.


### My Solution:


````java

import java.util.*;

public class Kata
{
  public static int[] foldArray(int[] array, int runs)
  {
    
    for (int i=0; i < runs; i++) {
      array = foldOnce(array);
    }
    
    return array;
  }
  
  public static int[] foldOnce(int[] array) {
    int n = array.length;
    
    int[] a = new int[(n + 1)/2];
    int[] b = new int[n - a.length];

    System.arraycopy(array, 0, a, 0, a.length);
    System.arraycopy(array, a.length, b, 0, b.length);
    
    int[] result = new int[a.length];
    
    
        
    if (n % 2 == 0) {
      
      for (int i=0; i < a.length; i++) {
        result[i] = a[i] + b[b.length-i -1];
      }
      
    }
    else {
       for (int i=0; i < a.length -1; i++) {
        result[i] = a[i] + b[b.length-i -1];
      }
      result[a.length-1] = a[a.length-1];
    }
    
    return result;
    
  }
}
````
