# Roadmap de implementación

## Fase 0 — Validación de cuenta y costos

- [ ] Confirmar región principal y región seleccionada.
- [ ] Revisar límites de servicio y cuotas de Compute.
- [ ] Comprobar disponibilidad de capacidad para AMD o Ampere.
- [ ] Confirmar qué recursos califican como Always Free.
- [ ] Revisar alertas y presupuesto de facturación.

**Criterio de salida:** conocer los límites y costos potenciales antes de aprovisionar.

## Fase 1 — Infraestructura base

- [ ] Diseñar VCN y subred.
- [ ] Crear instancia Ubuntu LTS con configuración elegible.
- [ ] Reservar o documentar IP pública si es necesario.
- [ ] Crear usuario administrativo no-root.
- [ ] Configurar SSH por llave.
- [ ] Actualizar paquetes.
- [ ] Configurar firewall de host y reglas OCI.
- [ ] Verificar acceso y recuperación.

**Criterio de salida:** servidor accesible y endurecido, con puertos mínimos.

## Fase 2 — VPN WireGuard

- [ ] Instalar WireGuard.
- [ ] Generar llaves en los dispositivos correspondientes.
- [ ] Configurar túnel y direccionamiento privado.
- [ ] Abrir únicamente el puerto UDP elegido.
- [ ] Configurar clientes de PC y móvil.
- [ ] Probar conectividad y rutas.
- [ ] Documentar revocación de clientes.

**Criterio de salida:** dispositivos autorizados conectados y servicios privados accesibles.

## Fase 3 — Plataforma de aplicaciones

- [ ] Instalar Docker Engine y Docker Compose.
- [ ] Definir estructura de directorios y redes.
- [ ] Configurar proxy inverso.
- [ ] Configurar HTTPS.
- [ ] Desplegar aplicación de prueba.
- [ ] Separar configuración y secretos del código.

**Criterio de salida:** aplicación de prueba desplegada de forma reproducible.

## Fase 4 — Datos y proyectos

- [ ] Desplegar PostgreSQL en red privada.
- [ ] Definir volúmenes persistentes.
- [ ] Configurar backups y prueba de restauración.
- [ ] Desplegar APIs y frontends personales.
- [ ] Documentar variables de entorno requeridas.
- [ ] Automatizar despliegues cuando el flujo esté estable.

**Criterio de salida:** al menos un proyecto personal desplegado y recuperable.

## Fase 5 — Operación y seguridad

- [ ] Instalar monitoreo.
- [ ] Configurar alertas de disponibilidad.
- [ ] Revisar logs y actualizaciones.
- [ ] Auditar puertos expuestos.
- [ ] Probar restauración de backups.
- [ ] Documentar incidentes y procedimientos.

**Criterio de salida:** operación básica documentada y comprobada.
