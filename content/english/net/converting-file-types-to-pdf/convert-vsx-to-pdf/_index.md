---
title: Convert VSX to PDF
linktitle: Convert VSX to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 16
url: /net/converting-file-types-to-pdf/convert-vsx-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert VSX file into PDF format.
    /// For more details about Vector Scalar Extension (.vsx) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-vsx-to-pdf
    /// </summary>
    internal static class ConvertVsxToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "vsx-converted-to.pdf");
            
            // Load the source VSX file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_VSX))
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
