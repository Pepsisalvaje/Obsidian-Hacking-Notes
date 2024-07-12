
---
## Recognition

First we need to discover the IP of the asset and we can perform that with the following command:

```
sudo nmap -sn 172.16.136.0/24
```

We have the [[IP]] of the machine 👊.

![[Pasted image 20240712104709.png]]

Now, we can perform the port discovery recognition.

![[Pasted image 20240712104819.png]]

We discover the 80 port that is running a web server and the port 22 for a [[ssh]] connection. At this time, is important for us know the specific service that is running and also if [[nmap]] has some extra information to use.

![[Pasted image 20240712111607.png]]

Nothing interesting on the output.

Now we check the service that is running on the port 80.

The web has a login form, I have tried with the most common credentials and sql injections and it didn't work so we register as a normal user to see what's in the web page.

![[Pasted image 20240712111936.png]]

---

## Explotation

We have few option on the web page but I checked the source on the web page and notice something on the change password form.

![[Pasted image 20240712112513.png]]

Every time you change the password of your user there is and input that is hidden. So the case here is if we can intercept the traffic when we performed a change of password we could change the id of the request and change the password of the id 1 (assuming the admin 1 is admin). We performed that with [[burpsuite]]. 

- First, we intercept the traffic with [[burpsuite]] and I got the following
	![[Pasted image 20240712112859.png]]
- Now, we can see that we can change the id here so I sent the request to the repeater and modify the id value with 1.
	![[Pasted image 20240712113136.png]]
- That's it! 🤪 I changed the password of user 1 and assuming that the username is admin we try to login with the credentials.
	![[Pasted image 20240712113327.png]]

Before that, as a admin user of the server we can check that there is a new field that is called **"UPLOAD"**. First we need to check if it can accept all type of files (I have already have a PHP web shell to upload). 

![[Pasted image 20240712115849.png]]

We can see that is block any filetypes  with the file extension ".php", but I've tried with other extension (in my case .phtml) and it worked.

Now we need to see where does this web server uploads all the files that we uploaded previously. To discover that information I ran a [[gobuster]].

![[Pasted image 20240712120148.png]]

As we can see there is a directory that is call **"/upload"**, so we enter to the directory and there are all the files that we uploaded on the admin platform.

![[Pasted image 20240712120303.png]]

The web shell that I uploaded is call shell.phtml and when we enter we have a shell.

Now on the shell we can run a reverse shell to get a shell on our command line so we performed that task.

![[Pasted image 20240712120802.png]]

And we have a shell!!

![[Pasted image 20240712120842.png]]

So now let's make it and [[interactive shell]].

---

## Privilege Escalation

We are working with a privilege escalation on Linux and we can see that we don't have permited to use sudo so we need to see something on the asset to see what can we use to have better privileges.

On the directory of user john we can see that there our first flag and also there are some extra information.

![[Pasted image 20240712121720.png]]

There's a SUID binary and when we execute it we have the command "id" performed by the user john.

![[Pasted image 20240712121850.png]]

Here is the problem, how we can get a shell with this file? With that I have the next hypothesis if we can change the command id to execute a bash we can have and as the command is being exucuted as the user jhon we can have his shell so I tried the following

```
echo 'bash' > /tmp/id; chmod +x /tmp/id; export PATH=/tmp:$PATH
```

![[Pasted image 20240712122654.png]]

We can see that all is configured and with that we only need to run the command **toto** to see if it works.

![[Pasted image 20240712122929.png]]

It works and we have the password of the user on a txt file!! 😄. Now as Jhon we need to get root privileges so we performed the first command on a linux privilege escalation procedure `sudo -l`.

We see that the python file /home/john/file.py is running as root so we need to edit that file with a command that can give us a shell as root. On GTFOBINS, we have the command python3 to get a root shell we just need to adapt it to the context.

The command ends as follows:

![[Pasted image 20240712123500.png]]

Now we just need to run the command as sudo.

![[Pasted image 20240712123630.png]]

We are ROOT! 💣🍾

