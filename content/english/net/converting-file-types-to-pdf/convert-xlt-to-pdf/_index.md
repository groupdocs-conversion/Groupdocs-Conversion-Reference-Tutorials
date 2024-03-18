---
title: Convert XLT to PDF
linktitle: Convert XLT to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 27
url: /net/converting-file-types-to-pdf/convert-xlt-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert XLT file into PDF format.
    /// For more details about Microsoft Excel Template (.xlt) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-xlt-to-pdf
    /// </summary>
    internal static class ConvertXltToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "xlt-converted-to.pdf");
            
            // Load the source XLT file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_XLT))
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
