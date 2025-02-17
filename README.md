# ASP.NET-Core-WebAPI-Guide


# ASP.NET Core Web API with Entity Framework Core & SQL Server

## 🚀 Step-by-Step Guide

### 1️⃣ Open Visual Studio 2022

### 2️⃣ Create a New Project
- Search for **ASP.NET Core Web API** in the template list.
- Select the template and click **Next**.

### 3️⃣ Name Your Project
- Enter your desired **Project Name**.
- Click **Create**.

### 4️⃣ Install Required NuGet Packages
Navigate to:
```
Tools → NuGet Package Manager → Manage NuGet Packages for Solution → Browse
```
Search and install the following packages:
- `Microsoft.EntityFrameworkCore (8.0.0)`
- `Microsoft.EntityFrameworkCore.Tools (8.0.0)`
- `Microsoft.EntityFrameworkCore.Design (8.0.0)`
- `Microsoft.VisualStudio.Web.CodeGeneration.Design (9.0.0)`
- `Microsoft.EntityFrameworkCore.SqlServer (8.0.0)`

### 5️⃣ Setup SQL Server Database
- Open **Microsoft SQL Server Management Studio (SSMS)**.
- Connect to your SQL Server.
- Create a **new Database**.
- Create a **Table** and insert a sample record.

### 6️⃣ Connect Database in Visual Studio
Navigate to:
```
View → Server Explorer → Data Connection → Connect to Database
```
Enter details:
- **Server Name**: (Enter your SQL Server name)
- **Database Name**: (Enter your database name)
- Check ✅ ‘Trust Server Certificate’
- Click **Test Connection → OK**

### 7️⃣ Configure `appsettings.json`
Update the **Connection String** in `appsettings.json`:
```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=[Enter Server Name];Database=[Enter Database Name];Trusted_Connection=True;TrustServerCertificate=true;"
  }
}
```

### 8️⃣ Scaffold Database Context & Models
Run the following command in **Package Manager Console**:
```sh
cd [YourProjectName]
dotnet ef dbcontext scaffold "Data Source=[Enter Server Name];Initial Catalog=[Enter Database Name];Integrated Security=True;Trust Server Certificate=True" Microsoft.EntityFrameworkCore.SqlServer -o Models --force
```

### 9️⃣ Register Database Context in `Program.cs`
Add the following:
```csharp
using Microsoft.EntityFrameworkCore;

var builder = WebApplication.CreateBuilder(args);

// Register Database Context
builder.Services.AddDbContext<[DatabaseName]Context>(options =>
    options.UseSqlServer(builder.Configuration.GetConnectionString("DefaultConnection")));

var app = builder.Build();
```

### 🔟 Add API Controller for CRUD Operations
Navigate to **Solution Explorer**:
```
Right-click on Controllers → Add → Controller
```
- Select **"API Controller with actions, using Entity Framework"**.
- Choose your **Model Class & DbContext Class**.
- Click **Add ✅**.

### 🎉 Run & Test Your API
✅ Run the application, test API endpoints using **Postman** or **Swagger UI**! 🚀

---
### 📌 Contribute
Feel free to contribute by forking the repo, making changes, and submitting a pull request!

### 🔗 License
This project is licensed under the **MIT License**.
