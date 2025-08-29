#**Solución para el Almacenamiento (storage.md)**

**Problema:** Justifiquen por qué los fallos de disco son críticos para la continuidad del negocio.

La infraestructura actual de TechSolutions Inc. presenta fallos frecuentes en el servidor de archivos principal debido a la ausencia de un sistema de redundancia en los discos. Este problema es crítico para la continuidad
del negocio porque:

•	La pérdida de datos afecta directamente la operación diaria de la empresa (documentos, configuraciones, registros de clientes, etc.).
•	La recuperación de información sin un sistema redundante implica tiempos muertos elevados y altos costos.
•	El riesgo de interrupción del servicio puede impactar negativamente en la productividad de los empleados y en la confianza de los clientes.
•	No contar con redundancia compromete la disponibilidad, la integridad y la seguridad de la información corporativa.

**Cuando un disco falla se deben a distintos factores:**

1.	Desgaste físico natural.
2.	Sobrecarga de operaciones.
3.	Factores eléctricos ambientales.
4.	Errores lógicos o de firmware.
   
**Propuesta:** Propongan un tipo de RAID específico. Expliquen la elección (ej. RAID 1, 5, 10) y cómo soluciona la necesidad de redundancia
La solución que proponemos es implementar un arreglo de discos en RAID 5.

**¿Por qué RAID 5?**
Porque combina rendimiento, capacidad de almacenamiento y redundancia, este combina 3 discos lo que hace esto es que distribuye la información en bloques, lo que permite esto es que si en caso un disco llega a fallar los datos se reconstruyen automáticamente a partir de la información de paridad, también aporta mejor aprovechamiento des espacio en comparación con RAID 1, además ofrece lecturas rápidas y escrituras equilibradas.

**Ventajas frente a otros niveles de RAID:**
- RAID 1 (espejo): Alta seguridad, pero desperdicia el 50% de la capacidad (cada disco es copia exacta del otro).
- RAID 10: Brinda mayor rendimiento, pero requiere al menos 4 discos y sacrifica más capacidad.
- RAID 5: Logra un **equilibrio óptimo** entre seguridad, rendimiento y capacidad, ideal para la etapa de crecimiento en la que se encuentra la empresa.

**Implementación de RAID 5:**
Requisitos previos
•Al menos 3 discos duros del mismo tamaño (ejemplo: /dev/sdb, /dev/sdc, /dev/sdd).
•Servidor con Linux (ejemplo: Ubuntu Server).
•Privilegios de superusuario (root o con sudo).

**Pasos para la configuracion:**
1. Instalar mdadm
```bash
sudo apt update
sudo apt install mdadm -y
```

2. Crear el arreglo RAID 5
Suponiendo que tenemos tres discos nuevos (/dev/sdb, /dev/sdc, /dev/sdd):

```bash
sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sdb /dev/sdc /dev/sdd
```

3. Verificar el estado del RAID

```bash
cat /proc/mdstat
```

4. Crear un sistema de archivos
Una vez creado el RAID, se debe formatear para usarlo:
```bash
sudo mkfs.ext4 /dev/md0
```

5. Montar el RAID en el sistema
```bash
sudo mkdir -p /mnt/raid5
sudo mount /dev/md0 /mnt/raid5
```

6. Comprobar que está montado:
```bash
df -h
```

7. Configurar montaje automático al iniciar
Editar el archivo /etc/fstab y agregar la línea:
```bash
/dev/md0    /mnt/raid5    ext4    defaults    0    0
```

8. Guardar la configuración de mdadm
Para que el sistema recuerde el arreglo:
```bash
sudo mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

**Conclusión**

Con la implementación de **RAID 5**, TechSolutions Inc. podrá:
- Minimizar riesgos de pérdida de datos.
- Garantizar la continuidad del negocio ante fallos de hardware.
- Mejorar la eficiencia en el uso de los discos disponibles.
- Asegurar que el servidor de archivos se mantenga disponible aun durante incidentes.


