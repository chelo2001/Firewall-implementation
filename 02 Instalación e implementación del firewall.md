## Descarga del instalador
Para la implementación de la herramienta de firewall pfsense se debe ingresar a la siguiente url;

[Download pfSense Community Edition](https://www.pfsense.org/download/)

Se debe seleccionar la opción que se muestra a continuación.
<p align="center">
  <img src="pfsense-descarga-resaltada.png" alt="Página de descarga de Netgate Installer con la opción AMD64 ISO IPMI/Virtual Machines resaltada" width="700">
</p>
<p align="center">
  <em>Figura 1. Descarga de pfSense: selecciona la opción AMD64 ISO IPMI/Virtual Machines para instalarlo en una máquina virtual.</em>
</p>
Una vez descargado el instalador, se debe descomprimir el archivo para obtener la ISO, importar la ISO, configurar las 2 interfaces de red en virtualbox (una en modo puente y la otra con conexión hacia una red interna que conectará con la máquina ubuntu), ejecutar la máquina e instalar el firewall pfsense. Una vez hecho todo lo anterior, se debe remover del disco óptico de virtualbox la ISO y reiniciar la máquina. Al hacer eso, aparecerá la terminal que se muestra en la figura 2.
<p align="center">
  <img src="pfsense-consola.png" alt="Consola de pfSense 2.9.0 en VirtualBox mostrando la interfaz WAN con IP 192.168.100.152/24 y la LAN con IP 192.168.1.1/24" width="700">
</p>
<p align="center">
  <em>Figura 2. Menú de consola de pfSense con la WAN (em0) en 192.168.100.152/24 por DHCP y la LAN (em1) en 192.168.1.1/24.</em>
</p>

## Configuración de interfaces de red e ingreso al gestor del firewall
Como se observa en la figura, se aprecian 2 interfaces de red (que son las que se configuraron anteriormente antes de arrancar la máquina con la iso). En este caso, cada una tiene asignada una dirección ip mediante protocolo DHCP. En el caso de que no se tenga dirección ip en alguna interfaz, se puede solicitar mediante protocolo DHCP con la opción 2. Una vez ambas interfaces tengan dirección IP asignada, se debe deshabilitar el firewall de pfsense para poder acceder al gestor web de este mismo con el comando pfsense -d. Una vez hecho eso, se puede ingresar al gestor con las credenciales por defecto admin-pfsense. una vez dentro, se verá algo así,
<p align="center">
  <img src="pfsense-reglas-wan.png" alt="Reglas del firewall pfSense en la interfaz WAN: una regla ICMP desde 192.168.100.115 y una regla TCP desde 192.168.100.0/24 hacia 192.168.100.152" width="800">
</p>
<p align="center">
  <em>Figura 3: Interfaz de configuración de firewall pfsense.</em>
</p>
