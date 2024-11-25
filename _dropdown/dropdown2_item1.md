---
layout: page
title: 🛡️ Guía para preparar el Examen BTL-1
description: Consejos y recursos
dropdown: BlueTeamsLabs
priority: 1
---
# Guía para preparar el Examen BTL-1
> **Resumen**  
> Este artículo combina consejos y recursos clave para prepararte para la certificación BTL-1, desde la inteligencia de amenazas hasta el análisis forense y la gestión de incidentes.

---

## Introducción

Hace un mes, logré aprobar el examen **Blue Team Level 1 (BTL-1)** en mi primer intento. Fue un gran reto, pero la preparación estructurada y práctica constante fueron esenciales. Esta guía reúne los puntos más importantes y recursos que utilicé para estudiar. Mi objetivo es que, ya seas estudiante actual o estés planeando realizar esta certificación, encuentres aquí todo lo necesario para avanzar con confianza.

---

## Áreas Clave del Examen

El examen abarca diversas disciplinas del equipo azul (Blue Team), como análisis de phishing, inteligencia de amenazas, forense digital, gestión de eventos (SIEM) y respuesta a incidentes. Aquí exploraremos cada área con recursos útiles y ejercicios prácticos.

---

## 1. Análisis de Phishing 🛑

El análisis de phishing es una habilidad clave en el examen. Aprenderás a identificar indicadores de compromiso (IOCs) en correos electrónicos, URLs y archivos adjuntos.

### Artefactos a Investigar
- **Correo Electrónico**: dirección del remitente, servidor de envío, asunto, y fecha/hora.  
- **Web**: URLs completas (defangadas) y dominios.  
- **Archivos**: nombre, extensión y hashes (MD5/SHA256).  

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

El conocimiento teórico predomina aquí. Dedica tiempo al marco **MITRE ATT&CK**, que clasifica tácticas y técnicas utilizadas por adversarios.

### Recursos Clave
- [MITRE ATT&CK](https://attack.mitre.org/)  
- [Awesome Threat Intelligence](https://github.com/hslatman/awesome-threat-intelligence)  

**Ejercicios recomendados**:
- [ATT&CK Challenge](https://blueteamlabs.online/home/challenge/attck-0e4914db5d)  
- [Cipher](https://blueteamlabs.online/home/investigation/cipher-e93c7f5942)
- [MITRE Room](https://tryhackme.com/r/room/mitre)

---

## 3. Forense Digital 🕵️‍♂️

La investigación forense es crítica para identificar y preservar evidencia digital. Se centra en Windows y Linux, incluyendo técnicas como carving, análisis de memoria y obtención de metadatos.

### Herramientas Útiles
- **Windows**: FTK Imager, Volatility.  
- **Linux**: `stat`, `exiftool`, `md5sum`, `sha256sum`.  

**Ejercicios recomendados**:
- [Sukana](https://blueteamlabs.online/home/investigation/sukana-3e7d31b12a)  
- [Sticky Situation](https://blueteamlabs.online/home/investigation/sticky-situation-d408891d73)
- [Autopsy Challenge](https://tryhackme.com/r/room/btautopsye0)
- [Autopsy 2](https://tryhackme.com/r/room/autopsy2ze0)
- [Volatility Challenge](https://tryhackme.com/r/room/volatility)

### Volatility - Comandos Básicos
- Listar procesos: `volatility -f memoria.dmp pslist`  
- Analizar conexiones de red: `volatility -f memoria.dmp netscan`  
- Crear línea de tiempo: `volatility -f memoria.dmp timeliner`

---

## 4. Gestión de Eventos (SIEM) 🔎

El manejo de herramientas como **Splunk** puede ser desafiante para muchos, pero es esencial. La clave es practicar consultas SPL y análisis de eventos.

### Recursos Clave
- [Splunk Documentation](https://docs.splunk.com/Documentation)  
- [TryHackMe: Splunk 101](https://tryhackme.com/room/splunk101)

**Ejercicio recomendado**:
- [Drilldown](https://blueteamlabs.online/home/investigation/drilldown-db9ea241de)
- [Investigando con Splunk](https://tryhackme.com/r/room/investigatingwithsplunk)
- [Splunk 201](https://tryhackme.com/r/room/splunk201)

---

## 5. Respuesta a Incidentes 🚧

Esta es la habilidad más importante del examen. Aprenderás a investigar ataques y proponer acciones de mitigación.

### Ejercicios recomendados  
- [SAM](https://blueteamlabs.online/home/investigation/sam-d310695187)  
- [Deep Blue](https://blueteamlabs.online/home/investigation/deep-blue-a4c18ce507)  

### Análisis de Red
Utiliza **Wireshark** para analizar capturas de tráfico (`.pcap`) y comandos como `netstat` o `wmic` en Windows.

**Ejercicios recomendados**  
- [PCAP Analysis](https://app.letsdefend.io/challenge/pcap-analysis)

---

## Puertos Comunes

| Puerto | Servicio | Descripción |
|--------|----------|-------------|
| 22     | SSH      | Acceso remoto seguro. |
| 80     | HTTP     | Navegación web no segura. |
| 443    | HTTPS    | Navegación web segura. |
| 514    | Syslog   | Notificaciones de sistema. |

---

## Consejos Generales para el Examen 💡

1. **Lee los escenarios con calma.** Si es necesario, relee varias veces.  
2. **Aprovecha San Google y todos tus apuntes.** Es tu mejor aliado durante el examen.  
3. **Valida tus respuestas.** Antes de enviarlas, asegúrate de que cumplen con el formato requerido.  
4. **Practica, practica y practica.** Familiarízate con las herramientas y técnicas antes del examen.

