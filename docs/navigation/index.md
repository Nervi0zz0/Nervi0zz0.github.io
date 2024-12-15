---
layout: page
title: 🛡️ Filtros en Wireshark
description: Consejos y recursos
parent: Supervivencia Sin Esfuerzo
priority: 4
---


# Filtros en Wireshark 🔍
Wireshark es una herramienta de análisis de red poderosa y versátil. Aquí te dejamos algunos de los filtros más utilizados para ayudarte a navegar en el tráfico de red y a identificar patrones relevantes de manera eficiente.

---

## 🔑 Filtros Básicos

| **Filtro**                  | **Descripción**                                                                                       |
|-----------------------------|-------------------------------------------------------------------------------------------------------|
| `ip.addr == X.X.X.X`         | Filtra el tráfico hacia o desde la dirección IP especificada.                                         |
| `ip.src == X.X.X.X`          | Filtra el tráfico cuyo origen es la dirección IP especificada.                                        |
| `ip.dst == X.X.X.X`          | Filtra el tráfico cuyo destino es la dirección IP especificada.                                       |
| `tcp.port == 80`             | Filtra todo el tráfico HTTP en el puerto 80.                                                           |
| `udp.port == 53`             | Filtra el tráfico DNS que utiliza el puerto 53.                                                       |
| `tcp.flags.syn == 1`         | Filtra los paquetes de inicio de una conexión TCP (SYN).                                              |
| `tcp.flags.fin == 1`         | Filtra los paquetes que indican el cierre de una conexión TCP (FIN).                                 |
| `http`                       | Filtra todo el tráfico HTTP.                                                                          |

> **Consejo**: Usa estos filtros básicos para enfocar tu análisis en el tráfico más relevante para tareas específicas como inspeccionar tráfico HTTP o monitorear la actividad de una IP en particular.

---

## ⚙️ Filtros Avanzados

| **Filtro**                           | **Descripción**                                                                                   |
|--------------------------------------|---------------------------------------------------------------------------------------------------|
| `tcp.stream eq X`                    | Filtra el flujo TCP con el identificador de flujo X.                                               |
| `ip.proto == 6`                      | Filtra el tráfico TCP (Protocolo de Internet TCP).                                                |
| `ip.proto == 17`                     | Filtra el tráfico UDP (Protocolo de Internet UDP).                                                |
| `dns.qry.name == "example.com"`      | Filtra las consultas DNS para el dominio "example.com".                                           |
| `http.request.method == "GET"`       | Filtra las solicitudes HTTP que usan el método GET.                                               |
| `http.response.code == 200`          | Filtra las respuestas HTTP con el código de estado 200 (OK).                                      |
| `ssl.record.version == 0x0303`       | Filtra el tráfico SSL/TLS de la versión 1.2.                                                       |

> **Consejo**: Los filtros avanzados son ideales cuando necesitas analizar protocolos específicos, como DNS, SSL o HTTP, o cuando trabajas con flujos TCP o UDP complejos.

---

## 🛡️ Filtros de Seguridad y Análisis

| **Filtro**                           | **Descripción**                                                                                   |
|--------------------------------------|---------------------------------------------------------------------------------------------------|
| `tcp.analysis.flags`                 | Filtra los paquetes TCP con análisis de flags, útil para detectar retransmisiones o duplicados.   |
| `icmp`                               | Filtra todo el tráfico ICMP (por ejemplo, Echo Request y Echo Reply).                             |
| `http.authbasic`                     | Filtra las solicitudes HTTP que contienen autenticación básica.                                   |
| `ftp`                                | Filtra todo el tráfico FTP.                                                                       |
| `tcp.port == 443`                    | Filtra el tráfico TLS/SSL (HTTPS).                                                                |
| `tcp.analysis.retransmission`        | Filtra las retransmisiones TCP, útiles para detectar problemas en la red.                         |
| `frame.len > 1500`                   | Filtra los paquetes cuyo tamaño es mayor a 1500 bytes.                                            |
| `ssl.handshake.type == 1`            | Filtra los paquetes "Client Hello" en un handshake SSL/TLS.                                        |

> **Consejo**: Estos filtros son esenciales para realizar análisis de seguridad en redes, como la identificación de tráfico malicioso o problemas en la red.

---

## 🕒 Filtros de Tiempo y Orden

| **Filtro**                           | **Descripción**                                                                                   |
|--------------------------------------|---------------------------------------------------------------------------------------------------|
| `frame.time >= "2024-12-01 00:00:00"` | Filtra los paquetes capturados a partir de una fecha y hora específica.                           |
| `frame.time <= "2024-12-05 23:59:59"` | Filtra los paquetes capturados hasta una fecha y hora específica.                                 |
| `frame.time >= "2024-12-01 00:00:00" && frame.time <= "2024-12-05 23:59:59"` | Filtra los paquetes dentro de un rango de fechas específico. |

> **Consejo**: El uso de filtros de tiempo te permite realizar un análisis más detallado y restringido a intervalos específicos, lo que es útil para auditorías o investigaciones forenses.

---

## 🧰 Consejos y Buenas Prácticas

- **Combinación de filtros**: Puedes combinar múltiples filtros usando `&&` (Y) o `||` (O) para crear filtros más complejos. Ejemplo: `ip.src == 192.168.1.1 && tcp.port == 80`.
- **Expresiones regulares**: Usa expresiones regulares en los filtros para buscar patrones complejos dentro del tráfico de red.
- **Excluir tráfico específico**: Puedes excluir tráfico con el operador `not`. Ejemplo: `not icmp` excluye todo el tráfico ICMP.
- **Filtro por protocolos**: Filtra por protocolos específicos como `http`, `dns`, `ftp`, etc., para concentrarte en el análisis de un tipo de tráfico particular.

---

> **Recuerda**: Cuanto más específicos sean tus filtros, más rápido y eficiente será tu análisis.

---

  <hr style="border: none; border-top: 1px solidrgb(255, 254, 248); margin: 50px 0; box-shadow: 0 1px 2px rgba(255, 215, 0, 0.6);">

  <div style="text-align: center; margin: 50px auto;">
    <img src="/assets/images/cojo.png" alt="Firma" style="max-width: 20%; border-radius: 50%; border: 1px solid #FFD700; box-shadow: 0 12px 24px rgba(0, 0, 0, 0.9);">
  </div>
  <div style="text-align: center; margin-top: 40px;">
    <p style="font-size: 0.9em; color: #888;">© 2024 Nervi0zz0</p>
  </div>