This link explains some functions:[RTKExplain](https://www.cnblogs.com/pylblog/p/10065037.html)
## Models 
### Time System
RTKLIB uses GPS Time for GNSS data handling to avoid leap seconds in UTC. GPST is expressed as GPS week number and time of week (TOW) since the start epoch of 00:00:00 UTC on January 6, 1980. 
#### GPST and UTC
The conversion of GPST to UTC is to subtract the leap seconds ($\Delta t_{LS}$)

$$ t_{UTC} = t_{GPS} - \Delta t_{LS} $$

the $t_{LS}$ can be found by the table.
### GLONASST
GLONASST is based on UTC and includes leap second insertion, and is also aligned to the local time.

$$t_{UTC}=t_{GLONASST}-10800$$

### GST (Galileo System Time)
GST start epoch is 00:00:00 UTC on August 22, 1999. At the start epoch, GST shall be ahead of UTC by 13 seconds. The GST is aligned to GPST except for the 1024 weeks difference of the time system origin and a small time offset (GGTO).
### QZSST
QZSST is aligned to GPST. It can be handled as the same as GPST.
### BDT
BDT is a continuous time system without leap second insertion. The start epoch of BDT is 00:00:00 UTC on January 1, 2006. 

$$ t_{BDT} = t_{GPST} - 14 $$
 
## C language notes
### Why use pointer to pointer or double pointer
If you want to have a list of characters (a word), you can use
```
char *word
```
If you want a list of words (a sentence), you can use
```
char **sentence
```
If you want a list of sentences (a monologue), you can use
```
char ***monologue
```
### Define a global variable
First define it in one source file with:
```
const int itest = 123;
```
Then to declare it in any source files that use it with:
```
extern const int itest; 
```
A general practice is to put the above declaration in a header file and include that header in any file that uses the variable, including the one that defines it.
## How to use vim
### Personalize and plugins
creat .vimrc file and input
```
set nu" display row number
set tabstop=4 "Set width of tab
set shifwidth=4
set syntax=on
```
Use plug.vim to update vim plugins
```
sudo apt install curl
curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```
Then open a file using vim and input the command
```
:PlugInstall
```
### Use GDB to debug the c/c++ program
Need to add "-g" to start the debug
```
gcc -g -o hello hello.c
```
Then you can run 
```
gdb hello
```
to start debuging

Some basic commands:
```
info breakpoints
b 9 # set breakpoint at line 9
b printNum # set breakpoint at printNum function
break test.c:23 if b==0 # program stop at line 23 if b equals 0
ignore 1 30 # run the program and ignore the breakpoint 1 for 30 times
disable # disable all breakpoints
disable 1 # disable breakpoint 1
enable # enable all breakpoints
enable 1 # enable breakpoint 1
continue # continue the program
clear # clear all breakpoints at this line
clear printNum # clear breakpoint at printNum function
delete # delete all breakpoints, watchpoints, and catachpoints
delete 1 # delete breakpoint 1
p a # print variable a
p 'testGdb.h'::a # print the variable a in testGdb.h
display e # dipaly variable e everytime the program stop
n # run the program by one step
s # run the program by one step and will enter the function
l # list the source program
until lineNum # run the program and stop at lineNum
```
### Modify the code in gdb
Set the editor beforehand
```
EDITOR=/usr/bin/vim
export EDITOR
```
Then you can edit the code
```
edit 3 # edit line 3
```
### Debug with files input to main function
One way is run with parameters
```
gdb hello
run files
```
or use
```
gdb \-\-args myprog input.txt
```
### When debug and says "optimized out"
It is because the Release version optimize the code to make it run faster and smaller, while we need to use Debug version to see the information. So we need to modify the makefile
```
./configure CFLAGS='-g -O0'
```
