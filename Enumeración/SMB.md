-----
SMB (Server Message Block) es un protocolo de red utilizado principalmente para compartir archivos, impresoras, puertos seriales y otros recursos entre nodos de una red, como computadoras, servidores y dispositivos de almacenamiento en red. SMB se ha convertido en el [[puerto]] estándar para compartir archivos en redes locales en entornos basados en Windows.

1. **Compartir archivos**: SMB permite a los usuarios compartir archivos y carpetas entre diferentes dispositivos en una red. Esto facilita la colaboración y el intercambio de recursos en entornos de trabajo compartido.
2. **Acceso remoto**: Con SMB, los usuarios pueden acceder a recursos compartidos en una red desde una ubicación remota, lo que permite el acceso a archivos y datos desde diferentes dispositivos y ubicaciones.
3. **Impresión compartida**: Además de compartir archivos, SMB también puede utilizarse para compartir impresoras en una red. Esto permite a varios usuarios imprimir documentos en una impresora compartida desde diferentes dispositivos en la red.
4. **Autenticación y control de acceso**: SMB proporciona mecanismos de autenticación y control de acceso para garantizar la seguridad de los recursos compartidos. Los administradores de red pueden configurar permisos de acceso para controlar quién puede acceder y modificar los recursos compartidos.
5. **Versiones**: A lo largo de los años, SMB ha evolucionado y ha tenido varias versiones. Algunas de las versiones más comunes incluyen SMB1, SMB2, SMB3, y SMB3.1.1. Las versiones más recientes suelen ofrecer mejoras en rendimiento, seguridad y funcionalidad.

Procedimiento de enumeración:
- Lista de directorios: ```smbmap -H 127.0.0.1```
- Lista directorios con una sesión nula: ```smbclient -L 127.0.0.1 -N```
- Ingresar a una carpeta: ```smbclient //127.0.0.1/carpeta1 -N```
- Copia una carpeta dentro nuestro sistema: ```mount -t cifs //127.0.0.1/carpeta/1 /carpeta/destino```
- Para buscar vulnerabilidades si es que se tiene abierto el SMB  es el siguiente con NMAP: ```nmap -p445 --script="smb-vuln-*" 127.0.0.1```
