---
title: Convert FODS OpenDocument Spreadsheets to PDF
linktitle: Convert FODS OpenDocument Spreadsheets to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 20
url: /net/convert-files-to-pdf/convert-fods-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert FODS file into PDF format.
    /// For more details about OpenDocument Flat XML Spreadsheet (.fods) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-fods-to-pdf
    /// </summary>
    internal static class ConvertFodsToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "fods-converted-to.pdf");
            
            // Load the source FODS file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_FODS))
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
