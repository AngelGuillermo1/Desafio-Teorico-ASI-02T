
# Solución de Seguridad para TechSolutions Inc.

## Problemática Identificada

La red interna de TechSolutions Inc. presenta varias vulnerabilidades críticas que comprometen la confidencialidad, integridad y disponibilidad de los servicios:

- **Acceso no controlado a servicios internos:** No existen mecanismos de autenticación robustos ni segmentación de red.
- **Firewall descentralizado y sin estandarización:** Las reglas de filtrado son inconsistentes o inexistentes, lo que permite tráfico no autorizado.
- **Ausencia de monitoreo y registro de accesos:** No se auditan las conexiones entrantes ni se detectan intentos de intrusión.

---

## Propuesta: Implementación de UFW (Uncomplicated Firewall)

**UFW** es una herramienta de configuración de firewall para sistemas Linux basada en `iptables`, diseñada para facilitar la administración de reglas de red.

### Ventajas de UFW

- Interfaz sencilla para usuarios y administradores.
- Permite definir reglas específicas por IP, puerto y protocolo.
- Compatible con scripts de automatización y monitoreo.

---

## Pasos para Implementar UFW

### 1. **Instalación y activación**

```bash
sudo apt update
sudo apt install ufw
sudo ufw enable
```

### 2. Establecer política por defecto

```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
```

## Ejemplos de aplicacion de reglas de seguridad 

### 1. permitir acceso SSH solo desde IP especificas

```bash
# Permitir SSH desde una IP autorizada
sudo ufw allow from 192.168.1.100 to any port 22 proto tcp

# Permitir SSH desde una segunda IP autorizada
sudo ufw allow from 192.168.1.101 to any port 22 proto tcp

# Bloquear acceso SSH desde otras IPs
sudo ufw deny 22/tcp
```

### 2. Bloquear tráfico no autorizado a otros servicios

```bash
# Bloquear acceso al puerto HTTP (si no se usa)
sudo ufw deny 80/tcp

# Bloquear acceso al puerto MySQL
sudo ufw deny 3306/tcp

# Bloquear acceso al puerto FTP
sudo ufw deny 21/tcp
```

---

## Recomendaciones Finales

- Integrar con herramientas de monitoreo: Como Fail2Ban para detectar intentos de acceso sospechosos.
- Revisar y actualizar reglas periódicamente: Especialmente al cambiar la infraestructura o servicios.

## Referencias

- https://help.ubuntu.com/community/UFW
- https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-ubuntu
