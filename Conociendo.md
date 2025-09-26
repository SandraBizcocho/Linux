# 1.- CONOCIENDO EL SERVIDOR LINUX

En este apartado se documentan los comandos pedidos en la tarea para conocer y administrar el servidor Linux.  Cada comando tiene su explicación y su captura correspondiente.  

---

### 1. Nombre del host

**Comando:** `hostname`  
Muestra el nombre del host actual del sistema.

![hostname](img/hostname.png)

**Comando:** `hostname -I`  
Muestra las direcciones IP asignadas al host.

![hostname -I](img/host.png)

**Comando:** `hostname -f`  
Muestra el FQDN (Fully Qualified Domain Name), es decir, el nombre de host completo con dominio.

![hostname -f](img/host.png)

**Comando:** `hostnamectl`  
Herramienta moderna para ver y cambiar el hostname sin reiniciar. Pertenece a `systemd`.

![hostnamectl](img/host.png)

**Comando:** `cat /etc/hostname`  
Muestra el nombre de host guardado en el archivo de configuración.

![cat /etc/hostname](img/hostname.png)

**Comando:** `hostnamectl set-hostname NuevoNombre`  
Permite cambiar el nombre del host de forma permanente (requiere cerrar sesión para aplicar).

---

### 2. Versión del sistema

**Comando:** `lsb_release -a`  
Muestra la distribución de Linux y su versión.

![versión sistema](img/sistema.png)

**Comando:** `cat /etc/os-release`  
Muestra información detallada de la distribución.

![os-release](img/sistema.png)

**Comando:** `cat /etc/debian_version`  
Muestra la versión de Debian.

![debian_version](img/sistema.png)

---

### 3. Versión del núcleo y arquitectura

**Comando:** `uname -a`  
Muestra información completa del kernel, arquitectura y compilación.

**Comando:** `uname -r`  
Muestra únicamente la versión del kernel.

![uname](img/sistema.png)

---

### 4. Memoria RAM

**Comando:** `free` y `free -h`  
Muestran el uso de la memoria RAM y swap. La opción `-h` lo muestra en formato legible (MB/GB).

![memoria RAM](img/ram.png)

---

### 5. CPU

**Comando:** `lscpu`  
Muestra información detallada de la CPU: arquitectura, núcleos, hilos, etc.

![CPU](img/cpu.png)

**Comando:** `nproc`  
Muestra el número de procesadores lógicos disponibles.

![núcleos](img/nucleo.png)

---

### 6. Discos y particiones

**Comando:** `lsblk` y `lsblk -f`  
Muestran los dispositivos de bloque y su información de sistema de archivos.

**Comando:** `sudo fdisk -l`  
Lista las particiones y discos del sistema.

![discos](img/discos.png)

---

### 7. Sistemas montados

**Comando:** `df -h`  
Muestra el uso de disco de cada sistema de archivos montado.

**Comando:** `df -hT`  
Incluye el tipo de sistema de archivos.

![sistemas montados](img/sistemasMontados.png)

---

### 8. Tamaño de carpetas

**Comando:** `du -h /home/`  
Muestra el tamaño de las carpetas dentro de `/home`.

**Comando:** `du -hs /home`  
Muestra el tamaño total de `/home`.

**Comando:** `du -hs /home/*`  
Muestra el tamaño de cada subcarpeta dentro de `/home`.

![tamaño carpetas](img/tamano.png)

---

### 9. Usuarios y grupos del sistema

**Comando:** `cat /etc/passwd` y `getent passwd`  
Muestran la lista de usuarios del sistema.

![passwd](img/passwd.png)

**Comando:** `cat /etc/shadow` y `getent shadow`  
Muestran las contraseñas encriptadas (requiere permisos de root).

![shadow](img/shadow.png)

**Comando:** `cat /etc/group` y `getent group`  
Muestran los grupos existentes.

![group](img/group.png)

**Comando:** `cat /etc/gshadow` y `getent gshadow`  
Muestran contraseñas de grupos.

![gshadow](img/gshadow.png)

**Comando:** `cat /etc/nsswitch.conf`  
Indica dónde busca el sistema la información de usuarios, grupos, hosts, etc. (archivos locales, DNS, etc.).

![nsswitch](img/nsswitch.png)

---

### 10. Información de la red

**Comando:** `ip a`  
Muestra todas las interfaces de red, direcciones IP y estado (UP/DOWN).

![ip a](img/ipa.png)

**Comando:** `ip r`  
Muestra la tabla de rutas y la puerta de enlace predeterminada.

![ip r](img/ipr.png)

**Comando:** `ping -c 4 <PuertaDeEnlace>`  
Verifica conectividad con el gateway y mide tiempo de respuesta (avg ~1ms en red local).

**Comando:** `ping -c 4 google.es`  
Verifica conectividad a Internet (avg < 20ms en condiciones normales).

![ping](img/ping.png)

---

### 11. Comprobar DNS

**Comando:** `nslookup google.es`  
Muestra qué servidor DNS responde la consulta y su IP.

**Comando:** `nslookup 8.8.8.8`  
Muestra quién es el propietario de esa IP.

![DNS](img/dns.png)

---

### 12. Configuración de la red

**Comando:** `cat /etc/network/interfaces`  
Muestra la configuración de las interfaces de red.

![interfaces](img/configuracion.png)

---

### 13. Configuración tradicional de DNS

**Comando:** `cat /etc/resolv.conf`  
Muestra los servidores DNS configurados en el sistema.

![resolv.conf](img/resolv.png)

---

### 14. Reiniciar la red

**Comando:**  
```bash
systemctl status networking
systemctl restart networking

---

### 15. Bajar o subir una tarjeta de red

**Comandos:**
```ifdown eth0
```ifup eth0
```ifdown eth0 && ifup eth0
Permiten desactivar y reactivar manualmente una interfaz de red.
