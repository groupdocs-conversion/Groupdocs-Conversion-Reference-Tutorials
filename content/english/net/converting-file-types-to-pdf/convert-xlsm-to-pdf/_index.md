---
title: Convert XLSM to PDF
linktitle: Convert XLSM to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 23
url: /net/converting-file-types-to-pdf/convert-xlsm-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert XLSM file into PDF format.
    /// For more details about Microsoft Excel Macro-Enabled Spreadsheet (.xlsm) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-xlsm-to-pdf
    /// </summary>
    internal static class ConvertXlsmToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "xlsm-converted-to.pdf");
            
            // Load the source XLSM file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_XLSM))
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
