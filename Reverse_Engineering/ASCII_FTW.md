# ASCII FTW
## Description: 
### This program has constructed the flag using hex ascii values. Identify the flag text by disassembling the program.

After downloading the given file,

![image](https://github.com/itguy19/picoCTF-Writeups/assets/125930481/284a6769-947c-4489-b726-e09fb61b4551)

we see that this is a Linux executable ELF file.

![image](https://github.com/itguy19/picoCTF-Writeups/assets/125930481/b1b3a6ae-dd5c-47c3-9bd6-a332d130d5e4)

After gaining execute rights with the command:

`chmod 700 asciiftw`

we can finally run the program.

![image](https://github.com/itguy19/picoCTF-Writeups/assets/125930481/c4294604-2d5f-4467-abf1-bf3b9d33c4c1)

The output 70 looks oddly similar to a hex value. With a single command, we can find out if our assumption is correct. If we decode this hex value to ascii, we should get a "p", because that has to be the first letter of our flag.

![image](https://github.com/itguy19/picoCTF-Writeups/assets/125930481/982eab71-1428-47da-8e3e-b7ec99f2c404)

Our assumption was correct. Now, we have to analyze this executable. We can put great reverse engineering tool called ghidra to good use. After starting ghidra, we have to create a new project and select our ElF file.

![image](https://github.com/itguy19/picoCTF-Writeups/assets/125930481/e77a2759-c2a5-44fc-9182-3ae23a59085b)

After successfully creating a project, we have to analyze the executable.

![image](https://github.com/itguy19/picoCTF-Writeups/assets/125930481/1ee405b6-5b27-4802-913e-8e9cfdeb08dc)

At the first glance, the application can be very overwhelming. Watch a couple of tutorials, play around with it. You will have to use this program for future challenges.

![image](https://github.com/itguy19/picoCTF-Writeups/assets/125930481/b7cd64ac-0922-4cc0-b68e-1b12ff182ae2)

But what is important for us right now, is the Symbol Tree. Click on the main function.

![image](https://github.com/itguy19/picoCTF-Writeups/assets/125930481/72be28e4-8cc7-4a3c-982d-355fc83cfb92)

This will display the decompiled version of the function.

![image](https://github.com/itguy19/picoCTF-Writeups/assets/125930481/2ab87729-c4e0-461f-8b76-af96ad21f04b)

We can immediatly see, that this is the program that we ran. The same output appears here that we had: "printf("The flag starts with %x\n",0x70)".

![image](https://github.com/itguy19/picoCTF-Writeups/assets/125930481/7c9d2fbd-baed-4ed6-988f-f89f7baa5d0b)

When we click on one of the hex values, we will be brought to the place, where these values are stored in Assembly:

![image](https://github.com/itguy19/picoCTF-Writeups/assets/125930481/7a38b2db-e035-44d7-a2c6-07ff243ac6f6)

Got it! We have found the place, where our flag is stored. Let's just copy the whole segment where the flag is

![image](https://github.com/itguy19/picoCTF-Writeups/assets/125930481/2ecfd320-da63-46c2-b87c-225de42bcd1e)

and save it into a file, named "data.txt".

The only step left is to extract the flag from the file.

![image](https://github.com/itguy19/picoCTF-Writeups/assets/125930481/8cd7cec2-ab88-4b98-b4b1-11ae7b31b237)

Flag: `picoCTF{ASCII_IS_EASY_8960F0AF}`

