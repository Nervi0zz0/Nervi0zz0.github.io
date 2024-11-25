---
layout: page
title: 🛡️ Deep Blue | Blue Team Labs Walkthrough |
description: Análisis técnico de actividad maliciosa en logs de Windows usando DeepBlueCLI.
dropdown: LetsDefends
---



# 🛡️ Deep Blue | Blue Team Labs Walkthrough  
Análisis forense de logs EVTX con herramientas especializadas.

---

## 📜 **Resumen**  

En este laboratorio de [Blue Team Labs](https://blueteamlabs.online/home/investigation/deep-blue-a4c18ce507), se analizan los logs `Security.evtx` y `System.evtx` para identificar rastros de un ataque mediante RDP y la ejecución de Meterpreter. La herramienta principal es **DeepBlueCLI**, un módulo de PowerShell diseñado para acelerar la identificación de eventos sospechosos.

---

## 🛠️ **Pasos**

```powershell
# Paso 1: Usuario que ejecutó `GoogleUpdate.exe`
.\DeepBlue.ps1 C:\Users\BTLOTest\Desktop\Investigation\Security.evtx

Resultado:
| Resultado | Respuesta              |
|-----------|------------------------|
| El archivo muestra que Mike Smith ejecutó el archivo GoogleUpdate.exe | ✔️ Mike Smith |

# Paso 2: Evidencia de actividad de Meterpreter
.\DeepBlue.ps1 C:\Users\BTLOTest\Desktop\Investigation\Security.evtx

Resultado:
| Resultado                                 | Respuesta     |
|-------------------------------------------|---------------|
| Actividad detectada a las 10:48:14.       | ✔️ 10:48:14   |

# Paso 3: Servicio sospechoso creado
.\DeepBlue.ps1 C:\Users\BTLOTest\Desktop\Investigation\System.evtx

Resultado:
| Resultado                                  | Respuesta   |
|--------------------------------------------|-------------|
| Se creó el servicio rztbzn.                | ✔️ rztbzn   |

# Paso 4: Ejecutable malicioso descargado
.\DeepBlue.ps1 C:\Users\BTLOTest\Desktop\Investigation\Security.evtx

Resultado:
| Resultado                                                        | Respuesta             |
|------------------------------------------------------------------|-----------------------|
| El archivo `serviceupdate.exe` fue descargado y ejecutado antes de la conexión. | ✔️ serviceupdate.exe |

# Paso 5: Cuenta creada para persistencia
.\DeepBlue.ps1 C:\Users\BTLOTest\Desktop\Investigation\Security.evtx

Resultado:
| Resultado                                                        | Respuesta                   |
|------------------------------------------------------------------|-----------------------------|
| Se creó la cuenta `ServiceAct` con privilegios administrativos.   | ✔️ `net user ServiceAct /add` |

# Paso 6: Grupos donde se añadió la cuenta
.\DeepBlue.ps1 C:\Users\BTLOTest\Desktop\Investigation\Security.evtx

Resultado:
| Resultado                                                               | Respuesta                                    |
|-------------------------------------------------------------------------|----------------------------------------------|
| La cuenta `ServiceAct` fue añadida a los grupos: Administrators, Remote Desktop Users | ✔️ Administrators, Remote Desktop Users      |

## 🏁 **Conclusión**

La investigación confirma:

- La ejecución de `GoogleUpdate.exe` por Mike Smith.
- Actividad maliciosa con Meterpreter a las 10:48:14.
- Creación del servicio `rztbzn`.
- Descarga del ejecutable `serviceupdate.exe` para el shell reverse.
- Creación de la cuenta `ServiceAct` con privilegios elevados.

Estos hallazgos demuestran un compromiso del sistema mediante RDP, seguido de acciones persistentes con Meterpreter.

---

**Herramienta clave:**  
**DeepBlueCLI** permite un análisis rápido y preciso de registros EVTX, acelerando la detección de eventos sospechosos.
