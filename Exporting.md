# Exporting

The following is an example of exporting a report in Jpeg file.

```		
            // export to image
            ImageExport image = new ImageExport();
            image.ImageFormat = ImageExportFormat.Jpeg;
            report.Export(image, "report.jpg");
```

[Next Page](WebReport.md)