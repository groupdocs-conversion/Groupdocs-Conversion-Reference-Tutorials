---
title: Convert VST to PDF
linktitle: Convert VST to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 14
url: /net/converting-file-types-to-pdf/convert-vst-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert VST file into PDF format.
    /// For more details about Visio Drawing Template (.vst) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-vst-to-pdf
    /// </summary>
    internal static class ConvertVstToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "vst-converted-to.pdf");
            
            // Load the source VST file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_VST))
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
