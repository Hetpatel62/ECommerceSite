# ECommerceSite

ASP.NET MVC 5 demo e-commerce site built with C#, Razor views, Entity Framework 6, Bootstrap 3, and Ninject.

## Overview

This sample application demonstrates a simple online store with product browsing, cart management, checkout, and email order notifications. It includes a layered architecture with a domain project for business logic and data access, and a WebUI project for the MVC front-end.

## Key Features

- Product listing and paging
- Shopping cart with add/remove/update functionality
- Checkout flow with shipping details
- Email order notification using SMTP settings
- Entity Framework Code First with SQL Server
- Dependency injection using Ninject
- ASP.NET MVC 5 + Razor views

## Requirements

- Visual Studio 2015/2017/2019/2022 or later with ASP.NET development tools
- .NET Framework 4.5.2
- SQL Server or LocalDB
- NuGet package restore enabled

## Getting Started

1. Clone or extract the repository.
2. Open `ECommerceSite.sln` in Visual Studio.
3. Restore NuGet packages.
4. Configure the database connection string in `ECommerceSite.WebUI/Web.config`.

### Database Configuration

The app uses the `EFDbContext` connection string in `ECommerceSite.WebUI/Web.config`:

```xml
<add name="EFDbContext" connectionString="Data Source=YOUR_SQL_SERVER;Initial Catalog=ECommerceSite;Integrated Security=True" providerName="System.Data.SqlClient" />
```

Replace `YOUR_SQL_SERVER` and database name as needed. If you use LocalDB, you can use a connection string like:

```xml
Data Source=(localdb)\MSSQLLocalDB;Initial Catalog=ECommerceSite;Integrated Security=True
```

The project contains Entity Framework migrations under `ECommerceSite.Domain/Migrations`, so the database schema can be created automatically on first run.

### Email Settings

Update `ECommerceSite.Domain/Concrete/EmailSettings.cs` with your SMTP settings:

- `MailToAddress`
- `MailFromAddress`
- `Username`
- `Password`
- `ServerName`
- `ServerPort`
- `UseSsl`

This enables the order confirmation email flow from `EmailOrderProcess`.

## Running the Application

- Set `ECommerceSite.WebUI` as the startup project.
- Build the solution.
- Run the application in IIS Express or your preferred web server.

## Project Structure

- `ECommerceSite.sln` — solution file
- `ECommerceSite.Domain/` — domain project, Entity Framework data access, business logic, email service
- `ECommerceSite.WebUI/` — ASP.NET MVC web application, controllers, views, UI assets

## Notes

- The sample uses older packages: MVC 5, EF 6, Bootstrap 3, and Ninject.
- If you want to change the email behavior, update `ECommerceSite.Domain/Concrete/EmailOrderProcess.cs`.
- For any configuration changes, prefer editing `Web.config` and `EmailSettings.cs` before running.

## License

This repository is provided as-is for learning and demonstration purposes.
