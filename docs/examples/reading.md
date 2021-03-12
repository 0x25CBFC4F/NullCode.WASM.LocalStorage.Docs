## Warning

Before reading this I suggest looking into 'Writing to local storage' article.

## Reading from local storage

I modified previous component example a bit.

1. I changed anonymous object to a real class.
2. I added reading/logging data into the console.

```csharp
@using NullCode.WASM.LocalStorage

@code {
    
    [Inject]
    private ILocalStorageService LocalStorageService { get; set; }

    protected override async void OnInitialized()
    {
        await LocalStorageService.SetRaw("example_key", "example value");
        await LocalStorageService.Set("example_object", new ExampleObject
        {
            A = 12345
        });

        var key = await LocalStorageService.GetRaw("example_key");
        var obj = await LocalStorageService.Get<ExampleObject>("example_object");
        
        Console.WriteLine($"Key value: [{key}], Object->A value: [{obj.A}]");
    }

}
```

## Checking results

After recompiling and opening `/counter` page again that's what we'll see in the console:

```
Key value: [example value], Object->A value: [12345]
```