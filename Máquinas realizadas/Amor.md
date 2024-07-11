----
## Recognition

First, we apply the usual command to discover all open ports on the host.

![[Pasted image 20240710171535.png]]

With that information we can perform a specific scan to discover the version and the scripts that [[nmap]] can give to resolve the machine on the ports that we found on the previous step.

![[Pasted image 20240710171733.png]]

We don't see anything unusual so we proceed to check the web browser and the service that is running in the port 80.

In the web page we see two possible users for the ssh session (juan, carlota). Also, we can see that the user that Juan shared the password is weak.

![[Pasted image 20240710172035.png]]

Before, we performed a brute force we need to investigate all the information on the webpage so we proceed to use [[gobuster]] to find all posible directories that we can have access.

![[Pasted image 20240710172418.png]]

---
## Brute force

We can't see anything to take our interest here so we move to try ssh authentication with the users that we have through ssh connection with [[hydra]].

![[Pasted image 20240710172814.png]]

We discover the credenctial for the user carlota so we can log in with ssh.

---
## Privilege Escalation

We ran the command `sudo -l` and see that carlota is not capable to run commands as sudo so we cannot do anything on there. We need to find anything interesting on there that may be suspicious.

In this case, we discover a image.jpg on the desktop folder of Carlos. We open a server with python a download the image. 

![[Pasted image 20240710174327.png]]

With the image on our system we can perform OSINT test with [[steghide]] and we do the following:

![[Pasted image 20240710174659.png]]

When I opened the secret text I noticed that that string is enconded so I use cyberchef to decrypt the information.

![[Pasted image 20240710174815.png]]

Now, I discover that there is another user on the system and is Oscar. So, I test the string that we have as a password for Oscar and we have his user 🍎. Now we have to get root so first I permorfed `sudo -l` so we can check if we can run any command as a sudo.

![[Pasted image 20240710175121.png]]

We have the command ruby so we go to gtfobins to find if there is a command to get root privileges and get the following: 

`sudo ruby -e 'exec "/bin/sh"'`

We execute the command and here we go! We are root 💠 

![[Pasted image 20240710175254.png]]