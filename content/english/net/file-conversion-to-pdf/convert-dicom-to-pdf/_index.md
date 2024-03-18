---
title: Convert DICOM Medical Images to PDF
linktitle: Convert DICOM Medical Images to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 19
url: /net/file-conversion-to-pdf/convert-dicom-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert DICOM file into PDF format.
    /// For more details about Digital Imaging and Communications in Medicine (.dicom) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-dicom-to-pdf
    /// </summary>
    internal static class ConvertDicomToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "dicom-converted-to.pdf");
            
            // Load the source DICOM file
            using (Converter converter = new Converter(Constants.SAMPLE_DICOM))
            {
                PdfConvertOptions options = new PdfConvertOptions();
                // Save converted PDF file
                converter.Convert(outputFile, options);
            }

            Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
        }
    }
}

```
