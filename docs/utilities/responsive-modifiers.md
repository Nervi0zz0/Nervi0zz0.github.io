---
title: Shodan
parent: Supervivencia Sin Esfuerzo
priority: 10
---

# 🛡 **Shodan Cheat Sheet** {: .fs-8 .fw-700 .text-blue-300}

### 📊 **¿Qué es Shodan?** {: .fs-6 .fw-500 .text-grey-dk-100}

Shodan es un **motor de búsqueda** público que escanea dispositivos conectados a Internet y muestra servicios, banners y ubicaciones relacionadas. Es una herramienta esencial en **ciberseguridad** para descubrir sistemas expuestos.

---

## 🗺 **Búsqueda por Ubicación Física** {: .fs-6 .fw-500 .text-yellow-300}

Shodan permite buscar dispositivos por **ubicación**:
- **País:** `country:"US"`
- **Ciudad:** `city:"New York"`
- **Estado/Región:** `state:"NY"` o `region:"NY"`
- **Código Postal:** `postal:"92127"`
- **Coordenadas GPS:**
    ```sh
    geo:"40.759487,-73.978356"
    geo:"40.759487,-73.978356,2"
    ```

{: .highlight }
### 💡 **Consejo:** Utiliza coordenadas precisas para una búsqueda más específica.

---

## 💻 **Direcciones IP & Subredes** {: .fs-6 .fw-500 .text-green-300}

🔍 **Ejemplos básicos:**
- **IP individual:** `52.179.197.205`
- **Hostname:** `hostname:"microsoft.com"`
- **Subred:** `net:"52.179.0.0/24"`
- **Puerto específico:**
    ```sh
    port:"21"
    ```
- **Proveedores ISP:** `isp:"Spectrum"`
- **Sistema Autónomo ASN:** `asn:"AS8075"`

{: .note-title }
> **Nota:**
> Puedes combinar filtros para obtener resultados más específicos.

---

## 🖥 **Sistemas Operativos y Productos** {: .fs-6 .fw-500 .text-red-200}

🔎 **Operativos y versiones específicas:**
- **Sistema Operativo:** `os:"Windows Server 2008"`
- **Organización/Empresa:** `org:"Microsoft"`
- **Producto:**
    ```sh
    product:"Cisco C3550 Router"
    ```
- **Categorías de Shodan:**
    ```sh
    category:"ics" o category:"malware"
    ```
- **SMB específico:** `smb:"1" o smb:"2"`
- **Carpetas Compartidas:**
    ```sh
    port:"445" "shares"
    ```

{: .important }
### ⚠️ **Importante:** Las búsquedas de categorías pueden revelar dispositivos altamente vulnerables.

---

## 🌐 **Aplicaciones Web** {: .fs-6 .fw-500 .text-blue-200}

🔍 **Ejemplos de búsquedas avanzadas en web:**
- **Título HTML:** `title:"Index of /ftp"`
- **Cuerpo HTML:** `html:"XML-RPC server accepts"`
- **Tecnologías web específicas:**
    ```sh
    http.component:"php"
    ```
- **SSL/TLS:**
    ```sh
    ssl.version:"ssl3" o ssl.version:"tlsv1.1"
    ssl.cert.expired:"true"
    ```

{: .note }
**Tip:** Filtra por versiones específicas de SSL/TLS para encontrar dispositivos con configuraciones inseguras.

---

## ⏰ **Filtros de Tiempo y Otros** {: .fs-6 .fw-500 .text-grey-200}

🔎 **Buscar por fechas:**
- **Después de:** `after:"01/01/18"`
- **Antes de:** `before:"12/31/17"`

🔎 **Buscar capturas de pantalla:**
- **Pantalla disponible:**
    ```sh
    port:"80" has_screenshot:"true"
    ```
- **Específico para Windows:**
    ```sh
    port:"3389" has_screenshot:"true"
    ```

{: .important }
### 🔍 **Recomendación:** Las capturas de pantalla pueden proporcionar información visual valiosa sobre dispositivos expuestos.

---

## 🔒 **Acceso Limitado** {: .fs-6 .fw-500 .text-purple-300}

Para cuentas premium:
- **Vulnerabilidades (CVE):**
    ```sh
    vuln:"CVE-2017-0143"
    ```
- **Tags específicos:**
    ```sh
    tag:"ics" o tag:"database"
    ```

{: .warning }
### ⚠️ **Atención:** Acceso a información sensible requiere cuenta premium.

---

## 🖼 **Shodan Cheat Sheet - Visual** {: .fs-6 .fw-500 .text-blue-300}

![Shodan Cheat Sheet](shodan.jpeg)
*Referencia rápida para tus búsquedas con Shodan.*
{: .text-center .mt-4}

---

### 🎯 **¿Por qué es importante?** {: .fs-5 .fw-400 .text-grey-dk-200}

Shodan permite descubrir vulnerabilidades y **recursos expuestos** en redes y servidores. Es una herramienta vital para **pentesters, investigadores** y **profesionales de ciberseguridad**.

---

[🔍 Explora Shodan](https://www.shodan.io){: .btn .btn-blue .mt-4}  
[💬 Comparte esta guía](#){: .btn .btn-outline .mt-4}
