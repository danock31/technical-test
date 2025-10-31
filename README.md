# Product API

API RESTful desarrollada con **.NET 8** que permite realizar operaciones CRUD sobre productos.  
Construida bajo una arquitectura por capas limpias (Clean Architecture) y conectada a una base de datos **MySQL**.  
Integra un frontend desarrollado en **Angular 18**.

---
## Product-App

Aplicacion web desarrollada con **Angular 18** que consume la API RESTful de **ProductApi (.NET 8)**.  
Permite gestionar productos (crear, listar, editar y eliminar) mediante un disenno responsive y componentes modulares.


## Tecnologias utilizadas

### Backend
- **.NET 8 (ASP.NET Core Web API)**
- **C#**
- **Entity Framework Core** (ORM)
- **MySQL**
- **Swagger / Swashbuckle**
- **Dependency Injection**
- **LINQ**
- **CORS configurado para frontend Angular**
- **Azure App Service** (despliegue en la nube)
---
### Frontend
- **Angular 18**
- **TypeScript**
- **HTML5 / CSS3**
- **Angular Material**
- **RxJS**
- **Azure Static Web Apps** (despliegue)

## Arquitectura del proyecto

### Backend
El proyecto sigue una estructura basada en **Clean Architecture**, separando la logica de negocio, acceso a datos y controladores.

#### Configuracion de la base de datos

Archivos: **`appsettings.json`**//**`Program.cs`**

#### Uso de CORS

Configurado para permitir unicamente peticiones desde el frontend en Azure
Archivo: **`Program.cs`**

#### Ejecucion local 
```bash
git clone https://github.com/danock31/technical-test-api.git
cd technical-test-api
dotnet restore
dotnet run
```

Por defecto, la API se ejecuta en:
URL: https://localhost:7110/

Para la documentacion se realiza con Swagger de manera local
URL: https://localhost:7110/swagger


### Frontend
El proyecto esta organizado siguiendo las buenas practicas de Angular, con separacion de componentes, servicios y modelos.

#### Comunicacion con el backend

La aplicacion consume la API **ProductApi (.NET 8)**
Archivo: `product.service.ts`

#### Funcionalidades principales

- Listar todos los productos
- Crear nuevos productos
- Editar productos existentes
- Eliminar productos
- Buscar productos por nombre
- Validaciones de formulario
- Conexion segura mediante CORS con la API en Azure

#### Ejecucion local
```bash
git clone https://github.com/danock31/technical-test-frontend.git
cd technical-test-frontend
npm install
ng serve
```
La aplicacion se ejecutara por defecto en:
http://localhost:4200

## Despliegue en Azure

**Backend (API)** esta en un **Azure App Service** y
la URL: https://technical-test-api-h7bxdybuhqcce6dk.canadacentral-01.azurewebsites.net/api/Product

**Frontend(App)** esta en un **Azure Static Web Apps** y
la URL: https://orange-bush-0a7574d1e.3.azurestaticapps.net/

**DATABASE** esta creado en **Azure MySQL Database**

## Respuesta a Que pasos seguirias para conectar esta API a una base de datos real (SQL Server o SQLite)?

Para conectar esta API desarrollada en **.NET 8** a una base de datos real como **SQL Server** o **SQLite**, seguiria los siguientes pasos:

---

### 1. Instalar el proveedor de base de datos correspondiente

Dependiendo del motor de base de datos, se deben instalar los paquetes de Entity Framework Core necesarios:

#### Para SQL Server:
```bash
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
dotnet add package Microsoft.EntityFrameworkCore.Tools
```
#### Para SQLite:
```bash
dotnet add package Microsoft.EntityFrameworkCore.Sqlite
dotnet add package Microsoft.EntityFrameworkCore.Tools
```
### 2. Configurar la cadena de conexion en appsettinhs.json
 La conexion de cada uno varia aqui dejo como ejemplo ambas
 ```bash
 SQL:
 "DefaultConnection": "Server=localhost;Database="NombreBaseDatos";Trusted_Connection=True;TrustServerCertificate=True;"

 SQLite:
 "DefaultConnection": "Data Source=/ruta/a/tu/base_de_datos.db"
 ```

### 3. Actualizar el contexto en program.cs
**SQL:`UseSqlServer`**
```bash
builder.Services.AddDbContext<ApplicacionDbContext>(options =>
    options.UseSqlServer(builder.Configuration.GetConnectionString("DefaultConnection"))
);
``` 
**SQLite:`UseSqlite`**

```bash
builder.Services.AddDbContext<ApplicacionDbContext>(options =>
    options.UseSqlite(builder.Configuration.GetConnectionString("DefaultConnection"))
);
```
## Analisis Final

    Trate de utilizar un entorno lo mas profecional usando herramientas como Azure y 
    todo el ambiente gitflow y demas, aprendi mucho realizando este CRUD ya sea en backend o frontend.
    El proyecto esta 100% funcional la parte de frontend consume correctamente el backend y lo pueden probar en las URLs de Azure.
## Autor

Daniel Picado Abarca
Desarrollador Web & Programador de Software
Github: https://github.com/danock31
