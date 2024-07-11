HTTPS (Hypertext Transfer Protocol Secure) es la versión segura del protocolo [[HTTP]]. Utiliza el protocolo SSL/TLS para cifrar los datos transmitidos entre el cliente (como un navegador web) y el servidor web, proporcionando así una capa adicional de seguridad durante la comunicación en línea.

Aquí hay algunas características clave de HTTPS:

1. ***Cifrado de datos***: HTTPS cifra los datos transmitidos entre el cliente y el servidor, lo que protege la confidencialidad de la información, como contraseñas, datos de tarjetas de crédito y otros datos sensibles.
2. ***Autenticación del servidor***: HTTPS utiliza certificados digitales para autenticar la identidad del servidor web. Esto ayuda a garantizar que el cliente esté comunicándose con el servidor correcto y no con un servidor falso o malicioso.
3. ***Integridad de los datos***: HTTPS también proporciona integridad de datos, lo que significa que garantiza que los datos transmitidos entre el cliente y el servidor no han sido alterados durante la transferencia.
4. ***Indicadores visuales de seguridad***: Los navegadores web suelen mostrar indicadores visuales, como un candado o un icono de color verde, para indicar que la conexión está protegida mediante HTTPS. Esto ayuda a los usuarios a identificar de forma visual si están navegando en un sitio web seguro.
5. ***Requisito para algunas características modernas***: Algunas características modernas de la web, como las notificaciones push y la geolocalización, solo están disponibles para sitios web que utilizan HTTPS. Además, los motores de búsqueda pueden favorecer los sitios HTTPS en sus resultados de búsqueda.

La capa de aplicación es la séptima capa del [[modelo OSI]] y es responsable de proporcionar servicios de red a las aplicaciones de usuario final. Esta capa se encarga de la comunicación entre las aplicaciones de usuario y los servicios de red subyacentes.

Procedimiento de enumeración:
- Vulnerable a heartbleed: ```nmap --script ssl-heartbleed -p443 127.0.0.1```
- Certificado vulnerable:  ```openssl s_client -connect tinder.com:443```
- Detección de protocolos vulnerables: ```sslscan tinder.com```