# 8. Reports in Web

## Inside WebReport

![](images/WebReportAjaxScheme.png)

## Browsers support

FastReport.OpenSource.Web supports latest versions of Chrome, Firefox, Safari, Opera and Edge browsers.

## Using **FastReport.OpenSource.Web** in ASP.NET MVC application

1. Add **FastReport.OpenSource.Web** as nuget dependency in your **ASP.NET Core** project:

```xml
<PackageReference Include="FastReport.Web" Version="*" />
```

2. Register **FastReport.OpenSource.Web** in the *Configure* method of your *Startup* class:

```csharp
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    ...
    app.UseFastReport();
    ...
}
```

3. Create **WebReport** object and render it in your view file:

```csharp
public IActionResult Index()
{
    var webReport = new WebReport();
    webReport.Report.Load("path/to/report.frx");

    return View(webReport);
}
```

```html
@model FastReport.Web.WebReport

<div>
    @await Model.Render()
</div>
```

## FastReport.OpenSource.Web Examples

You can see some examples [here](https://github.com/FastReports/FastReport/tree/master/Demos/Core).

---

[Exporting](Exporting.md) | [Top Page](README.md)
