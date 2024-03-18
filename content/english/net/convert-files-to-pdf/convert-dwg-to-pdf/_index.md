---
title: Convert DWG CAD Files to PDF
linktitle: Convert DWG CAD Files to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 10
url: /net/convert-files-to-pdf/convert-dwg-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert DWG file into PDF format.
    /// For more details about AutoCAD Drawing Database File (.dwg) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-dwg-to-pdf
    /// </summary>
    internal static class ConvertDwgToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "dwg-converted-to.pdf");
            
            // Load the source DWG file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_DWG))
            {
                var options = new PdfConvertOptions();
                // Save converted PDF file
                converter.Convert(outputFile, options);
            }

            Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
        }
    }
}

```
