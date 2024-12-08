---
layout: page
title: 🛡️ Detección de Phishing
description: Consejos y recursos
dropdown: Notas de un Cojo
priority: 4
---
# 🛡️ **Guía Técnica para el Análisis Forense de Cabeceras de Correo: Detección de Phishing 

## **Introducción**

La detección de **phishing** y **suplantación de identidad** (spoofing) es una de las principales amenazas a las que se enfrentan los equipos de **Blue Team**. Estos ataques pueden comprometer tanto la seguridad de los usuarios como la infraestructura de la organización. Para detectar estos ataques, los **analistas de seguridad** deben ser capaces de realizar un análisis exhaustivo de las **cabeceras de los correos electrónicos**.

Esta guia está orientada para el analisis de las cabeceras de un correo y realizar un análisis técnico utilizando herramientas de fácil acceso. La detección de correos electrónicos fraudulentos es una habilidad esencial para prevenir brechas de seguridad, y una comprensión adecuada de cómo analizar cabeceras es el primer paso para desarrollar esta habilidad.

---

## **Paso 1: Obtener las Cabeceras del Correo Electrónico**

### ¿Por qué es importante extraer las cabeceras?

Las **cabeceras de los correos electrónicos** contienen información detallada sobre el **origen** del correo, los **servidores intermedios** por los que ha pasado, las **verificaciones de autenticación** (como SPF, DKIM y DMARC) y otros metadatos clave. Extraer correctamente las cabeceras es esencial para determinar la legitimidad de un correo y detectar posibles intentos de **suplantación de identidad**.

---

### **Cómo obtener las cabeceras del correo:**

#### **1.1 Gmail**
1. Abre el correo electrónico sospechoso.
2. Haz clic en los tres puntos en la esquina superior derecha del mensaje.
3. Selecciona **"Mostrar original"**. Se abrirá una ventana con las cabeceras completas del correo.

#### **1.2 Outlook**
1. Abre el correo en Outlook.
2. Haz clic en los tres puntos en la parte superior derecha del correo.
3. Selecciona **"Ver fuente del mensaje"**. Aquí podrás copiar las cabeceras.

#### **1.3 Yahoo**
1. Abre el correo electrónico.
2. Haz clic en los tres puntos en la esquina superior derecha.
3. Selecciona **"Ver encabezado completo"**.

#### **1.4 Thunderbird**
1. Haz clic derecho sobre el correo.
2. Selecciona **"Ver fuente del mensaje"**.

> **Consejo**: Las cabeceras suelen estar ocultas de forma predeterminada en los clientes de correo. Si no puedes verlas, consulta la documentación de tu cliente de correo para activarlas.

---

## **Paso 2: Análisis Forense de la Cabecera**

Una vez que tengas las cabeceras del correo, el siguiente paso es analizar los campos clave que indican si el correo es legítimo o un intento de **phishing** o **suplantación de identidad**.

Las cabeceras contienen múltiples campos que describen la ruta del correo desde su origen hasta su destino. Como analista de SOC, debes centrarte en los siguientes campos:

### **Campos Clave de la Cabecera:**

| **Campo**                   | **Descripción**                                                                                       | **Indicadores de Phishing/Spoofing**                                    |
|-----------------------------|-------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
| **From**                     | Dirección de correo electrónico del remitente.                                                        | Si el dominio no coincide con el esperado o tiene errores de escritura, puede ser un indicio de suplantación. |
| **Reply-To**                 | Dirección a la que se debe responder, a menudo diferente del campo "From".                             | Si es diferente, verifica si el dominio es legítimo.                    |
| **Return-Path**              | Dirección de correo para el rebote de mensajes no entregados.                                          | Si es diferente a "From" o "Reply-To", podría ser sospechoso.          |
| **Received**                 | Información sobre los servidores intermedios por los que pasó el correo.                               | Si el correo pasó por servidores no autorizados o desconocidos, puede indicar un intento de suplantación. |
| **X-Originating-IP**         | Dirección IP del servidor de origen del correo.                                                       | Si la IP es sospechosa o proviene de un país inesperado, realiza un **Whois** de la IP. |
| **X-Spam-Flag**              | Marca que indica si el correo ha sido clasificado como spam por el servidor de correo.                | Si es "YES", el correo podría estar asociado a actividades maliciosas. |
| **X-Authentication-Results** | Resultado de las autenticaciones SPF, DKIM, y DMARC.                                                   | Si alguna de las verificaciones falla, el correo podría ser fraudulento. |

> **Consejo**: Si el campo **Received** muestra múltiples servidores de correo no confiables o desconocidos, es un indicio claro de que el mensaje ha sido manipulado.

---

## **Paso 3: Verificación de SPF, DKIM y DMARC**

Las tecnologías de autenticación de correo electrónico son fundamentales para verificar la autenticidad de un mensaje. Los estándares **SPF**, **DKIM** y **DMARC** se utilizan para evitar el **phishing** y la **suplantación de identidad**.

### **¿Qué son SPF, DKIM y DMARC?**

- **SPF (Sender Policy Framework)**: Permite a los dominios autorizar servidores de correo electrónicos para enviar mensajes en su nombre. Un fallo en SPF indica que el correo proviene de un servidor no autorizado.
  
- **DKIM (DomainKeys Identified Mail)**: Proporciona una firma digital que autentica el correo y asegura que no ha sido alterado en tránsito.

- **DMARC (Domain-based Message Authentication, Reporting, and Conformance)**: Requiere que los correos electrónicos pasen las verificaciones SPF y DKIM antes de ser aceptados como legítimos.

---

### **Cómo verificar SPF, DKIM y DMARC:**

| **Tecnología** | **Descripción**                                                 | **Cómo Verificarla**                                                    |
|----------------|---------------------------------------------------------------|-------------------------------------------------------------------------|
| **SPF**        | Verifica si el correo proviene de un servidor autorizado.      | Utiliza herramientas como [MXToolbox](https://mxtoolbox.com) para verificar el registro SPF de un dominio. |
| **DKIM**       | Asegura que el correo no ha sido alterado en el camino.        | Verifica la firma DKIM utilizando [MXToolbox](https://mxtoolbox.com). |
| **DMARC**      | Asegura que el correo pasa las validaciones de SPF y DKIM.     | Usa [MXToolbox](https://mxtoolbox.com) para comprobar el registro DMARC de un dominio. |

> **Consejo**: Si un correo no pasa alguna de estas verificaciones, es muy probable que sea un intento de suplantación.

---

## **Paso 4: Análisis de Enlaces y Archivos Adjuntos**

### **4.1 Análisis de Enlaces Sospechosos**

El phishing a menudo utiliza **redirecciones maliciosas** que llevan al usuario a sitios fraudulentos. Los enlaces pueden estar disfrazados o ser acortados para ocultar la verdadera URL. Verificar estos enlaces es esencial.

#### **Herramientas para verificar enlaces:**

| **Herramienta**                | **Descripción**                                                                                     | **Cómo Usarla**                                                      |
|---------------------------------|-----------------------------------------------------------------------------------------------------|----------------------------------------------------------------------|
| **VirusTotal**                  | Permite verificar enlaces para detectar si están asociados con malware o phishing.                 | Copia y pega el enlace en [VirusTotal](https://www.virustotal.com). |
| **CheckShortURL**               | Expande enlaces acortados para ver la URL real antes de hacer clic.                                  | Visita [CheckShortURL](https://checkshorturl.com) y expande el enlace. |

> **Consejo**: Si un enlace redirige a un dominio que no está relacionado con la empresa o entidad legítima, desconfía.

---

### **4.2 Análisis de Archivos Adjuntos**

Los correos de phishing también pueden contener **archivos adjuntos** maliciosos (como .exe, .pdf, .docx) que pueden contener malware. Es importante analizar estos archivos en un entorno controlado.

#### **Herramientas de Análisis de Archivos Adjuntos:**

| **Herramienta**                | **Descripción**                                                                                     | **Cómo Usarla**                                                     |
|---------------------------------|-----------------------------------------------------------------------------------------------------|---------------------------------------------------------------------|
| **Cuckoo Sandbox**              | Analiza archivos en un entorno aislado para detectar comportamientos maliciosos.                    | Descarga e instala [Cuckoo Sandbox](https://cuckoosandbox.org) y sube los archivos para su análisis. |
| **Hybrid Analysis**             | Plataforma de análisis de malware que proporciona un informe detallado de los archivos en un entorno controlado. | Visita [Hybrid Analysis](https://www.hybrid-analysis.com), sube los archivos y revisa los informes. |

> **Consejo**: Nunca abras un archivo adjunto sospechoso sin antes analizarlo en un **sandbox**.

---

## **Paso 5: Detección de Suplantación de Identidad a Través de Whois**

Si tienes dudas sobre la legitimidad de un dominio de envío, puedes realizar una búsqueda **Whois** para obtener información sobre su propietario y verificar su autenticidad.

#### **Herramienta para realizar búsqueda Whois:**

| **Herramienta**               | **Descripción**                                                                                       | **Cómo Usarla**                                                     |
|-------------------------------|-------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------|
| **Whois**                      | Consulta la información de registro de un dominio para verificar si es legítimo.                      | Visita [Whois.net](https://www.whois.net) y busca el dominio sospechoso. |

> **Consejo**: Si el dominio de envío es reciente o no tiene información de registro válida, es una señal de alerta.

---

## **Paso 6: Observa**



1. **Revisar la Autenticidad de los Certificados SSL/TLS**: Si el correo incluye enlaces que conducen a sitios web, asegúrate de que esos sitios utilizan **certificados SSL/TLS** válidos (el icono de candado junto a la URL).
2. **Análisis de Comportamiento de Usuario**: Los correos de phishing a menudo intentan inducir a los usuarios a realizar acciones rápidas y sin pensarlo, como compartir contraseñas. Mantén siempre los **procedimientos de verificación** establecidos.
3. **Revisión de Errores Gramaticales**: Los correos fraudulentos a menudo contienen errores de gramática, tipografía y lenguaje. Presta atención a cualquier anomalía en el tono o estilo del mensaje.

---


