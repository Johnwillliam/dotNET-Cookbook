# Entity Framework

Entity Framework (EF) is an Object-Relational Mapping (ORM) framework for .NET that simplifies database access by allowing you to work with databases using .NET objects. It provides a high-level abstraction for interacting with databases, making database-related tasks more efficient and developer-friendly.

## Key Features

- **Model-First Development:** EF allows you to define your data model using classes and attributes in your code, enabling a code-first approach.

- **Database Providers:** EF supports multiple database providers, including Microsoft SQL Server, MySQL, PostgreSQL, SQLite, and more.

- **LINQ Support:** EF allows you to query your data using Language Integrated Query (LINQ), which provides a strongly typed and intuitive way to retrieve data.

- **Migrations:** EF supports database schema migrations, making it easy to evolve your database schema as your application evolves.

- **Asynchronous Operations:** EF supports asynchronous database operations, improving the responsiveness and scalability of your applications.

## Resources

- **[Official Documentation](https://learn.microsoft.com/en-us/ef/):** The official documentation provides detailed information on using Entity Framework, including tutorials, best practices, and advanced features.

- **[GitHub Repository](https://github.com/dotnet/efcore):** The GitHub repository for Entity Framework Core (EF Core), the latest version of EF, is where you can find the latest source code, report issues, and contribute to the project.

- **[NuGet Packages](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore/):** You can add Entity Framework to your .NET projects via NuGet.

## Getting Started

To get started with Entity Framework, follow these simple steps:

1. Install the Entity Framework NuGet package in your project. Note that there are separate packages for EF Core and EF6.

2. Define your data model using C# classes. These classes represent the tables and relationships in your database.

3. Configure EF to use your data model. This typically involves creating a context class that derives from `DbContext`.

4. Use EF to interact with your database. You can perform CRUD (Create, Read, Update, Delete) operations, query data, and manage database schema migrations.

## Example

Here's a simple example of how to use Entity Framework (EF Core) to create a data model and perform database operations:

Suppose you have the following data model class:

```csharp
public class Product
{
    public int ProductId { get; set; }
    public string Name { get; set; }
    public decimal Price { get; set; }
}
```

You can create a context class that specifies your data model and connection string:

```csharp
public class AppDbContext : DbContext
{
    public DbSet<Product> Products { get; set; }
    
    protected override void OnConfiguring(DbContextOptionsBuilder options)
    {
        options.UseSqlServer("YourConnectionStringHere");
    }
}
```

Now, you can use Entity Framework to interact with your database:

```csharp
using (var context = new AppDbContext())
{
    // Add a new product
    var newProduct = new Product { Name = "Example Product", Price = 29.99 };
    context.Products.Add(newProduct);
    context.SaveChanges();

    // Query products
    var products = context.Products.ToList();
    foreach (var product in products)
    {
        Console.WriteLine($"Product: {product.Name}, Price: {product.Price:C}");
    }
}
```

Entity Framework simplifies database access in your .NET applications, making it easier to work with data.

## License

Entity Framework is open-source software and is released under the MIT License.