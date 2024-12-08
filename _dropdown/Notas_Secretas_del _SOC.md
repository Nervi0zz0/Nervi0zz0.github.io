---
layout: page
title: 🛡️ Guía de Monitoreo de Eventos en Windows con SIEM
description: Consejos y recursos
dropdown: Notas Secretas del SOC
priority: 4
---
# Guía de Monitoreo de Eventos en Windows con SIEM

El monitoreo de eventos en un entorno Windows es crucial para la detección de actividades sospechosas y amenazas de seguridad. Un SIEM (Security Information and Event Management) permite correlacionar eventos en tiempo real, facilitando la detección de anomalías y ataques. Esta guía está dirigida a analistas de seguridad y proporciona una visión detallada de los principales eventos de Windows que deben ser monitoreados para asegurar la infraestructura.

## Introducción: ¿Qué es un SIEM y por qué es crucial en entornos Windows?

El SIEM es una herramienta clave en la seguridad de la información que permite a los analistas gestionar y correlacionar eventos provenientes de distintas fuentes. En entornos Windows, los eventos de seguridad registrados en los logs del sistema son esenciales para identificar actividades inusuales o maliciosas. Los SIEM recogen y analizan estos eventos, facilitando la detección y respuesta ante posibles incidentes.

A continuación, se presentan 105 casos de uso clasificados por categorías, junto con los códigos de eventos correspondientes que deben ser supervisados en un entorno Windows.

## 1. **Monitoreo de Inicio de Sesión y Autenticación**

El monitoreo de intentos de autenticación es fundamental para detectar accesos no autorizados, ataques de fuerza bruta o comportamientos sospechosos en cuentas privilegiadas.

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

### Consejos Prácticos:
- **Correlación de eventos**: Para detectar intentos de fuerza bruta o accesos no autorizados, es útil correlacionar eventos de inicio de sesión fallidos (4625) con bloqueos de cuenta (4740).
- **Horarios fuera de lo común**: El evento 4624 puede configurarse para disparar alertas cuando los inicios de sesión ocurren fuera del horario laboral establecido.

## 2. **Monitoreo de Cambios en la Configuración de Usuarios y Grupos**

Es importante monitorear cualquier modificación en la configuración de cuentas y grupos de seguridad, ya que un atacante podría intentar agregar usuarios a grupos privilegiados.

| Caso de Uso                                             | Códigos de Evento                    |
|---------------------------------------------------------|--------------------------------------|
| Cambios en la cuenta de usuario                         | 4722, 4723, 4724, 4725, 4726         |
| Cambios en la membresía del grupo                       | 4727, 4731, 4735, 4737               |
| Cambios en la clave de cifrado de BitLocker             | 5379                                 |
| Cambios no autorizados de GPO                           | 5136                                 |

### Consejos Prácticos:
- **Vigilancia de cuentas privilegiadas**: Es esencial monitorear los eventos relacionados con la modificación de grupos de seguridad privilegiados (4727, 4731).
- **Cambios en BitLocker**: Cualquier modificación en las claves de cifrado de BitLocker debe ser revisada para evitar el acceso no autorizado a volúmenes protegidos.

## 3. **Monitoreo de Acceso a Archivos y Carpetas**

Controlar el acceso a archivos y carpetas sensibles permite identificar posibles intentos de exfiltración de datos o acceso no autorizado.

| Caso de Uso                                             | Códigos de Evento                    |
|---------------------------------------------------------|--------------------------------------|
| Acceso a archivos y carpetas                            | 4663, 4656                           |
| Acceso no autorizado a archivos compartidos             | 5145                                 |
| Intento de acceder a archivos confidenciales            | 4663                                 |

### Consejos Prácticos:
- **Alertas en datos sensibles**: Configura alertas para archivos o carpetas que contienen datos críticos. Esto te ayudará a detectar posibles fugas de información o accesos no autorizados.

## 4. **Supervisión de Servicios y Tareas Programadas**

La manipulación de servicios o tareas programadas puede ser un indicativo de actividad maliciosa, como la persistencia de malware.

| Caso de Uso                                             | Códigos de Evento                    |
|---------------------------------------------------------|--------------------------------------|
| Instalación o modificación del servicio                 | 4697                                 |
| Creación de tareas programadas                          | 4698                                 |
| Modificación de tareas programadas                      | 4699                                 |
| Intentos fallidos de iniciar un servicio                | 7041                                 |
| Instalación del controlador                             | 7045                                 |

### Consejos Prácticos:
- **Control de tareas programadas**: Las tareas programadas pueden ser abusadas para ejecutar malware de manera persistente. El monitoreo de los eventos 4698 y 4699 ayuda a identificar modificaciones no autorizadas.

## 5. **Supervisión de Cambios en la Configuración del Sistema**

Detectar cambios en la configuración del sistema es crucial para asegurar que no se estén implementando configuraciones maliciosas o no autorizadas.

| Caso de Uso                                             | Códigos de Evento                    |
|---------------------------------------------------------|--------------------------------------|
| Cambios en la configuración de red                      | 4254, 4255, 10400                    |
| Cambios en el Firewall de Windows                       | 4946, 4947, 4950, 4951               |
| Cambios en el registro                                  | 4657, 4660                           |

### Consejos Prácticos:
- **Cambios en el firewall**: Un cambio no autorizado en la configuración del firewall podría permitir tráfico malicioso. Los eventos 4946 y 4951 deben ser revisados regularmente.

## 6. **Detección de Actividad de Scripts y Procesos Sospechosos**

Los atacantes a menudo utilizan scripts para ejecutar comandos maliciosos. Es esencial monitorear eventos que indiquen la creación o ejecución de procesos sospechosos.

| Caso de Uso                                             | Códigos de Evento                    |
|---------------------------------------------------------|--------------------------------------|
| Ejecución de scripts sospechosos                        | 4688 (creación de procesos)          |
| Actividad sospechosa de PowerShell                      | 4104 (registros de PowerShell)       |
| Inyección de proceso inusual                            | 4688 (con EDR o Sysmon)              |

### Consejos Prácticos:
- **PowerShell bajo control**: Dado que PowerShell es una herramienta legítima frecuentemente utilizada por atacantes, es fundamental monitorear la actividad del evento 4104, que registra la ejecución de scripts.

## 7. **Supervisión de Movimientos Laterales y Persistencia**

El monitoreo de eventos relacionados con la autenticación y acceso a recursos puede detectar movimientos laterales dentro de la red, una técnica utilizada por atacantes para expandir su control.

| Caso de Uso                                             | Códigos de Evento                    |
|---------------------------------------------------------|--------------------------------------|
| Detección de movimiento lateral                         | 4648                                 |
| Uso de credenciales robadas                             | 4768, 4770                           |
| Supervisión de la cuenta de servicio                    | 4624, 4672                           |

### Consejos Prácticos:
- **Acceso inusual entre máquinas**: El evento 4648 puede correlacionarse con accesos inusuales entre equipos para identificar intentos de movimiento lateral.

## 8. **Monitoreo de Actividad del Sistema y Eventos Críticos**

Algunos eventos críticos, como la modificación o eliminación de registros, reinicios inesperados o la instalación de software, deben ser supervisados activamente para asegurar la integridad del sistema.

| Caso de Uso                                             | Códigos de Evento                    |
|---------------------------------------------------------|--------------------------------------|
| Reinicio o apagado del sistema                          | 6005, 6006, 1074                     |
| Borrado del registro de eventos                         | 1102                                 |
| Instalación y eliminación de aplicaciones               | 11707, 1033, 1034                    |

### Consejos Prácticos:
- **Borrado de registros**: La eliminación de registros (evento 1102) es un claro indicio de actividad maliciosa, ya que los atacantes suelen hacerlo para ocultar su presencia en el sistema.


