 # DLL-Injector

At the beginning of the code right after the include statement we add our password sniffer DLL in shellcode format as a global variable as shown below

<img src="https://imgur.com/O0j16lW.png" height="70%" width="75%" alt="Password Sniffer Steps"/>

Then we declare our custom SearchForProcess functions which we'll search for the process we specify as a parameter in main  
<img src="https://imgur.com/qhKBbQD.png" height="70%" width="75%" alt="Password Sniffer Steps"/>

Next we'll again declare a global variable of an empty string as pathToDLL & declare a custom function shown below that'll get the DLL path  
<img src="https://imgur.com/Pm1bpOI.png" height="70%" width="75%" alt="Password Sniffer Steps"/>

Before writing our Main function we'll finally declare the last custom function tha we'll unpack the DLL that is embeded in this trojan  
<img src="https://imgur.com/jhPml5Z.png" height="70%" width="75%" alt="Password Sniffer Steps"/>

In our main function we'll first call the `SearchForProcess` function and provide the string veracrypt as the argument. For it to search for veracrypt in memmory  
<img src="https://imgur.com/bsXYtm1.png" height="70%" width="75%" alt="Password Sniffer Steps"/>

Upon finding it we'll call GetPathToDLL function to retrive its path followed by the function UnpackDLL to unpack the embeded DLL which we'll pass to `LoadLibrary` Win API to load it into veracrypts memmory   

We'll then call `OpenProcess` API to obtain a handle to the process  
<img src="https://imgur.com/dd2DzEC.png" height="70%" width="75%" alt="Password Sniffer Steps"/>

If we get a valid handle which is a non zero we'll proceed to allocate memmory to the remote appliation **“Veracrypt”** using `VirtualAllocEX`, then write the path to our DLL into it using `WriteProcessMemory` & finally execute it using `CreateRemoteThread`   
<img src="https://imgur.com/6CXtOpX.png" height="70%" width="75%" alt="Password Sniffer Steps"/>






















