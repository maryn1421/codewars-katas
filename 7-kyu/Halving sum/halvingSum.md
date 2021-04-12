#Task
Given a positive integer n, calculate the following sum:

`n + n/2 + n/4 + n/8 + ... `
All elements of the sum are the results of integer division.

# Example
`25  =>  25 + 12 + 6 + 3 + 1 = 47`



##### my solution:


````java
 public class HalvingSum {
   int halvingSum(int n) {
     int sum = 0;
     int div = 2;
     sum += n;
     while(true) {
     int newNum = n / div;
     sum += newNum;
     div = div * 2;
     if (newNum <= 1) {
     break;
     }

     }
     return sum;
   }
 }
 ````