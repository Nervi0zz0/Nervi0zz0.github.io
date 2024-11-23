---
layout: page
title: 🥒 Pickle Rick | TryHackMe Walkthrough
description: Rick necesita tu ayuda. ¿Puedes encontrar los ingredientes secretos para ayudarlo a dejar de ser un pepinillo?
dropdown: TryHackMe
---

# 🧪 Pickle Rick | TryHackMe Walkthrough  
![Pickle Rick](../assets/img/rick.png)

---

## 📜 **Resumen**  

Bienvenidos al caos más delirante del hacking virtual. Tu misión: ayudar a Rick, quien ha vuelto a convertirse en un pepinillo porque, según él, "¡es ciencia, Morty!" Pero ahora no recuerda cómo volver a ser humano. Tienes que infiltrarte en un servidor, encontrar **tres ingredientes secretos** y devolverlo a su forma humana antes de que decida bañarse en vinagre para siempre.  

Si aún no conoces el desafío, [haz clic aquí](https://tryhackme.com/room/picklerick) para comenzar.  

---

## 🛠️ **Pasos**

### **Paso 1: Enumeración**  
Como cualquier hacker sensato, empezamos con **nmap** porque no hay mejor manera de revelar los secretos de un servidor que decirle educadamente: "Muéstrame tus puertos abiertos".  

| **Comando** | **Resultado** |
|-------------|---------------|
| `nmap -sV 10.10.53.48` | **Puertos abiertos:**<br>22/tcp - SSH<br>80/tcp - HTTP |
| **Tiempo de escaneo:** | 1.74 segundos . |
| **MAC Address:** | 02:57:FE:1E:66:A9 . |

Parece que tenemos un servidor web corriendo en el puerto 80. Vamos a ver qué esconde.

---

### **Paso 2: Inspección del Código Fuente**  
Accedemos al sitio web `http://10.10.53.48` y encontramos un mensaje desgarrador de Rick:  

> "¡Morty! Ayúdame... me convertí en un pepinillo otra vez y no sé qué hacer. Necesito que encuentres los ingredientes para mi poción... pero olvidé mi contraseña. ¡Ayúdame, Morty!"

Con lágrimas en los ojos, inspeccionamos el código fuente porque Rick dejó un comentario con la misma sutileza que un tanque en un campo de flores:  

| **Código fuente encontrado:** |
|-------------------------------|
| `<!-- Username: R1ckRul3s -->` |

Así que ahora tenemos el nombre de usuario: `R1ckRul3s`. ¿Qué sigue? La contraseña.

---

### **Paso 3: Exploración con Nikto**  
Decidimos lanzar **Nikto** contra el servidor web porque, si alguien usa Apache/2.4.18, claramente no es amigo de la seguridad.

| **Comando** | **Resultado** |
|-------------|---------------|
| `nikto -host 10.10.53.48` | **Puntos interesantes:**<br>- `/login.php`: Página de inicio de sesión.<br>- `robots.txt`: Archivo sospechoso sin restricciones visibles.<br>- Leaks en ETags (clásico Apache). |

Hemos encontrado `/login.php` y `robots.txt`. Vamos a inspeccionar primero el archivo `robots.txt`.

---

### **Paso 4: Inspección de robots.txt**  
Los robots son geniales... pero no en archivos `.txt`. Accedemos a `http://10.10.53.48/robots.txt` y encontramos:

| **Contenido del archivo:** |
|----------------------------|
| `Wubbalubbadubdub` |

Por supuesto, Rick pensó que "Wubbalubbadubdub" era una contraseña perfecta. Con esto y el usuario `R1ckRul3s`, vamos a intentar acceder al panel de administración en `/login.php`.

---

### **Paso 5: Acceso al Panel de Administración**  
Ingresamos las credenciales:

| **Usuario**    | **Contraseña**        |
|----------------|-----------------------|
| `R1ckRul3s`   | `Wubbalubbadubdub`    |

¡Éxito! Nos encontramos con un panel de comandos que nos permite ejecutar órdenes en el servidor. Ahora comienza la verdadera diversión.

---

### **Paso 6: Recolección de Ingredientes**  

#### 🥒 **Ingrediente 1: mr. meeseek hair**  
Usamos `ls` en el panel de comandos y encontramos el archivo **Sup3rS3cretPickl3Ingred.txt**. Para leer su contenido:

| **Comando** | **Resultado** |
|-------------|---------------|
| `cat Sup3rS3cretPickl3Ingred.txt` | `mr. meeseek hair` |

Primer ingrediente en la bolsa. Vamos por más.

---

#### 🥒 **Ingrediente 2: 1 jerry tear**  
Encontramos una pista en el archivo **clue.txt**, que nos dice que exploremos el sistema de archivos. Miramos dentro del directorio de Rick:

| **Comando** | **Resultado** |
|-------------|---------------|
| `ls -a /home/rick` | `second_ingredient.txt` |
| `cat /home/rick/second_ingredient.txt` | `1 jerry tear` |

Segundo ingrediente encontrado. Rick seguramente derramó esa lágrima al pensar en su yerno. 😏

---

#### 🥒 **Ingrediente 3: fleeb juice**  
Finalmente, exploramos el directorio raíz `/root` y encontramos el archivo **3rd.txt**.  

| **Comando** | **Resultado** |
|-------------|---------------|
| `cat /root/3rd.txt` | `fleeb juice` |

Con los tres ingredientes en la mano, la poción de Rick está lista.

---

## 🏁 **Conclusión**  
¡Misión cumplida! Has encontrado los tres ingredientes secretos y ayudado a Rick a revertir su transformación. A continuación, el resumen de los ingredientes recolectados:

| **Ingrediente**     | **Ubicación**       |
|---------------------|---------------------|
| `mr. meeseek hair`  | `/var/www/html`     |
| `1 jerry tear`      | `/home/rick`        |
| `fleeb juice`       | `/root`             |

Rick está de vuelta a su forma humana (por ahora). ¿Qué aprendimos hoy? Que la seguridad es tan importante como no beber fleeb juice directamente de la botella. 🚀  

¡Gracias por leer y nos vemos en el próximo caos! 😈
