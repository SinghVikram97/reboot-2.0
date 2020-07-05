## Problem 6
### Run command without any output 

Question-> 
  - Open terminal and type any command 
  - Once you press enter your output of given command must not  print
  - You are not allowed to redirect output anywhere
  
Answer->

  - If we had to redirect output then we could have written `exec > /dev/null` in our .bashrc file and it would work
  - We can use bash options to prevent the output
  - One of the option is `bash -n` it syntax checks the command but doesn't execute it. No commands will be executed
  - So write `bash -n` in your .bashrc file for permanent changes or just open terminal and run it for temporary change
  - We can also use `bash -D`. It does the following *List double-quoted strings prefixed by $, but do not execute commands in script*
  - Here is how it looks
  
  ![solution](https://i.ibb.co/pK5tLnQ/image.png)
  
  
