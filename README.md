# the-easiest-entityframework

TBD ...

# Overview

TBD ...

# DbContext

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

# DbSet

TBD ...

# Linq

TBD ...

# Lambda

TBD ...
