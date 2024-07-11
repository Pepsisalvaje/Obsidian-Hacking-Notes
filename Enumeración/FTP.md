-----
El Protocolo de Transferencia de Archivos (FTP, por sus siglas en inglés, File Transfer Protocol) es un estándar de red utilizado para transferir archivos entre un cliente y un servidor en una red [[TCP]]/[[IP]], como Internet. FTP permite a los usuarios cargar (subir) y descargar (bajar) archivos desde y hacia un servidor remoto con facilidad.

FTP opera en una arquitectura cliente-servidor, donde el cliente FTP se conecta al servidor FTP para realizar operaciones de transferencia de archivos. Los usuarios pueden navegar por el sistema de archivos del servidor remoto, cargar archivos desde su computadora local al servidor remoto (cargar), descargar archivos del servidor remoto a su computadora local (descargar), eliminar archivos en el servidor remoto y realizar otras operaciones de administración de archivos.

Procedimiento de enumeración:
- Para conectarse al servicio ftp es mediante el siguiente comando: ```ftp 192.168.0.1```
- Para realizar fuerza bruta se puede utilizar hydra de la siguiente forma: ```hydra -l user1 -P pass.txt ftp://127.0.0.1```
- Cuando existe un usuario anónimo NMAP te puede notificar esta información mediante uno de sus scripts llamado ftp-anon.nse. El usuario que tienes que utilizar es el de ***anonymous***.