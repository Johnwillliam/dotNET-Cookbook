# MediatR

MediatR is a .NET library that simplifies the implementation of the mediator pattern in your applications. The mediator pattern promotes decoupling between components, improving the organization of your code and making it easier to manage requests and notifications. MediatR is commonly used in .NET applications to handle commands, queries, and domain events.

## Key Features

- **Mediator Pattern:** MediatR provides a mediator pattern implementation, allowing you to send requests and notifications between components without direct dependencies.

- **CQRS Support:** MediatR is often used in conjunction with the Command-Query Responsibility Segregation (CQRS) pattern to separate read and write concerns.

- **Request and Response Objects:** You can define request and response objects, making it easy to structure and handle commands and queries.

- **Pipeline Behaviors:** MediatR allows you to define pipeline behaviors to perform cross-cutting concerns, such as validation, logging, and authorization.

- **Asynchronous Support:** MediatR supports asynchronous request handling, improving application responsiveness.

## Resources

- **[Official Documentation](https://github.com/jbogard/MediatR):** The official documentation provides comprehensive guidance on using MediatR, including examples, best practices, and advanced features.

- **[GitHub Repository](https://github.com/jbogard/MediatR):** The GitHub repository is where you can find the latest source code, report issues, and contribute to the project.

- **[NuGet Package](https://www.nuget.org/packages/MediatR/):** You can add the MediatR NuGet package to your .NET projects to start implementing the mediator pattern.

## Getting Started

To get started with MediatR, follow these simple steps:

1. Install the MediatR NuGet package in your project.

2. Define your request and notification objects. These objects represent the commands, queries, and events that you want to handle.

3. Create handlers for your request and notification objects. Handlers contain the logic to process requests.

4. Use the MediatR library to send requests and notifications to their respective handlers.

## Example

Here's a simple example of how to use MediatR to handle a command:

Suppose you have a command that adds a new product to your e-commerce system:

```csharp
public class AddProductCommand : IRequest
{
    public string Name { get; set; }
    public decimal Price { get; set; }
}
```

You can create a handler to process the command:

```csharp
using MediatR;

public class AddProductCommandHandler : IRequestHandler<AddProductCommand>
{
    public Task<Unit> Handle(AddProductCommand request, CancellationToken cancellationToken)
    {
        // Logic to add the product to the database
        // ...

        return Task.FromResult(Unit.Value);
    }
}
```

Now, you can use MediatR to send the command:

```csharp
var mediator = new Mediator(new ServiceFactory(serviceType => container.Resolve(serviceType)));
var command = new AddProductCommand { Name = "Sample Product", Price = 19.99 };
await mediator.Send(command);
```

MediatR simplifies the handling of commands, queries, and notifications, making your code more organized and maintainable.

## License

MediatR is open-source software and is released under the MIT License.