---
layout: page
title: 🛡️ Monitoreo de Eventos en Windows
description: Identificación de amenazas y detección de actividades sospechosas.
dropdown: Notas de un Cojo
priority: 4
---

# 🛡️ **Guía Completa de Monitoreo de Eventos en Windows**

El monitoreo de eventos en **Windows** es una de las prácticas esenciales en la administración de sistemas y la ciberseguridad. Los registros de eventos proporcionan información detallada sobre acciones en el sistema que, si se analizan correctamente, permiten detectar y mitigar amenazas en tiempo real.

Esta guía está diseñada para analistas de seguridad y administradores de sistemas que buscan comprender los eventos clave de Windows, su relevancia en la seguridad, y cómo utilizarlos en la práctica.

---

## 📝 **Introducción**

### ¿Por qué es importante el monitoreo de eventos?

El sistema operativo Windows genera eventos constantemente que abarcan actividades de autenticación, cambios en la configuración del sistema, movimientos de archivos y más. **Analizar estos eventos ayuda a:**
- Identificar intentos de acceso no autorizado.
- Detectar actividades sospechosas o maliciosas.
- Mantener registros de auditoría para investigaciones posteriores a un incidente.
- Garantizar el cumplimiento normativo en materia de seguridad (GDPR, ISO 27001, etc.).

### ¿Dónde se almacenan los eventos?

- **Visor de eventos (Event Viewer):** Herramienta principal para revisar eventos en Windows.
- **Registros predefinidos:**
  - **Aplicación**: Eventos generados por aplicaciones instaladas.
  - **Seguridad**: Eventos relacionados con la autenticación y la gestión de recursos.
  - **Sistema**: Eventos registrados por el sistema operativo.
- **Registros personalizados:** Configuraciones adicionales para supervisar eventos específicos.

---

## 🔍 **Eventos Clave para Monitorear en Windows**

### 1️⃣ **Inicio de Sesión y Autenticación**

El acceso al sistema es uno de los puntos más críticos a monitorear. Eventos relacionados con la autenticación ayudan a identificar ataques de fuerza bruta, acceso no autorizado o el compromiso de credenciales.

#### **Eventos Importantes:**
- **4624:** Inicio de sesión exitoso.
- **4625:** Intento de inicio de sesión fallido.
- **4740:** Bloqueo de cuenta.
- **4768/4770:** Actividades relacionadas con credenciales Kerberos.

#### **Ejemplo Práctico:**
Detectar intentos masivos de inicio de sesión fallido (ataques de fuerza bruta):
1. Revisa el evento **4625**.
2. Busca patrones como múltiples intentos fallidos desde una misma IP.
3. Correlaciona con eventos de bloqueo de cuentas (**4740**) para identificar posibles cuentas comprometidas.

---

### 2️⃣ **Cambios en la Configuración del Sistema**

Los atacantes suelen modificar configuraciones críticas para eludir controles de seguridad o establecer persistencia. Monitorear estos eventos es crucial para detectar configuraciones sospechosas.

#### **Eventos Importantes:**
- **4719:** Cambio en las políticas de auditoría.
- **4739:** Modificaciones en las políticas de seguridad local.
- **4688:** Creación de procesos.
- **4670:** Cambios en permisos de archivos o directorios.

#### **Caso de Uso Clave:**
Si detectas un evento **4719**, revisa si las políticas de auditoría han sido debilitadas, como la desactivación del monitoreo de inicios de sesión o cambios en privilegios de usuarios.

---

### 3️⃣ **Gestión de Cuentas de Usuario**

Los eventos relacionados con la creación, modificación o eliminación de cuentas pueden ser indicativos de actividad maliciosa, como la creación de cuentas backdoor.

#### **Eventos Importantes:**
- **4720:** Creación de una nueva cuenta de usuario.
- **4726:** Eliminación de una cuenta.
- **4728:** Adición de un usuario a un grupo de seguridad.
- **4738:** Modificación de una cuenta.

#### **Ejemplo Práctico:**
Si detectas la creación de una cuenta nueva (**4720**) y la adición inmediata de esta cuenta a un grupo privilegiado (**4728**), esto podría indicar un intento de escalada de privilegios.

---

### 4️⃣ **Actividad en Procesos y Aplicaciones**

Los atacantes pueden ejecutar scripts o aplicaciones maliciosas para comprometer el sistema. El monitoreo de la creación de procesos y eventos relacionados ayuda a detectar actividades sospechosas.

#### **Eventos Importantes:**
- **4688:** Creación de un nuevo proceso.
- **7045:** Instalación de un nuevo servicio.
- **4697:** Adición de un servicio al sistema.

#### **Caso de Uso Clave:**
Un evento **4688** que muestra la ejecución de un proceso inusual (como `powershell.exe` ejecutando scripts sospechosos) puede ser un indicador de un ataque basado en scripts.

---

## ⚙️ **Herramientas para el Monitoreo y Análisis de Eventos**

| **Herramienta**           | **Descripción**                                                                                     | **Enlace**                                   |
|---------------------------|---------------------------------------------------------------------------------------------------|---------------------------------------------|
| **Event Viewer**           | Herramienta nativa de Windows para visualizar registros de eventos.                              | Integrado en Windows                        |
| **Sysmon**                 | Genera eventos detallados de procesos, redes y archivos.                                         | [Sysinternals](https://learn.microsoft.com/en-us/sysinternals/) |
| **Splunk**                 | Plataforma para analizar y correlacionar registros de eventos.                                   | [Splunk](https://www.splunk.com/)           |
| **Graylog**                | Solución de gestión de logs centralizada y open-source.                                          | [Graylog](https://www.graylog.org/)         |
| **Wazuh**                  | Herramienta de seguridad integral que incluye análisis de eventos de Windows.                    | [Wazuh](https://wazuh.com/)                 |

---

## 📊 **Escenarios de Detección: Casos de Uso Detallados**

| **Escenario**                                    | **Evento Clave**                  | **Acción Recomendada**                                                                                   |
|--------------------------------------------------|-----------------------------------|---------------------------------------------------------------------------------------------------------|
| Intentos de fuerza bruta detectados              | 4625                              | Revisar IP de origen; bloquear la IP y analizar intentos fallidos relacionados.                        |
| Creación de cuentas sospechosas                  | 4720                              | Identificar quién creó la cuenta; validar si la acción fue legítima.                                   |
| Ejecución de procesos no autorizados             | 4688                              | Correlacionar con hashes de malware conocidos usando **VirusTotal** o sistemas de detección de amenazas. |
| Modificaciones en políticas de auditoría         | 4719                              | Restaurar configuraciones previas y revisar cuentas que realizaron el cambio.                         |
| Instalación de servicios sospechosos             | 7045                              | Validar el servicio; detenerlo inmediatamente si no es legítimo.                                       |

---

## 🔒 **Buenas Prácticas de Monitoreo**

1. **Establece alertas automatizadas:**
   Usa herramientas como **Wazuh** o **SIEM** para generar alertas en tiempo real ante eventos críticos.
   
2. **Revisa eventos correlacionados:**
   Analiza conjuntos de eventos relacionados para detectar patrones complejos.

3. **Mantén los registros centralizados:**
   Utiliza soluciones como **Graylog** o **ELK** para consolidar y analizar registros desde múltiples sistemas.

4. **Configura políticas de retención adecuadas:**
   Guarda los registros durante el tiempo necesario para auditorías o investigaciones posteriores.

5. **Automatiza respuestas:**
   Integra scripts o sistemas SOAR para mitigar amenazas automáticamente tras ciertos eventos.

---

## 📂 **Recursos Adicionales**

- [Sysmon Configuration Guide](https://github.com/SwiftOnSecurity/sysmon-config): Plantilla optimizada para configuraciones de Sysmon.
- [Microsoft Event IDs Reference](https://learn.microsoft.com/en-us/windows/security/threat-protection/auditing/event-4672): Documentación oficial de eventos clave.
- [Wazuh SIEM Tutorial](https://documentation.wazuh.com/current/): Guía para implementar Wazuh en tu infraestructura.

---

¡Esta guía te ayudará a estar mejor preparado para identificar y responder a amenazas en entornos Windows! 🚀
