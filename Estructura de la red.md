
 ## 1. Topología y Segmentación de Red
El laboratorio implementa un perímetro de red virtualizado utilizando pfSense como pasarela de seguridad entre la red externa y el segmento interno protegido.

- **Red WAN:** Conectada al host/Internet mediante DHCP (`em0`).
- **Red LAN (`192.168.1.0/24`):** Segmento interno aislado donde opera el nodo Wazuh (`em1`).
La figura 1 ilustra un diagrama que permite visualizar de mejor manera la topología de red

## 2. Especificaciones de Hardware Virtual
- **pfSense Firewall:** 
  - vCPU: 1-2
  - RAM: 2 GB
  - Almacenamiento: 20 GB VDI
- **Ubuntu-Desktop:** 
  - vCPU: 2
  - RAM: 4 GB
  - Almacenamiento: 40 GB VDI

