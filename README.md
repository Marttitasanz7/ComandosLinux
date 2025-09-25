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
oing google.com > &
ping www.google.com + alt y entramos en tty y nos volvemos a logger
ps -aux | grep ping
ps -aux | head
ps -aux | head n-1
echo $!      
```
    
11. Finaliza el proceso de Firefox usando su PID.
```bash
pgrep firefox            
kill -9 <PID>         

```
    
12. Vuelve a lanzarlo y esta vez deténlo, luego reactívalo.
```bash

kill -19 <PID>        

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







Marta@UbuntuServer:~$ history
    1  2025-09-25 09:55:07  shutdown now
    
    2  2025-09-25 09:55:07  pstree
    
    3  2025-09-25 09:55:07  ping 8.8.8.8
    
    4  2025-09-25 09:55:07  shutdown now
    
    5  2025-09-25 09:55:07  echo $0
    
    6  2025-09-25 09:55:07  shutdown now
    
    7  2025-09-25 09:55:07  mkafifo
    
    8  2025-09-25 09:55:07  mkfifo
    
    9  2025-09-25 09:55:07  shutdown now
   
   10  2025-09-25 09:55:07  mkfifo cola
   
   11  2025-09-25 09:55:07  shutdown now
   
   12  2025-09-25 09:55:07  sudo dpk-reconfigure keyboard-configuration
   
   13  2025-09-25 09:55:07  sudo dpkg-reconfigure keyboard-configuration
   
   14  2025-09-25 09:55:07  exit
   
   15  2025-09-25 09:55:07  sudo dpkg-reconfigure locales
   
   16  2025-09-25 09:55:07  exit
   
   17  2025-09-25 09:55:07  shutdown now
   
   18  2025-09-25 09:55:07  sudo loadkeys es
   
   19  2025-09-25 09:55:07  shoutdown now
   
   20  2025-09-25 09:55:07  shutdown now
   
   21  2025-09-25 09:55:07  sudo loadkeys es
   
   22  2025-09-25 09:55:07  sudo dpkg-reconfigure locales
   
   23  2025-09-25 09:55:07  cleaaan
   
   24  2025-09-25 09:55:07  clean
   
   25  2025-09-25 09:55:07  sudo loadkeys es
   
   26  2025-09-25 09:55:07  shoutdown now
   
   27  2025-09-25 09:55:07  shutdown now
   
   28  2025-09-25 09:55:07  sudo loadkeys es
   
   29  2025-09-25 09:55:07  sudo dpkg-reconfigure locales
   
   30  2025-09-25 09:55:07  shutdown now
   
   31  2025-09-25 09:55:07  sudo loadkeys es
   
   32  2025-09-25 09:55:07  HISTSIZE=10000
   
   33  2025-09-25 09:55:07  histfilesize=20000
   
   34  2025-09-25 09:55:07  histtimeformat="%f %t"
   
   35  2025-09-25 09:55:07  export histsize histfilesize histtimeformat
   
   36  2025-09-25 09:55:07  history
   
   37  2025-09-25 09:55:07  nano ~/.bashrc
   
   38  2025-09-25 09:55:07  UNAME -A
   
   39  2025-09-25 09:55:07  CLEAN
   
   40  2025-09-25 09:55:07  EXIT
   
   41  2025-09-25 09:55:07  uname -a
   
   42  2025-09-25 09:55:07  uname -r
   
   43  2025-09-25 09:55:07  df -h
   
   
   44  2025-09-25 09:55:07  sudo du -sh  /etc
   
   45  2025-09-25 09:55:07  free -h
   
   46  2025-09-25 09:55:07  top
   
   47  2025-09-25 09:55:07  sudo apt update && sudo apt install -y htop
   
   48  2025-09-25 09:55:07  ps aux
   
   49  2025-09-25 09:55:07  echo $$
   
   50  2025-09-25 09:55:07  ps -p  $$ -o pid,ppid,tty,cmd
   
   51  2025-09-25 09:55:07  pstree -p
   
   52  2025-09-25 09:55:07  ping google.com
   
   53  2025-09-25 09:55:07  pgrep firefox
   
   54  2025-09-25 09:55:07  kill -9
   
   55  2025-09-25 09:55:07  pgrep firefox
   
   56  2025-09-25 09:55:07  shutdown now
   
   57  2025-09-25 09:55:07  history
   
   58  2025-09-25 09:55:07  shutdown now
   
   59  2025-09-25 09:55:07  ip
   
   60  2025-09-25 09:55:07  ip a
   
   61  2025-09-25 09:55:07  history
   
   62  2025-09-25 09:55:07  ip a
   
   63  2025-09-25 09:55:07  shutdown now
   
   64  2025-09-25 09:55:57  HISTSIZE=10000
   
   65  2025-09-25 09:55:57  HISTFILESIZE=20000
   
   66  2025-09-25 09:55:57  HISTTIMEFORMAT="%F %T  "
   
   67  2025-09-25 09:56:08  export HISTSIZE HISTFILESIZE HISTTIMEFORMAT
   
   68  2025-09-25 09:56:18  history
   
   69  2025-09-25 09:58:45  nano ~/.bashrc
   
   70  2025-09-25 09:59:30  EXPORT HISTTIMEFORMAT="%F %T "
   
   71  2025-09-25 10:00:06  uname -a
   
   72  2025-09-25 10:00:19  uname -r
   
   73  2025-09-25 10:00:28  df -h
   
   74  2025-09-25 10:00:37  sudo du -sh /etc
   
   75  2025-09-25 10:00:48  free -h
   
   76  2025-09-25 10:01:00  top
   
   77  2025-09-25 10:01:15  sudo apt update && sudo apt install -y htop
   
   78  2025-09-25 10:03:15  ps aux
   
   79  2025-09-25 10:03:16  echo $$
   
   80  2025-09-25 10:03:16  ps -p $$ -o pid,ppid,tty,cmd
   
   81  2025-09-25 10:03:25  pstree -p
   
   82  2025-09-25 10:03:39  ping www.google.com
   
   83  2025-09-25 10:03:53  ps -aux | grep ping
   
   84  2025-09-25 10:03:53  ps -aux | head
   
   85  2025-09-25 10:03:54  ps -aux | head n-1
   
   86  2025-09-25 10:03:54  echo $!
   
   87  2025-09-25 10:04:04  pgrep firefox
   
   88  2025-09-25 10:04:25  systemctl status ssh
   
   89  2025-09-25 10:04:36  sudo systemctl start ssh
   
   90  2025-09-25 10:04:36  sudo systemctl status ssh
   
   91  2025-09-25 10:04:48  sudo systemctl disable ssh
   
   92  2025-09-25 10:04:53  sudo systemctl enable ssh
   
   93  2025-09-25 10:05:02  ls -la ~
   
   94  2025-09-25 10:05:10  mkdir -p ~/prueba
   
   95  2025-09-25 10:05:21  echo "Hola Linux" > ~/prueba/notas.txt
   
   96  2025-09-25 10:05:39  cp ~/prueba/notas.txt ~/prueba/notas_copia.txt
   
   97  2025-09-25 10:05:48  mv ~/prueba/notas_copia.txt ~/prueba/notas_renombrado.txt
   
   98  2025-09-25 10:05:56  rm ~/prueba/notas_renombrado.txt
   
   99  2025-09-25 10:06:05  ls -la > listado.txt
   
  100  2025-09-25 10:06:13  echo "Fin del listado" >> listado.txt
  
  101  2025-09-25 10:06:22  ps aux | grep bash | grep -v grep
  
  102  2025-09-25 10:06:29  tail -n 5 listado.txt
  
  103  2025-09-25 10:07:02  mkfifo mi_tuberia_to_guapa
  
  104  2025-09-25 10:07:06  ll
  
  105  2025-09-25 10:07:20  echo "friendly"
  
  106  2025-09-25 10:07:46  echo "Friendly"> mi_tuberia_to_guapa
  
  107  2025-09-25 10:08:25  tty
  
  108  2025-09-25 10:09:01  tty1
  
  109  2025-09-25 10:09:29  cat <mi_tuberia_to_guapa
  
  110  2025-09-25 10:12:59  tty1
  
  111  2025-09-25 10:14:20  ip a
  
  112  2025-09-25 10:14:29  ss -tuln
  
  113  2025-09-25 10:14:42  dig +short google.com
  
  114  2025-09-25 10:14:56  host google.com
  
  115  2025-09-25 10:15:13  sudo useradd -m alumno1
  
  116  2025-09-25 10:15:22  sudo passwd alumno1
  
  117  2025-09-25 10:15:37  chmod 755 archivo.sh
  
  118  2025-09-25 10:15:45  sudo chown otro_usuario:otro_usuario archivo.sh
  
  119  2025-09-25 10:15:52  sudo userdel -r alumno1
  
  120  2025-09-25 10:16:01  history
Marta@UbuntuServer:~$
