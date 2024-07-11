

Buscará todos los directorios de un sitio web
```gobuster dir -e -w WORDLIST -u http://url```

Si no se encuentra nada se puede probar con lo siguiente: 

Encontrará todos los directorios con extensión html, xml y php: 

```gobuster dir -u http://trust -w /usr/share/dirbuster/wordlists/directory-list-2.3-medium.txt -x html,xml,php```

