# Log

The `BulkOperation.Log` property can be set to a delegate for any method that takes a string to `log` all database events as soon as they happen. 

 - Most commonly, it is used with any `TextWriter` by setting it to the `Write` method of that `TextWriter`. 
 - All SQL generated by the current context will be logged to that writer.
 - Getting database `log` can often be useful for debugging and see what has been executed under the hood by the library.
  
For example, the following code will log database events to the console.

```csharp
context.BulkSaveChanges(options =>
{
    options.Log += s => Console.WriteLine(s);
});
```
{% include component-try-it.html href='https://dotnetfiddle.net/wXUAxN' %}

Notice that `BulkOperation.Log` is set to `Console.WriteLine`. This is all that is needed to log database events to the console. 

Another example which will log all the information to a `StringBuilder`.

```csharp
StringBuilder logger = new StringBuilder();

context.BulkSaveChanges(options =>StringBuilder
{
    options.Log += s => logger.AppendLine(s);
});
```
{% include component-try-it.html href='https://dotnetfiddle.net/NY0Hu2' %}