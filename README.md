
### Crack_Me Solution

https://crackme.s3.amazonaws.com/crack_me_platinum.html

The solution to this coding puzzle involves several steps:

#### 1. Displaying the Objective Message:
To get an overview of the task at hand, I manipulated the code to bypass the built-in logic and directly display the decoded message. The alert message was obtained by decoding the provided base64 strings:

```javascript
alert(atob("YWxlcn"+"QoIkNvbmdy"+"YXR1bGF0aW9uc"+"yBPaCAxMzM3I"+"E9uZSEgWW91IGh"+"hdmUgZm91bmQgbXkg"+"dHJlYXN1cmUhIik="));
```

![Objective Image](https://github.com/otammato/crack_me_solution/assets/104728608/2a7669ff-78f0-4a50-a58a-ef593fb4abb7)

#### 2. Understanding the Alert Mechanism:
Upon further examination, I discerned the mechanism triggering the alert:

- The `setInterval()` function's `if` condition performs two checks:
  - The length of the `runes` array must exceed 2.
  - The sum of ASCII values of characters in the clue string must be equal to 469.
  
If these conditions are met, the encoded congratulatory message displays:

```javascript
ee(b("YWxlcn"+"QoIkNvbmdy"+"YXR1bGF0aW9uc"+"yBPaCAxMzM3I"+"E9uZSEgWW91IGh"+"hdmUgZm91bmQgbXkg"+"dHJlYXN1cmUhIik="));
```

This message translates to:
```
alert("Congratulations Oh 1337 One! You have found my treasure!")
```

#### 3. Disabling debugger Mechanism:
A mechanism in the `setInterval()` function launches the debugger every 2 seconds to halt the code execution if DevTools are open. To bypass this, I disabled the function:

```javascript
// ee('dLb'.replace('L', 'e') +'ug' + '14r'.replace('14', 'ge'));
```

#### 4. Disabling Image ID Manipulation:
The code manipulates the `clue` variable based on the Image's ID. I disabled this mechanism to simplify the process:

```javascript
/* 
// var el = new Image();
// Object.defineProperty(el, 'id', {
// get: function () {
// clue = b(tY(spikes[0x05]));
// }
// });         
// requestAnimationFrame(function check() {
// console.dir(el);
// console.clear();
// requestAnimationFrame(check);
// });
*/
```

#### 5. Displaying Coordinates:
For convenience, I modified the IChing() function to display x and y coordinates in a standard format instead of the base64 encoded string:

```javascript
document.getElementById("gps").innerHTML = y.toString() + "," + x.toString();
```

#### 6. Retrieving the Clue:
Using DevTools and the `clue` command in the console, I identified the keyword 'LAMBERT'. 

```javascript
clue
// Outputs: 'LAMBERT'
```

The ASCII values for the characters in `LAMBERT` are:

- L: 76
- A: 65
- M: 77
- B: 66
- E: 69
- R: 82
- T: 84

#### 7. Solving Using Coordinates:
I then matched the ASCII values to the coordinates on the screen:

- Drag "X" to (x: 76, y: 65) for 'L' and 'A'.
  ```javascript
  runes
  // Outputs: ['alpha']
  ```

- Move "X" to (x: 77, y: 66) for 'M' and 'B'.
  ```javascript
  runes
  // Outputs: ['alpha', 'beta']
  ```

- Next, to (x: 69, y: 82) for 'E' and 'R'.
  ```javascript
  runes
  // Outputs: ['alpha', 'beta', 'gamma']
  ```

- The final position, (x: 84, y: 0), wasn't necessary. With the length of `runes` array > 2 and the sum of ASCII values of `LAMBERT` > 469, the `setInterval()` function successfully triggers the alert:

![Solution Image](https://github.com/otammato/crack_me_solution/assets/104728608/9c30ed14-b0cb-4034-866f-6de9f55e849d)

