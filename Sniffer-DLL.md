# Sniffer DLL

Coding this DLL is fairly simple after the include statements we'll start by declaring a pointer to the original API responsible the password which is `WideCharToMultiByte` API  

We'll then Define our hooking function shown below using detours library  
<img src="https://imgur.com/lPB6hgD.png" height="75%" width="75%" alt="Early-Bird APC injection steps"/>

 Next we define our HookTarget and UnhookTarget functions respectivly as shown and supply our pointer to the WidecharToMultiByte API as shown below  
<img src="https://imgur.com/LkutGhH.png" height="75%" width="75%" alt="Early-Bird APC injection steps"/>

Finally for our DllMain function we'll include the HookTarget function to be triggered when this DLL is attached and UnHookTarget to be triggered when the DLL is detached  
<img src="https://imgur.com/S4eo5Vl.png" height="75%" width="75%" alt="Early-Bird APC injection steps"/>






















