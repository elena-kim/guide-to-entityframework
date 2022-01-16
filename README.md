## The Easiest EntityFramework

이 리포지토리는 The Easiest EntityFramework에 대해 기술한 리포지토리입니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/the-easiest-entityframework/stargazers"><img src="https://img.shields.io/github/stars/devncore/the-easiest-entityframework" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/the-easiest-entityframework" alt="License"> | <a href="https://github.com/devncore/the-easiest-entityframework/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/the-easiest-entityframework" alt="Commits-per-month"></a> |

<br />
   
## Overview
- [Entity Framework](#entity-framework)
- [Entity Framework Core](#entity-framework-core)
  - [Installation](#installation)
  - [DbContext](#dbcontext)
  - [DbSet](#dbset)
  - [Linq](#linq)
  - [Lambda](#lambda)

<br>

## Entity Framework
**Entity Framework** is an object-relational mapper (O/RM) that enables .NET developers to work with a database using .NET objects. It eliminates the need for most of the data-access code that developers usually need to write. 

With the Entity Framework, developers can work at a higher level of abstraction when they deal with data, and can create and maintain data-oriented applications with less code compared with traditional applications.

<br>

## Entity Framework Core
**EF Core** is a modern object-database mapper for .NET. It supports LINQ queries, change tracking, updates, and schema migrations. EF Core works with SQL Server, Azure SQL Database, SQLite, Azure Cosmos DB, MySQL, PostgreSQL, and other databases through a provider plugin API.

### Installation
✔️ Install Entity Framework Core &nbsp; [**`Microsort.EntityFrameworkCore`**](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore)

✔️ Install EF Core DB Provider &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [**`Database Providers`**](https://docs.microsoft.com/en-us/ef/core/providers/?tabs=dotnet-core-cli)

<br>

### DbContext
A **DbContext** instance represents a session with the database and can be used to query and save instances of your entities.  
DbContext is a combination of the Unit Of Work and Repository patterns.

DbContext in EF Core allows us to perform following tasks:

1. Manage database connection  
1. Configure model & relationship  
1. Querying database  
1. Saving data to the database  
1. Configure change tracking  
1. Caching  
1. Transaction management  

To use DbContext in our application, we need to create the class that derives from DbContext, also known as context class.
```csharp
public class DevNcoreContext : DbContext
{
    // EF is very easy...!
}
```

The `OnConfiguring()` method allows us to select and configure the data source to be used with a context using `DbContextOptionsBuilder`.
```csharp

public class DevNcoreContext : DbContext
{
    protected override void OnConfiguring(DbContextOptionsBuilder optionsBuilder)
    {
        optionsBuilder.UseSqlServer(@"Server=(localdb)\mssqllocaldb;Database=Test");
    }
}
```

<br>

### DbSet
The **DbSet\<TEntity\>** class represents a collection for a given entity within the model and is the gateway to database operations against an entity. DbSet\<TEntity\> classes are added as properties to the DbContext and are mapped by default to database tables that take the name of the DbSet\<TEntity\> property.

```csharp
public class DevNcoreContext : DbContext
{
    public DbSet<User> Users { get; set; }
    public DbSet<Friend> Friends { get; set; }
    
    protected override void OnConfiguring(DbContextOptionsBuilder optionsBuilder)
    {
        optionsBuilder.UseSqlServer(@"Server=(localdb)\mssqllocaldb;Database=Test");
    }
}

public class User
{
    [Key]
    public int Seq { get; set; }
    public string Name { get; set; }
    public DateTime Created { get; set; }
    public DateTime Updated { get; set; }
}

public class Friend
{
    [Key]
    public int Seq { get; set; }
    public int UserSeq { get; set; }
    public int FriendsSeq { get; set; }
    public bool IsAccepted { get; set; }
    public DateTime Created { get; set; }
    public DateTime Updated { get; set; }
}
```
In the example above, two DbSet\<TEntity\> properties have been added to the DbContext class. The first represents a collection of User objects, which is mapped by convention to a database table named "Users", after the property name. The second DbSet property represents a collection of Friend objects, and is mapped to a table named "Friends".
    
<br>

***

## Reference
📑 [Entity Framework Tutorial](https://www.entityframeworktutorial.net/what-is-entityframework.aspx)   
📑 [Learn Entity Framework Core](https://www.learnentityframeworkcore.com/) 
