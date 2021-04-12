Let us begin with an example:

Take a number: 56789. Rotate left, you get 67895.

Keep the first digit in place and rotate left the other digits: 68957.

Keep the first two digits in place and rotate the other ones: 68579.

Keep the first three digits and rotate left the rest: 68597. Now it is over since keeping the first four it remains only one digit which rotated is itself.

You have the following sequence of numbers:

56789 -> 67895 -> 68957 -> 68579 -> 68597

and you must return the greatest: 68957.

####Task
Write function max_rot(n) which given a positive integer n returns the maximum number you got doing rotations similar to the above example.

So max_rot (or maxRot or ... depending on the language) is such as:

- max_rot(56789) should return 68957

 - max_rot(38458215) should return 85821534



##### My solutions:


##### Python:


````python
def max_rot(n):
    num = str(n)
    rot = []
    if len(num) <= 2 or None:
        return n 
    if len(num) > 2:
        rot.append(num)
        num = num[1:] + num[0]
        rot.append(num)
        num = num[0] + num[2:] + num[1]
        rot.append(num)
    if len(num) >= 4:
        num = num[0:2] + num[3:] + num[2] 
        rot.append(num)
    if len(num) >= 5:
        num = num[0:3] + num[4:] + num[3]
        rot.append(num)
        num = num[0:4] + num[5:] + num[4] 
        rot.append(num)
    if len(num) >= 7: 
        num = num[0:5] + num[6:] + num[5]
        rot.append(num)
    convert_r_input = [int(x) for x in rot]
    return max(convert_r_input)
````


##### javascript

````javascript
function maxRot(n) {
  let listOfNums = [];
  let array = Array.from(n.toString());
  let num = 0;
  while (num < array.length -1) {
    let number = array.splice(num, 1);
    array.push(Number(number));
    listOfNums.push(Number(array.join("")));
    num++;
  }
  listOfNums.unshift(n);
  listOfNums.sort((a, b) => b - a);
  return listOfNums[0]
}
````