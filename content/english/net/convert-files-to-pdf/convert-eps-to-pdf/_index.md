---
title: Convert EPS Encapsulated PostScript Files to PDF
linktitle: Convert EPS Encapsulated PostScript Files to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 17
url: /net/convert-files-to-pdf/convert-eps-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert EPS file into PDF format.
    /// For more details about Encapsulated PostScript File (.eps) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-eps-to-pdf
    /// </summary>
    internal static class ConvertEpsToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "eps-converted-to.pdf");
            
            // Load the source EPS file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_EPS))
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
