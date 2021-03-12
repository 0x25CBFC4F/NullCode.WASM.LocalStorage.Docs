## Installation

To install this library you can either download and compile it, or better, use NuGet package.

[![NuGet Shield](https://img.shields.io/nuget/v/NullCode.WASM.LocalStorage?color=green)](https://www.nuget.org/packages/NullCode.WASM.LocalStorage/)

You can install it via Packet Manager:

```
Install-Package NullCode.WASM.LocalStorage
```

..or via .NET CLI command:

```
dotnet add package NullCode.WASM.LocalStorage
```

## Adding to your project

Add this to your `Program.cs` in Blazor WASM project:

```csharp
builder.Services.AddLocalStorageService();
```