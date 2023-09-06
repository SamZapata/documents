# Creating a webapi using ASP .Net Core 6 and VS

### Database
Create the data base. For this use SQL server.

### Create project with VS
 Use ` ASP.NET Core Web Api` template.

### Configure NuGet Packages
In project option use `Manage NuGet Packages` and install
 - Microsoft.EntityFrameworkCore.SqlServer
 - Microsoft.EntityFrameworkCore.Tools
  
### Package Manager Console
Go to `Tools > NuGet Package Manager > Package Manager Console` and run the command
``` 
Scaffold-DbContext "server=server-name; DataBase=DBName; Integrated Security=true; TrustServerCertificate=True" Microsoft.EntityFrameworkCore.SqlServer -OutputDir Models 
```

### Check the project
Using Scaffold-DbContext (Microsoft.EntityFrameworkCore) with the `-OutputDir Models` option, the *Models* folder will be created with the models from database and a Database Context `DatabaseModelContex.cs`.

### Configure the DatabaseModelContext
Remove warning sentences on the `OnConfiguring` section.
```
protected override void OnConfiguring(DbContextOptionsBuilder optionsBuilder)
    {
    }
```

### Add Connection Strings in appsettings.json
use
```
"ConnectionStrings": {
    "SQLString": "server=DESKTOP-46TRFT3\\SQLEXPRESS; DataBase=CharactersRM; Integrated Security=true; TrustServerCertificate=True"
  },
```

### Configure Programs.cs
Import libraries and models
```
using Microsoft.EntityFrameworkCore;
using ProjectName.Models;
```
Add DbContext with the SQL connection string
```
builder.Services.AddDbContext<CharactersRmContext>(opt => opt.UseSqlServer(builder.Configuration.GetConnectionString("server=DESKTOP-46TRFT3\\SQLEXPRESS; DataBase=CharactersRM; Integrated Security=true; TrustServerCertificate=True")))
```

### Add controller and configure it
Use `API Controller - Empty`.