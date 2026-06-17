# Laboratorio de Pivoting Avanzado - Preparación eJPTv2

¡Bienvenido a mi primer proyecto de ciberseguridad en github! En este repositorio documento el diseño, montaje y explotación de un entorno de red compartimentada para practicar técnicas de **Pivoting** (enrutamiento de tráfico y salto entre redes), una de las habilidades críticas para el examen eJPTv2.

---

## Arquitectura de la Red del Laboratorio

El escenario simula una infraestructura empresarial donde el atacante no tiene acceso directo a los servidores internos más críticos.

| Máquina VM | Sistema Operativo | Red Expuesta (DMZ) | Red Interna (Oculta) | Rol en el Laboratorio |
| :--- | :--- | :--- | :--- | :--- |
| **Kali Linux** | Kali Linux (Atacante) | `10.10.10.5` | No tiene acceso | Máquina de Auditoría |
| **Windows Server** | Windows Server 2012 | `10.10.10.20` | `192.168.50.10` | Máquina Puente (Víctima 1) |
| **Metasploitable** | Linux Vulnerable | No tiene acceso | `192.168.50.20` | Objetivo Final (Víctima 2) |

---

## Objetivos del Proyecto
1. **Validación de Red:** Demostrar el aislamiento físico entre la máquina atacante y el objetivo final.
2. **Explotación Inicial:** Conseguir una sesión de Meterpreter estable en el Windows Server mediante un payload personalizado de 64 bits.
3. **Pivoting con Metasploit:** Configurar rutas automáticas (`autoroute`) hacia la red oculta.
4. **Túnel de Red Global:** Desplegar un proxy SOCKS5 integrado con `proxychains` para auditar la red interna con herramientas externas como Nmap.
