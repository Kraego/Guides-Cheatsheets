# Some hints and howto for asp.net

- [Some hints and howto for asp.net](#some-hints-and-howto-for-aspnet)
  - [Entity framework](#entity-framework)
    - [Work with relations](#work-with-relations)
    - [Initialize DB Code first](#initialize-db-code-first)
    - [Migrations](#migrations)

## Entity framework

### Work with relations

* Example
```c#
    // the db Context 
    public class ApplicationDbContext : DbContext, IApplicationDbContext
    {
        public ApplicationDbContext(DbContextOptions<ApplicationDbContext> options)
            : base(options)
        {
        }
        public DbSet<RadariaData> Dataset { get; set; }
    }

    public class Match
    {
        // don't forget to add a Id
        public int Id { get; set; }

        public string Name { get; set; }
        public IEnumerable<GameSituation> Situations { get; set; }

        // relation to containing Matches
        public int DatasetId { get; set; }
        public RadariaData Dataset { get; set; }
    }

    public class RadariaData
    {
        public int Id { get; set; }
        public IEnumerable<Match> Matches { get; set; }
    }
}
```

### Initialize DB Code first

* Create init method and call it at the end of the **ConfigureServices** (Startup.cs) -  `InitializeDatabase(services);`
```c#
private static void InitializeDatabase(IServiceCollection services)
{
    // avoid init when called from migration creation
    if ("ef" == Assembly.GetEntryAssembly().GetName().Name.ToLower(CultureInfo.InvariantCulture))
    {
        return;
    }

    static void Migrate(DbContext context)
    {
        // f.e. when using in unit testenvironment
        if (context.Database.ProviderName != "Microsoft.EntityFrameworkCore.InMemory")
        {
            context.Database.Migrate();
        }
    }

    using var serviceProvider = services.BuildServiceProvider();
    var appCtx = serviceProvider.GetRequiredService<ApplicationDbContext>();
    Migrate(appCtx);
}
```
* Create migration method (call it at end of end of **configure** (Startup.cs)  `MigrateDatabase(app);`)
``` c#
private static void MigrateDatabase(IApplicationBuilder app)
{
    if ("ef" == Assembly.GetEntryAssembly().GetName().Name.ToLower(CultureInfo.InvariantCulture))
    {
        return;
    }
    using var serviceScope = app.ApplicationServices
        .GetRequiredService<IServiceScopeFactory>()
        .CreateScope();
    using var context = serviceScope.ServiceProvider.GetService<ApplicationDbContext>();
    context.Database.Migrate();
}
```

### Migrations

* Install
``` bash
# install ef cli tools
dotnet tool install --global dotnet-ef
dotnet tool update --global dotnet-ef
# verify
dotnet ef
```
* (set Environmet) - create Migrations
``` bash
$env:ASPNETCORE_ENVIRONMENT="Local"
dotnet ef migrations add Initial -v

#if running in nuget manager console
add-migration Initial -v
```
