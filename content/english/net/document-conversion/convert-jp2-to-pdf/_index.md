---
title: Convert JP2 to PDF
linktitle: Convert JP2 to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 10
url: /net/document-conversion/convert-jp2-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert JP2 file into PDF format.
    /// For more details about JPEG 2000 Core Image File (.jp2) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-jp2-to-pdf
    /// </summary>
    internal static class ConvertJp2ToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "jp2-converted-to.pdf");
            
            // Load the source JP2 file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_JP2))
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
