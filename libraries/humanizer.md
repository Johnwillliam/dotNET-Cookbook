# Humanizer

Humanizer is a .NET library that provides helpful extensions for string manipulation and conversion. It aims to make your code more user-friendly by adding humanized formats for text, dates, numbers, and more. Humanizer simplifies the process of formatting data to be more human-readable and is commonly used in various .NET applications.

## Key Features

- **String Formatting:** Humanizer offers extensions for transforming strings into more readable formats, such as transforming camel case to space-separated words.

- **Date and Time Formatting:** You can humanize date and time intervals to create user-friendly representations like "a few seconds ago" or "yesterday."

- **Number Formatting:** Humanizer provides convenient methods for formatting numbers, such as converting numbers into words (e.g., 123 to "one hundred twenty-three").

- **Pluralization and Singularization:** You can pluralize or singularize words, which is useful for generating user-friendly text.

- **Casing and Capitalization:** Humanizer helps you change the casing and capitalization of strings to match the desired format.

## Resources

- **[Official Documentation](https://humanizr.net/):** The official documentation provides detailed information on using Humanizer, including examples, best practices, and advanced features.

- **[GitHub Repository](https://github.com/Humanizr/Humanizer):** The GitHub repository is where you can find the latest source code, report issues, and contribute to the project.

- **[NuGet Package](https://www.nuget.org/packages/Humanizer/):** You can add the Humanizer NuGet package to your .NET projects to start humanizing your data.

## Getting Started

To get started with Humanizer, follow these simple steps:

1. Install the Humanizer NuGet package in your project.

2. Use the provided extensions and methods to humanize your data as needed. You can format strings, dates, numbers, and more.

3. Customize the formatting to match your application's user experience and branding.

## Example

Here's a simple example of how to use Humanizer to format strings:

```csharp
using Humanizer;

public class Program
{
    public static void Main()
    {
        // Humanize a string by transforming camel case to space-separated words
        string input = "thisIsCamelCase";
        string humanized = input.Humanize();
        Console.WriteLine($"Humanized: {humanized}");
    }
}
```

In this example, we've used Humanizer to transform a camel case string into space-separated words. Humanizer provides many other formatting options for dates, numbers, and more.

Humanizer is a valuable tool for enhancing the user experience of your .NET applications by making data more human-readable.

## License

Humanizer is open-source software and is released under the MIT License.