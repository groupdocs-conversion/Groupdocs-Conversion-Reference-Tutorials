---
title: Convert CGM Vector Graphics to PDF
linktitle: Convert CGM Vector Graphics to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 14
url: /net/file-conversion-to-pdf/convert-cgm-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert CGM file into PDF format.
    /// For more details about Computer Graphics Metafile (.cgm) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-cgm-to-pdf
    /// </summary>
    internal static class ConvertCgmToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "cgm-converted-to.pdf");
            
            // Load the source CGM file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_CGM))
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
