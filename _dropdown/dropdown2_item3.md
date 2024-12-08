---
layout: page
title: 🛡️ Cheatsheet de Splunk 
description: Consejos y recursos
dropdown: Notas de un Cojo
priority: 4
---

# Cheatsheet de Splunk 🔍

Splunk es una poderosa herramienta de análisis y visualización de datos que permite realizar búsquedas, monitorización y análisis en tiempo real de grandes volúmenes de datos. A continuación, te presentamos los comandos más utilizados en Splunk, organizados de manera eficiente y con descripciones para facilitar su comprensión.

---

## 🔑 Comandos Básicos

Estos comandos son ideales para empezar a buscar y filtrar datos dentro de Splunk.

| **Comando**                      | **Descripción**                                                                                         |
|-----------------------------------|---------------------------------------------------------------------------------------------------------|
| `index="main"`                   | Filtra los eventos que pertenecen al índice llamado "main". Ideal para empezar a trabajar con datos de un índice específico.       |
| `source="logfile.log"`            | Filtra los eventos que provienen de una fuente específica, en este caso, un archivo de log.                            |
| `sourcetype="json"`               | Filtra eventos basados en un tipo de fuente determinado (en este caso, los eventos con sourcetype "json").                         |
| `host="server1"`                  | Filtra eventos por el nombre del host. Utilizado para analizar registros específicos de una máquina o servidor.                 |
| `*error*`                         | Realiza una búsqueda de eventos que contengan la palabra "error", útil para identificar fallos en los sistemas.                   |
| `status=200`                      | Filtra los eventos donde el campo "status" tenga el valor 200, lo que generalmente indica una respuesta exitosa en HTTP.        |
| `| stats count`                   | Realiza una agregación básica para contar la cantidad de eventos dentro del conjunto de datos filtrados.     |

> **Consejo**: Utiliza estos comandos básicos para realizar búsquedas simples y empezar a filtrar eventos de manera eficaz.

---

## ⚙️ Comandos de Búsqueda Avanzada

Estos comandos permiten realizar búsquedas más complejas y análisis detallados sobre los datos de Splunk.

| **Comando**                            | **Descripción**                                                                                                    |
|----------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| `index="main" sourcetype="json" | stats count by status`     | Filtra eventos por el índice "main" y el sourcetype "json", luego realiza un conteo de eventos agrupados por el campo "status". |
| `index="main" error | top 10 source`     | Filtra eventos que contienen la palabra "error" y muestra las 10 principales fuentes de esos eventos.                     |
| `index="security" | timechart span=1h count` | Genera una gráfica que muestra la cantidad de eventos por hora, útil para analizar eventos en función del tiempo.           |
| `index="logs" | stats avg(bytes) by host`  | Calcula el promedio de "bytes" por cada host, ideal para analizar el volumen de datos por servidor o máquina.            |
| `index="main" | dedup source`            | Elimina los registros duplicados basados en el campo "source", útil para limpiar datos repetidos en grandes volúmenes.    |
| `index="web" | eval response_time = end_time - start_time | stats avg(response_time)` | Calcula el tiempo de respuesta promedio entre los campos "start_time" y "end_time". Ideal para analizar tiempos de latencia. |

> **Consejo**: Utiliza las búsquedas avanzadas para identificar patrones más complejos en los datos, realizar análisis estadísticos y generar informes detallados.

---

## 🛡️ Comandos de Seguridad

Son comandos esenciales para realizar auditorías de seguridad y detectar posibles actividades maliciosas dentro de la infraestructura.

| **Comando**                            | **Descripción**                                                                                                  |
|----------------------------------------|--------------------------------------------------------------------------------------------------------------------|
| `index="security" sourcetype="syslog" | stats count by host`    | Filtra los eventos de tipo "syslog" en el índice "security" y muestra un conteo de eventos agrupados por host.        |
| `index="firewall" | stats values(ip) by action` | Muestra las direcciones IP asociadas con cada acción del firewall (permitir o bloquear), útil para detectar intentos sospechosos. |
| `index="security" | search "failed login" | stats count by user`  | Filtra los eventos que contienen "failed login" (intentos fallidos de inicio de sesión) y agrupa el conteo por usuario. |
| `index="security" | search "brute force" | stats count`         | Busca eventos que contengan la palabra "brute force" para identificar posibles intentos de ataque por fuerza bruta. |
| `index="firewall" | search "blocked" | stats count by ip`    | Filtra eventos del firewall que indican tráfico bloqueado y cuenta la cantidad de intentos por cada IP.                 |

> **Consejo**: Los comandos de seguridad son imprescindibles para auditar el tráfico de red y los intentos de acceso no autorizado, ayudando a detectar y prevenir intrusiones.

---

## 🕒 Comandos de Tiempo y Ordenación

La manipulación de los datos según el tiempo es crucial para el análisis de eventos y la identificación de tendencias.

| **Comando**                            | **Descripción**                                                                                                   |
|----------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| `index="main" | earliest=-24h@h latest=now` | Filtra los eventos ocurridos en las últimas 24 horas, facilitando el análisis de los registros más recientes.         |
| `index="main" | earliest="2024-12-01T00:00:00" latest="2024-12-05T23:59:59"` | Filtra eventos dentro de un rango de fechas específico, ideal para auditorías de periodos determinados. |
| `index="main" | sort - _time`             | Ordena los eventos por el campo "_time" en orden descendente, mostrando primero los eventos más recientes.           |
| `index="main" | sort + bytes`            | Ordena los eventos por el campo "bytes" en orden ascendente, útil para identificar picos de tráfico o anomalías.     |
| `index="main" | head 10`                 | Muestra los primeros 10 eventos de la búsqueda actual, ideal para obtener un resumen rápido de los eventos más relevantes. |

> **Consejo**: Los filtros de tiempo y ordenación son esenciales para realizar análisis en ventanas temporales específicas o para explorar eventos recientes en tiempo real.

---

## 🧰 Comandos de Agregación y Análisis

Estos comandos permiten realizar cálculos y agregaciones sobre grandes volúmenes de datos, proporcionándote análisis más detallados y agregados.

| **Comando**                            | **Descripción**                                                                                                   |
|----------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| `index="web" | stats sum(bytes) by host`    | Suma los valores del campo "bytes" por cada host, útil para ver cuántos datos han sido procesados por cada servidor.  |
| `index="web" | timechart span=1h avg(bytes)` | Muestra un gráfico de línea con el promedio de bytes procesados cada hora, ideal para ver tendencias de tráfico.        |
| `index="security" | top 10 src_ip`         | Muestra las 10 direcciones IP de origen más frecuentes, útil para identificar posibles puntos de origen de ataques.   |
| `index="main" | stats count by status, host` | Realiza un conteo de eventos por "status" y los agrupa por "host", ideal para análisis de errores o éxito por servidor. |
| `index="main" | chart count over _time by status` | Genera un gráfico de barras que muestra la cantidad de eventos agrupados por el campo "status" a lo largo del tiempo. |

> **Consejo**: Utiliza los comandos de agregación para analizar grandes volúmenes de datos de forma resumida, y crear gráficos para una mejor visualización de tendencias.

---



---



