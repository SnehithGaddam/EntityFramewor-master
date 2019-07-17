# Transaction

## BulkSaveChanges
As SaveChanges, BulkSaveChanges already save all entities within an internal transaction. So, there is nothing to do.

However, if you start a transaction within Entity Framework, BulkSaveChanges will honor it and will use this transaction instead of creating an internal transaction.


```csharp
var transaction = context.Database.BeginTransaction();
try
{
	context.BulkSaveChanges();
	transaction.Commit();
}
catch
{
	transaction.Rollback();
}
```
{% include component-try-it.html href='https://dotnetfiddle.net/Igr6zU' %}

## Bulk Operations
Bulk Operations such as BulkInsert, BulkUpdate, BulkDelete doesn't use a transaction by default. This is your responsibility to handle.

If you start a transaction within Entity Framework, Bulk Operations will honor it.


```csharp
var transaction = context.Database.BeginTransaction();
try
{
	context.BulkInsert(list1);
	context.BulkInsert(list2);
	transaction.Commit();
}
catch
{
	transaction.Rollback();
}
```
{% include component-try-it.html href='https://dotnetfiddle.net/zr1QSB' %}
