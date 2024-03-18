---
title: Convert VSSM to PDF
linktitle: Convert VSSM to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 10
url: /net/converting-file-types-to-pdf/convert-vssm-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert VSSM file into PDF format.
    /// For more details about Microsoft Visio Macro Enabled File Format (.vssm) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-vssm-to-pdf
    /// </summary>
    internal static class ConvertVssmToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "vssm-converted-to.pdf");
            
            // Load the source VSSM file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_VSSM))
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