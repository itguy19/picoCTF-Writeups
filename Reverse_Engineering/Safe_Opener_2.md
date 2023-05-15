# Safe Opener 2
## Description: 
### What can you do with this file? I forgot the key to my safe but this file is supposed to help me with retrieving the lost key. Can you help me unlock my safe?

First of all, let's download the file.

![image](https://github.com/itguy19/picoCTF-Writeups/assets/125930481/613f9393-3f93-4b1c-acf5-8360991b2176)

We have downloaded an already compiled Java class file.
The easiest way to find the flag is just by using the strings command:

![image](https://github.com/itguy19/picoCTF-Writeups/assets/125930481/b97f36a7-d253-4c28-b6c4-736781765a76)

![image](https://github.com/itguy19/picoCTF-Writeups/assets/125930481/d8d08bd5-7d7e-4899-ac6c-8f34d13a1980)

Flag: `picoCTF{SAf3_0p3n3rr_y0u_solv3d_it_b427942b}`

But because we are cool and I am pretty sure that this isn't the intended way to find the flag, let's try another route, just for fun!

First we open the given *.class file in ghidra and analyize it. 
When we look at the Symbol Tree,

![image](https://github.com/itguy19/picoCTF-Writeups/assets/125930481/1eb237c9-cfcb-408e-b0ab-166049c5f8d5)

we see two function names: "main" und "openSafe". Let's select the openSafe function.

![image](https://github.com/itguy19/picoCTF-Writeups/assets/125930481/905c1bcd-a53a-46a1-8f74-d551b61197d0)

There is our flag! Got it.

Flag: `picoCTF{SAf3_0p3n3rr_y0u_solv3d_it_b427942b}`
