---
title: Convert PS to PDF
linktitle: Convert PS to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 11
url: /net/file-format-conversion-tutorials/convert-ps-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert PS file into PDF format.
    /// For more details about PostScript (PS) (.ps) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-ps-to-pdf
    /// </summary>
    internal static class ConvertPsToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "ps-converted-to.pdf");
            
            // Load the source PS file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PS))
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
