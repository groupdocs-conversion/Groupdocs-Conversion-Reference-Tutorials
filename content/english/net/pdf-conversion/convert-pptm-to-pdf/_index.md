---
title: Convert PPTM to PDF
linktitle: Convert PPTM to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 27
url: /net/pdf-conversion/convert-pptm-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert PPTM file into PDF format.
    /// For more details about Microsoft PowerPoint Presentation (.pptm) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-pptm-to-pdf
    /// </summary>
    internal static class ConvertPptmToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "pptm-converted-to.pdf");
            
            // Load the source PPTM file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PPTM))
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
