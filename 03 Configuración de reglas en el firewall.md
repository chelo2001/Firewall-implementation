## Configuración de servidor DHCP para la máquina ubuntu
Antes de configurar más reglas en el firewall, es necesario configurar un servidor DHCP que permita que la máquina Ubuntu adquiera una dirección IP dentro de la red interna. Para eso de debe ir a las opciones Services → DHCP server en pfsense, marcar la opción de habilitar servidor DHCP en la interfaz LAN, dejar las configuraciones de IP como están y configurar la IP del servidor DNS como la IP del router doméstico (192.168.100.1 en este caso), lo cual permite resolución DNS. Una vez hecho esto, se debe ingresar a la máquina Ubuntu para confirmar si se le asignó dirección ip con el comando ip a por ejemplo como se ilustra en la figura 1.
<p align="center">
  <img src="ubuntu-ip-a.png" alt="Salida del comando ip a en Ubuntu mostrando la interfaz enp0s3 con la IP 192.168.1.100/24 asignada por DHCP" width="500">
</p>
<p align="center">
  <em>Figura 1. Configuración de red de Ubuntu: la interfaz enp0s3 obtiene la IP 192.168.1.100/24 por DHCP desde pfSense.</em>
</p>
