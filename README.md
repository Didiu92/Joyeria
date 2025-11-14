# Joyería: Gestión de tienda con PHP.

Resumen
-------
Esta joyería es una pequeña aplicación web de ejemplo para gestionar productos (CRUD) con imágenes y dos tipos de usuario con diferentes permisos. Está pensada como proyecto educativo para practicar PHP, Composer, PostgreSQL y despliegue con Docker/Apache.

Características principales
-------------------------
- Listado, creación, edición y borrado de productos.
- Formulario de búsqueda de productos por producto o categoría.
- Soporte y gestión para imágenes via URL. 
- Autenticación para usuario invitado y administrador.

Tecnologías
-----------
- PHP 8.2.29
- PostgreSQL 12.0+
- Bootstrap 4 
- Docker 28.1.1 
- Composer 2.0+


Estructura del proyecto
-----------------------
Raíz del repo:

- `public/` — Document root servido por Apache. Contiene `index.php` y los estilos CSS.
- `src/` — Código PHP de la aplicación (plantillas, controladores y servicios).
- `database/init.sql` — Esquema de la base de datos.
- `vendor/` — Dependencias de Composer (se genera con `composer install`).
- `Dockerfile`, `docker-compose.yml` — configuración para arrancar la aplicación con Docker.

Instrucciones de instalación - Requisitos previos
------------------
- PHP 8.0+ 
- Composer 2.x
- PostgreSQL 12+ 
- Docker 20+/Compose v2+.
- Git (para clonar el repositorio).


Instalación con Docker
------------------------------------------------
1. Clona el repositorio:

```powershell
git clone <repo-url> C:\Tienda
cd C:\Tienda
```

2. Copia (opcional) el fichero `.env.example` a `.env` y ajusta variables si procede. Por defecto la configuración usa los valores en `src/config/config.php` y variables de entorno.

3. Arranca el stack con Docker Compose:

```powershell
docker compose up -d --build
```

4. Importa la base de datos (si no se hizo automáticamente). El fichero `database/init.sql` contiene las tablas necesarias:

```powershell
# desde host con psql (ajusta credenciales según tu entorno)
# psql -h localhost -p 5432 -U postgres -d tienda -f database/init.sql
```

5. Abre la aplicación en el navegador:

```
http://localhost:8080/public/
```

Instalación sin Docker (local)
------------------------------
1. Instala dependencias con Composer:

```powershell
composer install
```

2. Configura tu servidor web (p. ej. Apache) apuntando el document root a la carpeta `public/`, o ejecuta el servidor interno de PHP *solo para desarrollo*:

```powershell
php -S localhost:8080 -t public
```

3. Crea la base de datos e importa `database/init.sql` (ver arriba).


Uso básico
----------
1. Cómo acceder a la aplicación

- Si arrancaste con Docker Compose y el `docker-compose.yml` mapea el puerto `8080` al servicio web, abre en el navegador:

```
http://localhost:8080/public/
```

- Si ejecutas local sin Docker (servidor interno PHP o un vhost), apunta el document root a la carpeta `public/` y usa la URL y puerto que hayas configurado (por ejemplo `http://localhost:8080/public/`).

2. Login de prueba
| Rol     | Usuario | Contraseña               |
|---------|---------|--------------------------|
| Admin   | admin1  | b9f19f31e08a88b57d46ca81 |
| Usuario | user1   | 2c1f707f88b01d1372b88016 |

3. Navegación principal

- Página principal / listado: muestra información básica y miniaturas en tabla y búsqueda por nombre o categoría.
- Detalle de producto: abre la vista con información completa y la imagen.
- Crear producto: permite añadir nuevos productos (admin).
- Editar / Borrar: enlaces en cada producto para modificar o eliminar (admin).
- Actualizar imagen: permite cambiar la URL de la imagen.
- Barra de búsqueda: para buscar uno o varios productos por categoría o producto. Busca también por palabras incompletas.
- Login / Logout: acceder o salir de la sesión.


Autora y créditos
------------------
- Autor: Diana Viñuales Alós
- Repositorio: https://github.com/Didiu92/Joyeria

Licencia
--------
Este proyecto se publica bajo la licencia Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0).