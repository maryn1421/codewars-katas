n this Kata, you will be given a string that has lowercase letters and numbers. Your task is to compare the number groupings and return the largest number. Numbers will not have leading zeros.

For example, `solve("gh12cdy695m1") = 695`, because this is the largest of all number groupings.

Good luck!

Please also try Simple remove duplicates



### My solution:

````java

import java.util.ArrayList;
import java.util.List;

class Solution{
   public static int solve(String str){
        str = str.replaceAll("[^\\d]", " ");
        str = str.trim();
        str = str.replaceAll(" +", " ");
        List<Integer> nums = new ArrayList<>();
        String[] split = str.split(" ");
        for (String item: split) {
            nums.add(Integer.parseInt(item));
        }
        int max = nums.get(0);

        for (int i = 0; i < nums.size(); i++) {
            if (max < nums.get(i)) {
                max = nums.get(i);
            }
        }

        return max;
    }
}
````