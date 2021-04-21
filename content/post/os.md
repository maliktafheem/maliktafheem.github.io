---
author : Malik Tafheem Ul Islam
title: "64 bit OS"
date : 2021-04-20
draft: false
---

## BUILDING A 64 bit OS
We used 2 youtube videos as references.
* https://www.youtube.com/watch?v=FkrpUaGThTQ
* https://www.youtube.com/watch?v=wz9CZBeXR6U

After carefully watching and follwing the procedure, I built a simple operating system that prints 
the logo of NUST using characters (alphabetic, *,  and / etc on the screen as was given in the image attached).  
This is the github repo to my OS https://github.com/maliktafheem/Operating-System  
 
  
#### Some of the important points are explained below.  
* Softwares we used:
    1. Docker: Used for containers to create our build-environment.
    2. QEMU: Emulator and Virtualizer that performs hardware virtualization.
    3. VSCode: For coding and programming purpose.  
* We used NASM to complile our assembly code and C to print our logo.
* To build our final ISO file we used GRUB.
* We first build a 32 bit OS later we'll switch it to 64 bit mode.
* Added magic data into an assembly file so that bootloaders can understand we have an OS that can be run on our computer.
* We followed multiboot 2 specifications which most bootloaders support.
* We created another assembly file (main.asm) that will be the entry point into our OS.
* For the first part we just printed 'OK'(0x2f4b2f4f).
* In order to print some characters on the screen we directly wrote to the video memory (0xb8000- begining address). The CPU hooks the text in this memory upto our screen.
* We created a linker file which will describe how to link our OS together.
* We created a grub config file which in turn will create an ISO file out of our OS. We can use the ISO file to run our OS anywhere.
* We then wrote commands for building our OS and included all that in a makefile.
* Finally we ran the OS and printed 'OK' as shown below.  
  

{{< figure src="/images/os3.png">}} 
  
   
* In the second part we printed NUST logo in 64 bit OS.
* First we set up a stack that will allow us to link in with 'C' code.
* We first check that we've been loaded by a multiboot2 bootloader else we'll display an error message.
* After setting up our stack, our main.asm file is complte
* Then we create another assembly file for the 64 bit purposes. We copy the 'OK' from 32 bit asm file to 64 bit asm file to test whether we've setup things correctly. If 'OK' prints after movig it to the 64 bit asm file then we've did everything right.
* Then we set up 'C' code which we use to print our logo made of characters and call it in the 64 bit asm file.
* Finally we made some slight changes to our makefile for compiling our 'C' code. Then we rebuild our OS and see if it's working fine.


{{< figure src="/images/os2.png">}} 