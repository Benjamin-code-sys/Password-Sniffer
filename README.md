# Password-Sniffer

• &nbsp;&nbsp;In this project I'll demo and provide sanitized codes on how to build a trojan that will use `DLL Injection` with `API hooking` to steal disk encryption password & will remain persistent acroos reboots 

## Objective
• &nbsp;&nbsp;To write a trojan that starts at boot time and monitors our enumerated software, a disk encryption software `veracrypt` for this example  
•&nbsp;&nbsp; When the user enters a password to mount a drive, the trjan will steal the password and save it to a file  
• &nbsp;&nbsp;This trojan is something like a keylogger, except that this one monitors a specific program  

## How It Works
• &nbsp;&nbsp;We need to first generate a DLL_Injector trojan that has an embeded Password Sniffer DLL shellcode that i developed and will explain shortly   
• &nbsp;&nbsp;This Trojan once executed will be constantly running and constantly mnitoring wherether or not Veracrypt has loaded  
• &nbsp;&nbsp;Upon detection of Veracrypt in memmory, it'll unpack the DLL that is embeded within  
• &nbsp;&nbsp;It'll then inject this DLL into the Veracrypt program  
• &nbsp;&nbsp;Once attached to veracrypt it'll hook one of the APIs in veracrypt that is responsible for recieving the password input from the user   
• &nbsp;&nbsp;It'll then retrive the provided password and write it to a file that we will specify

<img src="https://imgur.com/baswIN1.png" height="70%" width="75%" alt="Password Sniffer Steps"/>

## Walkthrough

First we need to find the api responsible for passwords for this we'll use `API Monitor`

<img src="https://imgur.com/pJuvmMa.png" height="70%" width="75%" alt="Password Sniffer Steps"/>

We'll be hooking the `WideCharToMultiByte` api since its the one containing the password as a parameter

Before writing our trojan we'll need to undergo the above process for testing on our home lab 






















