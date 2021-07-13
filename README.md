### About us

> &nbsp; :adult: __James Lee__ &nbsp;&nbsp; [Github](https://github.com/devncore-james) &nbsp;&nbsp; james.lee@devncore.org  
> &nbsp; :woman: __Elena Kim__ &nbsp;&nbsp; [Github](https://github.com/devncore-elena) &nbsp;&nbsp; elena.kim@devncore.org

We are very ordinary developers, so we need to communicate with you.   
You can always share information with us and we are looking forward to it.  

##### _Open Source &nbsp; https://github.com/devncore/devncore   &nbsp;&nbsp;   Official Website &nbsp; https://devncore.org_ 

### License Policy
[![MIT license](https://img.shields.io/badge/License-MIT-blue.svg)](https://lbesson.mit-license.org/)
[![GPLv3 license](https://img.shields.io/badge/License-GPLv3-blue.svg)](http://perso.crans.org/besson/LICENSE.html)


***

## Entity Framework
**Entity Framework** is an object-relational mapper (O/RM) that enables .NET developers to work with a database using .NET objects. It eliminates the need for most of the data-access code that developers usually need to write. 

With the Entity Framework, developers can work at a higher level of abstraction when they deal with data, and can create and maintain data-oriented applications with less code compared with traditional applications.

<br>

## Entity Framework Core
**EF Core** is a modern object-database mapper for .NET. It supports LINQ queries, change tracking, updates, and schema migrations. EF Core works with SQL Server, Azure SQL Database, SQLite, Azure Cosmos DB, MySQL, PostgreSQL, and other databases through a provider plugin API.

### Installation
✔️ Install Entity Framework Core &nbsp; [**`Microsort.EntityFrameworkCore`**](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore)

✔️ Install EF Core DB Provider &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [**`Database Providers`**](https://docs.microsoft.com/en-us/ef/core/providers/?tabs=dotnet-core-cli)

### DbContext

```csharp
public class DevNcoreContext : DbContext
{
    // EF is very easy...!
}
```

```csharp

public class DevNcoreContext : DbContext
{
    protected override void OnConfiguring(DbContextOptionsBuilder optionsBuilder)
    {
        optionsBuilder.UseSqlServer(@"Server=(localdb)\mssqllocaldb;Database=Test");
    }
}
```

TBD ...

### DbSet

TBD ...

### Linq

TBD ...

### Lambda

TBD ...

***

## Reference
:bookmark_tabs: [Entity Framework Tutorial](https://www.entityframeworktutorial.net/what-is-entityframework.aspx)   
:bookmark_tabs: [Learn Entity Framework Core](https://www.learnentityframeworkcore.com/) 
