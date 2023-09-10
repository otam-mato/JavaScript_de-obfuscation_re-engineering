
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
  - The sum of ASCII values of characters in the clue string must be equal to 469. I modified `tt == 469;` into `tt >= 469;` for the simplicity to trigger `setInterval()` function
  
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

- Drag "X" to (x: 65, y: 76) for 'A' and 'L'.
  ```javascript
  runes
  // Outputs: ['alpha']
  ```

- Move "X" to (x: 66, y: 77) for 'B' and 'M'.
  ```javascript
  runes
  // Outputs: ['alpha', 'beta']
  ```

- Next, to (x: 82, y: 69) for 'R' and 'E'.
  ```javascript
  runes
  // Outputs: ['alpha', 'beta', 'gamma']
  ```

- The final position, (x: 0, y: 84), wasn't necessary. With the length of `runes` array > 2 and the sum of ASCII values of `LAMBERT` > 469, the `setInterval()` function successfully triggers the alert:

![Solution Image](https://github.com/otammato/crack_me_solution/assets/104728608/9c30ed14-b0cb-4034-866f-6de9f55e849d)

<br>

---

<br>

The modified file is available here:

[https://github.com/otammato/crack_me_solution/blob/da85f213666ba2357f582e569ee83f354b6a0b44/crack_me_platinum.html](https://otammato.github.io/crack_me_solution/crack_me_platinum.html)https://otammato.github.io/crack_me_solution/crack_me_platinum.html

Instructions to test it:

1. Drag the "X" marker (canary) around the screen.
2. As you move the marker, the coordinates of the marker will be displayed by the IChing function.
3. Moving the marker to specific coordinates triggers checks against the ASCII values of the clue variable.
4. When the correct set of coordinates is hit in sequence, an alert should display the treasure message.
