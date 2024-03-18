---
title: Convert DOCM Word Documents (Macros) to PDF
linktitle: Convert DOCM Word Documents (Macros) to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 22
url: /net/file-conversion-to-pdf/convert-docm-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert DOCM file into PDF format.
    /// For more details about Microsoft Word Macro-Enabled Document (.docm) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-docm-to-pdf
    /// </summary>
    internal static class ConvertDocmToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "docm-converted-to.pdf");
            
            // Load the source DOCM file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_DOCM))
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
