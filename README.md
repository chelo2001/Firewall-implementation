# Firewall-implementation
Proyecto de implementación de firewall y reglas para bloqueo y paso de tráfico de red entre distintas redes mediante herramienta open source pfsense y máquinas virtuales.
<p align="center">
  <img src="images/topologia-red-equipos.png" alt="Topología de red con equipos de escritorio: Kali, pfSense y Ubuntu, conectados por la red puente 192.168.100.0/24 y la red interna 192.168.1.0/24" width="500">
</p>

## 📐 Topología y Segmentación de Red

| Equipo | Interfaz en VirtualBox | Dirección IP / Subred | Función |
| :--- | :--- | :--- | :--- |
| **pfSense (WAN)** | Adaptador Puente | `192.168.100.X/24` | Interfaz externa expuesta a la red puente |
| **pfSense (LAN)** | Red Interna (`intnet`) | `192.168.1.1/24` | Gateway por defecto para segmento interno |
| **Kali Linux** | Adaptador Puente | `192.168.100.Y/24` | Simulación de origen externo / auditoría |
| **Ubuntu** | Red Interna (`intnet`) | `192.168.1.Z/24` | Cliente interno protegido |

---

## 🛡️ Políticas y Reglas de Firewall Configuradas

### Reglas en Interfaz WAN / LAN
1. **Bloqueo de Tráfico Inbound No Solicitado (Pass vs Reject/Block):**
   * *Acción:* `REJECT` / `BLOCK`
   * *Origen:* Red WAN (`192.168.100.0/24`)
   * *Destino:* Red LAN (`192.168.1.0/24`)
   * *Justificación:* Evitar accesos no autorizados hacia el segmento interno desde el exterior.
2. **Permiso Controlado Outbound:**
   * *Acción:* `PASS`
   * *Protocolo:* ICMP / TCP (Puertos 80, 443)
   * *Origen:* LAN Net
   * *Destino:* Any

---

## 🧪 Pruebas de Verificación (Testing)

### 1. Verificación de Reglas de Rechazo/Bloqueo desde Kali Linux
* **Prueba:** Escaneo de puertos y prueba de conectividad `ping` desde Kali Linux hacia la IP de la máquina Ubuntu.
* **Resultado Esperado:** Paquetes rechazados / sin respuesta (`Destination Host Unreachable` o filtrados).
```bash
nmap -Pn -p 22,80,443 192.168.1.Z
