Solución para el Almacenamiento (storage.md).
Problema: Justifiquen por qué los fallos de disco son críticos para la continuidad del negocio.
La infraestructura actual de TechSolutions Inc. presenta fallos frecuentes en el servidor de archivos principal debido a la ausencia de un sistema de redundancia en los discos.Este problema es crítico para la continuidad del negocio porque:              •	La pérdida de datos afecta directamente la operación diaria de la empresa (documentos, configuraciones, registros de clientes, etc.).                                                                                                                  •	La recuperación de información sin un sistema redundante implica tiempos muertos elevados y altos costos.                     •	El riesgo de interrupción del servicio puede impactar negativamente en la productividad de los empleados y en la confianza de los clientes.                                                                                                                  •	No contar con redundancia compromete la disponibilidad, la integridad y la seguridad de la información corporativa.
Cuando un disco falla se deben a distintos factores:	                                                                        1.	Desgaste físico natural.                                                                                                  2.	Sobrecarga de operaciones.                                                                                                 3.	Factores eléctricos ambientales.                                                                                          4.	Errores lógicos o de firmware.
Propuesta: Propongan un tipo de RAID específico. Expliquen la elección (ej. RAID 1, 5, 10) y cómo soluciona la necesidad de redundancia                                                                                                                    La solución que proponemos es implementar un arreglo de discos en RAID 5.                                                      ¿Por qué RAID 5?                                                                                                                 Porque combina rendimiento, capacidad de almacenamiento y redundancia, este combina 3 discos lo que hace esto es que distribuye la informacion en bloques, lo que permite esto es que si en caso un disco llega a fallar los datos se reconstruyen automaticamente a partir de la informacion de paridad, tambien aporta mejor aprovechamiento des espacio en comparacion con RAID 1, ademas ofrece lecturas rapidas y escrituras equilibradas.

¿Como se implementaria?
Primero debemos verificar los requisitos previos para su implementacion:
•Al menos 3 discos duros del mismo tamaño.
•Servidor con linux.
•Privilegios del superusuario.

Para la configuracion
1. Instalar mdadm

sudo apt update
sudo apt install mdadm -y

2. Crear el arreglo RAID 5.
   
sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sdb /dev/sdc /dev/sdd

3. Verificar el estado del RAID.

cat /proc/mdstat




   
