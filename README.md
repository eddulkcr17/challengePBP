# Todo List

### ejecutar con docker

requisitos

-   [Docker](https://docs.docker.com/get-docker/)
-   [Docker compose](https://docs.docker.com/compose/install/)

corriendo estos comandos se levantara la base el front y el back

```
docker-compose up -d
```

ASP.NET API se ejecutara en  `http://localhost:5000`
ReactJS app se ejecutara en  `http://localhost:3000`

detener la aplicacion

```
docker-compose down
```

### ejecutar el proyecto sin docker

Pasos

En la carpeta del proyecto ubicarse en el Path del back y ejecutar 

```bash
$ dotnet restore
```

Correr los test

```
$ dotnet test
```

modificar el  `appsettings.json` se encuentra en ./src/TodoList.WebApi 

```json
{
    "ConnectionStrings": {
        "SqlServerConnection": "CONNECTION STRING HERE"
    },
    "CorsOptions": {
        "PolicyName": "TodoApiPolicy",
        "AllowedOrigin": "http://localhost:3000"
    },
    "JwtToken": {
        "Audience": "TodoClient",
        "Issuer": "TodoApi",
        "Key": "KEY",
        "Seconds": 180
    }
}
```

crear una base de datos con el script que esta en  ./database/scripts/init.sql

levantar el proyecto

```bash
$ dotnet run --project src/TodoList.WebApi
```

**correr el frontend**

modificar el archivo env que es ta en  ./src/todo-list-spa con la url de la api:

```
REACT_APP_API_URL=http://localhost:5000
```
ejecutar el proyecto desde la locacion del front

```bash
# Install dependencies
$ npm install --prefix src/todo-list-spa

# Starting the project
$ npm start --prefix src/todo-list-spa
```
