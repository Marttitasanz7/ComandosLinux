# ComandosLinux
## **Bloque 0: Historial**

0. Amplía el tamaño máximo del historial de la shell y configura que cada línea del historial muestre también la fecha y la hora.

```bash
# (temporal, solo para la sesión actual)
HISTSIZE=10000
HISTFILESIZE=20000
HISTTIMEFORMAT="%F %T  "           

# Aplica cambios en la sesión actual
export HISTSIZE HISTFILESIZE HISTTIMEFORMAT
```

1. Comprueba que ahora, al mostrar el historial, aparece la fecha y hora junto a los comandos ejecutados.

```bash
history
```

2. Configura estos cambios para que sean permantentes
```bash
nano ~/.bashrc
 dentro incorporamos los comandos anteriores
      export HISTIZE=10000 
      export HISTFILESIZE 20000 
EXPORT HISTTIMEFORMAT="%F %T "

```

---

## **Bloque 1: Gestión del sistema y el kernel**

1. Muestra toda la información de tu sistema operativo y kernel.
```bash
uname -a              
```
    
2. Averigua únicamente la versión del kernel.
```bash
uname -r
```
    
3. Comprueba el espacio en disco disponible.
```bash
df -h
```
    
4. Calcula cuánto espacio ocupa la carpeta `/etc`.
```bash
sudo du -sh /etc
```
    
5. Consulta la memoria RAM disponible y usada.
```bash
free -h
```

---

## **Bloque 2: Procesos**

6. Lanza un monitor de procesos en tiempo real y observa:
```bash
top           # salir con q

```
    
- Número total de procesos.	
- Cuál consume más CPU.	
- Sal del programa.
        
7. Instala y ejecuta una versión mejorada del monitor de procesos y compárala con la anterior.
```bash
sudo apt update && sudo apt install -y htop
htop          # salir con F10 o q
```
    
8. Obtén un listado de todos los procesos del sistema y localiza el proceso de tu shell.
```bash
ps aux
echo $$                              
ps -p $$ -o pid,ppid,tty,cmd        
```
    
9. Muestra la jerarquía de procesos en forma de árbol.
```bash
pstree -p 


```
    
10. Lanza el comando `ping` contra `google.com` en segundo plano (&) y obtén su identificador de proceso (PID).
```bash
ping 8.8.8.8
echo $!      
```
    
11. Finaliza el proceso de Firefox usando su PID.
```bash
pgrep firefox            
kill -TERM <PID>         

kill -KILL <PID>         # forzado
```
    
12. Vuelve a lanzarlo y esta vez deténlo, luego reactívalo.
```bash

kill -STOP <PID>        
sleep 2
kill -CONT <PID>        
```
    
13. Crea un script que capture la señal de interrupción (Ctrl+C) y muestre un mensaje en lugar de cerrarse.
```bash


```

---

## **Bloque 3: Gestión de servicios con systemd**

14. Consulta el estado del servicio de conexión remota (por ejemplo, `ssh`).
```bash
systemctl status ssh
```
    
15. Inicia dicho servicio si está instalado.
```bash
sudo systemctl start ssh
sudo systemctl status ssh
```
    
16. Desactívalo del arranque automático y vuelve a activarlo.
```bash
sudo systemctl disable ssh
sudo systemctl enable ssh
```

---

## **Bloque 4: Archivos y directorios**

17. Lista todos los archivos, incluidos los ocultos, en tu directorio personal.
```bash
ls -la ~
```
    
18. Crea una carpeta llamada `prueba`.
```bash
mkdir -p ~/prueba
```
    
19. Dentro de esa carpeta, crea un archivo `notas.txt` que contenga el texto “Hola Linux”.
```bash
echo "Hola Linux" > ~/prueba/notas.txt
```
    
20. Copia ese archivo con otro nombre.
```bash
cp ~/prueba/notas.txt ~/prueba/notas_copia.txt
```
    
21. Renombra el archivo copiado.
```bash
mv ~/prueba/notas_copia.txt ~/prueba/notas_renombrado.txt
```
    
22. Borra el archivo renombrado.
```bash
rm ~/prueba/notas_renombrado.txt
```

---

## **Bloque 5: Redirecciones y pipes**

23. Redirige la salida de un listado de archivos a un archivo llamado `listado.txt`.
```bash
ls -la > listado.txt
```
    
24. Añade una nueva línea al final del mismo archivo con el texto "Fin del listado".
```bash
echo "Fin del listado" >> listado.txt
```
    
25. Redirige los errores (2) de una operación no válida (`let a=3/0`) a un dispositivo nulo para ignorarlos.
```bash

```
    
26. Filtra de una lista de procesos únicamente aquellos que contengan la palabra “bash”.
```bash
ps aux | grep bash | grep -v grep
```
    
27. Muestra solo las últimas 5 líneas del archivo `listado.txt`.
```bash
tail -n 5 listado.txt
```

---

## **Bloque 6: Tuberías con nombre y sockets**

28. Crea una tubería con nombre llamada `cola`.
```bash

```
    
29. Desde una terminal, deja el archivo `cola` en espera de datos. Desde otra terminal, escribe un mensaje en esa tubería.
```bash



```
    
30. Verifica que `cola` es realmente una tubería.
```bash

    
31. Establece un canal de comunicación entre dos terminales locales utilizando una herramienta que permite redirigir flujos de entrada y salida entre sockets.
```bash




# Ahora lo que escribas en una aparece en la otra.
```

---

## **Bloque 7: Redes**

32. Comprueba la conectividad con el servidor `google.com` enviando unos pocos paquetes.
```bash

```
    
33. Muestra la configuración de tus interfaces de red.
```bash
ip a

# ifconfig
```
    
34. Revisa qué puertos están en escucha en tu máquina.
```bash
ss -tuln

# sudo netstat -tuln
```
    
35. Consulta la dirección IP asociada al dominio `google.com`.
```bash
dig +short google.com
```
    
36. Realiza la misma consulta de resolución DNS usando otra herramienta distinta.
```bash
host google.com

# nslookup google.com
```
    
37. Conéctate de forma remota a otra máquina mediante un protocolo seguro (si tienes acceso).
```bash
ssh usuario@host_remoto
```
    
38. Copia un archivo desde tu máquina a otra mediante una conexión remota segura.
```bash

```

---

## **Bloque 8: Usuarios y permisos**

39. Crea un usuario de prueba llamado `alumno1`.
```bash
sudo useradd -m alumno1
```
    
40. Cámbiale la contraseña.
```bash
sudo passwd alumno1
```
    
41. Cambia los permisos de un archivo a `755`.
```bash
chmod 755 archivo.sh
```
    
42. Cambia el propietario de un archivo a otro usuario.
```bash
sudo chown otro_usuario:otro_usuario archivo.sh
```
    
43. Elimina el usuario creado.
```bash
sudo userdel -r alumno1
```
