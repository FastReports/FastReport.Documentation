# 7. Exporting

FastReport Open Source can save documents in HTML, BMP, PNG, JPEG, GIF, TIFF, EMF.

The following is an example of exporting a report in Jpeg file.

```csharp
using FastReport;
using FastReport.Utils;
using FastReport.Export.Image;
            ...
            // Create new Report 
            Report report = new Report();
            // Load report from file
            report.Load("report.frx");
            // Set the parameter
            report.SetParameterValue("MYPARAMETER", 1024);
            // Prepare the report
            report.Prepare();
            // Export in Jpeg
            ImageExport image = new ImageExport();
            image.ImageFormat = ImageExportFormat.Jpeg;
            // Set up the quality
            image.JpegQuality = 90;
            // Decrease a resolution
            image.Resolution = 72;
            // We need all pages in one big single file
            image.SeparateFiles = false;
            report.Export(image, "report.jpg");
```

The following is an example of exporting a report in PNG file.

```csharp
            // Export in PNG
            ImageExport image = new ImageExport();
            image.ImageFormat = ImageExportFormat.Png;
            // Increase a resolution
            image.Resolution = 300;
            // We need separate file for each report page, they will be numbered: report.png, report.2.png, report.3.png, etc.
            image.SeparateFiles = true;
            report.Export(image, "report.png");
```

The following is an example of exporting a report in HTML file.

```csharp
using FastReport;
using FastReport.Utils;
using FastReport.Export.Html;
            ...
            // Export in HTML
            HTMLExport html = new HTMLExport();
            // We need embedded pictures inside html
            html.EmbedPictures = true;
            // Enable all report pages in one html file
            html.SinglePage = true;
            // We don't need a subfolder for pictures and additional files
            html.SubFolder = false;
            // Enable layered HTML
            html.Layers = true;
            // Turn off the toolbar with navigation
            html.Navigator = false;
            // Save the report in html
            report.Export(html, "report.html");
```

*To be continued ...*

---

[Creating Report Using Code](CreatingReportUsingCode.md) | [Top Page](README.md) | [Reports in Web](WebReport.md)