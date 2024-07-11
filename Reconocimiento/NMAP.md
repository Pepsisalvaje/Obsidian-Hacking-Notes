Nmap, abreviatura de "Network Mapper", es una poderosa herramienta de escaneo de red de código abierto para descubrir y mapear dispositivos conectados a una red, así como para evaluar la seguridad de las redes y sistemas informáticos.

Nmap es una herramienta versátil y ampliamente utilizada en la comunidad de seguridad informática y redes debido a su capacidad para proporcionar información detallada sobre los dispositivos y servicios en una red, lo que la convierte en una herramienta valiosa tanto para la administración de redes como para la evaluación de seguridad.

Los comandos más utilizados para agregar en la evaluación de una [[IP]] son los siguientes:
- -p: Especifica los puertos a escanear ``` nmap -p22,23,24 192.168.12.15```
- -p-: Realiza un escaneo de todos los puerto ``` nmap -p- 192.168.12.15```
- --open: Realiza un escaneo para notificar únicamente los puertos abiertos ``` nmap --open 192.168.12.15```
- -v: Permite conocer el avance del escaneo ``` nmap -v 192.168.12.15```
- -T0-5: Controla el rendimiento del escaneo ``` nmap -T4 192.168.12.15```
- -sT: Realiza un escaneo por medio de [[TCP]] ``` nmap -sT 192.168.12.15```
- -Pn: No realiza descubrimiento de host ``` nmap -Pn 192.168.12.15```
- -sU: Realiza un escaneo por medio de [[UDP]] ``` nmap -su 192.168.12.15```
- -sn: Escanea todos los activos de una red ``` nmap -sn 192.168.12.15/24```
- -O: Realiza un descubrimiento de Sistema Operativo ``` nmap -O 192.168.12.15```
- -sV: Detecta las versiones del [[puerto]] abiertos ``` nmap -sV 192.168.12.15```
- -sC: Detecta scripts que se puedan usar ``` nmap -sC 192.168.12.15```
- -f: Fragment a los paquetas ``` nmap -f 192.168.12.15```
- -D: Envía paquetes con distintas [[IP]] ``` nmap -D 192.168.12.15```
- --source-port: Eliges un puerto con el que conectarte ``` nmap --source-port 22 192.168.12.15```
- -sS: Permite no completar una conexión ``` nmap -sS 192.168.12.15```
- --min-rate: Controla la cantidad de paquetes ``` nmap --min-rate 400 192.168.12.15```
- --script: Utiliza un script en específico: ``` nmap --script ssl-heartbleed 192.168.12.15```
- -sn: Realiza un reconocimiento de red: ``` nmap -sn 192.168.12.0/24```


### Metodología para escanear segmentos
- Para escanear y descubrir todo un segmento de red aplicar el siguiente comando:  ```nmap -sn 10.10.0.10/24```
- Para escanear las [[ip]]s y descubrir los puertos abiertos aplicar el siguiente comando: ```nmap -sS --min-rate 5000 -p- --open 10.10.0.10,12,15,17,18 -oN output```
- Para sacar los puertos del output aplicar el siguiente comando: ```grep '^[0-9]' output | cut -d '/' -f1 | sort -u | xargs | tr ' ' ','```
- Una vez con los puertos aplicar el siguiente comando: ```nmap -p20,21,22,26,80,443,8080,3398 -sCV -Pn --open   10.10.0.10,12,15,17,18 -oN fullScan```