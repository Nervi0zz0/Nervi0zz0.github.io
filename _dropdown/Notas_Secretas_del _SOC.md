---
layout: page
title: 🛡️ Guía de Monitoreo de Eventos en Windows con SIEM
description: Consejos y recursos
dropdown: Notas Secretas del SOC
priority: 4
---
# 🛡️ Guía Completa de Monitoreo de Eventos en Windows con SIEM:  Casos de Uso Esenciales

El monitoreo de eventos en entornos Windows es fundamental para identificar amenazas de seguridad y actividades sospechosas. En un escenario de detección y respuesta, contar con un SIEM (Security Information and Event Management) optimizado para eventos de Windows puede ser la diferencia entre detectar una amenaza a tiempo o sufrir una brecha de seguridad.

Esta guía está dirigida a analistas de seguridad y detalla los eventos más importantes en Windows que deben ser monitoreados para proteger tu infraestructura.

## ⚙️ Introducción: ¿Qué es un SIEM y por qué es crucial en entornos Windows?

Un SIEM permite recolectar y correlacionar eventos de múltiples fuentes, generando alertas basadas en patrones predefinidos. En Windows, el sistema operativo registra eventos de seguridad que proporcionan información sobre los sucesos más críticos, como inicios de sesión, cambios en la configuración, acceso a archivos, etc.

Los códigos de eventos en Windows son identificadores únicos que el sistema genera cuando ocurre un suceso, como un intento de inicio de sesión o un cambio en la política de grupo. Estos eventos se registran en los "Event Logs" de Windows, y herramientas como los SIEM los interpretan para generar alertas y permitir la investigación de incidentes.

### 💾 ¿De dónde salen los códigos de eventos en Windows?

- **Event Viewer**: Windows almacena los eventos en los "Event Logs", que se pueden visualizar en el Visor de Eventos (Event Viewer). Cada evento tiene un código único que describe lo sucedido.
- **Security Log**: Es uno de los registros más importantes, donde se encuentran eventos relacionados con la seguridad, autenticación, accesos, y más.
- **Application & System Logs**: Aquí se encuentran eventos de aplicaciones, servicios, o problemas generales del sistema.
- **Custom Logs**: También se pueden habilitar logs personalizados para un monitoreo más avanzado.

Ahora que conoces el origen de estos eventos, veamos algunos de los casos de uso esenciales para un entorno Windows.

---

## 👤 1. Monitoreo de Inicio de Sesión y Autenticación

Es fundamental monitorear los intentos de autenticación para detectar accesos no autorizados, ataques de fuerza bruta o comportamientos anómalos. Los eventos de inicio de sesión y autenticación están entre los más cruciales, ya que suelen ser el primer indicio de un ataque o compromiso.

| Caso de Uso                                             | Códigos de Evento                    |
|---------------------------------------------------------|--------------------------------------|
| Intentos de inicio de sesión fallidos                   | 4625                                 |
| Bloqueos de cuenta                                      | 4740                                 |
| Inicio de sesión exitoso fuera del horario comercial    | 4624                                 |
| Creación de nuevos usuarios                             | 4720                                 |
| Uso de cuenta privilegiada                              | 4672                                 |
| Cambios de contraseña                                   | 4723 (intento), 4724 (éxito)         |
| Uso de credenciales robadas (Kerberos)                  | 4768, 4770                           |
| Acceso no autorizado a credenciales                     | 4771, 4776                           |
| Enumeración excesiva de cuentas                         | 4625, 4776                           |

### 📌 Consejos Prácticos:
- **Correlación de eventos**: Correlaciona eventos de inicio de sesión fallidos (4625) con bloqueos de cuenta (4740) para detectar posibles ataques de fuerza bruta.
- **Alertas fuera de horario**: Configura alertas cuando los inicios de sesión exitosos (4624) ocurran fuera de horas laborales.

---

## 👥 2. Monitoreo de Cambios en Usuarios y Grupos

Los cambios en las cuentas de usuario o los grupos de seguridad son eventos críticos, ya que un atacante podría intentar obtener acceso elevado modificando grupos o usuarios.

| Caso de Uso                                             | Códigos de Evento                    |
|---------------------------------------------------------|--------------------------------------|
| Cambios en la cuenta de usuario                         | 4722, 4723, 4724, 4725, 4726         |
| Cambios en la membresía del grupo                       | 4727, 4731, 4735, 4737               |
| Cambios en la clave de cifrado de BitLocker             | 5379                                 |
| Cambios no autorizados de GPO                           | 5136                                 |

### 📌 Consejos Prácticos:
- **Monitoreo de cuentas privilegiadas**: Es crucial revisar eventos de modificaciones en grupos de seguridad privilegiados (4727).
- **BitLocker**: Cualquier cambio en las claves de cifrado debe ser investigado para evitar compromisos en el cifrado de discos.

---

## 🗂️ 3. Monitoreo de Acceso a Archivos y Carpetas

Controlar el acceso a archivos sensibles es esencial para prevenir fugas de datos o accesos no autorizados.

| Caso de Uso                                             | Códigos de Evento                    |
|---------------------------------------------------------|--------------------------------------|
| Acceso a archivos y carpetas                            | 4663, 4656                           |
| Acceso no autorizado a archivos compartidos             | 5145                                 |
| Intento de acceder a archivos confidenciales            | 4663                                 |

### 📌 Consejos Prácticos:
- **Sensibilidad del acceso**: Configura alertas cuando se acceda a archivos que contienen información crítica o confidencial.

---

## 🔧 4. Supervisión de Servicios y Tareas Programadas

Los atacantes frecuentemente modifican servicios o tareas programadas para mantener su persistencia en los sistemas.

| Caso de Uso                                             | Códigos de Evento                    |
|---------------------------------------------------------|--------------------------------------|
| Instalación o modificación del servicio                 | 4697                                 |
| Creación de tareas programadas                          | 4698                                 |
| Modificación de tareas programadas                      | 4699                                 |
| Intentos fallidos de iniciar un servicio                | 7041                                 |
| Instalación del controlador                             | 7045                                 |

### 📌 Consejos Prácticos:
- **Persistencia de malware**: Monitorea los eventos de tareas programadas para detectar posibles abusos de malware.

---

## 🔄 5. Supervisión de Cambios en la Configuración del Sistema

Cualquier modificación en la configuración del sistema, ya sea en la red o el firewall, puede comprometer la seguridad del entorno.

| Caso de Uso                                             | Códigos de Evento                    |
|---------------------------------------------------------|--------------------------------------|
| Cambios en la configuración de red                      | 4254, 4255, 10400                    |
| Cambios en el Firewall de Windows                       | 4946, 4947, 4950, 4951               |
| Cambios en el registro                                  | 4657, 4660                           |

### 📌 Consejos Prácticos:
- **Cambios en el firewall**: Asegúrate de monitorear los cambios en el firewall para evitar que se abra tráfico malicioso.

---

## 🛠️ 6. Detección de Actividad de Scripts y Procesos Sospechosos

Monitorear la ejecución de scripts y procesos ayuda a detectar intentos de ejecución maliciosa o automatización de ataques.

| Caso de Uso                                             | Códigos de Evento                    |
|---------------------------------------------------------|--------------------------------------|
| Ejecución de scripts sospechosos                        | 4688 (creación de procesos)          |
| Actividad sospechosa de PowerShell                      | 4104 (registros de PowerShell)       |
| Inyección de proceso inusual                            | 4688 (con EDR o Sysmon)              |

### 📌 Consejos Prácticos:
- **PowerShell**: La ejecución de scripts a través de PowerShell (evento 4104) debe ser vigilada estrechamente, ya que es una herramienta comúnmente usada por atacantes.

---

## 🖧 7. Supervisión de Movimientos Laterales y Persistencia

El monitoreo de eventos relacionados con la autenticación y acceso a recursos puede detectar movimientos laterales dentro de la red, una técnica utilizada por atacantes para expandir su control.

| Caso de Uso                                             | Códigos de Evento                    |
|---------------------------------------------------------|--------------------------------------|
| Detección de movimiento lateral                         | 4648                                 |
| Uso de credenciales robadas                             | 4768, 4770                           |
| Supervisión de la cuenta de servicio                    | 4624, 4672                           |

### 📌 Consejos Prácticos:
- **Acceso inusual entre máquinas**: El evento 4648 puede correlacionarse con accesos inusuales entre equipos para identificar intentos de movimiento lateral.

---

## 🔍 8. Monitoreo de Actividad del Sistema y Eventos Críticos

Algunos eventos críticos, como la modificación o eliminación de registros, reinicios inesperados o la instalación de software, deben ser supervisados activamente para asegurar la integridad del sistema.

| Caso de Uso                                             | Códigos de Evento                    |
|---------------------------------------------------------|--------------------------------------|
| Reinicio o apagado del sistema                          | 6005, 6006, 1074                     |
| Borrado del registro de eventos                         | 1102                                 |
| Instalación y eliminación de aplicaciones               | 11707, 1033, 1034                    |

### 📌 Consejos Prácticos:
- **Borrado de registros**: La eliminación de registros (evento 1102) es un claro indicio de actividad maliciosa, ya que los atacantes suelen hacerlo para ocultar su presencia en el sistema.

---




