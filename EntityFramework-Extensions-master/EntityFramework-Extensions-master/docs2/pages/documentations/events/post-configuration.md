# PostConfiguration

The `PostConfiguration` event is raised just before a bulk method is called, such as, `BulkInsert`, `BulkUpdate`, `BulkDelete`, `BulkMerge`, `BulkSynchronize` etc. 

The following sets the `Log` property in the `PostConfiguration` event.
 
```csharp
using (var context = new EntityContext())
{
    context.BulkInsert(list, options =>
    {
        options.PostConfiguration = operations =>
        {
            operations.Log = Console.WriteLine;       
        };
    });
}
```

{% include component-try-it.html href='https://dotnetfiddle.net/8q6BdX' %}

In the `PostConfiguration` event, the Log property is set and to log the database commands and queries performed in that `BulkInsert` method.
