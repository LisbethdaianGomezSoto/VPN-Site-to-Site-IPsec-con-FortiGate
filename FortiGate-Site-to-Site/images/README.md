# 📸 Capturas de pantalla (evidencias)

Todas las imágenes del README viven en esta carpeta, ordenadas por sección.

**Estado:** ✅ ya incluida · 📸 pendiente de capturar y subir con **exactamente** ese nombre y en esa carpeta.

> **Antes de subir las capturas de la VPN:** tapa la **clave precompartida** (PSK) y recorta las líneas de claves de sesión (`SK_ei`, `SK_ai`, `key=`) de las salidas de `diagnose vpn ...`.


## 📂 `01-topologia/`

| Estado | Archivo | Dónde se captura | Qué debe verse |
|---|---|---|---|
| ✅ | [`01-diagrama-enunciado.png`](01-diagrama-enunciado.png) | Enunciado | Diagrama de la infraestructura del enunciado |
| ✅ | [`02-topologia-gns3.png`](02-topologia-gns3.png) | GNS3 | Topología completa (conviene recapturarla sin el mensaje emergente del enlace) |

## 📂 `02-isp-switch/`

| Estado | Archivo | Dónde se captura | Qué debe verse |
|---|---|---|---|
| 📸 | `01-isp-show-ip-interface-brief.png` | Consola del ISP | `show ip interface brief` con f0/0 y f0/1 en up/up |
| 📸 | `02-switch-show-vlan-brief.png` | Consola del SW-1 | `show vlan brief` con la VLAN 10 USUARIOS y Gi0/1 dentro |
| 📸 | `03-switch-show-interfaces-trunk.png` | Consola del SW-1 | `show interfaces trunk` con Gi0/0 en trunk y la VLAN 10 permitida |
| 📸 | `04-switch-show-interfaces-status.png` | Consola del SW-1 | `show interfaces status` con Gi0/0 y Gi0/1 en connected |
| 📸 | `05-switch-show-ip-ssh.png` | Consola del SW-1 | `show ip ssh` con SSH versión 2 habilitado |

## 📂 `03-fortigate-1/`

| Estado | Archivo | Dónde se captura | Qué debe verse |
|---|---|---|---|
| 📸 | `01-consola-vlan10.png` | Consola del FG-1 | Comandos del script de acceso inicial y `show system interface VLAN10` |
| ✅ | [`02-port1-wan.png`](02-port1-wan.png) | GUI FG-1: port1 | IP `203.7.1.2/255.255.255.252` y solo PING |
| ✅ | [`03-interfaces.png`](03-interfaces.png) | GUI FG-1: Network > Interfaces | Lista de interfaces con port1, VLAN10 y el DHCP (recapturar tras quitar HTTP) |
| 📸 | `04-ruta-por-defecto.png` | GUI FG-1: Network > Static Routes | Ruta `0.0.0.0/0` hacia `203.7.1.1` por port1 |
| 📸 | `05-dhcp-server-vlan10.png` | GUI FG-1: Network > Interfaces > VLAN10 | Sección DHCP Server con el rango `10.7.1.10-10.7.1.100` |
| 📸 | `06-politica-lan-to-wan.png` | GUI FG-1: Firewall Policy | Política `LAN-to-WAN` (VLAN10 → port1) con NAT habilitado |
| 📸 | `07-objetos-direccion.png` | GUI FG-1: Policy & Objects > Addresses | Objetos `VPN-LOCAL` y `VPN-REMOTE` con sus subredes |
| 📸 | `08-rutas-vpn-tunel-y-blackhole.png` | GUI FG-1: Network > Static Routes | Las dos rutas hacia `10.7.2.0/28`: por el túnel (distancia 10) y Blackhole (254) |
| 📸 | `09-politicas-vpn.png` | GUI FG-1: Firewall Policy | Las dos políticas del túnel con NAT deshabilitado |

## 📂 `04-fortigate-2/`

| Estado | Archivo | Dónde se captura | Qué debe verse |
|---|---|---|---|
| 📸 | `01-consola-port3-admin.png` | Consola del FG-2 | Comandos del script de acceso inicial del port3 |
| 📸 | `02-port1-wan.png` | GUI FG-2: Network > Interfaces > port1 | IP `198.7.1.2/255.255.255.252`, role WAN, solo PING |
| 📸 | `03-port2-lan.png` | GUI FG-2: Network > Interfaces > port2 | IP `10.7.2.1/255.255.255.240`, role LAN |
| 📸 | `05-ruta-por-defecto.png` | GUI FG-2: Network > Static Routes | Ruta `0.0.0.0/0` hacia `198.7.1.1` por port1 |
| ✅ | [`06-objeto-vpn-local.png`](06-objeto-vpn-local.png) | GUI FG-2: Addresses | Objeto `VPN-LOCAL` = `10.7.2.0/255.255.255.240` |
| 📸 | `06-politica-lan-to-wan.png` | GUI FG-2: Firewall Policy | Política `LAN-to-WAN` (port2 → port1) con NAT habilitado |
| ✅ | [`07-ruta-hacia-vpn.png`](07-ruta-hacia-vpn.png) | GUI FG-2: Static Routes | Ruta hacia `10.7.1.0/25` por `VPN-FG2-FG1`, distancia 10 |
| 📸 | `08-ruta-blackhole.png` | GUI FG-2: Network > Static Routes | Ruta Blackhole hacia `10.7.1.0/25` con distancia 254 |
| 📸 | `09-politicas-vpn.png` | GUI FG-2: Firewall Policy | Las dos políticas del túnel con NAT deshabilitado |
| 📸 | `10-interfaces.png` | GUI FG-2: Network > Interfaces | Lista de interfaces con port1, port2 y port3 configurados |

## 📂 `05-servidor-web/`

| Estado | Archivo | Dónde se captura | Qué debe verse |
|---|---|---|---|
| ✅ | [`01-network-configuration.png`](01-network-configuration.png) | GNS3: Network configuration | Bloque de red del servidor sin `#` |
| 📸 | `02-ip-addr-show-eth0.png` | Consola del servidor | `ip addr show eth0` y `ip route` con `10.7.2.2/28` y gateway `10.7.2.1` |
| 📸 | `03-netstat-puertos-80-443.png` | Consola del servidor | `netstat -tln` con Apache escuchando en 80 y 443 |

## 📂 `06-vpn/`

| Estado | Archivo | Dónde se captura | Qué debe verse |
|---|---|---|---|
| ✅ | [`01-tunel-red.png`](01-tunel-red.png) | GUI FG-1: IPsec Tunnels | Sección Network del túnel (clave tapada) |
| ✅ | [`02-fase1.png`](02-fase1.png) | GUI FG-1: IPsec Tunnels | Fase 1: IKE 2, DES + SHA256, DH 14 (clave tapada) |
| ✅ | [`03-fase2.png`](03-fase2.png) | GUI FG-1: IPsec Tunnels | Fase 2: DES + SHA256, PFS con DH 14, lifetime 43200 |
| 📸 | `04-fg2-tunel-red.png` | GUI FG-2: VPN > IPsec Tunnels | Sección Network del túnel `VPN-FG2-FG1` (**tapa la clave precompartida**) |
| 📸 | `05-fg2-fase1-fase2.png` | GUI FG-2: VPN > IPsec Tunnels | Fase 1 y Fase 2 del FG-2 (**tapa la clave precompartida**) |
| 📸 | `06-ike-gateway-list.png` | Consola del FG-1 | `diagnose vpn ike gateway list` recortada, **sin las líneas SK_ de claves** |
| 📸 | `08-dashboard-ipsec-up.png` | GUI FG-1: Dashboard > Network > IPsec | Túnel en estado Up |

## 📂 `07-pruebas/`

| Estado | Archivo | Dónde se captura | Qué debe verse |
|---|---|---|---|
| 📸 | `01-ipconfig-dhcp.png` | PC de usuarios | `ipconfig` con la IP recibida por DHCP y gateway `10.7.1.1` |
| 📸 | `02-ping-tunel-activo.png` | PC de usuarios | `ping 10.7.2.2` con respuestas **desde 10.7.2.2** |
| 📸 | `03-tracert-tunel-activo.png` | PC de usuarios | `tracert 10.7.2.2` llegando al servidor |
| 📸 | `04-https-servidor.png` | PC de usuarios | `https://10.7.2.2` mostrando la página del servidor |
| 📸 | `05-ping-continuo-tunel-activo.png` | PC de usuarios | `ping -t 10.7.2.2` respondiendo |
| 📸 | `06-tunel-deshabilitado.png` | GUI FG-1: Network > Interfaces | Interfaz `VPN-FG1-FG2` con Status Disabled |
| 📸 | `07-ping-falla.png` | PC de usuarios | `ping -t 10.7.2.2` fallando (tiempo agotado o destino inaccesible) |
| 📸 | `08-tracert-falla.png` | PC de usuarios | `tracert 10.7.2.2` fallando |
| 📸 | `09-https-falla.png` | PC de usuarios | `https://10.7.2.2` sin cargar |
| 📸 | `10-control-ping-isp.png` | PC de usuarios | `ping 10.7.1.1` y `ping 203.7.1.1` respondiendo con el túnel apagado |
| 📸 | `11-tunel-diag-deshabilitado.png` | Consola del FG-1 | `diagnose vpn tunnel list` con `accept_traffic=0` y `sa=0` (**recortada, sin claves**) |
| 📸 | `12-tunel-reactivado.png` | GUI FG-1: Network > Interfaces | Interfaz del túnel con Status Enabled |
| 📸 | `13-ping-recuperado.png` | PC de usuarios | `ping -t 10.7.2.2` volviendo a responder |
| 📸 | `14-tunel-diag-reactivado.png` | Consola del FG-1 | `diagnose vpn tunnel list` con `accept_traffic=1` y `sa=1` (**recortada, sin claves**) |


## 📂 `09-intento-asistente/`

| Estado | Archivo | Dónde se captura | Qué debe verse |
|---|---|---|---|
| ✅ | [`01-rutas-fg2-asistente.png`](01-rutas-fg2-asistente.png) | GUI FG-2: Static Routes | Rutas creadas por el asistente (primer intento) |
| ✅ | [`02-politicas-fg2-asistente.png`](02-politicas-fg2-asistente.png) | GUI FG-2: Firewall Policy | Políticas creadas por el asistente (primer intento) |

## 💡 Consejos

- Usa el mismo tamaño de ventana en todas las capturas y que se vea la URL o la barra de título del equipo.
- Para las salidas de consola, captura la ventana completa para que se vea el comando y su resultado.
- Antes de las capturas finales, quita `http` del acceso administrativo de las interfaces.
