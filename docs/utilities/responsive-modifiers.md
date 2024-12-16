---
title: 🛡️ Shodan  
parent: Supervivencia Sin Esfuerzo  
priority: 10  
---

# 🛡️ **Shodan Cheat Sheet**  
{: .fs-8 .fw-800 .text-cyan-300 .text-center .mt-8}

**Domina Shodan para explorar sistemas conectados y detectar vulnerabilidades críticas.**  
{: .fs-5 .text-grey-200 .text-center .mt-2}

Guía definitiva para **profesionales de ciberseguridad**, **pentesters** e investigadores.  
{: .fs-6 .text-grey-400 .text-center}

---

## 📊 **¿Qué es Shodan?**  
{: .fs-6 .fw-700 .text-grey-100 .mt-6}

**Shodan** es un motor de búsqueda que indexa dispositivos conectados a Internet, identificando servicios expuestos, banners de aplicaciones, puertos abiertos y más. Es una herramienta indispensable para auditar la seguridad de infraestructura crítica.  

### **Características principales:**  
- Localiza **dispositivos vulnerables** en tiempo real.  
- Analiza configuraciones incorrectas o servicios inseguros.  
- Identifica tecnologías implementadas en sistemas remotos.  

> 💡 **Tip:** Combina búsquedas avanzadas para un análisis más preciso.  

---

## 🗺️ **Búsqueda por Ubicación**  
{: .text-yellow-300 .fw-600 .mt-6}

<details class="border rounded-lg shadow-sm my-4 p-4 bg-grey-800">
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
</details>

---

## 💻 **Direcciones IP y Subredes**  
{: .text-green-300 .fw-600 .mt-6}

<details class="border rounded-lg shadow-sm my-4 p-4 bg-grey-800">
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
{: .text-orange-300 .fw-600 .mt-6}

<details class="border rounded-lg shadow-sm my-4 p-4 bg-grey-800">
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
{: .text-blue-300 .fw-600 .mt-6}

<details class="border rounded-lg shadow-sm my-4 p-4 bg-grey-800">
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

## 📄 **Resumen Visual**  
{: .fs-6 .fw-800 .text-grey-100 .mt-6}

| **Filtro**              | **Ejemplo**                 | **Uso Común**                              |
|--------------------------|-----------------------------|--------------------------------------------|
| **País**                | `country:"US"`             | Dispositivos en Estados Unidos             |
| **Puerto**              | `port:"443"`               | Servicios HTTPS                            |
| **Producto**            | `product:"nginx"`          | Servidores con nginx                       |
| **Sistema Operativo**   | `os:"Windows Server 2019"` | Dispositivos con Windows                   |
| **Vulnerabilidad CVE**  | `vuln:"CVE-2022-12345"`    | Detecta dispositivos con vulnerabilidades  |

---

![Shodan Cheat Sheet](/assets/images/shodan.jpeg){: .text-center .rounded-lg .shadow-lg .my-6}  
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

[🔍 Explora Shodan](https://www.shodan.io){: .btn .btn-blue .my-4}  
[💬 Comparte esta guía](#){: .btn .btn-outline .my-4}  

<div class="text-center">
  <img src="/assets/images/cojo.png" alt="Firma" class="rounded-full shadow-lg my-6" style="max-width: 15%;">
</div>
