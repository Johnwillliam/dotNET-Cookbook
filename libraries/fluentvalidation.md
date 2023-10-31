# FluentValidation

FluentValidation is a .NET library for building strongly-typed validation rules in your applications. It provides a fluent API for defining validation logic and is commonly used for form validation, data input validation, and ensuring data integrity in your .NET projects.

## Key Features

- **Strongly-Typed Validation:** FluentValidation allows you to define validation rules using strongly-typed models, making your validation logic clear and type-safe.

- **Fluent API:** It provides a fluent and expressive API for creating validation rules, with support for conditions and custom validators.

- **Server-Side and Client-Side Validation:** You can use FluentValidation for server-side validation and easily integrate it with client-side validation in web applications.

- **Custom Validators:** FluentValidation allows you to create custom validators to address specific validation requirements.

- **Localization:** You can localize validation error messages, making it accessible for internationalization.

## Resources

- **[Official Documentation](https://docs.fluentvalidation.net/en/latest/):** The official documentation provides comprehensive guidance on using FluentValidation, including examples, best practices, and advanced features.

- **[GitHub Repository](https://github.com/FluentValidation/FluentValidation):** The GitHub repository is where you can find the latest source code, report issues, and contribute to the project.

- **[NuGet Package](https://www.nuget.org/packages/FluentValidation/):** You can add the FluentValidation NuGet package to your .NET projects to start building validation rules.

## Getting Started

To get started with FluentValidation, follow these simple steps:

1. Install the FluentValidation NuGet package in your project.

2. Define your validation rules by creating a validation class that inherits from `AbstractValidator<T>`, where `T` is the model or object you want to validate.

3. In the validation class, use the fluent API to define validation rules for each property in your model.

4. Integrate FluentValidation with your application to perform validation, whether it's during form submissions or data processing.

## Example

Here's a simple example of how to use FluentValidation to define validation rules for a model:

Suppose you have a model class named `Person`:

```csharp
public class Person
{
    public string FirstName { get; set; }
    public string LastName { get; set; }
    public int Age { get; set; }
}
```

You can create a validation class for the Person model:

```csharp
using FluentValidation;

public class PersonValidator : AbstractValidator<Person>
{
    public PersonValidator()
    {
        RuleFor(person => person.FirstName).NotEmpty().WithMessage("First name is required.");
        RuleFor(person => person.LastName).NotEmpty().WithMessage("Last name is required.");
        RuleFor(person => person.Age).InclusiveBetween(18, 99).WithMessage("Age must be between 18 and 99.");
    }
}
```

Now, you can use FluentValidation to validate a Person object:

```csharp
var person = new Person { FirstName = "John", LastName = "Doe", Age = 25 };
var validator = new PersonValidator();
var result = validator.Validate(person);

if (result.IsValid)
{
    Console.WriteLine("Validation successful.");
}
else
{
    foreach (var error in result.Errors)
    {
        Console.WriteLine($"Validation Error: {error.ErrorMessage}");
    }
}
```

FluentValidation simplifies the process of defining and performing validations, helping you ensure data integrity in your applications.

## License

FluentValidation is open-source software and is released under the Apache License 2.0.