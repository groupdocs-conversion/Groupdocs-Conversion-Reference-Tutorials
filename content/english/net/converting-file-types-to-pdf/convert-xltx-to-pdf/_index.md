---
title: Convert XLTX to PDF
linktitle: Convert XLTX to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 28
url: /net/converting-file-types-to-pdf/convert-xltx-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert XLTX file into PDF format.
    /// For more details about Microsoft Excel Open XML Template (.xltx) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-xltx-to-pdf
    /// </summary>
    internal static class ConvertXltxToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "xltx-converted-to.pdf");
            
            // Load the source XLTX file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_XLTX))
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
