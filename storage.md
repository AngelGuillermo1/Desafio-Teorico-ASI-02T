# Solución de Seguridad para TechSolutions Inc.

## Problemática Identificada

La red interna de TechSolutions Inc. presenta varias vulnerabilidades críticas que comprometen la confidencialidad, integridad y disponibilidad de los servicios:

- **Acceso no controlado a servicios internos:** No existen mecanismos de autenticación robustos ni segmentación de red.
- **Firewall descentralizado y sin estandarización:** Las reglas de filtrado son inconsistentes o inexistentes, lo que permite tráfico no autorizado.
- **Ausencia de monitoreo y registro de accesos:** No se auditan las conexiones entrantes ni se detectan intentos de intrusión.

---

## 🛡️ Propuesta: Implementación de UFW (Uncomplicated Firewall)

**UFW** es una herramienta de configuración de firewall para sistemas Linux basada en `iptables`, diseñada para facilitar la administración de reglas de red.

### ✅ Ventajas de UFW

- Interfaz sencilla para usuarios y administradores.
- Permite definir reglas específicas por IP, puerto y protocolo.
- Compatible con scripts de automatización y monitoreo.

---

## ⚙️ Pasos para Implementar UFW

### 1. **Instalación y activación**

```bash
sudo apt update
sudo apt install ufw
sudo ufw enable

