---
layout: default
title: Pickle Rick | TryHackMe Walkthrough | by Juan (Gh0$ttt) | System Weakness
description: Rick needs your help. Can you help him turn back from pickle form? 
---

# **Pickle Rick | TryHackMe Walkthrough**

**Resumen:**  
Aquí estamos, otra vez con el reto **Pickle Rick** en TryHackMe. Si no sabes de qué hablo, haz clic [aquí para empezar el reto](https://tryhackme.com/room/picklerick). Spoiler: Ayudarás a Rick a dejar de ser un pepinillo, ¿pero lograrás encontrar todos los ingredientes a tiempo?

---

## **Paso 1: Enumeración**
Lo primero que tenemos que hacer es una **exploración de puertos** usando **nmap**. Porque sí, siempre es bueno empezar por lo básico:

```bash
Starting Nmap 7.60 ( https://nmap.org ) at 2024-11-23 12:47 UTC
Nmap scan report for ip-10-10-53-48.eu-west-1.compute.internal (10.10.53.48)
Host is up (0.00046s latency).
Not shown: 998 closed ports
PORT   STATE SERVICE
22/tcp open  ssh
80/tcp open  http
MAC Address: 02:57:FE:1E:66:A9 (Unknown)
Nmap done: 1 IP address (1 host up) scanned in 1.74 seconds
Resultado: Los puertos 22 y 80 están abiertos. Como puedes imaginar, SSH no es lo que necesitamos (ya no está de moda), así que vamos a darle una vuelta al puerto 80 (HTTP).

Paso 2: Revisando el Código Fuente
Accedemos a la IP 10.10.53.48:80 en el navegador y encontramos un mensaje bastante raro de Rick:

"Morty, necesito tu ayuda... He vuelto a convertirme en un pepinillo... y no sé cómo regresar."

¡Sí, esto es una emergencia de Rick! Decidimos buscar más detalles en el código fuente de la página.

html
Copiar código
Username: R1ckRul3s
¡Vaya, Rick tiene su usuario! Ahora necesitamos la contraseña.

Paso 3: Usando Nikto para Buscar Más Información
Decidí hacer un escaneo rápido con Nikto, porque siempre se puede encontrar algo interesante con este escáner.

bash
Copiar código
root@ip-10-10-175-58:~# nikto -host 10.10.53.48
+ /login.php: Admin login page/section found.
¡Bingo! Un login.php. Vamos a probar la contraseña que encontramos en el robots.txt.

Paso 4: Iniciamos Sesión
Probamos con el usuario R1ckRul3s y la contraseña Wubbalubbadubdub (sí, la misma que encontramos en robots.txt) y… ¡voilà! Accedemos a un panel de administración de Rick.

Paso 5: Recolectando Ingredientes
En el panel, encontramos varios archivos como:

Sup3rS3cretPickl3Ingred.txt
clue.txt
denied.php
El primero que probamos es Sup3rS3cretPickl3Ingred.txt. Abriendo la URL directamente, encontramos el primer ingrediente:

bash
Copiar código
mr. meeseek hair
¡Primer ingrediente encontrado!

Paso 6: Buscando Más Ingredientes
A continuación, encontramos un archivo llamado clue.txt, con un mensaje que dice:

"Busca alrededor del sistema de archivos para los otros ingredientes."

Decidimos explorar más y nos vamos a la carpeta /home donde encontramos la carpeta rick. Dentro, había un archivo llamado second ingredients.

Lo copiamos al directorio actual y… ¡bingo! Aquí está el segundo ingrediente:

bash
Copiar código
1 jerry tear
Paso 7: El Tercer Ingrediente
Finalmente, exploramos la carpeta /root y encontramos el archivo 3rd.txt. Lo copiamos a nuestro directorio actual y obtenemos:

bash
Copiar código
fleeb juice
Conclusión
¡Misión cumplida! Rick vuelve a ser humano. Ingredientes encontrados:

mr. meeseek hair
1 jerry tear
fleeb juice
¡Y con eso, hemos completado el reto! Ahora Rick puede dejar de ser un pepinillo y volver a la acción. ¡Nos vemos en el siguiente reto, o cuando Rick vuelva a necesitar ayuda!