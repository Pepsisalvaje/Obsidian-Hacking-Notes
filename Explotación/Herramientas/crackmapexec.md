CrackMapExec, también conocido como CME, es una herramienta de código abierto diseñada para la post-explotación. Su principal característica es que permite hacer movimientos laterales dentro de una red local. CrackMapExec utiliza la biblioteca Impacket para trabajar con protocolos de red y realizar una variedad de técnicas de post-explotación. Además, CrackMapExec puede enumerar usuarios conectados, explorar comparticiones SMB, ejecutar ataques al estilo psexec, inyectar automáticamente Mimikatz/Shellcode/DLL’s en memoria usando Powershell, volcar el NTDS.dit y más

Si queremos utilizar una null session en [[SMB]] utilizamos el siguiente comando: ```crackmapexec smb -u ''-p '' --shares```

Si queremos realizar fuerza bruta al usuario o contraseña es necesario realizar la siguiente acción (si estás probando los usuarios probar tanto en la contraseña con los mismos usuarios): ```crackmapexec smb -u usuarios.txt -p usuarios.txt --shares```
