---
name: weather-local
description: Use when necesites consultar el clima actual o pronóstico de una ciudad, o de la ubicación actual detectada por IP, sin necesidad de API key ni configuración previa
---

# Weather Local

## Overview
Consulta el clima desde la terminal usando `curl` contra wttr.in (servicio público, sin API key, sin registro).

## Uso rápido

- Clima actual, ubicación por IP: `curl -s "wttr.in?format=3"`
- Ciudad específica: `curl -s "wttr.in/Buenos+Aires?format=3"`
- Reporte visual completo (ASCII art), ubicación por IP: `curl -s wttr.in`
  - Un solo día (más corto): agregar `?0` a la URL
- JSON para parsear en scripts: `curl -s "wttr.in?format=j1"`
- En español: agregar `&lang=es` (ej: `curl -s "wttr.in/Madrid?format=%l:+%C+%t&lang=es"`)

## Formato personalizado

`curl -s "wttr.in?format=%l:+%c+%t+%h+%w"`

Placeholders más usados:

| Placeholder | Significado |
|---|---|
| `%l` | Ciudad/ubicación |
| `%c` | Condición (emoji) |
| `%C` | Condición (texto) |
| `%t` | Temperatura |
| `%f` | Sensación térmica |
| `%h` | Humedad |
| `%w` | Viento |
| `%p` | Precipitación |

## Notas

- Siempre usar `--max-time 10` en `curl` para evitar que el comando se cuelgue si no hay red.
- La ubicación por IP puede no coincidir con la ubicación real si hay VPN/proxy de por medio — en ese caso, pasar la ciudad explícita en la URL (`wttr.in/<ciudad>`).
- Combinar parámetros con `&` cuando hay más de uno (ej: `?format=3&lang=es`).
