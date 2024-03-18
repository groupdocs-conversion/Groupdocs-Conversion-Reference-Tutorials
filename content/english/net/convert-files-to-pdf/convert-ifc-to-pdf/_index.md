---
title: Convert IFC Building Information Modeling Files to PDF
linktitle: Convert IFC Building Information Modeling Files to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 25
url: /net/convert-files-to-pdf/convert-ifc-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert IFC file into PDF format.
    /// For more details about Industry Foundation Classes (IFC) File Format (.ifc) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-ifc-to-pdf
    /// </summary>
    internal static class ConvertIfcToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "ifc-converted-to.pdf");
            
            // Load the source IFC file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_IFC))
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
