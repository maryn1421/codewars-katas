I'm new to coding and now I want to get the sum of two arrays...actually the sum of all their elements. I'll appreciate for your help.

P.S. Each array includes only integer numbers. Output is a number too.



#### my solution:

````java
public class Sum {

  public static int arrayPlusArray(int[] arr1, int[] arr2) {
    int num = 0;
    for (int item : arr1){
      num += item;
    }
    for (int item : arr2){
      num += item;
    }
    // arr1 + arr2 is not working...
    return num;
  }

}
````