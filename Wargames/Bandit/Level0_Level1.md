# Bandit Level 0 --> Level 1  
## Level Goal

The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game. 

## Commands you may need to solve this level
ls, cd, cat, file, du, find

## Solution
ls command show that there is file in home directory "readme"
```
bandit0@bandit:~$ ls
readme
```
Lets see it
```
bandit0@bandit:~$ cat readme
boJ9jbbUNNfktd78OOpsqOltutMc3MY1
```

## Password
> boJ9jbbUNNfktd78OOpsqOltutMc3MY1

