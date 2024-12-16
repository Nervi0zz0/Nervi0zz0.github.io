---
title: 🛡️ Shodan 
description: Una referencia completa para dominar Shodan y descubrir dispositivos conectados, vulnerabilidades y configuraciones expuestas en Internet.  
parent: Supervivencia Sin Esfuerzo  
priority: 10  
---

# 🛡️ **Shodan Cheat Sheet**  
{: .fs-8 .fw-800 .text-cyan-300 .text-center}

**Domina Shodan para explorar sistemas conectados y detectar vulnerabilidades críticas.**  
La guía definitiva para **profesionales de ciberseguridad**, **pentesters** e investigadores.  
{: .fs-5 .text-grey-200 .text-center}

---

## 📊 **¿Qué es Shodan?**  
{: .fs-6 .fw-700 .text-grey-100}

**Shodan** es un motor de búsqueda que indexa dispositivos conectados a Internet, identificando servicios expuestos, banners de aplicaciones, puertos abiertos y más. Es una herramienta indispensable para auditar la seguridad de infraestructura crítica.  

### **Características principales:**  
- Localiza **dispositivos vulnerables** en tiempo real.  
- Analiza configuraciones incorrectas o servicios inseguros.  
- Identifica tecnologías implementadas en sistemas remotos.  

> 💡 **Tip:** Combina búsquedas avanzadas para un análisis más preciso.  

---

## 🗺️ **Búsqueda por Ubicación**  
{: .text-yellow-300 .fw-600}

<details>
<summary class="hover-underline">🗺️ **Filtra por País, Ciudad y Coordenadas**</summary>

### 🔍 **Filtros Prácticos:**  
- **Por País:** `country:"US"`  
- **Por Ciudad:** `city:"New York"`  
- **Por Código Postal:** `postal:"90210"`  
- **Coordenadas GPS:**  
    ```sh
    geo:"40.712776,-74.005974"
    geo:"40.712776,-74.005974,10"
    ```

> 💡 **Consejo:** Usa el filtro `geo` con precisión para identificar activos en ubicaciones específicas.  

---

## 💻 **Direcciones IP y Subredes**  
{: .text-green-300 .fw-600}

<details>
<summary class="hover-underline">💻 **Explora IPs, Hostnames y Proveedores**</summary>

### 🔍 **Búsquedas clave:**  
- **IP Individual:** `ip:"8.8.8.8"`  
- **Hostname:** `hostname:"example.com"`  
- **Subred:** `net:"192.168.0.0/24"`  
- **Por Puerto:**  
    ```sh
    port:"80"
    ```  
- **Proveedor ISP:** `isp:"Google LLC"`  
- **Sistema Autónomo (ASN):** `asn:"AS15169"`

> **Nota:** Combina filtros para afinar resultados.  
</details>

---

## 🖥️ **Sistemas Operativos y Productos**  
{: .text-orange-300 .fw-600}

<details>
<summary class="hover-underline">🖥️ **Encuentra Dispositivos por OS y Tecnologías**</summary>

### 🔍 **Filtros Avanzados:**  
- **Por Sistema Operativo:** `os:"Linux"`  
- **Organización:** `org:"Amazon"`  
- **Producto Específico:**  
    ```sh
    product:"Apache httpd 2.4.49"
    ```  
- **Por Categoría:**  
    ```sh
    category:"webcam"
    category:"ics"
    ```  
- **Carpetas Compartidas (SMB):**  
    ```sh
    port:"445" "shares"
    ```

⚠️ **Advertencia:** Los dispositivos de infraestructura crítica (ICS) suelen ser los más vulnerables.  
</details>

---

## 🌐 **Aplicaciones Web y Certificados**  
{: .text-blue-300 .fw-600}

<details>
<summary class="hover-underline">🌐 **Descubre Servicios Web y Configuraciones SSL/TLS**</summary>

### 🔍 **Búsquedas clave:**  
- **Título de Página Web:** `title:"Index of /"`  
- **Texto en HTML:** `html:"Welcome to nginx"`  
- **Tecnología Web Específica:**  
    ```sh
    http.component:"nginx"
    ```  
- **SSL/TLS inseguro:**  
    ```sh
    ssl.version:"tls1.0"
    ssl.cert.expired:"true"
    ```  

💡 **Consejo:** Busca configuraciones SSL/TLS débiles para priorizar correcciones.  
</details>

---

## ⏰ **Filtros Temporales y Capturas Visuales**  
{: .text-purple-300 .fw-600}

<details>
<summary class="hover-underline">⏰ **Filtra por Fecha y Visualiza Capturas**</summary>

### 🔍 **Filtros Temporales:**  
- **Después de una fecha:** `after:"2023-01-01"`  
- **Antes de una fecha:** `before:"2022-12-31"`  

### 🖼️ **Capturas de Pantalla:**  
- **Dispositivos con Capturas Disponibles:**  
    ```sh
    has_screenshot:"true"
    ```  
- **Pantallas RDP Específicas:**  
    ```sh
    port:"3389" has_screenshot:"true"
    ```  

💡 **Tip:** Las capturas de pantalla son útiles para identificar configuraciones visualmente expuestas.  
</details>

---

## 🔒 **Vulnerabilidades y Filtros Premium**  
{: .text-red-300 .fw-600}

<details>
<summary class="hover-underline">🔒 **Accede a Vulnerabilidades y Tags Premium**</summary>

### 🔍 **Filtros de Vulnerabilidad:**  
- **CVE Específico:** `vuln:"CVE-2021-44228"`  
- **Por Tag Avanzado:**  
    ```sh
    tag:"malware"
    tag:"database"
    ```  

⚠️ **Nota:** Algunos filtros avanzados requieren una cuenta premium.  
</details>

---

## 📄 **Resumen Visual**  
{: .fs-6 .fw-800 .text-grey-100}

| **Filtro**              | **Ejemplo**                 | **Uso Común**                              |
|--------------------------|-----------------------------|--------------------------------------------|
| **País**                | `country:"US"`             | Dispositivos en Estados Unidos             |
| **Puerto**              | `port:"443"`               | Servicios HTTPS                            |
| **Producto**            | `product:"nginx"`          | Servidores con nginx                       |
| **Sistema Operativo**   | `os:"Windows Server 2019"` | Dispositivos con Windows                   |
| **Vulnerabilidad CVE**  | `vuln:"CVE-2022-12345"`    | Detecta dispositivos con vulnerabilidades  |

---

![Shodan Cheat Sheet](/assets/images/shodan.jpeg){: .text-center .rounded-lg .shadow-lg .mt-4}  
*Guía visual de los filtros más importantes de Shodan.*  
{: .fs-6 .text-grey-200 .text-center}

---

## 🎯 **¿Por qué usar Shodan?**  

Shodan es una herramienta **esencial** en ciberseguridad para:  
- Identificar **recursos expuestos** (cámaras, servidores, routers).  
- Localizar **vulnerabilidades activas**.  
- Mapear infraestructura crítica conectada a Internet.  

Es una herramienta imprescindible para **equipos de respuesta, pentesters y analistas de seguridad**.  

---

[🔍 Explora Shodan](https://www.shodan.io){: .btn .btn-blue .mt-4}  
[💬 Comparte esta guía](#){: .btn .btn-outline .mt-4}  

<div class="text-center">
  <img src="/assets/images/cojo.png" alt="Firma" class="rounded-full shadow-lg" style="max-width: 15%;">
</div>
