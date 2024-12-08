layout: page
title: 🛡️ Filtros en Wireshark
description: Consejos y recursos
dropdown: Notas Secretas del SOC
priority: 4# Cheatsheet de Splunk 🔍

Splunk es una plataforma de análisis de datos que ayuda a monitorizar, buscar y analizar grandes volúmenes de datos de manera rápida. A continuación te presentamos algunos de los comandos y filtros más utilizados para maximizar tu uso de Splunk de manera eficiente.

---

## 🔑 Comandos Básicos

| **Comando**                  | **Descripción**                                                                                       |
|------------------------------|-------------------------------------------------------------------------------------------------------|
| `index="main"`               | Filtra por un índice específico (en este caso, "main").                                                |
| `source="logfile.log"`        | Filtra por la fuente de los datos (en este caso, un archivo de log específico).                       |
| `sourcetype="json"`           | Filtra por el tipo de fuente (en este caso, "json").                                                  |
| `host="server1"`              | Filtra por el host (en este caso, "server1").                                                         |
| `*error*`                     | Busca eventos que contengan la palabra "error".                                                       |
| `status=200`                  | Filtra eventos donde el campo "status" sea igual a 200 (por ejemplo, respuestas HTTP OK).            |
| `| stats count`               | Realiza una agregación de contadores, mostrando el número de eventos que coinciden con el filtro.     |

> **Consejo**: Usa estos filtros básicos para empezar a buscar datos específicos dentro de tus registros y eventos.

---

## ⚙️ Comandos de Búsqueda Avanzada

| **Comando**                           | **Descripción**                                                                                   |
|---------------------------------------|---------------------------------------------------------------------------------------------------|
| `index="main" sourcetype="json" | stats count by status`   | Filtra eventos de un índice y sourcetype específico, y realiza una agregación de cuenta por el campo "status".   |
| `index="main" error | top 10 source`   | Encuentra los 10 principales orígenes de eventos con la palabra "error".                            |
| `index="security" | timechart span=1h count` | Realiza un gráfico de línea mostrando el conteo de eventos por hora.                               |
| `index="logs" | stats avg(bytes) by host` | Calcula el promedio de bytes por cada host dentro del índice "logs".                               |
| `index="main" | dedup source`         | Elimina los registros duplicados por el campo "source".                                            |
| `index="web" | eval response_time = end_time - start_time | stats avg(response_time)` | Calcula el tiempo de respuesta promedio entre los eventos "start_time" y "end_time". |

> **Consejo**: Los comandos de búsqueda avanzada son ideales para analizar patrones en los datos y generar visualizaciones como gráficos y tablas.

---

## 🛡️ Comandos de Seguridad

| **Comando**                           | **Descripción**                                                                                   |
|---------------------------------------|---------------------------------------------------------------------------------------------------|
| `index="security" sourcetype="syslog" | stats count by host`   | Filtra los eventos del índice "security" y realiza un conteo por host.                           |
| `index="firewall" | stats values(ip) by action` | Muestra las direcciones IP asociadas con cada acción del firewall (permitir/denegar).               |
| `index="security" | search "failed login" | stats count by user` | Muestra el número de intentos fallidos de inicio de sesión por usuario.                           |
| `index="security" | search "brute force" | stats count`   | Busca eventos que contengan "brute force" (fuerza bruta) y cuenta cuántos se han registrado.     |
| `index="firewall" | search "blocked" | stats count by ip` | Filtra eventos de firewall que indican conexiones bloqueadas y muestra el conteo por IP.          |

> **Consejo**: Los comandos de seguridad son perfectos para realizar auditorías de eventos y detectar patrones relacionados con intentos de intrusión o actividades maliciosas.

---

## 🕒 Comandos de Tiempo y Ordenación

| **Comando**                           | **Descripción**                                                                                   |
|---------------------------------------|---------------------------------------------------------------------------------------------------|
| `index="main" | earliest=-24h@h latest=now` | Filtra eventos ocurridos en las últimas 24 horas.                                                 |
| `index="main" | earliest="2024-12-01T00:00:00" latest="2024-12-05T23:59:59"` | Filtra eventos dentro de un rango de fechas específico. |
| `index="main" | sort - _time`           | Ordena los eventos por el campo `_time` en orden descendente (últimos eventos primero).           |
| `index="main" | sort + bytes`          | Ordena los eventos por el campo "bytes" en orden ascendente.                                      |
| `index="main" | head 10`               | Muestra los primeros 10 eventos después de aplicar el filtro.                                      |

> **Consejo**: Los filtros de tiempo son cruciales para realizar análisis de eventos dentro de rangos de tiempo específicos o para buscar eventos recientes.

---

## 🧰 Comandos de Agregación y Análisis

| **Comando**                           | **Descripción**                                                                                   |
|---------------------------------------|---------------------------------------------------------------------------------------------------|
| `index="web" | stats sum(bytes) by host` | Muestra la suma de bytes enviados o recibidos por cada host en el índice "web".                   |
| `index="web" | timechart span=1h avg(bytes)` | Muestra un gráfico de línea con el promedio de bytes por hora.                                    |
| `index="security" | top 10 src_ip`       | Muestra las 10 direcciones IP de origen más frecuentes en el índice "security".                    |
| `index="main" | stats count by status, host` | Realiza un conteo de eventos por el campo "status" y agrupa por "host".                           |
| `index="main" | chart count over _time by status` | Muestra un gráfico con el conteo de eventos agrupados por el campo "status" en el tiempo.         |

> **Consejo**: Estos comandos de agregación te permiten realizar un análisis más profundo, como contar eventos o calcular promedios y sumas. Utiliza gráficos y tablas para visualizar tendencias y patrones.

---

## 📚 Conclusión

Splunk es una plataforma poderosa para el análisis de datos, y con estos comandos y filtros puedes aprovechar al máximo su potencial. Estos filtros te permitirán analizar patrones, detectar problemas y realizar auditorías de seguridad de manera efectiva.

> **Recuerda**: Combina diferentes comandos y filtros para realizar análisis más complejos y obtener información detallada sobre tu infraestructura.

---

¡A disfrutar del análisis de datos con Splunk! 🚀
