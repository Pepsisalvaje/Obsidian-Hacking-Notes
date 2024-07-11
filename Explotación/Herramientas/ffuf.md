Como mínimo, se nos piden dos opciones: -u para especificar una URL y -w para especificar una lista de palabras. La palabra clave por defecto FUZZ se utiliza para indicar a ffuf dónde se inyectarán las entradas de la lista de palabras. Podemos añadirla al final de la URL de la siguiente manera:

### Comandos básicos

```
ffuf -u http://10.10.68.239/FUZZ -w /usr/share/seclists/Discovery/Web-Content/big.txt

ffuf -u https://172.17.0.2/FUZZ -w /usr/share/KaliLists/dirbuster/directory-list-2.3-medium.txt -e .php,.html,.java,.txt,.css,.js,.php -t 100
```

Para poder saber con que tecnología se ha desarrollado la web lo mejor es realizar el siguiente descubrimiento:

`ffuf -u http://10.10.68.239/indexFUZZ -w /usr/share/seclists/Discovery/Web-Content/web-extensions.txt`

Si queremos esconder todos los errores para que no nos brinde falsos positivos tenemos que aplicar el siguiente comando:

```ffuf -u http://10.10.68.239/FUZZ -w /usr/share/seclists/Discovery/Web-Content/raft-medium-files-lowercase.txt -fc 403```

Si solo deseas ver los resultados con un específico estado es necesario aplicar el siguiente comando:

```ffuf -u http://10.10.68.239/FUZZ -w /usr/share/seclists/Discovery/Web-Content/raft-medium-files-lowercase.txt -mc 200```

### Fuzzing

Si quieres fuzzear parámetros este es un ejemplo de como se puede realizar

```ffuf -u 'http://10.10.241.152/sqli-labs/Less-1/?FUZZ=1' -c -w /usr/share/wordlists/SecLists-master/Discovery/Web-Content/burp-parameter-names.txt -fw 39```

```ffuf -u 'http://10.10.241.152/sqli-labs/Less-1/?FUZZ=1' -c -w /usr/share/wordlists/SecLists-master/Discovery/Web-Content/raft-medium-words-lowercase.txt -fw 39```

Si se requiere fuzzear un subdominio se puede realizar lo siguiente:

```ffuf -u http://FUZZ.mydomain.com -c -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt```


### Login Form Brute Force

Para esto se sigue la misma metodología que [[hydra]]; sin embargo, cambian en algunos aspectos:

```
ffuf -u http://172.17.0.2:8080/j_spring_security_check -H "Content-Type: application/x-www-form-urlencoded" -d "j_username=admin&j_password=FUZZ&from=&Submit=" -w /usr/share/KaliLists/rockyou.txt -t 50 -r -c -fl 9
```

- Para poner la path específica en la que se autentica es necesario que puedan ir específicamente al servicio que se muestra en el inspeccionar de la web
- El content type lo encuentran en el inspeccionar de la web
- El nombre y contraseña también se encuentra en el inspeccionar de la web
- Utilizar el -r, -c y -fl ya que son temas de formato
- Es importante utilizar la palabra FUZZ en lo que queremos realizar fuerza bruta