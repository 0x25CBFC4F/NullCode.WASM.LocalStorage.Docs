## Clearing local storage

You can remove specific key from local storage:

```csharp
await LocalStorageService.Remove("example_key");
```

..or remove key by object type:

```csharp
await LocalStorageService.Remove<T>();
```

..or simply remove all of the keys:

```csharp
await LocalStorageService.RemoveAll();
```