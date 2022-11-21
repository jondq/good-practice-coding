# UNIX WORKBENCH
Notas de curso en Coursera

## Creation and inspection
 - `wc` word count. Cuenta filas, oalabras y # caracteres en un archivo
 `wc leanme.txt`

## Pipe 
The pipe (|) takes the output of the program on its left side and directs the output to be the input for the program on its right side.

 ## Search

- `grep 'key' file.txt` busca key in file. 
- `egrep 'key' file.txt` extención de grep con soporte de multicaracteres 
  - `-n` display de line number 
  - `egrep "^[AEIOU]{1}.+[aeiou]{1}$" states.txt` state names that both begin and end with a vowel
- `find` busca archivos
  - `find . -name "*.jpg"` Busca en directorio local todos los archivo jpg

## Script

### Arguments 
The first argument to your script is stored in $1, the second argument is stored in $2, etc. An array of all of the arguments passed to your script is stored in $@

### Conditional, If and Else
- All Bash programs have an exit status. true has an exit status of 0 and false has an exit status of 1.

- Conditional execution uses two operators: AND (&&) and OR (||) which you can use to control what command get executed based on their exit status.

- Conditional expressions are always in double brackets ([[ ]]). They have exit an exit status of 0 if they contain a true assertion or 1 if they contain a false assertion.

- IF statements evaluate conditional expressions. If an expression is true then the code within an IF statement is executed, otherwise it is skipped.

- ELIF and ELSE statements also help control the flow of a Bash program, and IF statements can be nested within other IF statements.

### Functions
- Functions start with the function keyword followed by the name of the function and curly brackets ({}).

- Functions are small, reusable pieces of code that behave just like commands.

- You can use variables like $1, $2, and $@ in order to provide arguments to functions, just like a Bash script.

- Use the source command in order to read in a Bash script with function definitions so that you can use your functions in your shell.

- Use the local keyword to prevent your function from creating or modifying global variables.

- Be sure to echo the results of your function (if there are any) so that they can be captured with command substitution.