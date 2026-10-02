# 📄 Running-configs

Configuración en ejecución de cada equipo del laboratorio.

| Archivo | Equipo | Estado | Cómo se obtuvo |
|---|---|---|---|
| [`isp-running-config.txt`](isp-running-config.txt) | Router ISP (Cisco IOS) | ✅ Incluido | `show running-config` |
| [`sw1-running-config.txt`](sw1-running-config.txt) | Switch SW-1 (Cisco IOSvL2) | ✅ Incluido | `show running-config` |
| [`fg1-running-config.conf`](fg1-running-config.conf) | FortiGate-1 | 📸 Pendiente de pegar | `show full-configuration` |
| [`fg2-running-config.conf`](fg2-running-config.conf) | FortiGate-2 | 📸 Pendiente de pegar | `show full-configuration` |

## Antes de publicar las de los FortiGate

- Sustituir la clave precompartida: `set psksecret ENC ...` → `set psksecret <PSK>`
- Sustituir hashes de contraseñas de administrador: `set password ENC ...` → `set password <REDACTED>`

## Observaciones sobre las configuraciones incluidas

- El banner aparece como `GC3mez` / `GCez` porque la terminal de IOS no maneja bien la tilde de "Gómez"; el texto original del comando es `Lisbeth Gómez 2025-0701`.
- Las contraseñas de los equipos Cisco son de laboratorio (se ven en los scripts); no deben reutilizarse en equipos reales.
