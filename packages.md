**Gestión de paquetes** 
__Problemática__

En la infraestructura actual de TechnoSolutions Inc. Los usuarios actuales instalan paquetes de software manualmente en cada equipo. Esta práctica genera varias dificultades

Inconsistencia de versiones en los paquetes.
Diferentes servidores y estaciones de trabajo terminan con versiones distintas de un mismo paquete. 

1.**Alto consumo de ancho de banda.**
Cada equipo descarga directamente de internet los paquetes necesarios. Esto consume mayor ancho de banda de la red para obtener los mismos paquetes.

2.**Errores humanos.**
La instalación manual implica riesgo de equivocaciones, omisión de dependencias o instalación de software incorrecto.

3.**Escalabilidad Limitada.**
Con el crecimiento de la empresa, se volvería insostenible mantener la calidad y consistencia del software.

__Propuesta de solución__
Recomendamos implementar un repositorio espejo local de paquetes. Este servidor actuará como un punto central de control de la red corporativa desde el cual todos los equipos instalarán y actualizarán el software.

