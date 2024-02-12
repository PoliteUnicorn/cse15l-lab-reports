# Lab Report 3
## Part 1 - Bugs
* The bug that I chose is the one in the `reverseInPlace` method.
1. A failure inducing input for the buggy program is the integer array {3, 4, 5}. <br>
Example of JUnit test for {3, 4, 5}: 
```
@Test
 public void testReverseInPlaceOddNumber() {
   int[] input1 = {3 , 4, 5};
   ArrayExamples.reverseInPlace(input1);
   assertArrayEquals(new int[]{5, 4, 3}, input1);
 }
```
2. An input that doesn’t induce a failure is an array of just on element {3}. <br>
Example of JUnit test for {3}: 
```
@Test
 public void testReverseInPlace() {
   int[] input1 = {3};
   ArrayExamples.reverseInPlace(input1);
   assertArrayEquals(new int[]{3}, input1);
 }
```

3. The symptom, as the output of running the tests, is that the failure inducing input's test does not pass, while the array with just one element's test does pass.
   ![Image] (bug-failed-test-output.png)

4. The bug, as the before-and-after code change required to fix it
   * Bug from before:
     ```
      static void reverseInPlace(int[] arr) {
         for(int i = 0; i < arr.length; i += 1) {
           arr[i] = arr[arr.length - i - 1];
         }
       }
     ```
   * Code after bug was fixed:
     ```
     static void reverseInPlace(int[] arr) {
       for(int i = 0; i < arr.length / 2; i += 1) {
         //save previous value
         int prevVal = arr[i];
         arr[i] = arr[arr.length - i - 1];
         //switch the two values
         arr[arr.length - i - 1] = prevVal;
       }
     }
     ```
    
* This fix solves the problem of the bug because before, when the method tried to reverse the array, it was changing the values at the previous indices to the values at the later indices. However, the previous values were never stored, so when the method tried copying the values in the previous half (less than arr.length / 2) of the array to the indices in the second half of the array, it was just copying the new values (i.e. the values of the second half of the array). This resulted in the values in the second half of the array being copied twice in the original array. The solution fixes this by only traversing through the front half of the array, then storing the value in the earlier index before assigning it to the value in the larger index. However, because the value in the previous array is stored, it is successfully copied into the later index, and the array is reversed successfully. 

## Part 2 - Researching Commands 
Chosen command: `grep`

4 command line options 
1. Option: `-n`
   * Example 1:
       * command + OUPUT :
         ```
         grep -n "chapter" find-results.txt
         1386:technical//911report/chapter-13.4.txt
         1387:technical//911report/chapter-13.5.txt
         1388:technical//911report/chapter-13.1.txt
         1389:technical//911report/chapter-13.2.txt
         1390:technical//911report/chapter-13.3.txt
         1391:technical//911report/chapter-3.txt
         1392:technical//911report/chapter-2.txt
         1393:technical//911report/chapter-1.txt
         1394:technical//911report/chapter-5.txt
         1395:technical//911report/chapter-6.txt
         1396:technical//911report/chapter-7.txt
         1397:technical//911report/chapter-9.txt
         1398:technical//911report/chapter-8.txt
         1400:technical//911report/chapter-12.txt
         1401:technical//911report/chapter-10.txt
         1402:technical//911report/chapter-11.txt
         ```
         * This command is counting all of the repositories and files with “chapter” in
           their name and also provides the line number for each of the names of the files or 
           repositories that contain the chapter keyword.
         * This is useful in the case where you are going through a large list of files
           or trying to locate one file, and it would give you the line number to find
           the file at.
    * Example 2:
       * command + output:
         ```
         grep -n "bio" technical/biomed/1471-2105-3-2.txt
         11:    	theory on the origin and evolution of biological species [
         366:     biologically-active structure (see CRW Methods
         ```
      * In this case, the grep command is looking for the lines and line numbers
        of the file `technical/biomed/1471-2105-3-2.txt` that contain the word “bio”
        in them.
      * This is useful in the case where you are going through a very long file and
        trying to locate a specific line or topic, but you do not want to look through
        the entire document. Grep would give you the line numbers of the matches, and
        from there, you could look through a shorter list of lines to find the line you 
        are looking for, and you can go to that line in the file to find the rest of the 
        desired information.  
2. Option: `-v`
   * Example 1: 
     * Command + ouptput:
       ```
       $grep -v ".txt" find-results.txt
       
       technical/
       technical//government
       technical//government/About_LSC
       technical//government/Env_Prot_Agen
       technical//government/Alcohol_Problems
       technical//government/Gen_Account_Office
       technical//government/Post_Rate_Comm
       technical//government/Media
       technical//plos
       technical//biomed
       technical//911report
       ```
    * This is searching for all of the files in find-results.txt that do not
      contain .txt in their name.
    * This is useful if you want to get a list of files that do not contain a
      certain keyword or want to get all files except from a certain directory
      or of a certain type, and this will allow you to do so quickly.
      
   * Example 2:
      * Command + ouptput:
        ```
        grep -v "this" technical/plos/pmed.0020191.txt    
        ```
      * 
 

         





     

    





