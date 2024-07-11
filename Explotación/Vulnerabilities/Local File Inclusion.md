La inclusión de archivos locales (Local File Inclusion, LFI) es una vulnerabilidad de seguridad web que permite a un atacante incluir archivos de un servidor a través del navegador. Esta vulnerabilidad ocurre debido a una validación inadecuada de las entradas del usuario en la aplicación web.

Los ataques LFI suelen ocurrir cuando la aplicación permite al usuario especificar qué archivo debe cargarse sin una validación adecuada de la ruta del archivo. Un atacante puede explotar esta vulnerabilidad para incluir archivos sensibles del sistema (como `/etc/passwd` en sistemas Unix) o archivos de la aplicación, lo que puede llevar a la divulgación de información sensible o la ejecución de código malicioso.

Ejemplo de LFI:

1. Se presenta el siguiente error en la web: 
![[Pasted image 20240710140710.png]]
1. Por la sintaxis es un PHP que utiliza la variable archivo para cargar la imagen.
2. Utilizaremos una sintaxis básica para comprobar que esta vulnerabilidad exista la cual es la siguiente ```?archivo=../../../../etc/passwd``` (ponemos archivo porque es lo que queremos cambiar).
3. Una vez probada contra la web nos podemos dar cuenta que si es vulnerable.
![[Pasted image 20240710141045.png]]
