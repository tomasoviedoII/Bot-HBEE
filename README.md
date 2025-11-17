# 🤖 Bot de WhatsApp + sistema de tickets — HBEE

Sistema de soporte que combina:

1. Un **bot de WhatsApp** (Node.js + `whatsapp-web.js`) que recibe mensajes de los usuarios y genera tickets automáticamente.
2. Un **panel web** (PHP + MySQL) donde los agentes pueden gestionar esos tickets: ver el historial, cambiar estados, responder y cerrar.

> Proyecto pensado para uso real dentro de un entorno de soporte (por ejemplo, hospital HBEE / soporte técnico).

---

## 🧩 Arquitectura general

- El usuario escribe a un número de **WhatsApp**.
- El **bot**:
  - Identifica el número de teléfono.
  - Crea o busca el contacto en base de datos.
  - Abre un ticket nuevo o recupera el existente.
  - Guarda cada mensaje como una “respuesta” dentro del ticket.
- El **panel web**:
  - Lista los tickets (filtros por estado, agente, fecha, etc.).
  - Permite cambiar el estado (nuevo, en curso, resuelto, pausado…).
  - Muestra el historial de mensajes.
  - (Opcional) Envía respuestas de vuelta al usuario vía bot.

---

## 🚀 Características principales

- Creación automática de tickets al recibir un mensaje por WhatsApp.
- Asociación de tickets por número de teléfono / contacto.
- Múltiples estados de ticket, por ejemplo:
  - 🟢 Nuevo
  - 🟡 En curso
  - 🟠 Pausado
  - 🔴 Resuelto / Cerrado
- Asignación de tickets a agentes específicos.
- Registro de tiempos de atención (inicio, pausa, fin).
- Panel web con filtros para ver backlog, tickets asignados, resueltos, etc.

---

## 🧱 Stack tecnológico

### Bot

- Node.js
- [whatsapp-web.js](https://github.com/pedroslopez/whatsapp-web.js)
- dotenv
- MySQL (vía librería de conexión o servicios propios)
- moment / moment-timezone (para fechas y horarios)

### Panel web

- PHP 8+
- MySQL
- HTML, CSS
- (Opcional) Tailwind / Bootstrap

---

## 📸 Capturas de pantalla

Se recomienda agregar una carpeta `docs/` con imágenes del panel:

```text
docs/
  ├─ tickets-list.png       # listado de tickets
  ├─ ticket-detail.png      # detalle de ticket
  └─ dashboard.png          # (opcional) estadísticas
