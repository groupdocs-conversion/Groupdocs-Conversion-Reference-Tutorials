---
title: Convert SXC to PDF
linktitle: Convert SXC to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 17
url: /net/file-format-conversion-tutorials/convert-sxc-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert SXC file into PDF format.
    /// For more details about StarOffice Calc Spreadsheet (.sxc) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-sxc-to-pdf
    /// </summary>
    internal static class ConvertSxcToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "sxc-converted-to.pdf");
            
            // Load the source SXC file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_SXC))
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
