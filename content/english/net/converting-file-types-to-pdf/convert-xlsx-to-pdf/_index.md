---
title: Convert XLSX to PDF
linktitle: Convert XLSX to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 25
url: /net/converting-file-types-to-pdf/convert-xlsx-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert XLSX file into PDF format.
    /// For more details about Microsoft Excel Open XML Spreadsheet (.xlsx) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-xlsx-to-pdf
    /// </summary>
    internal static class ConvertXlsxToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "xlsx-converted-to.pdf");
            
            // Load the source XLSX file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_XLSX))
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
