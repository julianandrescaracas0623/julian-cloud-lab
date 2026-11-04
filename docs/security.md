# Línea base de seguridad

Este documento define controles mínimos para el laboratorio. Ajustar los procedimientos a la versión del sistema y a la arquitectura finalmente desplegada.

## Identidades y acceso

- Usar cuentas individuales y privilegios mínimos.
- Administrar SSH mediante llaves; evitar acceso SSH directo de root.
- Proteger las llaves privadas con permisos adecuados y, cuando sea posible, frase de contraseña.
- Restringir el origen de SSH en las reglas de red.
- Revocar inmediatamente clientes WireGuard que ya no deban tener acceso.

## Red y exposición

- Denegar por defecto el tráfico entrante que no sea necesario.
- Mantener sincronizadas las reglas de OCI y el firewall del sistema operativo.
- Publicar únicamente los puertos requeridos.
- Mantener bases de datos, paneles y métricas en redes privadas o detrás de VPN.
- No asumir que una VPN sustituye controles de autenticación o autorización.

## Sistema y aplicaciones

- Instalar actualizaciones de seguridad con regularidad.
- Ejecutar contenedores con los privilegios mínimos posibles.
- Evitar montar el socket Docker en aplicaciones no confiables.
- No almacenar secretos en imágenes, repositorios, logs ni archivos compartidos.
- Usar versiones fijadas y revisar imágenes antes de actualizarlas.

## Secretos

Nunca subir al repositorio:
- Llaves privadas SSH o WireGuard.
- Contraseñas y tokens.
- Archivos `.env` reales.
- Credenciales de OCI.
- Dumps de bases de datos con información sensible.

Usar variables de entorno o un gestor de secretos adecuado y mantener ejemplos con valores ficticios.

## Backups y continuidad

- Mantener copias fuera de la instancia.
- Cifrar backups cuando contengan información sensible.
- Definir retención.
- Probar restauraciones periódicamente.
- No considerar una snapshot como única copia de seguridad.

## Pruebas de seguridad

Realizar escaneos y pruebas únicamente sobre recursos propios o con autorización explícita. Registrar alcance, fecha, herramientas, hallazgos y acciones correctivas.

## Respuesta a incidentes

1. Aislar el servicio o credencial afectada.
2. Preservar logs y evidencia.
3. Rotar credenciales potencialmente expuestas.
4. Restaurar desde una copia confiable si es necesario.
5. Documentar causa raíz y medidas preventivas.
