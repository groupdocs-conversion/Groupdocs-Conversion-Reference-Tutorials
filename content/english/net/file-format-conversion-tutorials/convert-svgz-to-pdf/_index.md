---
title: Convert SVGZ to PDF
linktitle: Convert SVGZ to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 16
url: /net/file-format-conversion-tutorials/convert-svgz-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert SVGZ file into PDF format.
    /// For more details about Compressed Scalable Vector Graphics File (.svgz) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-svgz-to-pdf
    /// </summary>
    internal static class ConvertSvgzToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "svgz-converted-to.pdf");
            
            // Load the source SVGZ file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_SVGZ))
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
