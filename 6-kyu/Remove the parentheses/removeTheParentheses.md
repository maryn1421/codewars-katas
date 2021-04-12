Remove the parentheses
In this kata you are given a string for example:

````"example(unwanted thing)example"```` <br>

Your task is to remove everything inside the parentheses as well as the parentheses themselves.

The example above would return:

````"exampleexample"````

Notes
Other than parentheses only letters and spaces can occur in the string. Don't worry about other brackets like "[]" and "{}" as these will never appear.
There can be multiple parentheses.
The parentheses can be nested.


###### My Solution:


````java
public class Kata {
    public static String removeParentheses(final String str) {
        boolean toAdd = true;
      char[] chars = str.toCharArray();
      String out="";
      int numberOfBracket= 0;
      for(char word:chars){
        if(word == '('){
          numberOfBracket++;
          toAdd = false;
        }
        if (word == ')'){
          numberOfBracket--;
          toAdd = true;
      }
        if(toAdd && word != ')'&& numberOfBracket == 0){
          out += word;
        }
      }
        return out; // your code here
    }
}
````