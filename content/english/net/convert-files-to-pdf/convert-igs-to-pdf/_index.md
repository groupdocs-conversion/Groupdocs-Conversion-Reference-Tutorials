---
title: Convert IGS 3D Model Files to PDF
linktitle: Convert IGS 3D Model Files to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 26
url: /net/convert-files-to-pdf/convert-igs-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert IGS file into PDF format.
    /// For more details about Initial Graphics Exchange Specification (IGES) (.igs) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-igs-to-pdf
    /// </summary>
    internal static class ConvertIgsToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "igs-converted-to.pdf");
            
            // Load the source IGS file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_IGS))
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
