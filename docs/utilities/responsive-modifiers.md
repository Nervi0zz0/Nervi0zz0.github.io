---
title: 🛡️ Shodan Cheat Sheet
description: Una referencia completa para dominar Shodan y descubrir dispositivos conectados y vulnerabilidades.
parent: Supervivencia Sin Esfuerzo
priority: 10
---

# 🛡️ **Shodan Cheat Sheet** {: .fs-8 .fw-700 .text-cyan-300 .text-center}

**Domina Shodan para descubrir sistemas expuestos y vulnerabilidades en Internet.**  
Guía esencial para **profesionales de ciberseguridad** y **pentesters**.  
{: .fs-5 .text-grey-200 .text-center}

---

## 📊 **¿Qué es Shodan?**  
{: .fs-6 .fw-500 .text-grey-100}

Shodan es un **motor de búsqueda** que escanea dispositivos conectados a Internet, mostrando **servicios, banners y ubicaciones**.  
Permite encontrar desde servidores hasta cámaras IP.

---

## 🗺️ **Búsqueda por Ubicación**  
{: .text-yellow-300 .fw-600}

<details>
<summary class="hover-underline">🗺️ **Filtra por País, Ciudad y Coordenadas**</summary>

### 🔍 **Ejemplos Prácticos:**
- **País:** `country:"US"`  
- **Ciudad:** `city:"New York"`  
- **Código Postal:** `postal:"92127"`  
- **Coordenadas GPS:**
    ```sh
    geo:"40.759487,-73.978356"
    geo:"40.759487,-73.978356,2"
    ```

💡 **Consejo:** Utiliza coordenadas precisas para descubrir dispositivos cercanos.
</details>

---

## 💻 **Direcciones IP & Subredes**  
{: .text-green-300 .fw-600}

<details>
<summary class="hover-underline">💻 **Filtra por IP, Hostnames y Proveedores**</summary>

### 🔍 **Ejemplos Básicos:**
- **IP Individual:** `52.179.197.205`  
- **Hostname:** `hostname:"microsoft.com"`  
- **Subred:** `net:"52.179.0.0/24"`  
- **Puerto Específico:**
    ```sh
    port:"21"
    ```
- **Proveedor ISP:** `isp:"Spectrum"`  
- **Sistema Autónomo ASN:** `asn:"AS8075"`

> **Nota:** Combina múltiples filtros para resultados específicos.
</details>

---

## 🖥️ **Sistemas Operativos y Productos**  
{: .text-orange-300 .fw-600}

<details>
<summary class="hover-underline">🖥️ **Encuentra Sistemas por OS y Dispositivos**</summary>

### 🔍 **Ejemplos Comunes:**
- **Sistema Operativo:** `os:"Windows Server 2008"`  
- **Organización:** `org:"Microsoft"`  
- **Producto Específico:**
    ```sh
    product:"Cisco C3550 Router"
    ```
- **Categorías:** `category:"ics"` o `category:"malware"`  
- **SMB y Carpetas:**
    ```sh
    port:"445" "shares"
    ```

⚠️ **Importante:** Busca **dispositivos vulnerables** filtrando categorías específicas.
</details>

---

## 🌐 **Aplicaciones Web**  
{: .text-blue-300 .fw-600}

<details>
<summary class="hover-underline">🌐 **Encuentra Servicios Web y SSL**</summary>

### 🔍 **Ejemplos Avanzados:**
- **Título HTML:** `title:"Index of /ftp"`  
- **Cuerpo HTML:** `html:"XML-RPC server accepts"`  
- **Tecnologías Web:**
    ```sh
    http.component:"php"
    ```
- **SSL/TLS Inseguro:**
    ```sh
    ssl.version:"ssl3"
    ssl.cert.expired:"true"
    ```

💡 **Tip:** Identifica configuraciones **inseguras** para priorizar análisis.
</details>

---

## ⏰ **Filtros Temporales y Visuales**  
{: .text-purple-300 .fw-600}

<details>
<summary class="hover-underline">⏰ **Búsqueda por Fecha y Capturas de Pantalla**</summary>

### 🔍 **Por Fecha:**
- **Después de:** `after:"01/01/18"`  
- **Antes de:** `before:"12/31/17"`

### 🖼️ **Capturas de Pantalla:**
- **Pantalla Disponible:**
    ```sh
    port:"80" has_screenshot:"true"
    ```
- **Específico Windows:**
    ```sh
    port:"3389" has_screenshot:"true"
    ```

🔍 **Recomendación:** Las capturas visuales ofrecen **información clave** sobre dispositivos expuestos.
</details>

---

## 🔒 **Acceso Premium & Vulnerabilidades**  
{: .text-red-300 .fw-600}

<details>
<summary class="hover-underline">🔒 **Accede a Vulnerabilidades (CVE)**</summary>

### 🔍 **Filtros Premium:**
- **Buscar Vulnerabilidades:** `vuln:"CVE-2017-0143"`  
- **Tags Específicos:**
    ```sh
    tag:"ics"
    tag:"database"
    ```

⚠️ **Atención:** Acceder a estas búsquedas requiere una cuenta premium.
</details>

---

## 📄 **Resumen Visual**  
{: .fs-6 .fw-700 .text-grey-100}

| **Filtro**            | **Ejemplo**                 | **Descripción**                     |
|------------------------|-----------------------------|---------------------------------------|
| **País**              | `country:"US"`             | Dispositivos en Estados Unidos        |
| **Coordenadas**       | `geo:"40.7,-74"`           | Ubicación geográfica específica       |
| **Producto**          | `product:"Apache"`         | Servidores Apache                     |
| **Puerto**            | `port:"22"`                | Filtra servicios SSH                  |
| **SSL Expirado**      | `ssl.cert.expired:"true"`  | Certificados vencidos                 |
| **Vulnerabilidad CVE**| `vuln:"CVE-2021-34527"`    | Dispositivos vulnerables detectados   |

---

![Shodan Cheat Sheet](/assets/images/shodan.jpeg){: .text-center .rounded-lg .shadow-lg .mt-4}  
*Referencia visual para tus búsquedas.*  
{: .fs-6 .text-grey-200 .text-center}

---

## 🎯 **¿Por qué usar Shodan?**  

Shodan es **crucial** para descubrir:  
- Recursos **expuestos** (cámaras, servidores, routers).  
- **Vulnerabilidades conocidas** mediante CVE.  
- **Infraestructura crítica** que necesita atención.  

Es una herramienta vital para **pentesters, investigadores y equipos de respuesta** en ciberseguridad.

---

[🔍 Explora Shodan](https://www.shodan.io){: .btn .btn-blue .mt-4}  
[💬 Comparte esta guía](#){: .btn .btn-outline .mt-4}  

<div class="text-center">
  <img src="/assets/images/cojo.png" alt="Firma" class="rounded-full shadow-lg" style="max-width: 15%;">
</div>
