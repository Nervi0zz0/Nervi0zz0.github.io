---
title: 🛡️ Detectar y Analizar Intentos de Phishing
parent: Supervivencia Sin Esfuerzo
priority: 4
---

# 🛡️ **Guía Técnica para Detectar y Analizar Intentos de Phishing**

La **detección de phishing** es esencial para mantener la seguridad de los sistemas informáticos, proteger a los usuarios y mitigar riesgos organizacionales. En esta guía, aprenderás a **identificar correos fraudulentos** y a usar herramientas clave para analizar su legitimidad.

---

<div style="background-color: #2E3B4E; padding: 20px; text-align: center; border-radius: 8px; color: white; font-size: 28px; font-weight: bold;">
  🛡️ **Protégete del Phishing con Estrategias Efectivas**
</div>

---

## ✉️ **¿Qué es el Phishing?**

El **phishing** es un ataque cibernético que busca engañar a los usuarios para que proporcionen información confidencial (credenciales, datos bancarios, etc.) o realicen acciones perjudiciales, como descargar malware.

### **Características comunes de un ataque de phishing:**

- Enlaces sospechosos que redirigen a sitios falsificados.
- Solicitudes urgentes para ingresar información personal.
- Archivos adjuntos maliciosos.
- Correos provenientes de dominios o remitentes desconocidos.
- Contenido que genera **urgencia** o **miedo**.

{: .note }
**Nota**: Estar alerta a estos signos puede ayudarte a detectar un posible ataque de phishing.

---

## 🔍 **Análisis Forense de Correos Electrónicos**

El análisis de las **cabeceras de correos electrónicos** es crucial para detectar intentos de phishing. Aquí te explicamos cómo hacerlo.

### 🛠️ **Pasos para Obtener las Cabeceras del Correo:**

| **Cliente de Correo** | **Pasos para obtener cabeceras**                                                                 |
|-----------------------|--------------------------------------------------------------------------------------------------|
| **Gmail**             | Abre el correo > Haz clic en los tres puntos (⋮) > Selecciona **"Mostrar original"**.             |
| **Outlook**           | Abre el correo > Haz clic en los tres puntos (⋮) > Selecciona **"Ver fuente del mensaje"**.      |
| **Yahoo**             | Abre el correo > Haz clic en los tres puntos (⋮) > Selecciona **"Ver encabezado completo"**.      |
| **Thunderbird**       | Haz clic derecho sobre el correo > Selecciona **"Ver fuente del mensaje"**.                       |

{: .highlight }
**Consejo**: Al obtener las cabeceras, busca patrones extraños o inconsistentes en los valores de los campos. Esto puede ser un indicio de suplantación.

---

### 🛠️ **Campos Clave a Analizar:**

| **Campo**                   | **Descripción**                                                                                       | **Indicadores de Phishing/Spoofing**                                    |
|-----------------------------|-------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
| **From**                     | Dirección del remitente.                                                                             | Si el dominio es sospechoso o tiene errores tipográficos.               |
| **Reply-To**                 | Dirección para respuestas.                                                                          | Si es diferente al remitente, verifica su legitimidad.                  |
| **Received**                 | Ruta del correo por servidores.                                                                     | Si hay servidores desconocidos, revisa su confiabilidad.                |
| **X-Originating-IP**         | IP del servidor original.                                                                           | Realiza un análisis **Whois** si la IP parece sospechosa.               |
| **X-Authentication-Results** | Verificación SPF/DKIM/DMARC.                                                                         | Fallos en estas verificaciones son indicadores de suplantación.         |

> {: .important }
> **Importante**: Si encuentras fallos en las verificaciones de SPF/DKIM/DMARC, es un **fuerte indicio de phishing**. 

---

## 🔐 **Tecnologías de Autenticación: SPF, DKIM y DMARC**

Para identificar correos legítimos, los servidores de correo utilizan tres tecnologías clave:

1. **SPF (Sender Policy Framework):** Confirma que el correo proviene de un servidor autorizado por el dominio.
2. **DKIM (DomainKeys Identified Mail):** Garantiza que el contenido del correo no ha sido modificado durante el tránsito.
3. **DMARC (Domain-Based Message Authentication, Reporting, and Conformance):** Combina SPF y DKIM para validar la autenticidad del correo.

### 🌍 **Cómo Funciona DMARC**

![Cómo Funciona DMARC](1734322748523.gif)

{: .callout-note }
**Nota**: El protocolo DMARC ayuda a evitar la suplantación de dominios, aplicando una política de **rechazo, cuarentena o entrega** según los resultados de SPF y DKIM.

### **Ejemplo de DMARC en Acción**

Imagina que recibes un correo de **"banco-importante.com"**, pero su autenticación SPF y DKIM falla:

- **Resultado SPF:** Fallo (el servidor de origen no está en la lista autorizada).
- **Resultado DKIM:** Fallo (la firma del mensaje no coincide).
- **Política DMARC:** **Rechazar**.

> Resultado: El correo es rechazado o marcado como spam, protegiendo al usuario.

| **Herramienta**           | **Función**                              | **Enlace**                               |
|---------------------------|------------------------------------------|------------------------------------------|
| **MXToolbox**             | Verifica registros SPF/DKIM/DMARC.       | [MXToolbox](https://mxtoolbox.com)       |
| **DMARC Analyzer**        | Analiza políticas DMARC implementadas.   | [DMARC Analyzer](https://www.dmarcian.com) |

> {: .highlight }
> **Ejemplo práctico**: Si un correo falla en la autenticación DMARC, es probable que el dominio haya sido **suplantado**.

---

## 🛠️ **Herramientas de Análisis de Phishing**

Para facilitar el análisis, aquí tienes una lista de herramientas útiles:

| **Herramienta**           | **Descripción**                                                                                     |
|---------------------------|---------------------------------------------------------------------------------------------------|
| **VirusTotal**            | Analiza enlaces y archivos para detectar amenazas.                                               |
| **PhishTank**             | Base de datos comunitaria de URLs phishing reportadas.                                           |
| **AbuseIPDB**             | Identifica IPs maliciosas asociadas a actividades sospechosas.                                    |
| **CheckShortURL**         | Expande enlaces acortados para comprobar su legitimidad.                                         |
| **Cuckoo Sandbox**        | Analiza archivos en un entorno aislado para detectar comportamientos maliciosos.                |
| **Microsoft SmartScreen** | Filtro integrado en productos de Microsoft para detectar correos fraudulentos.                  |
| **ThePhish**              | Herramienta open-source para automatizar el análisis de correos phishing.                       |
| **Mimecast Email Security** | Utiliza inteligencia artificial para filtrar correos maliciosos y proteger contra amenazas sofisticadas. |
| **URLScan.io**            | Escanea y analiza sitios web sospechosos en tiempo real.                                         |

---

## 🔒 **Mejores Prácticas para Protegerte del Phishing**

1. **Verifica siempre la dirección del remitente.**
2. **No hagas clic en enlaces sospechosos.**
3. **Evita descargar archivos de remitentes desconocidos.**
4. **Habilita autenticación en dos pasos (2FA) siempre que sea posible.**
5. **Educa a los usuarios sobre los riesgos del phishing.**
6. **Reporta correos sospechosos a tu proveedor de correo electrónico.**

{: .highlight }
**Sugerencia**: La autenticación de dos factores (2FA) es una capa adicional de seguridad que **redunda enormemente** en la protección contra ataques de phishing.

---

## 📂 **Recursos Adicionales**

- [PhishTank: Base de datos de phishing](https://www.phishtank.com)
- [Guía oficial de SPF](https://www.openspf.org)
- [Analizador de Cabeceras de Gmail](https://toolbox.googleapps.com/apps/messageheader/)
- [URLScan.io](https://urlscan.io)
- [MITRE ATT&CK: Técnicas de Phishing](https://attack.mitre.org/techniques/T1566/)

<hr style="border: none; border-top: 1px solidrgb(255, 254, 248); margin: 50px 0; box-shadow: 0 1px 2px rgba(255, 215, 0, 0.6);">

<div style="text-align: center; margin: 50px auto;">
  <img src="/assets/images/cojo.png" alt="Firma" style="max-width: 20%; border-radius: 50%; border: 1px solid #FFD700; box-shadow: 0 12px 24px rgba(0, 0, 0, 0.9);">
</div>
<div style="text-align: center; margin-top: 40px;">
  <p style="font-size: 0.9em; color: #888;">&copy; 2024 Nervi0zz0</p>
</div>
