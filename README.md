# Julian Cloud Lab

Laboratorio personal para diseñar, desplegar, proteger y administrar infraestructura en la nube con Oracle Cloud Infrastructure (OCI).

El proyecto reúne aprendizaje práctico de **Linux, redes, VPN, DevOps, contenedores, bases de datos y ciberseguridad**, además del alojamiento de proyectos personales.

> **Estado:** planificación e implementación inicial. Los recursos de OCI todavía deben verificarse antes de desplegar servicios.

## Objetivos

- Crear una máquina virtual dentro de los límites elegibles de Always Free.
- Configurar administración segura mediante SSH con llaves.
- Implementar una VPN personal con WireGuard.
- Desplegar aplicaciones web y APIs.
- Administrar servicios con Docker Compose.
- Incorporar bases de datos, monitoreo y copias de seguridad.
- Documentar decisiones, comandos y procedimientos reproducibles.

## Arquitectura objetivo

```text
                        Internet
                           |
                 +---------+---------+
                 |                   |
            HTTPS público       WireGuard UDP
                 |                   |
          Reverse proxy          VPN privada
                 |                   |
        +--------+-------------------+--------+
        |             Ubuntu Server           |
        |                                      |
        |  Docker / Docker Compose             |
        |  +-------------+  +---------------+  |
        |  | Aplicaciones|  | APIs          |  |
        |  +-------------+  +---------------+  |
        |  +-------------+  +---------------+  |
        |  | PostgreSQL  |  | Monitoreo     |  |
        |  +-------------+  +---------------+  |
        +--------------------------------------+
```

La arquitectura es una propuesta, no una descripción de recursos ya desplegados. Los servicios se habilitarán gradualmente según la capacidad disponible.

## Componentes previstos

| Área | Tecnología | Propósito |
|---|---|---|
| Infraestructura | Oracle Cloud Infrastructure | Máquina virtual y red |
| Sistema operativo | Ubuntu Server LTS | Sistema base |
| Acceso remoto | OpenSSH | Administración segura |
| VPN | WireGuard | Acceso privado |
| Contenedores | Docker / Compose | Despliegue de servicios |
| Proxy inverso | Nginx | Enrutamiento HTTPS |
| Base de datos | PostgreSQL | Persistencia de aplicaciones |
| Monitoreo | Uptime Kuma | Disponibilidad de servicios |
| Control de versiones | GitHub | Código y documentación |

## Roadmap

- [ ] Verificar límites, región y capacidad Always Free en OCI.
- [ ] Crear y asegurar la instancia Linux.
- [ ] Configurar firewall de red y firewall del sistema.
- [ ] Instalar y probar WireGuard.
- [ ] Instalar Docker y Docker Compose.
- [ ] Configurar proxy inverso y HTTPS.
- [ ] Desplegar una primera aplicación de prueba.
- [ ] Configurar PostgreSQL y copias de seguridad.
- [ ] Implementar monitoreo y alertas.
- [ ] Documentar pruebas de seguridad y recuperación.

Consulta [docs/roadmap.md](docs/roadmap.md) para el plan detallado.

## Seguridad

- No guardar contraseñas, tokens, claves privadas, archivos `.env` ni datos personales en Git.
- Usar autenticación SSH por llaves y proteger la llave privada.
- Exponer únicamente los puertos estrictamente necesarios.
- Mantener bases de datos y paneles administrativos en redes privadas o accesibles por VPN.
- Aplicar actualizaciones y mantener copias de seguridad fuera de la instancia.
- Revisar costos, cuotas y límites antes de crear recursos.

Más detalles: [docs/security.md](docs/security.md).

## Costos y límites

El objetivo es utilizar recursos elegibles para Always Free. La disponibilidad de capacidad, cuotas, límites de almacenamiento, tráfico y condiciones de Oracle pueden variar. **Free Tier no significa capacidad garantizada ni riesgo cero de cargos.** Revisar siempre el estimador, los límites de la cuenta y el consumo antes de aprovisionar recursos.

## Documentación

- [Arquitectura](docs/architecture.md)
- [Roadmap](docs/roadmap.md)
- [Seguridad](docs/security.md)
- [Despliegue](docs/deployment.md)

## Alcance del laboratorio

Todos los experimentos de seguridad se realizarán sobre infraestructura propia o sistemas para los que exista autorización explícita. No se realizarán pruebas contra terceros sin permiso.

---
Proyecto personal de aprendizaje y portafolio: **Julian Cloud Lab**.
