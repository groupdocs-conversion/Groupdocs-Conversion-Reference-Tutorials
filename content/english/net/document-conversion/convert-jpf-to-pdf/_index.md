---
title: Convert JPF to PDF
linktitle: Convert JPF to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 13
url: /net/document-conversion/convert-jpf-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert JPF file into PDF format.
    /// For more details about JPEG 2000 Image File (.jpf) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-jpf-to-pdf
    /// </summary>
    internal static class ConvertJpfToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "jpf-converted-to.pdf");
            
            // Load the source JPF file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_JPF))
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
