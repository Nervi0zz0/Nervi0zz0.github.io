---
title: 🛡️ Modelo OSI en Ciberseguridad
parent: Supervivencia Sin Esfuerzo
priority: 9
---

# 🌐 **Modelo OSI en Ciberseguridad** {: .fs-8 .fw-700 .text-blue-300 .text-center}

**Domina las 7 capas del Modelo OSI con una guía interactiva y visual.**  
Explora sus funciones, amenazas comunes y estrategias de defensa.  
{: .fs-5 .text-grey-dk-200 .text-center}

---

<div class="interactive-container">

## 📌 **1. Capa Física**  
<div class="accordion">
  <details>
    <summary>🖥️ **Hardware y Seguridad Física**</summary>
    La **Capa Física** trata sobre **cables, switches y señales físicas**.

    ### 🔍 **Amenazas**  
    - **Eavesdropping/Tapping**: Interceptar cables para obtener datos.  
    - **Interferencia Electromagnética**: Ruido externo que afecta señales.  
    - **Manipulación Física**: Acceso no autorizado al equipo.  

    ### 🛡 **Defensa Sugerida**  
    - Uso de **fibra óptica** para seguridad.  
    - Monitoreo con **CCTV**.  
    - Controles de acceso físico restringido.  
  </details>
</div>

---

## 🔒 **2. Capa de Enlace de Datos**  
<div class="accordion">
  <details>
    <summary>🔗 **Transmisión Segura en Redes Locales**</summary>
    La **Capa de Enlace** controla la transmisión de **frames** y **direcciones MAC**.

    ### 🔍 **Amenazas**  
    - **MAC Address Spoofing**: Suplantación de direcciones MAC.  
    - **ARP Spoofing**: Manipulación de la tabla ARP para interceptar tráfico.  

    ### 🛡 **Defensa Sugerida**  
    - Implementar **ARP Inspection**.  
    - Usar **switches seguros** con autenticación.  
  </details>
</div>

---

## 🚚 **3. Capa de Red**  
<div class="accordion">
  <details>
    <summary>🌐 **Movimiento Inteligente de Paquetes**</summary>
    Gestiona las **direcciones IP** y el **enrutamiento de paquetes**.

    ### 🔍 **Amenazas**  
    - **IP Spoofing**: Falsificación de direcciones IP.  
    - **Manipulación de Tablas de Rutas**.  

    ### 🛡 **Defensa Sugerida**  
    - Configuración de **firewalls robustos**.  
    - Autenticación segura en rutas dinámicas.  
  </details>
</div>

---

## 📡 **4. Capa de Transporte**  
<div class="accordion">
  <details>
    <summary>🚦 **Flujo Controlado de Datos**</summary>
    Garantiza la **entrega confiable y segmentada** de datos.

    ### 🔍 **Amenazas**  
    - **SYN Flood**: Agotamiento de recursos con conexiones falsas.  
    - **UDP Flood**: Saturación de redes con tráfico UDP.

    ### 🛡 **Defensa Sugerida**  
    - Implementar **rate limiting**.  
    - Usar sistemas de **detección y mitigación DDoS**.  
  </details>
</div>

---

## 🔄 **5. Capa de Sesión**  
<div class="accordion">
  <details>
    <summary>💬 **Gestión Segura de Sesiones**</summary>
    Administra sesiones de **comunicación activa** entre dispositivos.

    ### 🔍 **Amenazas**  
    - **Session Replay**: Reutilización de sesiones autenticadas.  
    - **MITM (Man-in-the-Middle)**: Interceptación y manipulación de datos.

    ### 🛡 **Defensa Sugerida**  
    - Uso de **TLS** (Transport Layer Security).  
    - Autenticación robusta y renovada.  
  </details>
</div>

---

## 🔐 **6. Capa de Presentación**  
<div class="accordion">
  <details>
    <summary>🔐 **Conversión y Cifrado de Datos**</summary>
    Maneja la **transformación de datos** y su cifrado para proteger la integridad.

    ### 🔍 **Amenazas**  
    - **SSL Stripping**: Degradación de conexiones seguras.  
    - **Data Manipulation**: Alteración del formato y codificación.

    ### 🛡 **Defensa Sugerida**  
    - Implementar **TLS/SSL actualizado**.  
    - Validación estricta de certificados digitales.  
  </details>
</div>

---

## 🌍 **7. Capa de Aplicación**  
<div class="accordion">
  <details>
    <summary>🌐 **Servicios al Usuario Final**</summary>
    Administra los servicios más visibles como **HTTP, FTP y SMTP**.

    ### 🔍 **Amenazas**  
    - **SQL Injection**: Ejecución de comandos maliciosos.  
    - **Cross-Site Scripting (XSS)**: Scripts no autorizados en navegadores.  
    - **DDoS Attacks**: Saturación de servicios.

    ### 🛡 **Defensa Sugerida**  
    - Configurar un **WAF (Web Application Firewall)**.  
    - Validar entradas de usuarios y proteger contra **DDoS**.  
  </details>
</div>

</div> <!-- End Interactive Container -->

---

## 🎯 **Resumen Visual** {: .fs-7 .fw-700 .text-purple-200}

| **Capa**             | **Amenazas Clave**                    | **Defensas Principales**         |
|:---------------------|:-------------------------------------|:---------------------------------|
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

[🔒 **Explora más sobre Seguridad**](#){: .btn .btn-blue .mt-4}  
[🌐 **Comparte esta guía**](#){: .btn .btn-outline .mt-4}

---

<div style="text-align: center;">
  <img src="/assets/images/cojo.png" alt="Firma" style="max-width: 20%; border-radius: 50%; box-shadow: 0 12px 24px rgba(0, 0, 0, 0.5);">
</div>


