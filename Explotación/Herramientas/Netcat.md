Netcat, también conocido como "nc", es una herramienta de red de utilidad que permite la lectura y escritura de datos a través de conexiones de red utilizando el protocolo [[TCP]]/[[IP]]. Es una herramienta extremadamente versátil y se utiliza comúnmente para realizar tareas como:

1. Establecer conexiones TCP o UDP.
2. Escuchar en puertos específicos para aceptar conexiones entrantes.
3. Transmitir datos a través de la red.
4. Escanear puertos en un host remoto.
5. Crear túneles de red.

Netcat es popular debido a su simplicidad y su capacidad para manejar una amplia variedad de tareas relacionadas con la red. Es una herramienta de línea de comandos y está disponible en la mayoría de los sistemas operativos tipo Unix/Linux, así como en sistemas Windows. Debido a su flexibilidad y capacidades, Netcat a veces se conoce como la "navaja suiza de la red".

Modo de uso: ```nc -nlvp 443```
- -v: verbose
- -l:  ponerse en modo escucha
- -n: modo [[IP]] (no DNS)
- -p: sirve para especificar un puerto en específico