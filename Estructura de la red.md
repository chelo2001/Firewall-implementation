## Máquinas a utilizar
1. Ubuntu Desktop 
2. Segundo elemento o paso
3. Tercer elemento o paso
 ## 1. Topología y Segmentación de Red
El laboratorio implementa un perímetro de red virtualizado utilizando pfSense como pasarela de seguridad entre la red externa y el segmento interno protegido.

- **Red WAN:** Conectada al host/Internet mediante DHCP (`em0`).
- **Red LAN (`192.168.1.0/24`):** Segmento interno aislado donde opera el nodo Wazuh (`em1`).

## 2. Especificaciones de Hardware Virtual
- **pfSense Firewall:** 
  - vCPU: 1
  - RAM: 2 GB
  - Almacenamiento: 20 GB VDI
- **Wazuh SIEM (Ubuntu Server):** 
  - vCPU: 2
  - RAM: 4 GB
  - Almacenamiento: 40 GB VDI

## Configuración del entorno de laboratorio
En la figura 1 se muestra cómo estará configurado el laboratorio a nivel de red. El firewall 
