---
title: Convert XLSB to PDF
linktitle: Convert XLSB to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 22
url: /net/converting-file-types-to-pdf/convert-xlsb-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert XLSB file into PDF format.
    /// For more details about Microsoft Excel Binary Spreadsheet File (.xlsb) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-xlsb-to-pdf
    /// </summary>
    internal static class ConvertXlsbToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "xlsb-converted-to.pdf");
            
            // Load the source XLSB file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_XLSB))
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
