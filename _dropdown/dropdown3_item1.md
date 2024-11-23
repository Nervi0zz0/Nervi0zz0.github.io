---
layout: page
title: 🥒 Pickle Rick | TryHackMe Walkthrough
description: Rick necesita tu ayuda. ¿Puedes encontrar los ingredientes secretos para ayudarlo a dejar de ser un pepinillo?
dropdown: dropdown3
---

# 🧪 Pickle Rick | TryHackMe Walkthrough  
![Pickle Rick](../assets/img/rick.png)

---

## 📜 **Resumen**  

En este reto de TryHackMe, tu misión es ayudar a Rick a revertir su transformación en pepinillo. ¿Lograrás encontrar todos los **ingredientes secretos** y salvar el día? Si aún no conoces el desafío, [haz clic aquí](https://tryhackme.com/room/picklerick) para comenzar.  

---

## 🛠️ **Pasos**  

### **Paso 1: Enumeración**  
Comenzamos con un escaneo de puertos usando **nmap** para identificar los servicios abiertos.  

```bash
nmap -sV 10.10.53.48
Resultado:

arduino
Copiar código
PORT   STATE SERVICE
22/tcp open  ssh
80/tcp open  http
Encontramos los puertos 22 (SSH) y 80 (HTTP). Continuamos con el puerto HTTP para investigar.
Paso 2: Inspección del Código Fuente
Al acceder al sitio web en 10.10.53.48:80, Rick nos deja un mensaje solicitando ayuda. Inspeccionamos el código fuente de la página y encontramos el siguiente dato:

html
Copiar código
<!-- Username: R1ckRul3s -->
Ahora tenemos el nombre de usuario, pero necesitamos la contraseña.

Paso 3: Exploración con Nikto
Usamos Nikto para buscar vulnerabilidades o archivos sensibles en el servidor web.

bash
Copiar código
nikto -host 10.10.53.48
Resultado:

bash
Copiar código
+ /login.php: Admin login page/section found.
Identificamos una página de inicio de sesión en /login.php.

Paso 4: Encontrando la Contraseña
Exploramos el archivo robots.txt del servidor para encontrar posibles pistas.

bash
Copiar código
curl http://10.10.53.48/robots.txt
Resultado:

Copiar código
Wubbalubbadubdub
Con esta contraseña y el nombre de usuario R1ckRul3s, accedemos al panel de administración en /login.php.

Paso 5: Recolectando Ingredientes
🥒 Ingrediente 1
Dentro del panel de administración, encontramos el archivo Sup3rS3cretPickl3Ingred.txt, que contiene:

Copiar código
mr. meeseek hair
🥒 Ingrediente 2
Seguimos las pistas del archivo clue.txt, que nos indica explorar el sistema de archivos. En la carpeta /home/rick/, hallamos el archivo second_ingredient.txt:

Copiar código
1 jerry tear
🥒 Ingrediente 3
Finalmente, navegamos al directorio /root/ y encontramos el archivo 3rd.txt:

Copiar código
fleeb juice
🏁 Conclusión
¡Misión cumplida! Has encontrado los tres ingredientes secretos, ayudando a Rick a revertir su transformación en pepinillo. 🎉

Ingredientes encontrados:
mr. meeseek hair
1 jerry tear
fleeb juice
Rick ahora es humano nuevamente. ¡Nos vemos en el próximo desafío! 🚀

Detalles Adicionales
🔍 Enumeración con Nmap
El escaneo inicial reveló los puertos abiertos (22 y 80), guiándonos al análisis del servidor web.

🌐 Exploración del Sitio Web
Inspeccionamos el código fuente y usamos herramientas como Nikto para descubrir rutas clave como /login.php y el archivo robots.txt.

🧑‍💻 Recolección de Ingredientes
Gracias a la exploración del sistema de archivos, encontramos los ingredientes secretos en ubicaciones clave del servidor.

¡Gracias por leer! 😊