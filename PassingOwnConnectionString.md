# 7.4. Passing Own Connection String

If you use data sources that are defined inside a report, you may need to pass an application-defined connection string to a report. 
This can be done in three ways.

**The first method:** you pass a connection string directly to the Connection object in a report. Do the following:
 
```csharp
report1.Load(...); 
// do it after loading the report, before running it
// assume we have one connection in the report
report1.Dictionary.Connections[0].ConnectionString = my_connection_string;
report1.Show();
```

**The second method:** you pass a connection string using the report parameter. Do the following:

- run the report designer; 
- in the "Data" window, create a new report parameter (with "MyParameter" name, for example); 
- in the "Data" window, select the "Connection" object that contains a data source; 
- switch to the "Properties" window and set the ConnectionStringExpression property to the following: 
```
[MyParameter]
```
- pass the connection string to the MyParameter parameter: 
```csharp
report1.SetParameterValue("MyParameter", my_connection_string);
```

---

[Configuring the Environment](ConfiguringEnvironment.md) | [Top Page](README.md) | [Passing Custom SQL](PassingCustomSQL.md)