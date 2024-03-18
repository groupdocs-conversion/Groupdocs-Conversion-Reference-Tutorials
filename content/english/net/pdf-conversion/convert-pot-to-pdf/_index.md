---
title: Convert POT to PDF
linktitle: Convert POT to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 22
url: /net/pdf-conversion/convert-pot-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert POT file into PDF format.
    /// For more details about PowerPoint Template (.pot) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-pot-to-pdf
    /// </summary>
    internal static class ConvertPotToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "pot-converted-to.pdf");
            
            // Load the source POT file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_POT))
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
