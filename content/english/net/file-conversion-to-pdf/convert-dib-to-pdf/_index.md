---
title: Convert DIB Images to PDF
linktitle: Convert DIB Images to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 18
url: /net/file-conversion-to-pdf/convert-dib-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert DIB file into PDF format.
    /// For more details about Device Independent Bitmap File (.dib) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-dib-to-pdf
    /// </summary>
    internal static class ConvertDibToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "dib-converted-to.pdf");
            
            // Load the source DIB file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_DIB))
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
