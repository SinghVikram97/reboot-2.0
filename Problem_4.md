## Problem 4
### Share and files and folder 

Question-> 
  - Create two users name jack and Jill  from command line
  - Create all the data under home directory of each users 
  - Login with jack user and create a file name  jack.txt using vim editor and write "hello jack"
  - From jack user also create two directories name jack1 & jack2 
  - Now login from Jill user and create a file. Jill.txt using vim editor and write "hey jiil"
  - From Jill also create two directoires named jill1 & jill2 
  
*Important :  swap these files and directories in between users  and to swap don't use root account.*

Answer->

  Setup
  - /tmp directory is shared among all users
  - Login as Root (Since we need root account to create users)
  - `useradd jack` (Add user jack)
  - `passwd jack` (Set password for user jack)
  - `useradd jill` (Add user jill)
  - `passwd jill` (Set password for user jill)
  - Now we have 2 users jack and jill
  - Now login as jack
  - Open terminal and do following steps
  - `vim jack.txt` (Opening file in vim)
  - Press `i` to get into insert mode type `hello jack` then press `:wq` to save and exit
  - `mkdir {jack1,jack2}` (To make 2 directories named jack1 and jack2)
  - Now logout and login as jill
  - Open terminal and do following steps
  - `vim jill.txt` (Opening file in vim)
  - Press `i` to get into insert mode type `hello jill` then press `:wq` to save and exit
  - `mkdir {jill1,jill2}` (To make 2 directories named jill1 and jill2)
  
  Swap
   - Login as jack
   - Open terminal and run following command
   - `cp -r /home/jack/{jack1,jack2,jack.txt} /tmp` (Copying jack's data to tmp folder)
   - Now log out and login as jill
   - Open terminal and run following command
   - `cp -r /tmp/{jack1,jack2,jack.txt} /home/jill`  (Copying from tmp folder to jill home directory)
   - This will copy files of jack to jill user
   - Now run the following command
   - `cp -r /home/jill/{jill1,jill2,jill.txt} /tmp` (Copying jill's data to tmp folder)
   - Now log out and login as jack
   - Open terminal and run following command
   - `cp -r /tmp/{jill1,jill2,jill.txt} /home/jack` (Copying from tmp folder to jack home directory)
   - This will copy files of jill to jack user
