---
layout: page
title: 🛡️ Deep Blue | Walkthrough
description: Análisis técnico del laboratorio Deep Blue de Blue Team Labs Online usando DeepBlueCLI.
dropdown: BlueTeamsLabs
priority: 3
---

![DeepBlue](/assets/img/Deep-blue/image.jpg)

En este laboratorio gratuito de [Blue Team Labs Online](https://blueteamlabs.online/home/investigation/deep-blue-a4c18ce507), se realiza un análisis detallado de logs EVTX (`Security.evtx` y `System.evtx`) para investigar un compromiso del sistema mediante un ataque RDP y la ejecución de Meterpreter. Se utiliza **DeepBlueCLI**, un módulo de PowerShell que facilita la identificación de eventos sospechosos y permite una respuesta más rápida.

---

# Escenario
Un sistema Windows fue comprometido mediante RDP expuesto a internet. Posteriormente, el atacante desplegó Meterpreter para realizar actividades maliciosas. Los archivos `Security.evtx` y `System.evtx` se proporcionan para análisis forense.

# Herramientas utilizadas
- DeepBlueCLI: Herramienta para analizar eventos críticos en logs EVTX.
- PowerShell: Ejecuta comandos para análisis dinámico.
- Event Viewer: Inspección manual de eventos.

# Análisis técnico

# Paso 1: Usuario que ejecutó GoogleUpdate.exe
Ejecutamos DeepBlueCLI sobre el archivo `Security.evtx`.
Comando:
.\DeepBlue.ps1 C:\Users\BTLOTest\Desktop\Investigation\Security.evtx

![DB1](../assets/img/Deep-blue/deepblue-1.png)

Resultado:
Mike Smith ejecutó `GoogleUpdate.exe`, un archivo sospechoso vinculado al inicio del ataque.

| Respuesta      |
|----------------|
| Mike Smith     |

# Paso 2: Evidencia de actividad de Meterpreter
Analizamos el archivo `Security.evtx` para identificar eventos relacionados con Meterpreter.

![DP2](../assets/img/Deep-blue/deepblue-2.png)

Resultado:
La actividad maliciosa ocurrió a las 10:48:14. El uso de pipes en comandos, una técnica común de Meterpreter, permitió la escalación de privilegios.

| Respuesta   |
|-------------|
| 10:48:14    |

# Paso 3: Servicio sospechoso creado
Utilizamos DeepBlueCLI para analizar `System.evtx` y detectar servicios sospechosos.
Comando:
.\DeepBlue.ps1 C:\Users\BTLOTest\Desktop\Investigation\System.evtx

![DB3](../assets/img/Deep-blue/deepblue-3.png)

Resultado:
El servicio `rztbzn` fue creado como parte de la persistencia del atacante.

| Respuesta   |
|-------------|
| rztbzn      |

# Paso 4: Ejecutable malicioso descargado
Revisamos eventos de creación de procesos (ID 4688) en el rango de tiempo identificado.

![DB4](../assets/img/Deep-blue/deepblue-4.png)

Resultado:
El archivo `serviceupdate.exe`, descargado en la carpeta Descargas, fue ejecutado antes de la conexión de Meterpreter.

| Respuesta            |
|----------------------|
| serviceupdate.exe    |


# Paso 5: Cuenta creada para persistencia
Buscamos comandos relacionados con la creación de cuentas en `Security.evtx`.

![DB5](../assets/img/Deep-blue/deepblue-5.png)

Resultado:
La cuenta `ServiceAct` fue creada mediante el comando `net user ServiceAct /add`.

| Respuesta                |
|--------------------------|
| net user ServiceAct /add |


# Paso 6: Grupos donde se añadió la cuenta
Identificamos los grupos a los que fue añadida la cuenta `ServiceAct`.

![DB6](../assets/img/Deep-blue/deepblue-6.png)

Resultado:
La cuenta fue añadida a los grupos `Administrators` y `Remote Desktop Users`.

| Respuesta                            |
|--------------------------------------|
| Administrators, Remote Desktop Users |


# Conclusión
La investigación revela:
1. Mike Smith ejecutó `GoogleUpdate.exe`, probablemente el vector inicial.
2. Se detectó actividad de Meterpreter a las 10:48:14.
3. El servicio `rztbzn` fue creado para persistencia.
4. El ejecutable malicioso `serviceupdate.exe` permitió el shell reverse.
5. La cuenta `ServiceAct` fue creada con privilegios elevados.
6. La cuenta se añadió a grupos críticos: Administrators y Remote Desktop Users.

Estos hallazgos confirman un ataque exitoso mediante RDP seguido de actividades maliciosas con Meterpreter.

# Herramienta clave:
DeepBlueCLI acelera la revisión de eventos críticos en logs EVTX, optimizando la respuesta a incidentes.

![DB6](../assets/img/Deep-blue/1tvm.gif)

