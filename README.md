# crack_me_solution

1. To see what to expect manipulated the code to bypass all the logic and directly display the decoded alert message, decoded base64 strings:
   ```
   alert(atob("YWxlcn"+"QoIkNvbmdy"+"YXR1bGF0aW9uc"+"yBPaCAxMzM3I"+"E9uZSEgWW91IGh"+"hdmUgZm91bmQgbXkg"+"dHJlYXN1cmUhIik="));
   ```
3. found out how the mechanism of triggering the alert works and modified the `if` condition of `setInterval()` function.
   
   The if condition checks two things:
    - That the length of the runes array is greater than 2.
    - The immediately-invoked function expression (IIFE) calculates the sum of ASCII values of the characters in the clue string and checks if it equals 469.
    If both conditions are true, the nested code within the if-statement gets executed:

   `ee(b("YWxlcn"+"QoIkNvbmdy"+"YXR1bGF0aW9uc"+"yBPaCAxMzM3I"+"E9uZSEgWW91IGh"+"hdmUgZm91bmQgbXkg"+"dHJlYXN1cmUhIik="));`

    This base64 string, when decoded, translates to: alert("Congratulations Oh 1337 One! You have found my treasure!"). It's a congratulatory message that pops up when you solve the puzzle.

   
5. switched off the mechanism of launching the debugger: `// ee('dLb'.replace('L', 'e') +'ug' + '14r'.replace('14', 'ge'));`
   
7. switched off the mechanism of replacing the clue:
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

 8. To display the coordinates in a regular format on the screen (not base64 encoded), modified the IChing function:

    ```
    // document.getElementById("gps").innerHTML = btoa(y.toString() + "," + x.toString()).replace("=", "\n\<br>\\n");
    document.getElementById("gps").innerHTML = y.toString() + "," + x.toString();
    ```

 
