# 7. Exporting

The following is an example of exporting a report in Jpeg file.

```csharp
            // export to image
            ImageExport image = new ImageExport();
            image.ImageFormat = ImageExportFormat.Jpeg;
            report.Export(image, "report.jpg");
```

---

[Creating Report Using Code](CreatingReportUsingCode.md) | [Top Page](README.md) | [Reports in Web](WebReport.md)