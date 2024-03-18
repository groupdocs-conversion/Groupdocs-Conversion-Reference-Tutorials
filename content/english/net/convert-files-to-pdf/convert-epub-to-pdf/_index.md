---
title: Convert EPUB eBooks to PDF
linktitle: Convert EPUB eBooks to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 18
url: /net/convert-files-to-pdf/convert-epub-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert EPUB file into PDF format.
    /// For more details about Digital E-Book File Format (.epub) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-epub-to-pdf
    /// </summary>
    internal static class ConvertEpubToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "epub-converted-to.pdf");
            
            // Load the source EPUB file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_EPUB))
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
