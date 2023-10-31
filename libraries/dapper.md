# Dapper

Dapper is a micro ORM (Object-Relational Mapping) library for .NET. It provides a simple and efficient way to access and work with databases in your .NET applications. Dapper is known for its lightweight and high-performance characteristics.

## Key Features

- **Simplicity:** Dapper offers a straightforward API for executing database queries and commands. It avoids unnecessary abstractions, making it easy to understand and use.

- **High Performance:** Dapper is designed for speed. It's one of the fastest ORMs available for .NET, making it an excellent choice for performance-critical applications.

- **Object Mapping:** Dapper provides automatic object mapping, allowing you to work with database records as .NET objects. This simplifies data access and manipulation.

- **Parameterized Queries:** Dapper supports parameterized queries, which help protect your application against SQL injection attacks.

- **Raw SQL Queries:** While Dapper can work with object mapping, it also allows you to execute raw SQL queries when needed, giving you full control.

## Resources

- **[Official Documentation](https://dapperlib.github.io/Dapper/):** The official documentation provides in-depth guidance on using Dapper, including examples and best practices.

- **[GitHub Repository](https://github.com/DapperLib/Dapper):** The GitHub repository is the place to find the latest source code, report issues, and contribute to the project.

- **[NuGet Package](https://www.nuget.org/packages/Dapper/):** You can easily add Dapper to your .NET projects via NuGet.

## Getting Started

To get started with Dapper, follow these simple steps:

1. Install the Dapper NuGet package in your project.

2. Create a database connection. Dapper is database-agnostic, so it works with a variety of database systems.

3. Write your queries and commands using Dapper's API. Dapper simplifies data access by providing methods for executing queries and mapping the results to objects.

4. Execute your queries and work with the results in your .NET application.

## Example

Here's a simple example of how to use Dapper to query a database and map the results to a .NET object:

```csharp
using System;
using System.Data;
using System.Data.SqlClient;
using Dapper;

public class Person
{
    public int Id { get; set; }
    public string Name { get; set; }
    public int Age { get; set; }
}

public class Program
{
    public static void Main()
    {
        using IDbConnection dbConnection = new SqlConnection("YourConnectionStringHere");
        dbConnection.Open();

        var people = dbConnection.Query<Person>("SELECT * FROM People");
        
        foreach (var person in people)
        {
            Console.WriteLine($"Name: {person.Name}, Age: {person.Age}");
        }
    }
}
```

In this example, we've queried a database table named "People" and mapped the results to a list of Person objects using Dapper.

Dapper simplifies the process of working with databases, and its performance benefits make it an excellent choice for database access in .NET applications.

## License

Dapper is open-source software and is released under the MIT License.