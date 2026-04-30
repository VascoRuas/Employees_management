# 14599 Employees Management

Sistema de gestão de funcionários em ASP.NET Core MVC com Entity Framework Core,
SQL Server, AdminLTE e ASP.NET Identity para autenticação.

## Setup inicial

1. Garante que o SQL Server Docker está a correr: `docker ps`
   (se não estiver: `docker start sqlserver`)

2. Dentro da pasta do projeto:
   ```
   dotnet restore
   dotnet ef migrations add InitialCreate
   dotnet ef database update
   dotnet run
   ```

3. Abre http://localhost:5000

## Importante - migrar de versão anterior

Se já tinhas a versão antiga (sem Identity) corrida, tens de RECRIAR a base de dados:

```
docker exec -it sqlserver /opt/mssql-tools18/bin/sqlcmd -S localhost -U sa -P 'Dev@Pass123' -C -Q "DROP DATABASE Employees14599"
```

Depois corre os comandos de Setup acima.

## Funcionalidades

- **Dashboard** (/) - Estatísticas (total funcionários, departamentos, países)
- **Employees** (/Employees) - CRUD completo (requer login)
- **Register/Login** - Sistema de autenticação ASP.NET Identity

A primeira coisa a fazer é registar um utilizador (Register no canto superior direito).
Depois faz login e podes começar a adicionar funcionários. Os campos CreatedBy/ModifiedBy
são preenchidos automaticamente com o ID do utilizador autenticado.
