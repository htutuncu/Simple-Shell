# Simple-Shell
A simple shell implementation that can handle Linux commands.


#### The shell program can work in 2 ways: `Interactive mode` and `batch mode`.

Interactive mode can be used only by typing commands.
Any shell process you use to get its output back.
In batch (batch) mode, when the script runs, here
A non-interactive shell that runs commands is started. Your commands
After running, exits when the file is finished.



Program terminates when CTRL + D is pressed or quit command is entered while `interactive mode` is running.


When the shell is run in `batch mode`, one of the commands in the file
If one is not "quit", all commands written to the end of the file are executed.
If the "quit" command is encountered while reading the file, the
commands are executed and the following commands are not executed.


### Functions

```c
void interactiveMode(): This function clears the screen, making it a shell
provides the appearance. At each step in a loop, the prompt is displayed on the screen.
it waits for the user to enter a command continuously. The line the user entered
send it to the execution () function for processing.
```

```c
void batchMode(char**): File name sent from the main function
opens the file in read mode using. It prints the file contents on the screen first.
Then it takes each row one by one and sends it to the function execution () to process those lines.
```


```c
void execution(char*): Separates the sent line according to ";". 
It bifurcates processes using the fork () function. Then each command parsed, 
sends to the function myExecvp (). Arranges using functions wait() and waitpid() execute the processes. 
In this way, when processes are run in parallel
prevents new entries. 
```


```c
int myExecvp(char*): Commands separated by ";"
in view of the possibility of not having the splitLine () function
sends. The two-dimensional array that returns from the splitLine () function
allows the command to be executed with the execvp () function.
```


```c
char **splitLine(char*) : Separating the submitted one-dimensional array into spaces.
It is an auxiliary function that assigns a two dimensional array.
```

```c
char* removeLeadingSpaces(char*) : Submitted one-dimensional index
helper that returns back by deleting leading and trailing spaces
is function.
```
