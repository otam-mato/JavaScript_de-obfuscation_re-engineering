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

...

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
