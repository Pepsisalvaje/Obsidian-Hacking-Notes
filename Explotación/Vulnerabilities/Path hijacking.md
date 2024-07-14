
---
Path hijacking, in the context of computer networking and security, refers to a situation where an attacker maliciously redirects network traffic destined for a legitimate endpoint to flow through a different, unauthorized path. This unauthorized path may be controlled by the attacker or could be a route that allows the attacker to intercept, monitor, or manipulate the traffic. Path hijacking can occur at various layers of the networking stack, from routing protocols (like BGP hijacking) to application-layer redirections. The goal of path hijacking can vary from eavesdropping on communications to facilitating a man-in-the-middle attack to disrupt or manipulate communication between legitimate parties.


## Manipulation Linux Path Variable
---
In this case, we can change the path variable to add a directory so when the terminal ask for some binary, first search on the path that we add and it's gonna execute the command that's on there. 

Example:

Imagine that there's a python that in the code source when you execute the python file it execute as a system the command ls. If we add a file to the **/tmp** directory (it can be everywhere you want), make it executable and then add the directory at the beginning of the path, when you run the python file is gonna execute the command that you have on there.

To make that change you need to apply the next command on the terminal

```
echo '/bin/bash -p' > /tmp/ls; chmod +x /tmp/ls; export PATH=/tmp:$PATH
```

