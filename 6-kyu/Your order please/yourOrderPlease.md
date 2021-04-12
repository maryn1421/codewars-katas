Your task is to sort a given string. Each word in the string will contain a single number. This number is the position the word should have in the result.

Note: Numbers can be from 1 to 9. So 1 will be the first word (not 0).

If the input string is empty, return an empty string. The words in the input String will only contain valid consecutive numbers.

###Examples
````
"is2 Thi1s T4est 3a"  -->  "Thi1s is2 3a T4est"
"4of Fo1r pe6ople g3ood th5e the2"  -->  "Fo1r the2 g3ood 4of th5e pe6ople"
""  -->  ""
````


### My solution:


````java
import java.util.*;

public class Order {
  public static String order(String words) {
    String[] arr = words.split(" ");
    int n = arr.length; 
        for (int i = 0; i < n-1; i++) 
            for (int j = 0; j < n-i-1; j++) 
                if (getNumberFromWord(arr[j]) > getNumberFromWord(arr[j+1])) 
                { 
                    String temp = arr[j]; 
                    arr[j] = arr[j+1]; 
                    arr[j+1] = temp; 
                }
    StringBuilder newWord = new StringBuilder();
    
    for (String word : arr) {
      newWord.append(word).append(" ");
    }
    
    return newWord.toString().trim();
  }
  
  
  public static int getNumberFromWord(String word) {
    int number = 0;
    for (char character : word.toCharArray()) {
      if (Character.isDigit(character)) {
        number = Character.getNumericValue(character);
      }
    }
    return number;
  }
}

````

