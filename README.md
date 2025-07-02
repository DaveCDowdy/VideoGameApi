Video Game API
A modern RESTful API built with .NET 9, designed to manage a collection of video game data. This API provides full CRUD (Create, Read, Update, Delete) operations for video game entries, backed by a SQL Server Express database. This project serves as a hands-on learning exercise, developed by following a YouTube tutorial to understand the core functionalities and new aspects of .NET 9 Web APIs.

🚀 Features
Full CRUD Operations:

Retrieve all video games.

Retrieve a single video game by ID.

Add new video games.

Update existing video games.

Delete video games.

RESTful Design: Adheres to REST principles for clear and consistent API interactions.

Entity Framework Core: Utilizes EF Core for seamless object-relational mapping with SQL Server.

Database Seeding: Includes initial seed data for immediate testing and development.

Built-in OpenAPI (Swagger/Scalar) Documentation: Automatically generated interactive API documentation for easy exploration and testing of endpoints.

📦 Technologies Used
.NET 9: The latest stable version of Microsoft's versatile developer platform.

ASP.NET Core Web API: For building robust and scalable HTTP services.

Entity Framework Core: Modern object-relational mapper for database interactions.

Microsoft.EntityFrameworkCore.SqlServer

SQL Server Express: Local database solution for development.

OpenAPI (Built-in .NET 9): For API specification.

Scalar.AspNetCore: The default interactive UI for OpenAPI documentation in .NET 9.

🚦 Getting Started
Follow these steps to get the API up and running on your local machine.

Prerequisites
.NET 9 SDK (Stable release)

Visual Studio 2022 (or Visual Studio Code with C# Dev Kit)

SQL Server Express (or a local instance of SQL Server)

Installation
Clone the repository:

Bash

git clone [your-repo-url]
cd VideoGameApi
Restore NuGet packages:

Bash

dotnet restore
Database Setup
This project uses SQL Server Express with Entity Framework Core Migrations and includes seed data.

Set up your connection string:
Your DefaultConnection string points to a local SQL Server Express instance using Windows Authentication. For security, this connection string should be set up using .NET User Secrets.

Open your terminal in the VideoGameApi project directory and run:

Bash

dotnet user-secrets set "ConnectionStrings:DefaultConnection" "Server=localhost\\SQLEXPRESS;Database=VideoGameDb;Trusted_Connection=True;MultipleActiveResultSets=true"
(Note: If your SQL Server Express instance name is different, or you're using (localdb)\\mssqllocaldb, adjust the Server part accordingly.)

Apply Migrations and Seed Data:
The VideoGameDbContext contains seed data that will be populated when you apply the migrations.

Bash

dotnet ef database update
This command will:

Create the VideoGameDb database (if it doesn't exist) on your localhost\SQLEXPRESS instance.

Create the VideoGames table.

Populate the table with initial game data (Spider-Man 2, The Legend of Zelda, Cyberpunk 2077).

Running the Application
Once the database is set up, you can run the API:

From Visual Studio 2022:

Open the VideoGameApi.sln solution.

Press F5 to run the application in debug mode.

From the command line:

Bash

dotnet run
The API will typically run on https://localhost:7297 (check your console output for the exact URL).

🚀 API Endpoints
The API base URL is https://localhost:7297/api/VideoGame (adjust port if different).

Video Game Endpoints (/api/VideoGame)
Method

Path

Description

Request Body (JSON)

Response Body (JSON) / Status Codes

GET

/

Retrieves a list of all video games.

None

200 OK + List<VideoGame>

GET

/{id}

Retrieves a single video game by ID.

None

200 OK + VideoGame / 404 Not Found

POST

/

Adds a new video game.

{"title": "New Game", "platform": "PC", ...}

201 Created + VideoGame / 400 Bad Request

PUT

/{id}

Updates an existing video game by ID.

{"id": 1, "title": "Updated Title", "platform": "PC", ...}

204 No Content / 404 Not Found

DELETE

/{id}

Deletes a video game by ID.

None

204 No Content / 404 Not Found


Export to Sheets
VideoGame Model Example
C#

public class VideoGame
{
    public int Id { get; set; }
    public string? Title { get; set; }
    public string? Platform { get; set; }
    public string? Developer { get; set; }
    public string? Publisher { get; set; }
}
📄 API Documentation (OpenAPI / Scalar UI)
This project automatically generates interactive API documentation using the built-in OpenAPI support in .NET 9 and the Scalar UI.

Interactive UI: Open your browser and navigate to:
https://localhost:7297/ (or your application's root URL)

Raw OpenAPI JSON: You can access the raw OpenAPI specification at:
https://localhost:7297/openapi/v1.json
