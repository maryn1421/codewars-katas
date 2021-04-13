Write a function that takes in a string of one or more words, and returns the same string, but with all five or more letter words reversed (like the name of this kata).

* Strings passed in will consist of only letters and spaces.
* Spaces will be included only when more than one word is present.

Examples:

`````spinWords("Hey fellow warriors") => "Hey wollef sroirraw"
spinWords("This is a test") => "This is a test"
spinWords("This is another test") => "This is rehtona test"
`````



### My solution:

````java

public class SpinWords {

  public String spinWords(String sentence) {
     String[] words = sentence.split(" ");

        for (int i=0;i < words.length; i++) {
            if (words[i].length() > 4) {
                StringBuilder builder = new StringBuilder();
                builder.append(words[i]);
                builder.reverse();
                words[i] = builder.toString();
            }
        }
        return String.join(" ", words);    
  }
}
````