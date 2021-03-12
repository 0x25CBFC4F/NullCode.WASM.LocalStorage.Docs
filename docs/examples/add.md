## Adding this package in empty Blazor WASM project

Default `Program.cs` looks something like this:

```csharp
namespace Example
{
    public class Program
    {
        public static async Task Main(string[] args)
        {
            var builder = WebAssemblyHostBuilder.CreateDefault(args);
            builder.RootComponents.Add<App>("#app");

            builder.Services.AddScoped(
                sp => new HttpClient {BaseAddress = new Uri(builder.HostEnvironment.BaseAddress)});

            await builder.Build().RunAsync();
        }
    }
}
```

You need to register the service via `IServiceCollection`.

You can access it from `WebAssemblyHostBuilder.Services` property.

```csharp
builder.Services.AddLocalStorageService();
```

So in the end it looks like this:

```csharp
namespace Example
{
    public class Program
    {
        public static async Task Main(string[] args)
        {
            var builder = WebAssemblyHostBuilder.CreateDefault(args);
            builder.RootComponents.Add<App>("#app");

            builder.Services.AddScoped(
                sp => new HttpClient {BaseAddress = new Uri(builder.HostEnvironment.BaseAddress)});
            
            builder.Services.AddLocalStorageService();

            await builder.Build().RunAsync();
        }
    }
}
```

Now you can use it!