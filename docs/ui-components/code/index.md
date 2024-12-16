---
title: Métodos de Solicitud HTTP 
parent: Cheat sheet
grand_parent: ¿Y dónde practicar?
priority: 4
---


# Métodos de Solicitud HTTP

En este artículo se cubren los **9 principales métodos de solicitud HTTP** utilizados en las aplicaciones web. Cada método tiene un propósito específico dentro de la comunicación entre cliente y servidor. Esta guía te ayudará a comprender el uso correcto de cada método y cuándo aplicarlos.

![ImagendeBytebyteGo](/assets/images/gif/http.gif)

## 1. GET

<div style="border: 1px solid #ccc; padding: 10px; margin-bottom: 15px;">
<strong>Descripción:</strong> El método `GET` se utiliza para recuperar información de un servidor. Generalmente, no tiene efectos secundarios y no modifica el estado del recurso.  
<strong>Uso:</strong> Ideal para obtener datos como recursos estáticos (páginas HTML, imágenes, etc.) o consultar el estado de un recurso.  
<strong>Ejemplo:</strong> `GET /v1/products/iphone`
</div>

## 2. POST

<div style="border: 1px solid #ccc; padding: 10px; margin-bottom: 15px;">
<strong>Descripción:</strong> `POST` envía datos al servidor, usualmente para crear un nuevo recurso.  
<strong>Uso:</strong> Utilizado para crear elementos, enviar formularios, o cargar archivos. Los datos suelen ir en el cuerpo de la solicitud.  
<strong>Ejemplo:</strong> `POST /v1/users`
</div>

## 3. PUT

<div style="border: 1px solid #ccc; padding: 10px; margin-bottom: 15px;">
<strong>Descripción:</strong> El método `PUT` actualiza o reemplaza un recurso existente en el servidor.  
<strong>Uso:</strong> Utilizado para actualizar un recurso existente, especificando el recurso completo en el cuerpo de la solicitud.  
<strong>Ejemplo:</strong> `PUT /v1/users/123`
</div>

## 4. DELETE

<div style="border: 1px solid #ccc; padding: 10px; margin-bottom: 15px;">
<strong>Descripción:</strong> `DELETE` elimina un recurso en el servidor.  
<strong>Uso:</strong> Utilizado para eliminar recursos existentes.  
<strong>Ejemplo:</strong> `DELETE /v1/users/123`
</div>

## 5. PATCH

<div style="border: 1px solid #ccc; padding: 10px; margin-bottom: 15px;">
<strong>Descripción:</strong> `PATCH` modifica parcialmente un recurso existente.  
<strong>Uso:</strong> Utilizado para realizar cambios parciales o actualizaciones incrementales en un recurso.  
<strong>Ejemplo:</strong> `PATCH /v1/users/123`
</div>

## 6. HEAD

<div style="border: 1px solid #ccc; padding: 10px; margin-bottom: 15px;">
<strong>Descripción:</strong> `HEAD` es similar a `GET`, pero solo devuelve los encabezados de la respuesta sin el cuerpo.  
<strong>Uso:</strong> Se utiliza para verificar la existencia de un recurso o consultar los metadatos sin descargar todo el contenido.  
<strong>Ejemplo:</strong> `HEAD /v1/products/iphone`
</div>

## 7. OPTIONS

<div style="border: 1px solid #ccc; padding: 10px; margin-bottom: 15px;">
<strong>Descripción:</strong> `OPTIONS` devuelve los métodos HTTP soportados por el servidor para un recurso específico.  
<strong>Uso:</strong> Utilizado para verificar qué métodos son aceptados por el servidor antes de enviar una solicitud.  
<strong>Ejemplo:</strong> `OPTIONS /v1/users`
</div>

## 8. CONNECT

<div style="border: 1px solid #ccc; padding: 10px; margin-bottom: 15px;">
<strong>Descripción:</strong> `CONNECT` establece una conexión de túnel bidireccional con el servidor, frecuentemente utilizado para establecer una conexión segura (SSL/TLS).  
<strong>Uso:</strong> Ideal para conexiones a través de un proxy, como conexiones HTTPS.  
<strong>Ejemplo:</strong> `CONNECT xxx.com:80`
</div>

## 9. TRACE

<div style="border: 1px solid #ccc; padding: 10px; margin-bottom: 15px;">
<strong>Descripción:</strong> `TRACE` realiza un seguimiento del camino recorrido por la solicitud en la red. Devuelve la solicitud original recibida por el servidor.  
<strong>Uso:</strong> Utilizado principalmente para pruebas y depuración, permitiendo diagnosticar problemas de red.  
<strong>Ejemplo:</strong> `TRACE /index.html`
</div>

---

Estos métodos son la base para la comunicación entre cliente y servidor en aplicaciones web modernas. Es importante conocer cuándo utilizarlos para optimizar el rendimiento, seguridad y eficiencia de la interacción con los servidores.

### Recursos Adicionales

- [Documentación oficial de HTTP](https://developer.mozilla.org/es/docs/Web/HTTP/Methods)
- [Curso sobre Métodos HTTP en TryHackMe](https://tryhackme.com)
- [Ejercicios de Métodos HTTP en Hack The Box](https://hackthebox.com)

  <hr style="border: none; border-top: 1px solidrgb(255, 254, 248); margin: 50px 0; box-shadow: 0 1px 2px rgba(255, 215, 0, 0.6);">

  <div style="text-align: center; margin: 50px auto;">
    <img src="/assets/images/cojo.png" alt="Firma" style="max-width: 20%; border-radius: 50%; border: 1px solid #FFD700; box-shadow: 0 12px 24px rgba(0, 0, 0, 0.9);">
  </div>
  <div style="text-align: center; margin-top: 40px;">
    <p style="font-size: 0.9em; color: #888;">© 2024 Nervi0zz0</p>
  </div>