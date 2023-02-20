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

