# **Lab Report 2**
>## *Code changes in order to fix a bug*

### **Code Change #1**
![alt text](code_change_1_(LR2).png)
>Code changes/edits to the original given code

[*link to failure-inducing input file*](https://github.com/KristinEbu/markdown-parser/blob/main/test-file-new.md)

![alt text](output_for_error_(LR2).png)
>Output of the error (symptom/bug)

 **Relationship Between the Bug, the Symptom, and the Failure-inducing Input:**

 The failure-inducing input file did not include parenthesis in the input we wanted to test, therefore, the value of `closeParen` became `-1` as `")"` couldn't be found in the code. Because of this, we couldn't use the substring method correctly (as `-1` is not a proper index) and caused a "crashing" symptom being error exception `IndexOutOfBounds`. The exception (`IndexOutOfBounds`) itself was the bug in this code. I fixed this by making a substring without looking for parenthesis and just starting the link itself.

 ### **Code Change #2**
![alt text](code_change_2_(LR2).png)
>Code changes/edits to the previous code from "Code Change #1"

[*link to failure-inducing input file*](https://github.com/KristinEbu/markdown-parser/blob/main/test-file-new2.md)

![alt text](output_for_error2_(LR2).png)
>Wrong answer ouput (symptom)

 **Relationship Between the Bug, the Symptom, and the Failure-inducing Input:**

The failure-inducing input file contained a second line that wasn't a link, however, it was still included in the output. This caused the "wrong answer" symptom we could see in the output. The "wrong answer" symptom helped me identify the bug, which was the line `int endLink = markdown.length() - 1;`. This line made the substring method include everything in the file, including new lines. I fixed this by identifying new lines and making sure it substrings by each line.

 ### **Code Change #3**
![alt text](code_change_3_(LR2).png)
>Code changes/edits to the previous code from "Code Change #2"

[*link to failure-inducing input file*](https://github.com/KristinEbu/markdown-parser/blob/main/test-file-new3.md)

![alt text](output_for_error3_(LR2).png)
>Wrong answer output (symptom)

 **Relationship Between the Bug, the Symptom, and the Failure-inducing Input:**

The failure-inducing input file contained two links, each on a separate line, which should've resulted in two links inside the `toReturn` array, but there was only one in the output. This wrong output is another "wrong answer" symptom that led me to find the bug, which was the `break` line in the while loop. By breaking the code after it read one line, it would always produce one element in the `toReturn` array and not read other lines in the given file. I originally wrote this `break` statement because I didn't want it to read the new line that wasn't a link in the last test case, but this new failure-inducing input made me realize I still needed to change a lot in my code. I fixed this by making it check each line individually and checking to see if a link is included in the line. I did this by using `openBracket` and `closeBracket` from the original code; if their values weren't `-1`, then it meant there's a link in the line that needs to be added in the `toReturn` array.