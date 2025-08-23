**Configuración de Red**
__Problema__
Actualmente, las máquinas virtuales en el área de desarrollo utilizan el modo de red NAT (Network Address Translation) en VirtualBox. Este modo, aunque permite que las máquinas accedan a internet, presenta serias limitaciones para el entorno corporativo:

1.**Aislamiento entre máquinas virtuales**
En NAT, las máquinas no pueden comunicarse directamente entre ellas de forma directa, lo cual dificulta la comunicación cuando se están llevando a cabo proyectos.

2.**Falta de integración con la red corporativa.**
Las VMs no aparecen como dispositivos propios en la red local, lo cual impide que otros equipos de la empresa puedan acceder a ellas.

3.**Limitaciones en configuración de red avanzadas.**
Configuraciones como servidores web internos, servicios de base de datos o servidores de correo no pueden ser expuestos a la red corporativa bajo NAT, reduciendo la utilidad de los VMs en un escenario empresarial.

__Propuesta de solución__
Se recomienda configurar las máquinas virtuales en modo Puente (Bridged Adapter).
Esto permitirá que cada VM:
.- **Obtenga una dirección IP en la misma red que los demás dispositivos de la empresa.**

.- **Sea visible y accesible por otros servidores, estaciones de trabajo y VMs.**

.- **Facilite el trabajo colaborativo entre los desarrolladores.**

Además, es necesario configurar direcciones IP estáticas en las VMs. Esto garantiza que los equipos de desarrollo puedan acceder siempre a las mismas direcciones, evitando problemas de conectividad por cambios en las IPs dinámicas.



