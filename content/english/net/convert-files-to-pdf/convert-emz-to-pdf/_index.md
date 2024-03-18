---
title: Convert EMZ Enhanced Metafiles to PDF
linktitle: Convert EMZ Enhanced Metafiles to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 16
url: /net/convert-files-to-pdf/convert-emz-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert EMZ file into PDF format.
    /// For more details about Enhanced Windows Metafile Compressed (.emz) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-emz-to-pdf
    /// </summary>
    internal static class ConvertEmzToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "emz-converted-to.pdf");
            
            // Load the source EMZ file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_EMZ))
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
