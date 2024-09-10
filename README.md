# Todo List

### Run with docker

Requires

-   [Docker](https://docs.docker.com/get-docker/)
-   [Docker compose](https://docs.docker.com/compose/install/)

Run the following command to start database, backend and frontend

```
docker-compose up -d
```

ASP.NET API will be available in `http://localhost:5000`
ReactJS app will be available in `http://localhost:3000`

To stop the application run

```
docker-compose down
```

### ejecutar el proyecto sin docker

Requires

En la carpeta del proyecto ubicarse en el Path del back y ejecutar 

```bash
$ dotnet restore
```

To run the tests

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

**Run the React app**

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
