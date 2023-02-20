# Work-Docs
## C# Interfaces. 
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
