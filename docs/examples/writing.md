## Using LS Service in Blazor Component

To use this library in your component you need to first inject it.

```csharp
[Inject]
private ILocalStorageService LocalStorageService { get; set; }
```

I'll use `OnInitialized()` event so our code will be executed on page load.

Here's how you can put raw text or object into the local storage:

```csharp
@using NullCode.WASM.LocalStorage

@code {
    
    [Inject]
    private ILocalStorageService LocalStorageService { get; set; }

    protected override void OnInitialized()
    {
        LocalStorageService.SetRaw("example_key", "example value");
        LocalStorageService.Set("example_object", new
        {
            key = "value",
            key2 = 0xDEADBEEF,
            key3 = true
        });
    }

}
```

## Adding component

I'll add newly created component into a `Counter.razor` page.

```csharp
@page "/counter"

<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button class="btn btn-primary" @onclick="IncrementCount">Click me</button>

<ExampleComponent />

@code {
    private int currentCount = 0;

    private void IncrementCount()
    {
        currentCount++;
    }

}
```

## Checking the results

After we've built, ran, and opened `/counter` page we can finally check our local storage:

![](component_example_scr.png)