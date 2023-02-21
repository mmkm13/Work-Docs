# Work-Docs
## C# Interfaces
### Deklaration
[Interfaceklasse] [Name] = new [Konstruktorausdruck];

Beispiel:
```c#
void ISampleInterface.SampleMethod()
    {
        // Method implementation.
    }

    static void Main()
    {
        // Declare an interface instance.
        ISampleInterface obj = new ImplementationClass();

        // Call the member.
        obj.SampleMethod();
    }
}
```
### Code-Beispiel
Hauptprogramm:
```c#
    public class Program
    {
        public static void Main(string[] args)
        {
           
            IConfiguration configuration = new ConfigurationBuilder()
                                                  .SetBasePath(Directory.GetCurrentDirectory())
                                                  .AddJsonFile("appsettings.json", optional: false)
                                                  .AddCommandLine(args)
                                                  .AddEnvironmentVariables()
                                                  .Build(); // Gibt IConfiguration zurück
                                                              
            .
            .
            .
        }
     }
        
```
Definition von CofnigurationBuilder()
```c#
.
.
.
public class ConfigurationBuilder : IConfigurationBuilder
    {
    .
    .
    .
    public IConfigurationRoot Build()  // Gibt ein IConfigurationRoot zurück
        {
            var providers = new List<IConfigurationProvider>();
            foreach (IConfigurationSource source in Sources)
            {
                IConfigurationProvider provider = source.Build(this);
                providers.Add(provider);
            }
            return new ConfigurationRoot(providers); // <= Rückgabe, ConfigurationRoot muss ein IConfiguration Root sein.
        }
    }
    .
    .
    .
```

Definition von IConfiguration:

```c#
    .
    .
    .
    public interface IConfigurationRoot : IConfiguration
    {
        .
        .
        .
    }
    .
    .
    .
```
## Docker Container to WSL Container
1. docker pull image
2. docker run image as container
3. docker export container image to tarball
4. wsl import tarball




## Blogposts
### Robert C. Martin

[if/else/switch](http://blog.cleancoder.com/uncle-bob/2021/03/06/ifElseSwitch.html)
- Interface Segregation Priciple
- Acrylic Visitor Pattern

[Singletons](https://blog.cleancoder.com/uncle-bob/2015/07/01/TheLittleSingleton.html)

[Response Singletons](http://blog.cleancoder.com/uncle-bob/2015/07/05/PatternPushers.html)

