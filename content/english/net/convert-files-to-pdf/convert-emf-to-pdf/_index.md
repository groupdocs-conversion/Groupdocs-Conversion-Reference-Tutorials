---
title: Convert EMF Windows Metafiles to PDF
linktitle: Convert EMF Windows Metafiles to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 13
url: /net/convert-files-to-pdf/convert-emf-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert EMF file into PDF format.
    /// For more details about Enhanced Metafile Format (.emf) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-emf-to-pdf
    /// </summary>
    internal static class ConvertEmfToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "emf-converted-to.pdf");
            
            // Load the source EMF file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_EMF))
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
