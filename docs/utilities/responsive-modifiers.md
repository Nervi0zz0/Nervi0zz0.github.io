---
title: 🛡️ Shodan: Guía Técnica Definitiva  
description: Una referencia exhaustiva para profesionales de ciberseguridad que buscan dominar Shodan y descubrir vulnerabilidades en dispositivos conectados.  
parent: Supervivencia Sin Esfuerzo  
priority: 10  
---

# 🛡️ **Shodan Cheat Sheet**  
{: .fs-8 .fw-800 .text-cyan-300 .text-center}

**Explora el panorama de dispositivos conectados y servicios expuestos en Internet con Shodan.**  
Una guía técnica indispensable para **analistas de ciberseguridad**, **pentesters** e investigadores.  
{: .fs-5 .text-grey-200 .text-center}

---

## 📊 **Introducción a Shodan**  
{: .fs-6 .fw-600 .text-grey-100}

**Shodan** es un **motor de búsqueda especializado** que permite descubrir dispositivos conectados a Internet, identificando **servicios, banners, puertos abiertos** y más. Desde cámaras IP hasta servidores críticos, Shodan es una herramienta vital para el análisis de exposición y seguridad.  

### **Características principales:**  
- Descubre **infraestructura crítica** en riesgo.  
- Identifica **vulnerabilidades activas** mediante CVEs.  
- Explora servicios y tecnologías implementadas en sistemas conectados.

> 💡 **Tip:** Shodan puede revelar configuraciones inseguras en redes y dispositivos.  

---

## 🗺️ **Búsquedas Geolocalizadas**  
{: .text-yellow-300 .fw-600}

<details>
<summary class="hover-underline">🌍 **Filtrar por País, Ciudad y Coordenadas**</summary>

### 🔍 **Ejemplos de búsqueda:**  
- **País específico:** `country:"US"`  
- **Ciudad:** `city:"San Francisco"`  
- **Código Postal:** `postal:"90210"`  
- **Coordenadas GPS:**  
    ```sh
    geo:"37.7749,-122.4194"
    geo:"37.7749,-122.4194,5"
    ```

💡 **Consejo:** Las coordenadas permiten un análisis granular, útil para mapear activos expuestos en ubicaciones específicas.  
</details>

---

## 💻 **Direcciones IP y Subredes**  
{: .text-green-300 .fw-600}

<details>
<summary class="hover-underline">🔎 **Explora IPs, Hostnames y Proveedores**</summary>

### 🔍 **Búsquedas avanzadas:**  
- **IP específica:** `52.179.197.205`  
- **Hostname:** `hostname:"example.com"`  
- **Subred:** `net:"192.168.0.0/24"`  
- **Puerto activo:**  
    ```sh
    port:"80"
    ```  
- **Proveedor ISP:** `isp:"Google"`  
- **Sistema Autónomo (ASN):** `asn:"AS15169"`

> 🔐 **Pro Tip:** Combina estos filtros con palabras clave para obtener resultados más detallados.  
</details>

---

## 🖥️ **Sistemas Operativos y Dispositivos**  
{: .text-orange-300 .fw-600}

<details>
<summary class="hover-underline">🖥️ **Identifica Sistemas por OS, Organizaciones y Productos**</summary>

### 🔍 **Filtros útiles:**  
- **Sistema Operativo:** `os:"Linux"`  
- **Organización:** `org:"Amazon"`  
- **Producto específico:**  
    ```sh
    product:"OpenSSH 7.4"
    ```  
- **Categorías predefinidas:** `category:"ics"` o `category:"webcam"`  
- **Carpetas compartidas (SMB):**  
    ```sh
    port:"445" "shares"
    ```  

⚠️ **Nota:** La búsqueda por categoría es útil para identificar dispositivos críticos como ICS o cámaras expuestas.  
</details>

---

## 🌐 **Aplicaciones Web y SSL**  
{: .text-blue-300 .fw-600}

<details>
<summary class="hover-underline">🌐 **Descubre Servicios Web y Certificados Inseguros**</summary>

### 🔍 **Filtros relevantes:**  
- **Título de página HTML:** `title:"Index of /admin"`  
- **Cuerpo HTML:** `html:"Welcome to nginx"`  
- **Tecnología web:**  
    ```sh
    http.component:"nginx"
    ```  
- **SSL/TLS inseguro:**  
    ```sh
    ssl.version:"tls1.0"
    ssl.cert.expired:"true"
    ```  

💡 **Tip avanzado:** Identifica configuraciones SSL/TLS débiles para priorizar acciones correctivas.  
</details>

---

## ⏰ **Búsquedas Temporales y Capturas**  
{: .text-purple-300 .fw-600}

<details>
<summary class="hover-underline">⏰ **Filtrar por Tiempo y Visualización**</summary>

### 🔍 **Filtrando por fechas:**  
- **Después de una fecha específica:** `after:"2023-01-01"`  
- **Antes de una fecha:** `before:"2022-12-31"`  

### 🖼️ **Capturas de Pantalla:**  
- **Servicios con capturas:**  
    ```sh
    has_screenshot:"true"
    ```  
- **Pantallas RDP específicas:**  
    ```sh
    port:"3389" has_screenshot:"true"
    ```  

💡 **Consejo:** Las capturas son una herramienta visual poderosa para identificar configuraciones expuestas.  
</details>

---

## 🔒 **Vulnerabilidades (CVE) y Tags Premium**  
{: .text-red-300 .fw-600}

<details>
<summary class="hover-underline">🛡️ **Filtra Vulnerabilidades Conocidas**</summary>

### 🔍 **Accediendo a CVEs:**  
- **Vulnerabilidad específica:** `vuln:"CVE-2021-44228"`  
- **Tags avanzados:**  
    ```sh
    tag:"database"
    tag:"ics"
    ```  

⚠️ **Importante:** Algunos filtros requieren una suscripción premium de Shodan.  
</details>

---

## 📄 **Resumen de Filtros Comunes**  
{: .fs-6 .fw-700 .text-grey-100}

| **Filtro**              | **Ejemplo**                  | **Uso Común**                              |
|--------------------------|------------------------------|--------------------------------------------|
| **País**                | `country:"US"`              | Dispositivos en Estados Unidos             |
| **Puerto**              | `port:"443"`                | Servicios HTTPS                            |
| **Producto**            | `product:"nginx"`           | Servidores web con nginx                   |
| **Sistema Operativo**   | `os:"Windows 10"`           | Dispositivos con Windows 10                |
| **Certificado Vencido** | `ssl.cert.expired:"true"`   | Detecta certificados TLS/SSL expirados     |
| **Vulnerabilidad CVE**  | `vuln:"CVE-2023-12345"`     | Dispositivos afectados por CVEs específicos|

---

![Shodan Cheat Sheet](../assets/images/shodan-cheat-sheet.png){: .text-center .rounded-lg .shadow-lg .mt-4}  
*Representación visual de los filtros más utilizados.*  
{: .fs-6 .text-grey-200 .text-center}

---

## 🎯 **Por qué Usar Shodan**  

Shodan es una herramienta crítica para la ciberseguridad, permitiendo:  
- Identificar **recursos expuestos** como cámaras, servidores o routers.  
- Localizar **vulnerabilidades activas** en infraestructura conectada.  
- Mapear **activos críticos** para reforzar su seguridad.  

> **Ideal para:** Analistas de ciberseguridad, pentesters e investigadores de amenazas.  

---

[🔍 Explora Shodan](https://www.shodan.io){: .btn .btn-blue .mt-4}  
[📤 Comparte esta guía](#){: .btn .btn-outline .mt-4}  

<div class="text-center">
  <img src="../assets/images/signature.png" alt="Firma" class="rounded-full shadow-lg" style="max-width: 15%;">
</div>
