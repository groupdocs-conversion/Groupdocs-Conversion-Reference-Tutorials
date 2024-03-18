---
title: Convert VSDX to PDF
linktitle: Convert VSDX to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 28
url: /net/file-format-conversion-tutorials/convert-vsdx-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert VSDX file into PDF format.
    /// For more details about Microsoft Visio File Format (.vsdx) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-vsdx-to-pdf
    /// </summary>
    internal static class ConvertVsdxToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "vsdx-converted-to.pdf");
            
            // Load the source VSDX file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_VSDX))
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
