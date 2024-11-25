---
layout: page
title: 🛡️ CheatSheet BTL-1
description: CheatSheet completo con comandos útiles para preparar el examen Blue Team Level 1 (BTL-1).
dropdown: BlueTeamsLabs
priority: 2
---

# CheatSheet BTL-1 📝

![bt](/assets/img/cheatbtl.jpg)



Este CheatSheet recopila los comandos más útiles para las herramientas que se pueden utilizar en el examen Blue Team Level 1 (BTL-1). 

---

## 1. **Comandos de Análisis de Phishing**

### Obtener Hashes en Windows:

| Comando | Descripción |
|---------|-------------|
| `get-filehash -algorithm MD5 <archivo>` | Calcula el hash MD5 de un archivo. |
| `get-filehash -algorithm SHA256 <archivo>` | Calcula el hash SHA256 de un archivo. |

### Comandos en Linux:

| Comando | Descripción |
|---------|-------------|
| `md5sum <archivo>` | Calcula el hash MD5 de un archivo. |
| `sha256sum <archivo>` | Calcula el hash SHA256 de un archivo. |

---

## 2. **Comandos de Forense Digital**

### FTK Imager (Windows):

| Comando | Descripción |
|---------|-------------|
| `ftkimager.exe <source> <destination>` | Captura una imagen de disco. |
| `ftkimager.exe -hash <path-to-image>` | Verifica el hash de una imagen de disco. |

### Volatility (Análisis de Memoria):

| Comando | Descripción |
|---------|-------------|
| `volatility -f memoria.dmp pslist` | Lista los procesos en una imagen de memoria. |
| `volatility -f memoria.dmp netscan` | Muestra las conexiones de red en una imagen de memoria. |
| `volatility -f memoria.dmp timeliner` | Crea una línea de tiempo a partir de una imagen de memoria. |
| `volatility -f memoria.dmp imageinfo` | Obtiene información sobre la imagen de memoria. |
| `volatility -f memoria.dmp procdump --pid <PID> --dump-dir <output>` | Volca la memoria de un proceso específico. |
| `volatility -f memoria.dmp dlllist` | Muestra las bibliotecas cargadas por un proceso. |

---

## 3. **Comandos para SIEM (Splunk)**

| Comando | Descripción |
|---------|-------------|
| `index="main" src="192.168.1.1"` | Realiza una consulta para eventos desde la IP origen `192.168.1.1`. |
| `index="security" sourcetype="syslog" "error"` | Filtra eventos de tipo syslog que contienen el texto "error". |
| `index="security" | stats count by sourcetype` | Cuenta el número de eventos por tipo. |
| `index="security" | head 10` | Muestra los 10 eventos más recientes. |
| `index="security" | table _time, host, src_ip, dest_ip, _raw` | Muestra una tabla con los campos de tiempo, host, IP origen, IP destino y evento crudo. |
| `index="security" | timechart span=1h count by sourcetype` | Muestra un gráfico de eventos agrupados por hora y tipo de fuente. |
| `index="main" "failed login" | top src_ip` | Muestra las IPs que intentaron iniciar sesión sin éxito. |

---

## 4. **Comandos de Análisis de Red (Wireshark)**

| Comando | Descripción |
|---------|-------------|
| `http` | Filtra el tráfico HTTP. |
| `ip.src == 192.168.1.1` | Filtra el tráfico por la IP de origen `192.168.1.1`. |
| `ip.dst == 192.168.1.1` | Filtra el tráfico por la IP de destino `192.168.1.1`. |
| `tcp` | Filtra el tráfico TCP. |
| `udp` | Filtra el tráfico UDP. |
| `dns` | Filtra el tráfico DNS. |
| `tshark -i eth0 -w capture.pcap` | Captura tráfico de red y lo guarda en un archivo `.pcap`. |
| `tshark -r capture.pcap -Y "http.request"` | Filtra solicitudes HTTP en un archivo `.pcap` capturado. |
| `wireshark -k -Y "ip.addr==192.168.1.1"` | Inicia Wireshark y filtra el tráfico para la IP `192.168.1.1`. |

---

## 5. **Comandos para Respuesta a Incidentes**

### Comandos en Windows:

| Comando | Descripción |
|---------|-------------|
| `wmic process list brief` | Muestra una lista de procesos activos en el sistema. |
| `netstat -ano` | Muestra las conexiones de red activas y sus identificadores de proceso (PID). |
| `query user` | Muestra los usuarios actuales del sistema. |
| `tasklist /fi "pid eq <PID>"` | Muestra detalles de un proceso específico utilizando su PID. |
| `netstat -an | find "80"` | Filtra conexiones en el puerto 80. |
| `net user` | Muestra todos los usuarios en el sistema Windows. |

### Comandos en Linux:

| Comando | Descripción |
|---------|-------------|
| `ps aux` | Muestra una lista de todos los procesos activos en el sistema. |
| `netstat -tuln` | Muestra las conexiones de red activas. |
| `who` | Muestra los usuarios actualmente conectados. |
| `netstat -tulnp` | Muestra las conexiones de red con información del proceso. |
| `top` | Muestra los procesos activos en tiempo real. |
| `lsof -i :80` | Muestra los procesos que están utilizando el puerto 80. |

---

## 6. **Comandos de Carving con Scalpel (Recuperación de Archivos)**

| Comando | Descripción |
|---------|-------------|
| `scalpel -b -o <output> <imagen-disco>` | Realiza carving en una imagen de disco y guarda los resultados en la carpeta de salida. |
| `scalpel -c` | Verifica las configuraciones del archivo de configuración de Scalpel. |
| `scalpel -z <archivo>` | Realiza carving con el archivo de imagen especificado. |

---

## 7. **Comandos para el Análisis de Archivos (ExifTool)**

| Comando | Descripción |
|---------|-------------|
| `exiftool <archivo>` | Obtiene los metadatos completos de un archivo. |
| `exiftool -T -filename -filesize -createdate <archivo>` | Extrae información específica como nombre, tamaño y fecha de creación de un archivo. |
| `exiftool -all= <archivo>` | Elimina todos los metadatos de un archivo. |
| `exiftool -ExifToolVersion` | Muestra la versión de ExifTool. |

---

## 8. **Comandos para la Gestión de Eventos (Syslog)**

| Comando | Descripción |
|---------|-------------|
| `cat /var/log/syslog` | Muestra el contenido del archivo de log `syslog`. |
| `grep "error" /var/log/syslog` | Busca la palabra "error" dentro del archivo `syslog`. |
| `tail -n 50 /var/log/syslog` | Muestra las últimas 50 líneas del archivo `syslog`. |
| `less /var/log/syslog` | Muestra el archivo `syslog` página por página. |
| `journalctl -xe` | Muestra los logs del sistema en tiempo real. |

---

## 9. **Comandos de Búsqueda en Log de Windows (Event Viewer)**

| Comando | Descripción |
|---------|-------------|
| `Get-WinEvent -LogName Security` | Muestra los logs de seguridad de Windows. |
| `Get-WinEvent -LogName Security | Where-Object {$_.Message -like "*failed*"}` | Filtra los logs de seguridad para eventos que contengan "failed". |
| `Get-WinEvent -LogName Application | Where-Object {$_.LevelDisplayName -eq "Error"}` | Filtra los eventos de la aplicación que tienen el nivel "Error". |


