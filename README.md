![Docker](https://img.shields.io/badge/docker-ready-blue)
![WordPress](https://img.shields.io/badge/wordpress-ready-blue)

# WordPress-Template-Docker
Iniciando entorno Wordpress usando Docker


# Descripcion

Dar Permiso: chmod +x docker/entrypoint.sh

Inicial Docker: docker compose up -d

`Agrega -v al final, elimina volumenes`
Finalizar Docker: docker compose down

docker compose logs wordpress

## Versión de WordPress
*latest*

## Versión de la base de datos
*latest*

## Tipo de Base de Datos
*MariaDB*

## Ruta y puesto de conexión a nivel local

## Rutas ignoradas en .gitignore y por qué
Ejemplos recomendados:
- `wp-config.php` — contiene credenciales sensibles.
- `/wp-content/uploads/` — archivos subidos por usuarios, no deben versionarse.
- `.env` — variables de entorno y credenciales locales.
- `.DS_Store`, `Thumbs.db` — archivos del sistema operativo.
- `.vscode/` — configuraciones de editor/IDE.
- `*.log` — archivos de registro.
- `docker-compose.override.yml` — overrides locales que no deben compartirse.

*Nota:* evitar subir credenciales, binarios/dependencias pesadas, datos generados/locales y archivos de configuración del entorno de desarrollo.

## Versiones de las imágenes Docker en el proyecto
Comprobar versiones:
- `docker compose images`
