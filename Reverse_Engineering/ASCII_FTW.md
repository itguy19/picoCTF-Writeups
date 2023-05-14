# ASCII FTW
## Description: 
### This program has constructed the flag using hex ascii values. Identify the flag text by disassembling the program.

After downloading the given file,

![image](https://github.com/itguy19/picoCTF-Writeups/assets/125930481/284a6769-947c-4489-b726-e09fb61b4551)

we see that this file is a Linux executable ELF file.

![image](https://github.com/itguy19/picoCTF-Writeups/assets/125930481/b1b3a6ae-dd5c-47c3-9bd6-a332d130d5e4)

After gaining execute rights with the command:

`chmod 700 asciiftw`

we can finally run the program.

![image](https://github.com/itguy19/picoCTF-Writeups/assets/125930481/c4294604-2d5f-4467-abf1-bf3b9d33c4c1)

The output 70 looks oddly similar to a hex value. With a single command, we can find out if our assumption is correct. If we decode this hex value to ascii, we should get a "p", because that has to be the first letter of our flag.

![image](https://github.com/itguy19/picoCTF-Writeups/assets/125930481/982eab71-1428-47da-8e3e-b7ec99f2c404)

Our assumption was correct. Now, we have to analyze this executable. We can put great reverse engineering tool called ghidra to good use. After starting ghidra, we have to create a new project and select our ElF file. After successfully creating a project, we have to analyze the executable.

![image](https://github.com/itguy19/picoCTF-Writeups/assets/125930481/1ee405b6-5b27-4802-913e-8e9cfdeb08dc)


