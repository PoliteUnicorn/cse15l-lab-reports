# Lab Report 5 

## Part 1 - Debugging scenario 

Student’s Original Post:
 ### Aneed Halp: 
Hi! I’m having some trouble with implementing the autograder code. 
When I run the bash script with the link `https://github.com/ucsd-cse15l-f22/list-methods-lab3` 
it works and provides a score and no error message. However, when I run it with the corrected methods link, 
`https://github.com/ucsd-cse15l-f22/list-methods-corrected`, it does not work. It prints me a weird message about how 
`expression recursion level exceeded` and doesn’t print out the score correctly either. However, it works for the compile 
errors code too. I think that there is something wrong with my grading code at line 51 as to how I call the variables to 
do subtraction, so I put a `$` in front of the variable names. Am I assigning my variable correctly? Do you know how to 
solve this? 
Thanks!

`<Screenshot>` This is my code at line 51 and the output for the corrected methods when it throws a bug: ![Image](step_1_student_list_correct_bug.png)

`<Screenshot>` This is my code and the output for the other tests where it works. ![Image](step_1_student_subtle_bug.png)

### TA Response 
Hi Aneed! 
Have you tried to print out the values for the `tests` and `failures`? It might be helpful to see what 
values are being stored before they are printed out into the terminal. Additionally, I don’t think that 
you need the `$` before each variable name when assigning a value to `successes` because you have the 
double parentheses already. In bash, arithmetic is done in the form `$(())`, and the inner variables do 
not need another `$` before them.

### Aneed Halp
Thanks for the help! I tried printing out the value of the `tests` and `failures` variables. I added the echo statements, 
but nothing was printed out at first. Then, I tried printing out the `lastline` variable and I realized that the bug is 
that I didn’t take into account the format of the JUnit tests when all of the test cases pass. It says `OK (2 tests)`, 
so it doesn’t get the correct values for the score. The `tests` variable stores the word `tests)` and the failures variable is out of bound for the length of the output, so it stores nothing. That’s why when the final score is printed it says ` / tests)` instead of the actual score.

<Screenshot> These are the values of `tests` and `failures` when all of the test cases pass. We can see that `tests` and `failures` do not contain the correct nuber of tests run and failed respectively.
![Image](student-finds-bug.png)
<Screenshot> These are the values of `tests` and failures when not all test cases pass. In this you can see that the correct number of tests and failures are actually stored in the correct variables. 
![Image](student-finds-bug2.png)




