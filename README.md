# GoF_Csharp_Adapter_Pattern

Converts the interface of one class into another interface that clients expect.

Suppose we have an existing LegacyPrinter class with an incompatible interface that clients are currently using. We want to create an adapter class that converts the interface of LegacyPrinter into a new interface called IPrinter that clients expect.

```csharp
using System;

public class Program
{
    public static void Main(string[] args)
    {
        // Client code using the adapter
        LegacyPrinter legacyPrinter = new LegacyPrinter();
        PrinterAdapter printerAdapter = new PrinterAdapter(legacyPrinter);
        Client client = new Client(printerAdapter);

        client.Print("Hello, Adapter Pattern!");

        // Output will be:
        // Legacy Printer: Hello, Adapter Pattern!
    }
}

// Existing class with an incompatible interface
public class LegacyPrinter
{
    public void Print(string text)
    {
        Console.WriteLine($"Legacy Printer: {text}");
    }
}

// New interface that clients expect
public interface IPrinter
{
    void PrintText(string text);
}

// Adapter class that implements the new interface and adapts the LegacyPrinter
public class PrinterAdapter : IPrinter
{
    private LegacyPrinter legacyPrinter;

    public PrinterAdapter(LegacyPrinter legacyPrinter)
    {
        this.legacyPrinter = legacyPrinter;
    }

    public void PrintText(string text)
    {
        // The adapter calls the appropriate method of the LegacyPrinter
        legacyPrinter.Print(text);
    }
}

// Client code that expects the IPrinter interface
public class Client
{
    private IPrinter printer;

    public Client(IPrinter printer)
    {
        this.printer = printer;
    }

    public void Print(string text)
    {
        printer.PrintText(text);
    }
}
```

## How to setup Github actions

![Csharp Github actions](https://github.com/luiscoco/GoF_Csharp-6.Adapter_Pattern/assets/32194879/d804a168-a8d6-4ff3-9133-ba8cc0e5b39b)









