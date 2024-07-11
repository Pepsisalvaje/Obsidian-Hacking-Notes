Primero es necesario que se pueda conocer que puertos tienen abiertos con [[nmap]]:
```sudo nmap -p- --open -Ss -Pn --min-rate 5000 IP -oN allPorts```
Luego a los puertos abiertos realizarle un escaneo específico:
```sudo nmap -p22,80,224,945 -sCV IP -oN targeted```

Una vez con los puertos va a depender de que servicio esté abierto de pruebas tengas que realizar para explotar alguna vulnerabilidad.
- Si tiene un servicio web utilizar [[gobuster]]
- Si tiene vulnerabilidades se puede obtener información con [[nikto]]
- Si se tiene alguna credencial utilizar de algún servicio se puede usar fuerza bruta con [[hydra]]
- Revisa el código de la web
- Añadir el hostname (en caso se requiera) al /etc/hosts
- Revisar la versión de la web.
- En caso sea un Wordpress utilizar [[wpscan]] para buscar vulnerabilidades.

