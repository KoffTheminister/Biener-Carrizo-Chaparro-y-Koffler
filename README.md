# Libertadn't
> Propuesta y especificación del proyecto para Desarrollo de Software
> 
> Repositorio web de reseñas e información de videojuegos

## Grupo
### Integrantes
- 51739 - [Koffler, Ignacio](https://github.com/KoffTheminister)
- 51091  - [Carrizo, Gonzalo](https://github.com/maig0l)

### Repositorios
- [Frontend app](https://github.com/KoffTheminister/FrontEnd-Proyecto.git)
- [Backend app](https://github.com/KoffTheminister/BackEnd-Proyecto.git)

## Tema
### Descripción
Libertadnt es un sistema de gestión carcelario, se encarga de la administración tanto del personal de seguridad como de los reclusos, cuenta tanto con una base de datos para poder contabilizar e indicar cada preso y su sector asignado, como sus actividades diarias y el personal de seguridad asignado.

### Modelos
#### Diagrama de clases
![Diagrama de Clases]()

## Alcance de regularidad

|Req|Detalle|
|:-|:-|
| CRUD simple       | 1. CRUD Recluso |
|                   | 2. CRUD Guardia |
|                   | 3. CRUD Actividad Ilegal |
|                   | 4. CRUD Sentencia |
|                   | 5. CRUD Sector |
| CRUD dependiente  | 1. CRUD Turno (depende de CRUDs Guardia, Sector) |
|                   | 2. CRUD Condena (depende de CRUDs Sentencia, Recluso, Sector) |
| Listado + detalle | 1. Listado de reclusos a liberar. liberar aquellos cuya fecha de fin de condena estimada sea menor a la fecha actual|
|                   | 2. Listado de sentecias |
|                   | 3. Listado de turnos por sector y turno |
| CUU/Epic          | 1. Registrar un turno |
|                   | 2. Registrar una inscripción a actividad ilegal |

## Alcance de Aprobacion Directa
|Req|Detalle|
|:-|:-|
| CRUD simple       | 1. CRUD Recluso |
|                   | 2. CRUD Guardia |
|                   | 3. CRUD Actividad Ilegal |
|                   | 4. CRUD Sentencia |
|                   | 5. CRUD Sector |
|                   | 6. CRUD Turno |
|                   | 7. CRUD Guardia |
|                   | 8. CRUD Actividad |
|                   | 9. CRUD Actividad Ilegal |
|                   | 10. CRUD Administrador |
| CUU/Epic          | 1. Ingresar a un Recluso (se define un recluso con condena. A partir de cual es la peor sentencia dentro de la condena, se define a qué sector se asignará el recluso. Aquí también se le asigna una celda.) |
|                   | 2. Presentar los guardias en los 3 turnos de un sector, poder eliminar ciertos guardias de ciertos turnos y establecer otros|
|                   | 3. Crear actividad, asignar automáticamente los reclusos que cumplen las especificaciones y crear un vínculo con un guardia y la actividad |


<!-- TODO: Falta 1 Epic para AD -->

## Aplicación

### Instrucciones de Instalación

Usa los siguientes vinculos para acceder al proyecto completo:

```
mkdir libertadnt
cd libertadnt
mkdir backend
cd backend
git remote add origin https://github.com/KoffTheminister/BackEnd-Proyecto.git
cd -
mkdir frontend
cd frontend
git remote add origin https://github.com/KoffTheminister/FrontEnd-Proyecto.git
```

Instalá las dependencias e inicializá el archivo de configuración del backend:

```
cd backend
pnpm install
```

Para usar la base de datos en nuestro caso implementamos un servidor SQL en docker. Para ello debe descargar docker, ejecutar el comando docker pull percona/percona-server para obtener la imagen del servidor de percona a partir de la cual crearemos nuestro container y la base de datos. 
Ejecute:
docker run --name mysql_des_back -v mysql_data:/var/lib/mysql -e MYSQL_ROOT_HOST='%' -e MYSQL_ALLOW_EMPTY_PASSWORD="yes" -e MYSQL_PASSWORD="password" -e MYSQL_USER="user_name" -e MYSQL_DATABASE='libertant' -p 3306:3306 -d percona/percona-server
mysql_data tiene que ser cambiada por el PATH a una carpeta dentro de la carpeta de sus volmenes personales de docker. Tambien deberia cambiar password y user_name a unos de preferencia. Estos valores deben ser cambiados en el archivo .env para que el server funcione.
si se asegura que el container esta corriendo entonces corra el server de backend:

```
cd backend
pnpm start:dev
```
---

En una nueva terminal, instala las dependencias del frontend:

```
cd frontend
pnpm install
```

Iniciá el frontend:

```
ng serve
```

La aplicación está desplegada.
Ingresá a http://localhost:4200/log-in con las credenciales:

- Codigo de usuario: `1`
- Contraseña: `123r`

### Documentación de la API

Para acceder a la documentacion, primero es necesario ejecutar el servidor de backend con pnpm start:dev y luego se usa el path: 'http://localhost:8080/api-docs' en el buscador.

