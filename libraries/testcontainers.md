# TestContainers

TestContainers is a .NET library that provides lightweight, reliable, and disposable containers for integration tests. It allows you to use containers like Docker in your test suite while maintaining simplicity and performance. TestContainers is commonly used in .NET projects to facilitate testing of applications that rely on external services, databases, or other containerized components.

## Key Features

- **Container Management:** TestContainers allows you to manage container lifecycles, including starting, stopping, and cleaning up containers.

- **Container Types:** It supports a variety of container types, including Docker containers, databases, message brokers, and more.

- **Container Configuration:** You can configure containers with various settings to match your testing needs, such as ports, environment variables, and initialization scripts.

- **Test Framework Integration:** TestContainers integrates with popular .NET testing frameworks, enabling you to easily incorporate containers into your test cases.

- **Container Disposal:** Containers are automatically disposed of at the end of the test, ensuring resources are cleaned up.

## Resources

- **[Official Documentation](https://dotnet.testcontainers.org/):** The official documentation provides comprehensive guidance on using TestContainers, including examples, best practices, and advanced features.

- **[GitHub Repository](https://github.com/Quamotion/TestContainers):** The GitHub repository is where you can find the latest source code, report issues, and contribute to the project.

- **[NuGet Package](https://www.nuget.org/packages/Quamotion.TestContainers/):** You can add the TestContainers NuGet package to your .NET projects to start using containers in your integration tests.

## Getting Started

To get started with TestContainers, follow these simple steps:

1. Install the TestContainers NuGet package in your project.

2. Choose the type of container you need for your tests (e.g., a database, message broker, or custom Docker container).

3. Configure the container with any necessary settings, such as ports and environment variables.

4. Use the container in your integration tests to create realistic testing scenarios.

5. Ensure the container is properly disposed of at the end of the test to clean up resources.

## Example

Here's a simple example of how to use TestContainers to run a PostgreSQL database container in your integration tests:

```csharp
using Npgsql;
using Quamotion.Testcontainers;
using Quamotion.Testcontainers.PostgreSql;

public class MyIntegrationTests
{
    [Fact]
    public void TestWithPostgresContainer()
    {
        // Arrange
        using var containerBuilder = new ContainerBuilder<PostgreSqlContainer>()
            .ConfigureDatabaseConfiguration("mydatabase", "myuser", "mypassword")
            .ConfigurePort(5432)
            .ConfigureNetwork("my-network");

        var container = containerBuilder.Build();

        using var connection = new NpgsqlConnection(container.GetConnectionString());

        // Act
        connection.Open();

        // Perform tests using the database connection

        // Assert
        // Assert the results of your integration tests

        // The container will be disposed of automatically when it goes out of scope
    }
}
```

In this example, we use TestContainers to create and manage a PostgreSQL database container for integration tests.

TestContainers simplifies the process of incorporating containers into your integration tests, enabling you to validate your application's behavior with realistic dependencies.

## License

TestContainers is open-source software and is released under the Apache License 2.0.