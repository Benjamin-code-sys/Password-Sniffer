# Password-Sniffer

• &nbsp;&nbsp;In this project I'll demo and provide sanitized codes on how to build a trojan that will use `DLL Injection` with `API hooking` to steal disk encryption password & will remain persistent acroos reboots 

## Objective
• &nbsp;&nbsp;To write a trojan that starts at boot time and monitors our enumerated software, a disk encryption software `veracrypt` for this example  
•&nbsp;&nbsp; When the user enters a password to mount a drive, the trjan will steal the password and save it to a file  
• &nbsp;&nbsp;This trojan is something like a keylogger, except that this one monitors a specific program  

## How It Works
1. &nbsp;&nbsp;We need to first generate a DLL_Injector trojan that has an embeded Password Sniffer DLL shellcode that i developed and will explain shortly   
2. &nbsp;&nbsp;This Trojan once executed will be constantly running and constantly mnitoring wherether or not Veracrypt has loaded  
3. &nbsp;&nbsp;Upon detection of Veracrypt in memmory, it'll unpack the DLL that is embeded within  
4. &nbsp;&nbsp;It'll then inject this DLL into the Veracrypt program  
5. &nbsp;&nbsp;Once attached to veracrypt it'll hook one of the APIs in veracrypt that is responsible for recieving the password input from the user   
6. &nbsp;&nbsp;It'll then retrive the provided password and write it to a file that we will specify

<img src="https://imgur.com/baswIN1.png" height="70%" width="75%" alt="Password Sniffer Steps"/>
