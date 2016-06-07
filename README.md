Aldsoft.ACORD
=============

Aldsoft.ACORD is a **free, open-source** library that helps serialize and deserialize the ACORD LA XML standard. The library follows the ACORD XML Schema, so if you have trouble deserializing your ACORD XML string, then it probably wouldn't pass ACORD xsd validation.

The library also provides a helpful Fluent API for constructing the ACORD XML Object programatically.

## Getting Started

There will be documentation shortly provided on Read The Docs. But for now, below will need to suffice.

### 30 Second Tutorial:

`install-package <nuget package coming soon>`

#### Construct and object and then Serialize:

```csharp
...
// Construct
var builder = TXLife_Type
    .CreateBuilder()
    .Version("2.35.00")
    .AddTXLifeRequest(new TXLifeRequest_Type { id = "3" })
    .AddUserAuthRequest(new UserAuthRequest_Type());
var txLife = builder.Build();

// Serialize to string
string xmlString;
txLife.Serialize(out xmlString);

// SaveToFile
txLife.SaveToFile("c:\\path\\to\\file.xml");
...
```

#### or, Deserialize a string, or file

```csharp
...
// ACORD XML String received
var xmlString = "<?xml version=\"1.0\" encoding=\"utf-8\"?>\r\n<TXLife xmlns:xsi=\"http://www.w3.org/2001/XMLSchema-instance\" xmlns:xsd=\"http://www.w3.org/2001/XMLSchema\" Version=\"2.35.00\" xmlns=\"http://ACORD.org/Standards/Life/2\">\r\n  <UserAuthRequest />\r\n  <TXLifeRequest id=\"3\" />\r\n</TXLife>"

// Deserialize
var txLifeObjectFromString = TXLife_Type.Deserialize(xmlString);

Console.WriteLine(txLifeObject.Version);
// output: 2.35.00

// Load From File
var txLifeObjectFromFile = TXLife_Type.LoadFromFile("c:\\path\\to\\file.xml");
...
```

## Building from Source

 1. Clone the source down to your machine. 
 1. Build in visual studio

## Contributing

 1. Make sure you have Visual Studio extension EditorConfig installed
 1. Improve/Fix!
 1. Make a pull request.

## Builds

Will be getting Appveyor going soon.
 
# Requirements
* .Net 4.0 or greater