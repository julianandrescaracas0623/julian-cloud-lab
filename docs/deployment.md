# Guía de despliegue

## Antes de comenzar

- Confirmar que la instancia y los recursos de red están dentro de los límites gratuitos aplicables.
- Verificar el sistema operativo y arquitectura reales.
- Tener acceso administrativo mediante SSH.
- Confirmar reglas de red y firewall.
- Mantener los secretos fuera del repositorio.

## Preparación del servidor

Los comandos definitivos se documentarán después de crear y verificar la instancia. No ejecutar comandos de instalación hasta confirmar la distribución y versión:

```bash
cat /etc/os-release
uname -m
```

Actualizar el sistema según las prácticas recomendadas para la versión instalada y comprobar que los servicios esenciales sigan funcionando.

## Estructura sugerida en el servidor

```text
/opt/
  apps/
    app-name/
      compose.yaml
      .env
  proxy/
  monitoring/
  backups/
```

Los archivos `.env` reales deben permanecer en el servidor y estar excluidos de Git.

## Despliegue de una aplicación

1. Revisar el repositorio y su Dockerfile.
2. Definir variables de entorno en el servidor.
3. Configurar red y persistencia.
4. Construir o descargar una imagen confiable.
5. Levantar el servicio con Docker Compose.
6. Revisar logs y health checks.
7. Configurar proxy y HTTPS solo si la aplicación será pública.
8. Probar funcionamiento y procedimiento de rollback.

## Verificación

Registrar:
- Fecha y responsable del despliegue.
- Versión o commit desplegado.
- Servicios y puertos utilizados.
- Resultado de health checks.
- Procedimiento de rollback.
- Estado del backup.

Esta guía se completará con comandos concretos cuando la infraestructura real esté creada.
