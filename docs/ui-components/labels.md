---
title: 🛡️ **Modelo OSI en Ciberseguridad**
parent: Supervivencia Sin Esfuerzo
priority: 9
---

# 🌐 Modelo OSI en Ciberseguridad

**Domina las 7 capas del Modelo OSI con una guía interactiva y visual.**  
Explora sus funciones, amenazas comunes y estrategias de defensa.  
{: .text-center }

---

## 📌 Capa 1: Física

### 🖥️ **Hardware y Seguridad Física**

La **Capa Física** trata sobre **cables, switches y señales físicas**.

### 🔍 Amenazas Comunes:
- **Eavesdropping/Tapping**: Interceptar cables para obtener datos.  
- **Interferencia Electromagnética**: Ruido externo que afecta señales.  
- **Manipulación Física**: Acceso no autorizado al equipo.  

### 🛡️ **Defensas Sugeridas**:
- Uso de **fibra óptica** para seguridad.  
- Monitoreo con **CCTV**.  
- Controles de acceso físico restringido.  

> **Importante**: Mantén el acceso físico restringido en áreas sensibles para evitar manipulaciones no autorizadas.

---

## 🔒 Capa 2: Enlace de Datos

### 🔗 **Transmisión Segura en Redes Locales**

La **Capa de Enlace** controla la transmisión de **frames** y **direcciones MAC**.

### 🔍 Amenazas Comunes:
- **MAC Address Spoofing**: Suplantación de direcciones MAC.  
- **ARP Spoofing**: Manipulación de la tabla ARP para interceptar tráfico.  

### 🛡️ **Defensas Sugeridas**:
- Implementar **ARP Inspection**.  
- Usar **switches seguros** con autenticación.  

> **Recomendación**: Configura la inspección ARP para evitar ataques de suplantación y proteger la integridad de la red.

---

## 🚚 Capa 3: Red

### 🌐 **Movimiento Inteligente de Paquetes**

Gestiona las **direcciones IP** y el **enrutamiento de paquetes**.

### 🔍 Amenazas Comunes:
- **IP Spoofing**: Falsificación de direcciones IP.  
- **Manipulación de Tablas de Rutas**: Alteración de rutas en la red.

### 🛡️ **Defensas Sugeridas**:
- Configuración de **firewalls robustos**.  
- Autenticación segura en rutas dinámicas.

---

## 📡 Capa 4: Transporte

### 🚦 **Flujo Controlado de Datos**

Garantiza la **entrega confiable y segmentada** de datos.

### 🔍 Amenazas Comunes:
- **SYN Flood**: Agotamiento de recursos con conexiones falsas.  
- **UDP Flood**: Saturación de redes con tráfico UDP.

### 🛡️ **Defensas Sugeridas**:
- Implementar **rate limiting**.  
- Usar sistemas de **detección y mitigación DDoS**.  

> **Advertencia**: Los ataques DDoS pueden causar interrupciones significativas en los servicios, asegúrate de contar con protección adecuada.

---

## 🔄 Capa 5: Sesión

### 💬 **Gestión Segura de Sesiones**

Administra sesiones de **comunicación activa** entre dispositivos.

### 🔍 Amenazas Comunes:
- **Session Replay**: Reutilización de sesiones autenticadas.  
- **MITM (Man-in-the-Middle)**: Interceptación y manipulación de datos.

### 🛡️ **Defensas Sugeridas**:
- Uso de **TLS** (Transport Layer Security).  
- Autenticación robusta y renovada.

---

## 🔐 Capa 6: Presentación

### 🔐 **Conversión y Cifrado de Datos**

Maneja la **transformación de datos** y su cifrado para proteger la integridad.

### 🔍 Amenazas Comunes:
- **SSL Stripping**: Degradación de conexiones seguras.  
- **Data Manipulation**: Alteración de datos a través de formatos no seguros.

### 🛡️ **Defensas Sugeridas**:
- Implementar **TLS/SSL actualizado**.  
- Validación estricta de certificados digitales.  

> **Importante**: Siempre valida los certificados digitales para evitar ataques de intermediarios.

---

## 🌍 Capa 7: Aplicación

### 🌐 **Servicios al Usuario Final**

Administra los servicios más visibles como **HTTP, FTP y SMTP**.

### 🔍 Amenazas Comunes:
- **SQL Injection**: Ejecución de comandos maliciosos en la base de datos.  
- **Cross-Site Scripting (XSS)**: Inserción de scripts no autorizados en el navegador.  
- **DDoS Attacks**: Saturación de los servicios web.

### 🛡️ **Defensas Sugeridas**:
- Configurar un **WAF (Web Application Firewall)**.  
- Validar las entradas de usuarios y proteger contra **DDoS**.

> **Recomendación**: Protege tus aplicaciones web utilizando un WAF y realizando pruebas regulares de seguridad.

---

## 🎯 Resumen Visual

| **Capa**             | **Amenazas Clave**                    | **Defensas Principales**         |
|:---------------------|:--------------------------------------|:---------------------------------|
| **1. Física**        | Eavesdropping, manipulación física    | Fibra óptica, CCTV, acceso físico|
| **2. Enlace**        | MAC Spoofing, ARP Spoofing            | ARP Inspection, switches seguros |
| **3. Red**           | IP Spoofing, manipulación de rutas    | Firewalls, autenticación rutas   |
| **4. Transporte**    | SYN Flood, UDP Flood                  | Rate limiting, detección DDoS    |
| **5. Sesión**        | Session Replay, MITM                  | TLS, autenticación fuerte        |
| **6. Presentación**  | SSL Stripping, manipulación de datos  | TLS/SSL actualizado, validación  |
| **7. Aplicación**    | SQL Injection, XSS, DDoS              | WAF, validación de entradas      |

---

![Interfaz Visual](/assets/images/gif/osi.gif)  
*Interactúa con las capas y amenazas visualmente.*  
{: .text-center .mt-4}

---

[🔒 Explora más sobre Seguridad](#)  
[🌐 Comparte esta guía](#)

---

<div style="text-align: center;">
  <img src="/assets/images/cojo.png" alt="Firma" style="max-width: 20%; border-radius: 50%; box-shadow: 0 12px 24px rgba(0, 0, 0, 0.5);">
</div>
