---
title: Examen BTL-1
parent: BTL
nav_order: 1
---

---

![BTL-1](../assets/img/btl1.png)

> **Resumen**  
> En este artículo encontrarás consejos prácticos y recursos clave para prepararte para la certificación **BTL-1**. Desde inteligencia de amenazas hasta análisis forense y gestión de incidentes, cubrimos las áreas fundamentales del examen.

---

## Introducción

Hace un mes, logré aprobar el examen **Blue Team Level 1 (BTL-1)** en mi primer intento, y aunque fue un desafío, la preparación estructurada y la práctica constante fueron esenciales. Este artículo compila los puntos más relevantes que me ayudaron a prepararme. Si estás considerando esta certificación, aquí encontrarás los recursos y consejos necesarios para avanzar con confianza.

---

## Áreas Clave del Examen

El examen **BTL-1** cubre varias disciplinas del equipo azul, incluidas el análisis de phishing, la inteligencia de amenazas, el forense digital, la gestión de eventos (SIEM) y la respuesta a incidentes. A continuación, exploramos cada área con los recursos más útiles y ejercicios prácticos.

---

## 1. Análisis de Phishing 🛑

El análisis de phishing es esencial para detectar ataques mediante correos electrónicos maliciosos. Durante el examen, se evalúa tu capacidad para identificar indicadores de compromiso (IOCs) en correos, URLs y archivos adjuntos.

### Artefactos a Investigar
- **Correo Electrónico**: Remitente, servidor de envío, asunto, fecha y hora.  
- **Web**: URLs (defangadas) y dominios.  
- **Archivos**: Nombres, extensiones y hashes (MD5/SHA256).

### Herramientas Útiles
- **Visualización**: [URLScan](https://urlscan.io/), [URL2PNG](https://www.url2png.com/).  
- **Reputación**: [VirusTotal](https://www.virustotal.com/gui/), [URLhaus](https://urlhaus.abuse.ch/).  
- **Análisis Sandbox**: [Hybrid Analysis](https://www.hybrid-analysis.com/).

**Ejercicios recomendados**:
- [Phishing Analysis](https://blueteamlabs.online/home/challenge/phishing-analysis-f92ef500ce)  
- [Phishing Analysis 2](https://blueteamlabs.online/home/challenge/phishing-analysis-2-a1091574b8)  
- [Phishing Email Challenge](https://app.letsdefend.io/challenge/phishing-email)  
- [Email Analysis](https://app.letsdefend.io/challenge/email-analysis)

---

## 2. Inteligencia de Amenazas 🧠

La inteligencia de amenazas es un componente clave del examen, que pone a prueba tu comprensión del marco **MITRE ATT&CK**, un sistema que clasifica las tácticas y técnicas de los adversarios.

### Recursos Clave
- [MITRE ATT&CK](https://attack.mitre.org/)  
- [Awesome Threat Intelligence](https://github.com/hslatman/awesome-threat-intelligence)  

**Ejercicios recomendados**:
- [ATT&CK Challenge](https://blueteamlabs.online/home/challenge/attck-0e4914db5d)  
- [Cipher](https://blueteamlabs.online/home/investigation/cipher-e93c7f5942)  
- [MITRE Room](https://tryhackme.com/r/room/mitre)

---

## 3. Forense Digital 🕵️‍♂️

El análisis forense es fundamental para identificar, preservar y analizar evidencia digital. En este examen, se evalúa tu capacidad para trabajar tanto con sistemas Windows como Linux y usar técnicas como el carving y el análisis de memoria.

### Herramientas Útiles
- **Windows**: FTK Imager, Volatility.  
- **Linux**: `stat`, `exiftool`, `md5sum`, `sha256sum`.

**Ejercicios recomendados**:
- [Sukana](https://blueteamlabs.online/home/investigation/sukana-3e7d31b12a)  
- [Sticky Situation](https://blueteamlabs.online/home/investigation/sticky-situation-d408891d73)  
- [Autopsy Challenge](https://tryhackme.com/r/room/btautopsye0)  
- [Autopsy 2](https://tryhackme.com/r/room/autopsy2ze0)  
- [Volatility Challenge](https://tryhackme.com/r/room/volatility)

### Comandos Básicos de Volatility
- Listar procesos: `volatility -f memoria.dmp pslist`  
- Analizar conexiones de red: `volatility -f memoria.dmp netscan`  
- Crear línea de tiempo: `volatility -f memoria.dmp timeliner`

---

## 4. Gestión de Eventos (SIEM) 🔎

El manejo de herramientas SIEM, como **Splunk**, es crucial. La clave aquí es practicar las consultas SPL y aprender a analizar grandes volúmenes de datos y eventos.

### Recursos Clave
- [Splunk Documentation](https://docs.splunk.com/Documentation)  
- [TryHackMe: Splunk 101](https://tryhackme.com/room/splunk101)

**Ejercicio recomendado**:
- [Drilldown](https://blueteamlabs.online/home/investigation/drilldown-db9ea241de)  
- [Investigando con Splunk](https://tryhackme.com/r/room/investigatingwithsplunk)  
- [Splunk 201](https://tryhackme.com/r/room/splunk201)

---

## 5. Respuesta a Incidentes 🚧

La capacidad de responder a incidentes es la habilidad más importante que se evalúa en el examen. Deberás investigar ciberataques y proponer acciones para mitigar los daños.

**Ejercicios recomendados**:
- [SAM](https://blueteamlabs.online/home/investigation/sam-d310695187)  
- [Deep Blue](https://blueteamlabs.online/home/investigation/deep-blue-a4c18ce507)

### Análisis de Red
Utiliza **Wireshark** para analizar capturas de tráfico (`.pcap`) y herramientas como `netstat` o `wmic` en Windows.

**Ejercicio recomendado**:
- [PCAP Analysis](https://app.letsdefend.io/challenge/pcap-analysis)

---

## Puertos Comunes

| Puerto | Servicio | Descripción                    |
|--------|----------|--------------------------------|
| 22     | SSH      | Acceso remoto seguro.          |
| 80     | HTTP     | Navegación web no segura.      |
| 443    | HTTPS    | Navegación web segura.         |
| 514    | Syslog   | Notificaciones de sistema.     |

---

## Consejos Generales para el Examen 💡

1. **Lee los escenarios cuidadosamente.** Si es necesario, relee varias veces para asegurarte de entender el contexto.  
2. **Usa todos los recursos disponibles.** San Google y tus apuntes son tus mejores aliados durante el examen.  
3. **Valida tus respuestas.** Asegúrate de que tus respuestas cumplan con el formato y requisitos especificados.  
4. **Practica constantemente.** Familiarízate con las herramientas y técnicas antes de presentarte al examen. Cuanto más practiques, más preparado estarás.

---

Esta guía te proporcionará las bases para estudiar de manera efectiva y afrontar el examen **BTL-1** con confianza. ¡Prepárate, practica y afronta el examen con todo lo aprendido!

