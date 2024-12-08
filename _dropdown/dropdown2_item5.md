---
layout: page
title: 🛡️ Microsoft Sentinel
description: Consejos y recursos
dropdown: Notas Secretas del SOC
priority: 4
---


# 🔍 **Guía en Microsoft Sentinel** 🔐

## **Introducción**

**Microsoft Sentinel** es una plataforma SIEM (Security Information and Event Management) que permite a los equipos de seguridad detectar, investigar y responder a amenazas en tiempo real. El lenguaje de consultas **Kusto Query Language (KQL)** es fundamental para analizar los datos de seguridad. Este cheatsheet te ayudará a utilizar **KQL** de manera eficiente para realizar búsquedas complejas y detectar incidentes de seguridad en un entorno corporativo.

En esta guía, cubrimos **consultas avanzadas** de **KQL** que puedes usar para analizar **eventos de seguridad**, **detectores de intrusión**, **actividades sospechosas** y mucho más. Está dirigido a analistas de seguridad que utilizan **Microsoft Sentinel**.

---

## **1. Consultas Básicas de KQL para Monitoreo de Seguridad**

### **1.1 Buscar Eventos de Inicio de Sesión Fallidos (Evento 4625)**

La detección de **intentos fallidos de inicio de sesión** es esencial para identificar posibles **ataques de fuerza bruta**.

| **Comando** | **Explicación** |
|-------------|-----------------|
| ```kql | SecurityEvent | where EventID == 4625 | project TimeGenerated, Account, Computer, FailureReason | order by TimeGenerated desc``` | Este comando filtra los eventos **4625**, que indican intentos fallidos de inicio de sesión. Muestra la hora del evento, la cuenta, la computadora y la razón del fallo. Los resultados se ordenan por la hora de generación del evento. |

---

### **1.2 Buscar Inicios de Sesión Exitosos (Evento 4624)**

El monitoreo de **inicios de sesión exitosos** te ayuda a identificar accesos a tu red por parte de usuarios autorizados.

| **Comando** | **Explicación** |
|-------------|-----------------|
| ```kql | SecurityEvent | where EventID == 4624 | where TimeGenerated > ago(1d) | project TimeGenerated, Account, Computer | order by TimeGenerated desc``` | Filtra los eventos de **inicio de sesión exitoso (4624)** y limita la búsqueda a los últimos 24 horas. Los resultados incluyen la hora, la cuenta y la computadora. |

---

## **2. Detección de Actividades Sospechosas y Anomalías**

### **2.1 Buscar IPs de Origen con Múltiples Intentos Fallidos de Ingreso**

Los **ataques de fuerza bruta** a menudo involucran múltiples intentos fallidos de inicio de sesión desde una misma IP.

| **Comando** | **Explicación** |
|-------------|-----------------|
| ```kql | SecurityEvent | where EventID == 4625 | summarize FailedAttempts = count() by SourceIP, bin(TimeGenerated, 5m) | where FailedAttempts > 5 | order by FailedAttempts desc``` | Este comando agrupa los eventos fallidos por **IP de origen** y los resume en intervalos de **5 minutos**. Si hay más de 5 intentos fallidos, se genera una alerta. |

---

### **2.2 Análisis de Inicios de Sesión en Horas Inusuales**

Los inicios de sesión fuera del horario laboral pueden ser indicativos de un compromiso de seguridad o acceso no autorizado.

| **Comando** | **Explicación** |
|-------------|-----------------|
| ```kql | SecurityEvent | where EventID == 4624 | where TimeGenerated between (datetime(2024-12-01 00:00:00) .. datetime(2024-12-01 06:00:00)) | project TimeGenerated, Account, Computer, SourceIP | order by TimeGenerated desc``` | Esta consulta filtra los inicios de sesión exitosos que ocurren en un horario específico, en este caso entre la medianoche y las 6 de la mañana. |

---

### **2.3 Correlación de Inicios de Sesión Fallidos con Bloqueo de Cuenta (Evento 4740)**

Detecta **cuentas bloqueadas** después de múltiples intentos fallidos, un posible indicio de un ataque de **fuerza bruta**.

| **Comando** | **Explicación** |
|-------------|-----------------|
| ```kql | SecurityEvent | where EventID == 4625 | join kind=inner (SecurityEvent | where EventID == 4740) on Account | project TimeGenerated, Account, SourceIP, Computer | order by TimeGenerated desc``` | Esta consulta utiliza una **unión** para correlacionar los eventos de **inicio de sesión fallido** (4625) con los eventos de **cuenta bloqueada** (4740), lo que ayuda a identificar bloqueos de cuentas como resultado de intentos de inicio de sesión fallidos. |

---

## **3. Detección de Malware y Amenazas Avanzadas**

### **3.1 Identificar Archivos Ejecutables Sospechosos en Endpoints**

Los archivos **ejecutables sospechosos** pueden ser utilizados por **malware** para comprometer un dispositivo.

| **Comando** | **Explicación** |
|-------------|-----------------|
| ```kql | DeviceFileEvents | where FileType == "Executable" | where FileName in ('powershell.exe', 'cmd.exe', 'mshta.exe') | project TimeGenerated, DeviceName, FileName, InitiatingProcessFileName | order by TimeGenerated desc``` | Filtra los eventos relacionados con archivos ejecutables como **`powershell.exe`**, **`cmd.exe`** y **`mshta.exe`**, que a menudo se utilizan en ataques de **phishing** o **exploit**. Muestra la hora, el dispositivo, el archivo ejecutado y el proceso que lo inició. |

---

### **3.2 Detección de Alertas de Defender para Endpoint**

Si tienes **Defender for Endpoint** habilitado, esta consulta detecta alertas con alta gravedad relacionadas con posibles **amenazas avanzadas**.

| **Comando** | **Explicación** |
|-------------|-----------------|
| ```kql | SecurityAlert | where ProductName == "Microsoft Defender for Endpoint" | where Severity == "High" | project TimeGenerated, AlertName, Computer, Description | order by TimeGenerated desc``` | Filtra las alertas generadas por **Microsoft Defender for Endpoint** con **alta severidad**. Muestra la hora del evento, el nombre de la alerta, el dispositivo afectado y una breve descripción del incidente. |

---

## **4. Análisis de Correlación y Respuesta a Incidentes**

### **4.1 Correlación de Eventos de Redirección HTTP y Phishing**

Las redirecciones HTTP a dominios maliciosos son una técnica común en ataques de **phishing**. Esta consulta permite correlacionar **eventos HTTP** con dominios de **phishing** conocidos.

| **Comando** | **Explicación** |
|-------------|-----------------|
| ```kql | CommonSecurityLog | where HTTPMethod == "GET" and URL contains "phishing" | project TimeGenerated, SourceIP, DestinationIP, URL | order by TimeGenerated desc``` | Filtra los eventos de **redirección HTTP** (método `GET`) que contienen la palabra **`phishing`** en la URL. Muestra la hora, la IP de origen, la IP de destino y la URL redirigida. |

---

### **4.2 Detectar Conexiones RDP Sospechosas**

Las conexiones **Remote Desktop Protocol (RDP)** no autorizadas o desde ubicaciones inusuales son una señal de posible **compromiso de red**.

| **Comando** | **Explicación** |
|-------------|-----------------|
| ```kql | SecurityEvent | where EventID == 4624 and Account == "Administrator" | where TimeGenerated > ago(1d) and SourceIP != "192.168.0.1" | project TimeGenerated, Account, Computer, SourceIP | order by TimeGenerated desc``` | Filtra los eventos de **inicio de sesión** de la cuenta **Administrator** a través de **RDP** desde **IPs** no conocidas o fuera de horario laboral. Muestra los detalles del evento y la IP de origen. |

---

## **5. Respuesta Rápida a Incidentes**

### **5.1 Bloquear IPs Maliciosas Basado en Logs de Seguridad**

Puedes bloquear IPs sospechosas detectadas en tus logs de seguridad.

| **Comando** | **Explicación** |
|-------------|-----------------|
| ```kql | SecurityEvent | where SourceIP in ('192.168.1.100', '203.0.113.45') | project TimeGenerated, Account, SourceIP, Computer | order by TimeGenerated desc``` | Filtra los eventos donde el **SourceIP** es una IP maliciosa conocida y genera alertas de seguridad. Puedes usar esta información para **bloquear** esas IPs en tu firewall. |

---

## **6. Consejos Adicionales para el Análisis y Detección en Sentinel**

| **Consejo** | **Explicación** |
|-------------|-----------------|
| **Optimización de Consultas** | Usa el operador **`summarize`** para agrupar grandes cantidades de datos y mejorar el rendimiento de las consultas. |
| **Uso de `project` y `extend`** | **`project`** selecciona las columnas relevantes para la consulta, mientras que **`extend`** agrega columnas adicionales a los resultados. |
| **Automatización con Playbooks** | Integra consultas de **KQL** con **playbooks de Azure Sentinel** para automatizar respuestas ante incidentes (por ejemplo, bloquear IPs). |

---


