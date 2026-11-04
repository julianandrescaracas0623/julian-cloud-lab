# Arquitectura

## Estado

Documento de arquitectura objetivo. No implica que los componentes ya estén desplegados ni que exista capacidad confirmada en OCI.

## Vista lógica

1. **OCI Networking:** VCN, subredes, tablas de rutas, gateways y reglas de seguridad.
2. **Compute:** instancia Ubuntu Server dentro de las cuotas y recursos elegibles.
3. **Administración:** SSH con llaves; preferiblemente restringido a IPs autorizadas o disponible mediante VPN.
4. **VPN:** WireGuard como punto de entrada privado para dispositivos autorizados.
5. **Aplicaciones:** contenedores Docker conectados a redes internas.
6. **Publicación:** proxy inverso HTTPS solo para aplicaciones que deban ser públicas.
7. **Datos:** PostgreSQL sin exposición directa a Internet.
8. **Operación:** monitoreo, logs, actualizaciones y backups externos.

## Flujo de tráfico esperado

- Tráfico web público: Internet → puertos 80/443 → proxy inverso → aplicación correspondiente.
- Acceso privado: dispositivo autorizado → WireGuard UDP → red privada → servicios internos.
- Administración: SSH mediante VPN o IP de origen explícitamente permitida.
- Base de datos: únicamente desde aplicaciones o redes autorizadas.

## Principios

- Mínima exposición de puertos.
- Separación entre servicios públicos y privados.
- Secretos fuera del repositorio.
- Backups independientes de la máquina virtual.
- Despliegues reproducibles y documentados.
- Dimensionamiento según cuotas reales, no según recursos supuestos.

## Decisiones pendientes

- Forma y tamaño de la instancia según capacidad y límites Always Free.
- Diseño de subredes y direccionamiento.
- Dominio y estrategia de certificados TLS.
- Si conviene ejecutar todos los servicios en una VM o separar cargas.
- Política de backups y retención.
