---
title: Convert POTX to PDF
linktitle: Convert POTX to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 23
url: /net/pdf-conversion/convert-potx-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert POTX file into PDF format.
    /// For more details about Microsoft PowerPoint Open XML Template (.potx) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-potx-to-pdf
    /// </summary>
    internal static class ConvertPotxToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "potx-converted-to.pdf");
            
            // Load the source POTX file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_POTX))
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
