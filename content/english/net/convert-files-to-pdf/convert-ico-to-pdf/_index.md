---
title: Convert ICO Icons to PDF
linktitle: Convert ICO Icons to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 24
url: /net/convert-files-to-pdf/convert-ico-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert ICO file into PDF format.
    /// For more details about Microsoft Icon File (.ico) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-ico-to-pdf
    /// </summary>
    internal static class ConvertIcoToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "ico-converted-to.pdf");
            
            // Load the source ICO file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_ICO))
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
