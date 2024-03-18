---
title: Convert VSDM to PDF
linktitle: Convert VSDM to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 26
url: /net/file-format-conversion-tutorials/convert-vsdm-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert VSDM file into PDF format.
    /// For more details about Visio Macro-Enabled Drawing (.vsdm) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-vsdm-to-pdf
    /// </summary>
    internal static class ConvertVsdmToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "vsdm-converted-to.pdf");
            
            // Load the source VSDM file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_VSDM))
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
