## Problem 1
### Block System Call

Q1(a). Block system call for date command. That means you don't have to uninstall date command but if you run kernel must not accept. <br><br>
A. 1st I searched about how to see system calls happening when a program gets executed. I found out about strace. So I used strace to find what system calls were 
   happening. 
   
   <strong> strace -o date.log date </strong>
   
   This saved system calls in date.log file. The 1st command in this file was:  
   <strong> execve("/usr/bin/date", ["date"], 0x7ffd5b29a750 /* 45 vars */) = 0 </strong> <br>
    
   I looked up about execve online. It is used to execute programs. It's syntax is <br>
   <strong> int execve(const char *pathname, char *const argv[],char *const envp[]); </strong> <br> <br> 
    execve() executes the program referred to by pathname. So I looked up the definition of this function in kernel. I found it here 
   [exec.c](https://github.com/torvalds/linux/blob/16f73eb02d7e1765ccab3d2018e0bd98eb93d973/fs/exec.c) under SYSCALL_DEFINE3. 
    <br><br>
    *So here we can put a check on pathname/filename (1st argument of execve) to look if it is referring to date (/usr/bin/date) and if it does we can just return
    and do nothing*
    <br><br>
    
Q1(b). Do the same Firefox as well<br>
A. *We can follow the same approach for Firefox as well and see if 1st argument supplied to execve refers to firefox if it does we just return and do nothing*
<br><br>

*<strong> Note: In this approach we have to download kernel source code, edit it and recompile the kernel. I'm still searching for an approach to do it 
without this. We can do this using various kernel modules available. 
</strong>*
<br><br>

Q2(a). Create a directory without name from command line <br>
A. We can't have a directory/file with an empty name. However, the name can be something we can't see like whitespace or control characters.
   We can do this by `mkdir " " `. It will look like that the folder has no name.
<br><br>

Q2(b). Create a directory with name "-okgoogle" <br>
A. Tried running mkdir -okgoogle. Got invalid option -- 'o'. The reason I found was it treats anything after <strong> (-) </strong> as an option. -o is used 
   to write output to files. But there is no such option. Hence error. There are 2 options for creating files with this kind of name. <br>
   1. `mkdir ./-okgoogle` <br>
   2. `mkdir -- -okgoogle` 
