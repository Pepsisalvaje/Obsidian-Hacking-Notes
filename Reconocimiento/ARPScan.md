Arpscan es una herramienta de línea de comandos utilizada para escanear y mostrar la información sobre dispositivos conectados a una red local. El término "ARP" significa Protocolo de Resolución de Direcciones, que es un protocolo utilizado para mapear direcciones IP a direcciones físicas ([[MAC]]) en una red.

La herramienta arpscan envía solicitudes ARP a la red local y recibe respuestas de dispositivos que están activos y accesibles en la red. Esto permite a los administradores de red identificar qué dispositivos están conectados y obtener información como direcciones [[IP]], direcciones [[MAC]] y nombres de host.

Se utiliza de la siguiente forma el comando: ```arp-scan -I ens33 --localnet```
- -I: Hace referencia a la interfaz de red que desees utilizas dentro del escaneo
- --localnet: Hace referencia a que quieres escanear la red local

