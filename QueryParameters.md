# 3.3. Query parameters

There can be parameters in a query text. Let us see the following query:
 
```sql
select * from DVDs
where Title = @param1
```

This is the query to MS SQL demonstration database. The parameter with "param1" name is defined in a query. Here it should be noted: method of describing parameters in a query differs for different DBMS. For MS SQL a parameter is marked by a "@" symbol, MS Access parameters do not have names and are marked by the "?" symbol.

If your SQL query contains parameters, you have to declare them. It can be done in the third step of the "Query Wizard" which we have looked at above. To create a parameter, press the "Add parameter" button.

The following parameter's properties should be set in the properties window:
 
| Property | Description | 
|:-|:-|
| Name | Parameter name. Here you need to indicate the same name which you use in the query text. Some DBMS (for example, MS Access) do not support named parameters. In this case do not change this property. |
| DataType | Parameter data type. |
| DefaultValue | Value which will be used if the "Expression" property is not specified, or if it is impossible to calculate it (for example, when operating with the query in the report design mode). |
| Expression | Expression which returns parameter's value. This expression will be processed when you run the report. You can indicate any expression in this property (see details in the "Expressions" chapter). |
| Size | Parameter data size. This property should be indicated if the parameter is of "string" data type. |

## Passing a value to the parameter

Parameters are often used to ask a value from the user. Let us look at two ways to pass a value to the query parameter.

In the first way, you pass a value programmatically. Since there is no easy way to pass a value directly to the query parameter, you need to use the report parameter, which can be easily set via code. You should do the following:

- Create the report parameter. Set the same DataType for the report parameter, as it is used in the query parameter.

- In the "Expression" property of the query parameter, refer to a report parameter, for example:

```
[MyReportParameter]
```

- Pass a value to the report parameter:

```csharp
report1.SetParameterValue("MyReportParameter", 10);
```

---

[Report Parameters](ReportParameters.md) | [Top Page](README.md) | [System Variables](SystemVariables.md)