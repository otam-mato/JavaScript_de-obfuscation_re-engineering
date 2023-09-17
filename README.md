# Code re-engineering task (Crack_Me Solution)

[View the puzzle here](https://crackme.s3.amazonaws.com/crack_me_platinum.html)

This solution walkthrough covers multiple steps in deciphering the coding puzzle:

---

## Step 1: Understanding the Objective
To understand the objective, bypass the built-in logic to display the decoded message directly. The alert message was obtained by decoding the provided base64 strings:

```javascript
alert(atob("YWxlcn"+"QoIkNvbmdy"+"YXR1bGF0aW9uc"+"yBPaCAxMzM3I"+"E9uZSEgWW91IGh"+"hdmUgZm91bmQgbXkg"+"dHJlYXN1cmUhIik="));
```

![Objective Image](https://github.com/otammato/crack_me_solution/assets/104728608/2a7669ff-78f0-4a50-a58a-ef593fb4abb7)

---

## Step 2: Analysis of Primary Functions and Variables

### A. Main Function Triggering the Alert

```javascript
// Set up a function to run every 2000 milliseconds (2 seconds)
setInterval(() => {

    // Run the "debugger" command (by obfuscating the string "debugger" and then evaluating it)
    ee('dLb'.replace('L', 'e') +'ug' + '14r'.replace('14', 'ge'));
    
    // Check if the "runes" array has more than 2 elements
    // AND if the sum of character codes of the "clue" string is 469
    if (runes.length > 2 && (function (targ) {
                                 tt = 0;
                                 // Calculate the sum of character codes
                                 for (i = 0; i < targ.length; i++) {
                                     tt += targ.charCodeAt(i);
                                 }
                                 // Return true if the sum is 469
                                 return tt == 469;
                             })(clue)){
        // Display an alert saying "Congratulations Oh 1337 One! You have found my treasure!"
        // (By obfuscating the message and then decoding and evaluating it)
        ee(b("YWxlcn"+"QoIkNvbmdy"+"YXR1bGF0aW9uc"+"yBPaCAxMzM3I"+"E9uZSEgWW91IGh"+"hdmUgZm91bmQgbXkg"+"dHJlYXN1cmUhIik="));
        
        // Reset the "runes" array to be empty
        runes=[];
    }
}, 2000);

```

<details markdown=1><summary markdown="span">Detailed description for the `setInterval()` function</summary>

 The `setInterval` function sets up a repeated action to be taken at a fixed interval. In this case, it's set to 2000 milliseconds (or 2 seconds). This means the provided function inside `setInterval` will execute every 2 seconds.
    
 #### a. `ee('dLb'.replace('L', 'e') +'ug' + '14r'.replace('14', 'ge'));`
 This line is obfuscating a string:
 
 - `'dLb'.replace('L', 'e')` results in the string "deb".
 - `'ug'` is just the string "ug".
 - `'14r'.replace('14', 'ge')` results in the string "ger".
 
 So, the final concatenated string is "debugger". This means the line translates to `ee("debugger")`. I also found out that `ee` is an alias for the `eval` function, this is a command to execute the "debugger" statement, which will pause execution in debugging tools like the Chrome DevTools.
 
 #### b. The `if` statement:
 
 This checks two conditions:
 
 i. `runes.length > 2`: This checks if the `runes` array has more than 2 elements.
 
 ii. `(function (targ) {...})(clue)`: This is an immediately-invoked function expression (IIFE). It receives `clue` as its argument (named `targ` inside the function). The function calculates the sum of the Unicode character codes of `targ` and checks if the sum equals 469.
 
 If both conditions are true, then:
 
 - The obfuscated string `b("YWxlcn"+"QoIkNvbmdy"+"YXR1bGF0aW9uc"+"yBPaCAxMzM3I"+"E9uZSEgWW91IGh"+"hdmUgZm91bmQgbXkg"+"dHJlYXN1cmUhIik=")` is decoded using function `b` (which is a variable for `atob`, responsible for decoding base64 strings) and then evaluated using `ee` (which is `eval`). The decoded string is: `alert("Congratulations Oh 1337 One! You have found my treasure!")`, which will show an alert box with this congratulatory message.
 
 - The `runes` array is reset to be empty with `runes=[]`.
 
 In summary, every 2 seconds, this script triggers a debugger, checks if certain conditions are met, and if they are, alerts the user that they've found a "treasure".

</details>

### B. Core Logic Function

```javascript
function IChing(x,y){

       // This commented-out code would set the innerHTML of an element with id "gps" to a base64 encoded version of the coordinates x and y.
   
       // document.getElementById("gps").innerHTML = btoa(y.toString() + "," + x.toString()).replace("=", "\n\<br>\\n");
   
       // For manual interaction and moving the "X" on the screen to hit the coordinates, I set up the x and y coordinates to be displayed in the decoded format:
       document.getElementById("gps").innerHTML = y.toString() + "," + x.toString();
   
       // Check if y matches the char code of the first character in clue, x matches the char code of the second character in clue, and the runes array is currently empty.
       if (y == clue.charCodeAt(0) && x == clue.charCodeAt(1) && !runes.length){
           // If conditions are met, push a value from spikes[11] to the runes array
           runes.push(b(tY(spikes[11])));
       } 
       // Similar to the above, but now checking the 3rd and 4th characters in clue and if the runes array currently has 1 element.
       else if (y == clue.charCodeAt(2) && x == clue.charCodeAt(3) && runes.length == 1){
           runes.push(b(tY(spikes[12])));
       } 
       // Similarly, checking the 5th and 6th characters in clue and if the runes array currently has 2 elements.
       else if (y == clue.charCodeAt(4) && x == clue.charCodeAt(5) && runes.length == 2){
           runes.push(b(tY(spikes[13])));
         }
      }
```

<details markdown=1><summary markdown="span">Detailed description for the `IChing()` function</summary>

1. IChing takes in x and y as parameters and sets an HTML element with ID "gps" to display these coordinates.
2. The function then checks whether x and y match specific characters from the clue string and also ensures that the runes array has a specific length before making any operations:
- If y and x match the first two characters of clue and runes is empty, the function gets the 12th item from spikes, translates its Y position using the tY function, and then pushes its 'decoded' form (using function b) to the runes array.
- If y and x match the third and fourth characters of clue and runes has one item, a similar operation is performed but using the 13th item from spikes.
- If they match the fifth and sixth characters and runes has two items, the 14th item from spikes is used.

</details>

### C. Other Artifacts

The 'spikes' array serves as a source of values for all logic of the puzzle

```javascript
// The spikes array contains obfuscated data and is used by all primary functions
let spikes = ["ymF2aWdhdG9b", "0XNlckFnZW5d", "=W5kZXhPZg=a", "=EFNQkVSVA=T", "ZklQTEVU", "=UxERVJTT04Q", "=kxBQ0tTRUEQ", "yGlZ", "=2xlYXIY", "=2x1ZQ=Y", "52FuYXJY", "=WxwaGEY", "=mV0YQ=Y", "=2FtbWEZ"]
```

The decoding mechanizm of the 'spikes' values

```javascript
// Decoding requires swapping the first and last characters of base64 strings
let tY = (function(){
                function n(s){
                    bb = s[0], nn = s[s.length-1];
                    return nn + s.substring(1, s.length-1) + bb;
                }
                return n;
            })()
```

---

## Further steps

To satisfy the conditions in the `setInterval()` function, we need to retrieve the clue, convert its characters into coordinates, hit those coordinates by moving "X" over the screen or just calling IChing(...) using those coordinates

## Step 3: Retrieving the Clue

### A. Logic for determining the clue:

The clue is retrieved from `spikes` array and can be either `b(tY(spikes[3]))` which equals to 'LAMBERT' or `b(tY(spikes[4]))` which equals to 'RIPLEY' using this logic:

```javascript
let clue = (function(){
                if (window[b(tY(spikes[0x00]))][b(tY(spikes[0x01]))].indexOf(b(tY(spikes[0x06]))) == 9){
                    return b(tY(spikes[0x04]));
                } else {
                    return b(tY(spikes[0x03])); 
                }; 
            })();
```

### B. Using DevTools determine the current value of 'clue'

Type the command `clue` to retrieve the actual one:

```javascript
clue
// outputs 'LAMBERT'
```

### C. Switching the 'clue' to 'RIPLEY'

To switch the 'clue' to 'RIPLEY', some user agent manipulations are necessary. Please see below for details. 

---

## Step 4: Understanding Character Values

For the clue to satisfy the second condition of setInterval(), its character values should sum up to 469. 


### A. For 'LAMBERT', 

The ASCII values for the characters in `LAMBERT` are:

   - L: 76
   - A: 65
   - M: 77
   - B: 66
   - E: 69
   - R: 82
   - T: 84
     
The sum is 499.

the coordinates are:

   (65, 76)
   (66, 77)
   (82, 69)


### B. For 'RIPLEY'

the ASCII values for each letter in 'RIPLEY':

   - R: 82
   - I: 73
   - P: 80
   - L: 76
   - E: 69
   - Y: 89

The sum is 469.

the coordinates are:

   (73,82)
   (76,80)
   (89,69)

---

## Step 5: Options to Trigger the Alert

### A. Modifying the setInterval() function

For the 'LAMBERT' clue, modify the setInterval() function:

```javascript
return tt >= 469;
```

### B. Modifying the 'User Agent'

For the `RIPLEY` clue:

Change the 'User Agent' string in your browser to have the string `BLACKSEA` at index 9, to satisfy this condition:

```javascript
let clue = (function(){
                if (window[b(tY(spikes[0x00]))][b(tY(spikes[0x01]))].indexOf(b(tY(spikes[0x06]))) == 9){
                    return b(tY(spikes[0x04]));
                } else {
                    return b(tY(spikes[0x03])); 
                }; 
            })();
```

---

![Image](https://github.com/otammato/crack_me_solution/assets/104728608/27ae99ce-755c-4f1b-a882-f2db61a81de5)


---

## **Step 6: Triggering the Alert**

- Manually drag and drop the "X" to the identified coordinates.
- Alternatively, use the `IChing(x,y)` function with the discovered x and y coordinates.
- With each correct coordinate input, the 'runes' array gets updated.
- Once the conditions are met, the alert activates.

> **Note**: You might need to disable the debugging mechanism that halts script execution or hit the debugger's 'play' button multiple times to finalize the script execution.
