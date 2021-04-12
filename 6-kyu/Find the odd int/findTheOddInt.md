Given an array of integers, find the one that appears an odd number of times.

There will always be only one integer that appears an odd number of times.



my solution:

````java
class FindOdd {
    public static int findIt(int[] a) {
        int result = 0;
        Map<Integer, Integer> numberAppears = new HashMap<Integer, Integer>();

        for (int num : a) {
            int appear = 0;
            for (int secondNum : a) {
                if (secondNum == num) {
                    appear++;
                }
            }
         numberAppears.put(num, appear);
        }
        for (Map.Entry<Integer, Integer> entry : numberAppears.entrySet()) {
             if (entry.getValue() % 2 != 0) {
                 result = entry.getKey();
                 break;
             }
        }

        return result;

    }
}
````