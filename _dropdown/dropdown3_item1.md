---
layout: default
title: Pickle Rick | TryHackMe Walkthrough |
description: Rick needs your help. Can you help him turn back from pickle form?
---

# Pickle Rick | TryHackMe Walkthrough

## Resumen

Aquí estamos con el reto **Pickle Rick** de TryHackMe. Si no sabes de qué hablo, haz clic [aquí](https://tryhackme.com/room/picklerick) para empezar el reto. Spoiler: Ayudarás a Rick a dejar de ser un pepinillo, pero ¿podrás encontrar todos los ingredientes secretos a tiempo? No me sorprendería si no.

## Pasos

| **Paso**               | **Descripción**                                                                                     | **Comandos / Resultados**                                                                                                                                                                 |
|------------------------|-----------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **1: Enumeración**      | Primero, realizamos una **enumeración** utilizando **nmap** para ver los puertos abiertos.          | Ejecutamos el siguiente comando de **nmap**: <br>```bash<br>Starting Nmap 7.60 ( https://nmap.org ) at 2024-11-23 12:47 UTC<br>Nmap scan report for ip-10-10-53-48.eu-west-1.compute.internal (10.10.53.48)<br>Host is up (0.00046s latency).<br>Not shown: 998 closed ports<br>PORT   STATE SERVICE<br>22/tcp open  ssh<br>80/tcp open  http<br>MAC Address: 02:57:FE:1E:66:A9 (Unknown)<br>Nmap done: 1 IP address (1 host up) scanned in 1.74 seconds<br>```<br><br>**Resultado**: Los puertos 22 y 80 están abiertos. Nos dirigimos al puerto 80 (HTTP), ya que **SSH** no es útil en este caso. |
| **2: Revisando el Código Fuente** | Accedemos a la IP `10.10.53.48:80` en el navegador y encontramos un mensaje extraño de Rick: "Morty, necesito tu ayuda... He vuelto a convertirme en un pepinillo y no sé cómo regresar." | Al inspeccionar el código fuente de la página, encontramos lo siguiente: <br> ```html<br>Username: R1ckRul3s<br>``` <br>¡Rick tiene un nombre de usuario! Ahora necesitamos encontrar la contraseña para salvarlo. |
| **3: Usando Nikto**      | Usamos **Nikto** para escanear más a fondo la página web. Esto nos ayuda a encontrar más puntos de entrada. | Ejecutamos el siguiente comando de **Nikto**: <br>```bash<br>root@ip-10-10-175-58:~# nikto -host 10.10.53.48<br>+ /login.php: Admin login page/section found.<br>```<br>¡Y encontramos una página de login en `/login.php`! Esto es una buena pista de que podemos intentar acceder con el nombre de usuario que encontramos. |
| **4: Iniciamos Sesión**  | Usamos el nombre de usuario **R1ckRul3s** y la contraseña **Wubbalubbadubdub** (que encontramos en el archivo `robots.txt`). | Al intentar iniciar sesión con estos datos, ¡accedemos con éxito al panel de administración de Rick! |
| **5: Recolectando Ingredientes** | Dentro del panel de administración de Rick, encontramos varios archivos, entre ellos: **Sup3rS3cretPickl3Ingred.txt**, **clue.txt** y **denied.php**. Empezamos a explorar estos archivos. | Primero, abrimos el archivo **Sup3rS3cretPickl3Ingred.txt** y encontramos el primer ingrediente: <br>```bash<br>mr. meeseek hair<br>``` <br>¡Ingrediente 1 encontrado! |
| **6: Buscando Más Ingredientes** | El archivo **clue.txt** nos da un consejo útil: "Busca alrededor del sistema de archivos para los otros ingredientes." | Decidimos explorar más el sistema de archivos. Al ingresar a la carpeta `/home`, encontramos la carpeta **rick**, y dentro de ella un archivo llamado **second_ingredient.txt**. Copiamos el archivo y encontramos el segundo ingrediente: <br>```bash<br>1 jerry tear<br>``` |
| **7: El Tercer Ingrediente** | Finalmente, buscamos más en el directorio raíz `/root` y encontramos el archivo **3rd.txt**. Lo copiamos y descubrimos el tercer ingrediente. | Ejecutamos el siguiente comando para obtener el tercer ingrediente: <br>```bash<br>fleeb juice<br>``` |
| **Conclusión**          | Con todos los ingredientes encontrados, hemos completado la misión y Rick ha vuelto a ser humano. | Ingredientes encontrados: <br> - **mr. meeseek hair**: Primer ingrediente <br> - **1 jerry tear**: Segundo ingrediente <br> - **fleeb juice**: Tercer ingrediente <br><br>**Misión cumplida**: ¡Rick deja de ser un pepinillo! |

---

¡Y así hemos completado el reto de **Pickle Rick** en TryHackMe! Ahora Rick puede volver a la acción. Nos vemos en el siguiente reto o cuando Rick necesite ayuda nuevamente.
