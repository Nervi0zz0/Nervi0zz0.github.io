---
layout: page
title: 🛡️ Eventos en Windows
description: Consejos y recursos
dropdown: Notas de un Cojo
priority: 4
---

# Guía de Monitoreo de Eventos en Windows: Casos de Uso Esenciales

El monitoreo de eventos en entornos Windows es fundamental para identificar amenazas de seguridad, detectar actividades sospechosas y prevenir brechas de seguridad. Windows registra una amplia gama de eventos que proporcionan información crítica sobre el estado de los sistemas y las acciones de los usuarios, permitiendo a los analistas de seguridad detectar problemas potenciales a tiempo.

Esta guía está dirigida a analistas de seguridad y proporciona una descripción detallada de los eventos más importantes en Windows que deben ser monitoreados, junto con casos de uso y explicaciones sobre su relevancia para la seguridad.

## Introducción: ¿Por qué es crucial el monitoreo de eventos en Windows?

Windows registra una variedad de eventos que son fundamentales para la detección de intrusiones y el monitoreo de la seguridad. Estos eventos están almacenados en los registros del sistema, que contienen información detallada sobre sucesos relacionados con la autenticación, cambios en la configuración, acceso a archivos, y más. Al monitorear estos eventos, los administradores pueden identificar comportamientos anómalos que podrían indicar un ataque o un compromiso en el sistema.

### ¿De dónde provienen los códigos de eventos en Windows?

Los eventos generados por Windows provienen de diversos registros:

- **Visor de eventos (Event Viewer)**: Herramienta principal para visualizar los eventos del sistema.
- **Registro de seguridad (Security Log)**: Contiene eventos relacionados con la seguridad, como inicios de sesión, cambios de contraseñas, acceso no autorizado y más.
- **Registros de aplicaciones y sistema**: Registran eventos generados por aplicaciones o servicios del sistema.
- **Registros personalizados**: Permiten la creación de registros específicos para monitorear aplicaciones o eventos particulares.

---

## 1. Monitoreo de Inicio de Sesión y Autenticación

El monitoreo de intentos de autenticación es fundamental para detectar accesos no autorizados, ataques de fuerza bruta, o comportamientos anómalos. Estos eventos son clave para identificar el acceso no autorizado o el compromiso de cuentas.

### Eventos Clave:
- **4624**: Inicio de sesión exitoso
- **4625**: Intento de inicio de sesión fallido
- **4740**: Bloqueo de cuenta
- **4768/4770**: Uso de credenciales robadas (Kerberos)

### Tabla de Casos de Uso:

| Caso de Uso                                             | Códigos de Evento                    | Descripción                                                                                                                                               | Relevancia para la Seguridad                                                                                  |
|---------------------------------------------------------|--------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
| Intentos de inicio de sesión fallidos                   | 4625                                 | Registra intentos de inicio de sesión que no fueron exitosos, incluyendo ataques de fuerza bruta.                                                         | Indica intentos de acceso no autorizado que podrían estar relacionados con un ataque de contraseña.           |
| Bloqueos de cuenta                                      | 4740                                 | Registra cuando una cuenta es bloqueada después de múltiples intentos fallidos.                                                                            | Ayuda a identificar intentos de acceso repetidos que podrían estar relacionados con ataques de fuerza bruta.  |
| Inicio de sesión exitoso fuera del horario comercial    | 4624                                 | Indica un inicio de sesión exitoso fuera de los horarios habituales de trabajo.                                                                            | Puede señalar un acceso no autorizado o actividad sospechosa fuera de los horarios normales.                  |
| Creación de nuevos usuarios                             | 4720                                 | Este evento se genera cuando se crea un nuevo usuario en el sistema.                                                                                       | Un nuevo usuario podría ser creado por un atacante para obtener acceso persistente al sistema.                 |
| Uso de cuenta privilegiada                              | 4672                                 | Indica el uso de cuentas con privilegios elevados, como administradores.                                                                                  | El acceso de cuentas privilegiadas es crítico, ya que los atacantes suelen buscar escalada de privilegios.    |
| Cambios de contraseña                                   | 4723 (intento), 4724 (éxito)         | Registra cuando un intento de cambio de contraseña es realizado o cuando un cambio es exitoso.                                                             | El cambio de contraseña podría ser un intento de un atacante de tomar control de una cuenta comprometida.     |
| Uso de credenciales robadas (Kerberos)                  | 4768, 4770                           | Los eventos indican el uso de credenciales robadas para autenticarse mediante el protocolo Kerberos.                                                       | Los atacantes pueden usar credenciales robadas para obtener acceso a recursos sin ser detectados.             |
| Acceso no autorizado a credenciales                     | 4771, 4776                           | Indica intentos de acceder o utilizar credenciales de manera no autorizada.                                                                               | Este tipo de acceso puede ser indicativo de un intento de uso indebido de credenciales o explotación de vulnerabilidades. |
| Enumeración excesiva de cuentas                         | 4625, 4776                           | Eventos relacionados con intentos masivos de acceso a cuentas, indicando posibles intentos de enumeración.                                                  | Los atacantes intentan encontrar cuentas válidas para luego atacarlas con contraseñas débiles o robadas.       |

---

## 2. Monitoreo de Cambios en la Configuración del Sistema

Los cambios no autorizados en la configuración del sistema o en las políticas de seguridad pueden comprometer la integridad de un entorno Windows. Monitorear estos eventos permite detectar configuraciones erróneas o maliciosas.

### Eventos Clave:
- **4732**: Un grupo de seguridad ha sido modificado
- **4719**: Cambio en la política de auditoría
- **4739**: Cambio en la política de seguridad local
- **4688**: Creación de un nuevo proceso

### Tabla de Casos de Uso:

| Caso de Uso                                             | Códigos de Evento                    | Descripción                                                                                                                                               | Relevancia para la Seguridad                                                                                  |
|---------------------------------------------------------|--------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
| Modificación en grupos de seguridad                     | 4732                                 | Se genera cuando se modifica un grupo de seguridad, como la adición o eliminación de usuarios de grupos privilegiados.                                    | Modificar grupos de seguridad puede ser un indicio de un atacante intentando escalar privilegios o ampliar su acceso. |
| Cambio en la política de auditoría                       | 4719                                 | Se genera cuando hay un cambio en las configuraciones de auditoría de seguridad.                                                                          | Los atacantes pueden cambiar las políticas de auditoría para desactivar la recopilación de logs de eventos críticos. |
| Modificación en las políticas de seguridad              | 4739                                 | Registra cambios en las políticas de seguridad del sistema.                                                                                             | Alterar las políticas de seguridad puede permitir que los atacantes eludan la detección o la protección del sistema. |
| Creación de un nuevo proceso                            | 4688                                 | Registra la creación de un nuevo proceso dentro del sistema.                                                                                             | La creación de procesos inesperados o desconocidos es un indicativo de que un atacante podría haber comprometido el sistema. |

---

## 3. Monitoreo de Gestión de Cuentas

Los eventos de gestión de cuentas, como la eliminación de cuentas o la adición de usuarios a grupos privilegiados, son cruciales para detectar actividades maliciosas. Estos eventos pueden indicar que un atacante está intentando crear o modificar cuentas para mantener el acceso o escalar privilegios.

### Eventos Clave:
- **4726**: Eliminación de un usuario
- **4728**: Un usuario ha sido agregado a un grupo
- **4729**: Un usuario ha sido removido de un grupo
- **4738**: Cambio de nombre de un usuario
- **4741**: Creación de un nuevo grupo de seguridad

### Tabla de Casos de Uso:

| Caso de Uso                                             | Códigos de Evento                    | Descripción                                                                                                                                               | Relevancia para la Seguridad                                                                                  |
|---------------------------------------------------------|--------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
| Eliminación de usuarios                                 | 4726                                 | Este evento se genera cuando un usuario es eliminado del sistema.                                                                                        | La eliminación de cuentas es una táctica comúnmente utilizada por los atacantes para cubrir su rastro o impedir la detección. |
| Adición de un usuario a un grupo de seguridad           | 4728                                 | Registra cuando un usuario es agregado a un grupo de seguridad, lo cual podría concederle permisos elevados.                                               | La adición de un usuario a un grupo privilegiado podría ser un intento de escalada de privilegios.             |
| Remoción de un usuario de un grupo de seguridad         | 4729                                 | Se genera cuando un usuario es removido de un grupo de seguridad.                                                                                        | Los atacantes pueden intentar remover cuentas o modificar su pertenencia a grupos para obtener acceso a otros recursos. |
| Cambio de nombre de usuario                              | 4738                                 | Registra cuando se cambia el nombre de un usuario.                                                                                                        | Cambiar el nombre de un usuario puede ser un intento de ocultar actividades o manipular registros de auditoría.  |
| Creación de un nuevo grupo de seguridad                 | 4741                                 | Indica que un nuevo grupo de seguridad ha sido creado en el sistema.                                                                                      | La creación de nuevos grupos puede ser un indicio de un atacante buscando organizar privilegios o estructurar su acceso. |

### Importancia del Monitoreo de Gestión de Cuentas

La gestión de cuentas de usuario es un área crítica en la seguridad de un sistema Windows. Los atacantes pueden eliminar o modificar cuentas de usuario para desactivar la vigilancia, crear nuevas cuentas con privilegios elevados o agregar usuarios a grupos privilegiados. Detectar estos eventos a tiempo es esencial para evitar que los atacantes mantengan el acceso a la infraestructura de TI.

---

## 4. Monitoreo de Acceso a Archivos y Recursos

El acceso no autorizado a archivos o recursos críticos es una de las principales señales de que un atacante ha penetrado en el sistema. Los eventos que registran la creación, modificación o eliminación de archivos deben ser monitoreados cuidadosamente.

### Eventos Clave:
- **4656**: Un intento de acceso a un objeto se ha realizado
- **4663**: Acceso a un objeto ha sido realizado
- **4670**: Permisos de un objeto han sido modificados

### Tabla de Casos de Uso:

| Caso de Uso                                             | Códigos de Evento                    | Descripción                                                                                                                                               | Relevancia para la Seguridad                                                                                  |
|---------------------------------------------------------|--------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
| Intento de acceso a un objeto                           | 4656                                 | Registra cuando un proceso intenta acceder a un objeto del sistema, como un archivo o directorio.                                                           | Los atacantes a menudo intentan acceder a archivos críticos para extraer información confidencial.            |
| Acceso a un objeto                                       | 4663                                 | Registra el acceso real a un archivo u objeto, proporcionando detalles sobre qué proceso realizó el acceso.                                                | Los accesos a archivos críticos son una indicación de que los atacantes podrían estar intentando robar o modificar datos. |
| Modificación de permisos de un objeto                   | 4670                                 | Registra cuando se modifican los permisos de un archivo o recurso.                                                                                         | Los cambios en permisos de archivos son una señal de que un atacante podría estar escalando privilegios o manipulando accesos. |

---


