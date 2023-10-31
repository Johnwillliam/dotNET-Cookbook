# AutoMapper

AutoMapper is a popular object-to-object mapping library for .NET. It simplifies the process of mapping data between different data models in your .NET applications, reducing the need for repetitive code and making your codebase cleaner and more maintainable.

## Key Features

- **Object Mapping:** AutoMapper allows you to map data between objects with ease. It automatically resolves property mapping, simplifying the mapping process.

- **Custom Mapping:** You can define custom mappings when needed, giving you full control over how data is mapped between objects.

- **Flattening:** AutoMapper supports flattening complex objects and nested objects into a single object, making it convenient for data transfer.

- **Expression-Based:** AutoMapper uses expressions and convention-based mapping to improve performance and accuracy.

## Resources

- **[Official Documentation](https://automapper.org/):** The official documentation provides comprehensive guidance on using AutoMapper, including examples, best practices, and advanced features.

- **[GitHub Repository](https://github.com/AutoMapper/AutoMapper):** The GitHub repository is the central hub for AutoMapper, where you can find the latest source code, report issues, and contribute to the project.

- **[NuGet Package](https://www.nuget.org/packages/AutoMapper/):** You can add the AutoMapper NuGet package to your .NET projects to start using object-to-object mapping.

## Getting Started

To get started with AutoMapper, follow these simple steps:

1. Install the AutoMapper NuGet package in your project.

2. Define your mapping profiles, which specify how objects should be mapped between source and destination types.

3. Configure AutoMapper to use your mapping profiles. You typically do this during application startup.

4. Use AutoMapper to map objects in your application. It's as simple as calling `Mapper.Map`.

## Example

Here's a simple example of how to use AutoMapper to map objects between a source and a destination type:

Suppose you have the following source and destination classes:

```csharp
public class Source
{
    public int Id { get; set; }
    public string Name { get; set; }
}

public class Destination
{
    public int Identifier { get; set; }
    public string FullName { get; set; }
}
```

You can create a mapping profile to specify how to map these objects:

```csharp
public class MappingProfile : Profile
{
    public MappingProfile()
    {
        CreateMap<Source, Destination>()
            .ForMember(dest => dest.Identifier, opt => opt.MapFrom(src => src.Id))
            .ForMember(dest => dest.FullName, opt => opt.MapFrom(src => src.Name));
    }
}
```

In your application's configuration, you set up AutoMapper to use this mapping profile:

```csharp
var config = new MapperConfiguration(cfg =>
{
    cfg.AddProfile<MappingProfile>();
});

var mapper = config.CreateMapper();
```

Now, you can use AutoMapper to map objects:

```csharp
var source = new Source { Id = 1, Name = "John Doe" };
var destination = mapper.Map<Source, Destination>(source);
```

The destination object will be automatically mapped from the source object according to the mapping profile.

AutoMapper simplifies object-to-object mapping, making your code more maintainable and efficient.

## License

AutoMapper is open-source software and is released under the MIT License.