---
title: 🛡️ Shodan
parent: Supervivencia Sin Esfuerzo
priority: 10
---

# 🛡️ **Shodan Cheat Sheet** {: .fs-8 .fw-700 .text-blue-300 .text-center}

**Domina Shodan para descubrir sistemas expuestos y vulnerabilidades en Internet.**  
Una guía imprescindible para **profesionales de ciberseguridad** y **pentesters**.  
{: .fs-5 .text-grey-dk-200 .text-center}

---

## 📊 **¿Qué es Shodan?**  
{: .fs-6 .fw-500 .text-grey-dk-100}

Shodan es un **motor de búsqueda** que escanea dispositivos conectados a Internet, mostrando **servicios, banners y ubicaciones**.  
Permite encontrar desde servidores hasta cámaras IP.

---

## 🗺️ **Búsqueda por Ubicación**  
<div class="accordion">
  <details>
    <summary>🗺️ **Filtra por País, Ciudad y Coordenadas**</summary>

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
</div>

---

## 💻 **Direcciones IP & Subredes**  
<div class="accordion">
  <details>
    <summary>💻 **Filtra por IP, Hostnames y Proveedores**</summary>

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
</div>

---

## 🖥️ **Sistemas Operativos y Productos**  
<div class="accordion">
  <details>
    <summary>🖥️ **Encuentra Sistemas por OS y Dispositivos**</summary>

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
</div>

---

## 🌐 **Aplicaciones Web**  
<div class="accordion">
  <details>
    <summary>🌐 **Encuentra Servicios Web y SSL**</summary>

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
</div>

---

## ⏰ **Filtros Temporales y Visuales**  
<div class="accordion">
  <details>
    <summary>⏰ **Búsqueda por Fecha y Capturas de Pantalla**</summary>

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
</div>

---

## 🔒 **Acceso Premium & Vulnerabilidades**  
<div class="accordion">
  <details>
    <summary>🔒 **Accede a Vulnerabilidades (CVE)**</summary>

### 🔍 **Filtros Premium:**  
- **Buscar Vulnerabilidades:** `vuln:"CVE-2017-0143"`  
- **Tags Específicos:**
    ```sh
    tag:"ics"
    tag:"database"
    ```

⚠️ **Atención:** Acceder a estas búsquedas requiere una cuenta premium.
  </details>
</div>

---

## 📄 **Resumen Visual**  

| **Filtro**            | **Ejemplo**                 | **Descripción**                     |
|------------------------|----------------------------|-------------------------------------|
| **País**              | `country:"US"`             | Dispositivos en Estados Unidos      |
| **Coordenadas**       | `geo:"40.7,-74"`           | Ubicación geográfica específica     |
| **Producto**          | `product:"Apache"`         | Servidores Apache                   |
| **Puerto**            | `port:"22"`                | Filtra servicios SSH                |
| **SSL Expirado**      | `ssl.cert.expired:"true"`  | Certificados vencidos               |
| **Vulnerabilidad CVE**| `vuln:"CVE-2021-34527"`    | Dispositivos vulnerables detectados |

---

![Shodan Cheat Sheet](/assets/images/shodan.jpeg){: .text-center .rounded-lg .mt-4}  
*Referencia visual para tus búsquedas.*  
{: .fs-6 .text-grey-dk-200 .text-center}

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

<div style="text-align: center;">
  <img src="/assets/images/cojo.png" alt="Firma" style="max-width: 15%; border-radius: 50%; box-shadow: 0 12px 24px rgba(0, 0, 0, 0.3);">
</div>
