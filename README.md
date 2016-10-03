# IntelHexFormatReader #

A .NET library to parse [an Intel HEX file](https://en.wikipedia.org/wiki/Intel_HEX) into a representative "memory representation".

## How to use the .NET library##

Link the following nuget package in your project in order to use the Intel Hex format file reader: https://www.nuget.org/packages/IntelHexFormatReader/

Alternatively, install the package using the nuget package manager console:

```
Install-Package IntelHexFormatReader
```

The following minimal snippet demonstrates loading a hex file and printing out it's resulting memory representation:

```csharp
using System.Diagnostics;
using IntelHexFormatReader;

namespace IntelHexFormatReaderDemo
{
    internal class Program
    {
        private static void Main(string[] args)
        {
            var reader = new HexFileReader(@"C:\\MyHexFiles\\myHexFile.hex", 32768);
            var memoryRepresentation = reader.Parse();
            foreach (var cell in memoryRepresentation.Cells)
                Debug.WriteLine(cell);
        }
    }
}
```
HexFileReader has 2 constructors (with one accepting a filename as first argument, and another accepting an IEnumerable<string> as first argument). The second argument is the memory size the HEX file it to be applied to.
