# crack_me_solution

1. To see the objective, manipulated the code to bypass all the logic and directly display the decoded alert message, decoded base64 strings:
   ```
   alert(atob("YWxlcn"+"QoIkNvbmdy"+"YXR1bGF0aW9uc"+"yBPaCAxMzM3I"+"E9uZSEgWW91IGh"+"hdmUgZm91bmQgbXkg"+"dHJlYXN1cmUhIik="));
   ```
2. found out how the mechanism of triggering the alert works and modified the `if` condition of the `setInterval()` function.
   
   The if condition checks two things:
    - That the length of the runes array is greater than 2.
    - The immediately-invoked function expression (IIFE) calculates the sum of ASCII values of the characters in the clue string and checks if it equals 469.
    If both conditions are true, the nested code within the if-statement gets executed:

   `ee(b("YWxlcn"+"QoIkNvbmdy"+"YXR1bGF0aW9uc"+"yBPaCAxMzM3I"+"E9uZSEgWW91IGh"+"hdmUgZm91bmQgbXkg"+"dHJlYXN1cmUhIik="));`

    This base64 string, when decoded, translates to: alert("Congratulations Oh 1337 One! You have found my treasure!"). It's a congratulatory message that pops up when you solve the puzzle.

   
3. switched off the mechanism embedded in the `setInterval()` function  which prevents from using DevTools (which launches the debugger every 2 seconds and stopping the execution of code if DevTools are open):
  
   `// ee('dLb'.replace('L', 'e') +'ug' + '14r'.replace('14', 'ge'));`
   
6. switched off the mechanism related to the manipulation of the `clue` variable based on the Image's ID. 
   ```
   // var el = new Image();
            // Object.defineProperty(el, 'id', {
            //     get: function () {
            //         clue = b(tY(spikes[0x05]));
            //     }
            // });         
            // requestAnimationFrame(function check() {
            //     console.dir(el);
            //     console.clear();
            //     requestAnimationFrame(check);
            // }); 
   ```

8. To display the coordinates when the "x" is being moved over the screen in a regular format on the screen (rather than base64 encoded),  modified the IChing() function:

    ```
    // document.getElementById("gps").innerHTML = btoa(y.toString() + "," + x.toString()).replace("=", "\n\<br>\\n");
    document.getElementById("gps").innerHTML = y.toString() + "," + x.toString();
    ```

9. To find the `clue`, used DevTools and launched the `clue` command in the console and got 'LAMBERT':

   ```
   clue
   'LAMBERT'
   ```

10. tyuyyut
    
   ```
   
   L = ASCII value: 76
   A = ASCII value: 65
   M = ASCII value: 77
   B = ASCII value: 66
   E = ASCII value: 69
   R = ASCII value: 82
   T = ASCII value: 84
   
   ```

11. Drag the "X" to the following coordinates:

   Drag the "X" to (x: 76, y: 65), corresponding to the ASCII values of the characters 'L' and 'A'.<br>
   Move the "X" to (x: 77, y: 66) for 'M' and 'B'.<br>
   Then, drag it to (x: 69, y: 82) for 'E' and 'R'.<br>
   Finally, move the "X" to (x: 84, y: 0). The y value is 0 since we've run out of paired characters.<br>
