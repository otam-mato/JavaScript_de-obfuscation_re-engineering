# Crack_Me Solution

[Link to the puzzle](https://crackme.s3.amazonaws.com/crack_me_platinum.html)

The solution to this coding puzzle involves several steps:

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
// A function to trigger the alert which runs every 2000 milliseconds (2 seconds)
setInterval(() => {
   ...
}, 2000);
```

<details markdown=1>
<summary markdown="span">Detailed description for the `setInterval()` function</summary>

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

### B. Core Puzzle Logic Function

```javascript
function IChing(x,y){
   ...
}
```

### C. Other Artifacts

```javascript
// The spikes array contains obfuscated data
let spikes = ["ymF2aWdhdG9b", ...];
```

```javascript
// Decoding requires swapping the first and last characters of base64 strings
let tY = ...
```

---

## Step 3: Retrieving the Clue

To satisfy the conditions in the `setInterval()` function, we need to retrieve the clue. 

### A. By Deciphering 

Using either: `b(tY(spikes[3]))` or `b(tY(spikes[4]))`.

```javascript
let clue = ...
```

### B. Using DevTools

Simply use the command `clue` to retrieve the actual clue:

```javascript
clue
// outputs 'LAMBERT'
```

---

## Step 4: Understanding Character Values

For the clue to satisfy the conditions, its character values should sum up to 469. 

For example:

For `LAMBERT`, the sum is 499.
For `RIPLEY`, the sum is 469.

---

## Step 5: Options to Trigger the Alert

### A. Modifying the setInterval()

For the `LAMBERT` clue, modify the setInterval() function:

```javascript
return tt >= 469;
```

### B. Modifying the 'User Agent'

Change the 'User Agent' string in your browser to have the string `BLACKSEA` at index 9:

```javascript
let clue = ...
```

---

![Image](https://github.com/otammato/crack_me_solution/assets/104728608/27ae99ce-755c-4f1b-a882-f2db61a81de5)
