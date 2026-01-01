![Docker](https://img.shields.io/badge/docker-ready-blue)
![WordPress](https://img.shields.io/badge/wordpress-ready-blue)

# WordPress Template con Docker 🐳

Plantilla base para iniciar proyectos **WordPress** de forma rápida usando **Docker Compose**, con acceso a base de datos mediante **phpMyAdmin**. Ideal para entornos de desarrollo locales.

---

## 📋 Requisitos

* Docker
* Docker Compose
* Git

> **Windows:** Asegúrate de que Docker Desktop esté iniciado.
> **Linux:** Verifica que Docker y Docker Compose estén instalados y en ejecución.

---

## 🚀 Inicialización del entorno

### 1️⃣ Clonar el repositorio

```bash
# HTTPS
git clone https://github.com/DraconShade/WordPress-Template-Docker.git

# SSH
git clone git@github.com:DraconShade/WordPress-Template-Docker.git
```

Accede al directorio del proyecto:

```bash
cd wordpress-template-docker
```

> **Ejemplo en Windows:**
> `C:\Users\[usuario]\Desktop\wordpress-template-docker`

> **Ejemplo en Linux:**
> `home\usr\Desktop\wordpress-template-docker`

---

### 2️⃣ Levantar los contenedores

```bash
docker compose up -d
```

Comandos útiles:

```bash
# Detener contenedores (mantiene volúmenes)
docker compose down

# Detener contenedores y borrar volúmenes
docker compose down -v
```

---

### 3️⃣ Configuración de PHP (`php.ini`)

Puedes personalizar la configuración de PHP editando el archivo:

```text
./php/custom.ini
```

Agrega, modifica o elimina las directivas necesarias. Luego reinicia el contenedor de WordPress con **una** de las siguientes opciones (según tu entorno):

```bash
# Opción recomendada
docker compose restart wordpress

# Alternativas
docker restart wordpress
docker exec wordpress service apache2 restart
docker exec wordpress supervisorctl restart apache2
```

También puedes:

```bash
# Detener
docker compose stop wordpress

# Iniciar
docker compose start wordpress
```

> ⚠️ Dependiendo de tu versión de Docker / imagen, algunas opciones pueden no funcionar. Usa la que mejor se adapte a tu configuración.

---

## 📁 Estructura del proyecto

```text
📁 wordpress-template-docker/
├── 📁 database/
├── 📁 php/
│   └── 📄 custom.ini
├── 📁 wordpress/
├── 🔒 .env
├── 📄 env.example
├── 📄 .gitignore
├── 🐳 docker-compose.yaml
├── 📄 LICENSE
└── 📖 README.md
```

### Descripción de directorios y archivos

* **database/** – Volúmenes o configuración de la base de datos
* **php/** – Configuración personalizada de PHP
  * `custom.ini` – Overrides de configuración PHP
* **wordpress/** – Archivos principales de WordPress
* **.env** – Variables de entorno (⚠️ no versionar)
* **env.example** – Ejemplo de variables de entorno
* **.gitignore** – Archivos ignorados por Git
* **docker-compose.yaml** – Definición de servicios Docker
* **LICENSE** – Licencia del proyecto
* **README.md** – Documentación del proyecto

---

## ⚙️ Configuración del archivo `.env`

El proyecto utiliza un archivo `.env` para centralizar la configuración del entorno.
Debes crear tu propio archivo `.env` a partir del archivo de ejemplo:

```bash
cp env.example .env
```

A continuación se describen las variables disponibles y su función:

```env
# Proyecto
PROJECT_NAME=name_cliente

# Base de datos
DB_ROOT_PASSWORD=password_cliente
DB_NAME=name_cliente_db

# Puertos
WP_PORT=8082
PMA_PORT=8083

# PHP - Elementor / WordPress
PHP_MEMORY_LIMIT=512M
PHP_UPLOAD_MAX_FILESIZE=128M
PHP_POST_MAX_SIZE=128M
PHP_MAX_EXECUTION_TIME=300
PHP_MAX_INPUT_TIME=300
PHP_MAX_INPUT_VARS=5000
```

### 🧾 Descripción de variables

#### 📦 Proyecto

* **PROJECT_NAME**: Nombre del proyecto/cliente. Se utiliza para identificar contenedores, volúmenes o servicios.

#### 🗄️ Base de datos (MariaDB)

* **DB_ROOT_PASSWORD**: Contraseña del usuario `root` de la base de datos.
* **DB_NAME**: Nombre de la base de datos que usará WordPress.

> ⚠️ No compartas este archivo ni subas credenciales a repositorios públicos.

#### 🔌 Puertos

* **WP_PORT**: Puerto local para acceder a WordPress desde el navegador.
* **PMA_PORT**: Puerto local para acceder a phpMyAdmin.

#### 🐘 Configuración PHP (optimizada para WordPress / Elementor)

* **PHP_MEMORY_LIMIT**: Memoria máxima disponible para PHP.
* **PHP_UPLOAD_MAX_FILESIZE**: Tamaño máximo permitido para subir archivos.
* **PHP_POST_MAX_SIZE**: Tamaño máximo de datos enviados por POST.
* **PHP_MAX_EXECUTION_TIME**: Tiempo máximo de ejecución de un script PHP (en segundos).
* **PHP_MAX_INPUT_TIME**: Tiempo máximo para procesar datos de entrada.
* **PHP_MAX_INPUT_VARS**: Cantidad máxima de variables de entrada permitidas.

---

### 🌐 Acceso desde el navegador

Una vez levantados los contenedores con `docker compose up -d`, podrás acceder a:

* **WordPress:**
  👉 [http://localhost:8082](http://localhost:8082)

* **phpMyAdmin:**
  👉 [http://localhost:8083](http://localhost:8083)

---

## 🧩 Tecnologías incluidas

* **WordPress:** `latest`
* **Base de datos:** `MariaDB (latest)`
* **Administrador DB:** phpMyAdmin
* **Contenedores:** Docker & Docker Compose

---

## 🔐 Archivos y rutas ignoradas (`.gitignore`)

Se recomienda ignorar los siguientes archivos y directorios:

* `wp-config.php` — contiene credenciales sensibles
* `/wp-content/uploads/` — archivos subidos por usuarios
* `.env` — variables de entorno y secretos
* `.DS_Store`, `Thumbs.db` — archivos del sistema operativo
* `.vscode/` — configuración del editor/IDE
* `*.log` — archivos de registro
* `docker-compose.override.yml` — configuraciones locales

> **Nota:** Evita subir credenciales, datos locales, binarios pesados o configuraciones específicas del entorno de desarrollo.

---

## 📝 Descripción del proyecto

Este proyecto sirve como **plantilla base** para iniciar rápidamente desarrollos en WordPress usando Docker, facilitando:

* Entornos reproducibles
* Configuración rápida
* Acceso simple a la base de datos
* Separación clara de configuración y código

---

## 📄 Licencia

Este proyecto se distribuye bajo la licencia especificada en el archivo `LICENSE`.

---