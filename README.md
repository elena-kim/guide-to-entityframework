## Guide to EntityFramework

이 리포지토리는 EntityFramework에 대해 기술한 리포지토리입니다. <br />

<a href="https://github.com/devncore/devncore"><strong>더 알아보기 »</strong></a>
 
| Star | License | Activity |
|:----:|:-------:|:--------:|
| <a href="https://github.com/devncore/guide-to-entityframework/stargazers"><img src="https://img.shields.io/github/stars/devncore/guide-to-entityframework" alt="Github Stars"></a> | <img src="https://img.shields.io/github/license/devncore/guide-to-entityframework" alt="License"> | <a href="https://github.com/devncore/guide-to-entityframework/pulse"><img src="https://img.shields.io/github/commit-activity/m/devncore/guide-to-entityframework" alt="Commits-per-month"></a> |

<br />
   
## Entity Framework
**Entity Framework**는 .NET 개발자가 .NET 객체를 사용하여 데이터베이스로 작업할 수 있도록 하는 O/RM(개체 관계형 매퍼)입니다. 개발자가 일반적으로 작성해야 하는 대부분의 데이터 액세스 코드가 필요하지 않습니다.

Entity Framework를 통해 개발자는 데이터를 처리할 때 더 높은 수준의 추상화를 수행할 수 있으며, 기존 애플리케이션에 비해 적은 코드로 데이터 지향 애플리케이션을 만들고 유지할 수 있습니다.

<br>

## Entity Framework Core
**EF Core**는 .NET을 위한 최신 객체 데이터베이스 매퍼입니다. LINQ 쿼리, 변경 추적, 업데이트 및 스키마 마이그레이션을 지원합니다. EF Core는 공급자 플러그인 API를 통해 SQL Server, Azure SQL Database, SQLite, Azure Cosmos DB, MySQL, Postgre 및 기타 데이터베이스와 함께 작동합니다.

✔️ Entity Framework Core 설치 &nbsp; [**`Microsort.EntityFrameworkCore`**](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore)

✔️ EF Core DB Provider 설치 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [**`Database Providers`**](https://docs.microsoft.com/en-us/ef/core/providers/?tabs=dotnet-core-cli)

<br>

### DbContext
**DbContext** 인스턴스는 데이터베이스와의 세션을 나타내며, 쿼리문을 보내고 엔티티의 인스턴스를 저장하는 데 사용할 수 있습니다. DbContext는 작업 단위 및 Repository 패턴의 조합입니다.

EF Core의 DbContext는 아래와 같은 일들을 수행합니다.

1. 데이터베이스 연결 관리  
1. 모델 및 관계 구성  
1. 데이터베이스 쿼리  
1. 데이터베이스에 데이터 저장  
1. 변경 추적 구성  
1. 캐싱  
1. 트랜잭션 관리  

DbContext를 애플리케이션에서 사용하기 위해서는 DbContext를 상속받은 클래스를 생성해야 합니다.
```csharp
public class DevNcoreContext : DbContext
{
    // EF is very easy!
}
```

`OnConfiguring()` 메서드는  `DbContextOptionsBuilder`를 사용하여 데이터 소스를 선택하고 구성할 수 있게 합니다.
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
**DbSet\<TEntity\>** 클래스는 모델 내에서 지정된 엔티티에 대한 컬렉션을 나타내며, 엔티티에 대한 데이터베이스 작업의 관문입니다. DbSet\<TEntity\> 클래스는 DbContext에 프로퍼티로 추가되고 기본적으로 DbSet\<TEntity\> 프로퍼티의 이름을 사용하는 데이터베이스 테이블에 매핑됩니다.

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
위의 예에서는 두 개의 DbSet\<TEntity\> 프로퍼티가 DevNcoreContext 클래스에 추가되었습니다. 첫 번째는 User 객체의 컬렉션을 나타내며, "Users"라는 데이터베이스 테이블에 매핑됩니다. 두 번째 DbSet 프로퍼티는 Friend 객체의 컬렉션을 나타내며 "Friends"라는 테이블에 매핑됩니다.
    
<br>

***

## Reference
📑 [Entity Framework Tutorial](https://www.entityframeworktutorial.net/what-is-entityframework.aspx)   
📑 [Learn Entity Framework Core](https://www.learnentityframeworkcore.com/) 
