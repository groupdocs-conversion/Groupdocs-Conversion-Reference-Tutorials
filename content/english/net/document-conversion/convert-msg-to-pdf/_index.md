---
title: Convert MSG to PDF
linktitle: Convert MSG to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 26
url: /net/document-conversion/convert-msg-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert MSG file into PDF format.
    /// For more details about Microsoft Outlook Email Format (.msg) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-msg-to-pdf
    /// </summary>
    internal static class ConvertMsgToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "msg-converted-to.pdf");
            
            // Load the source MSG file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_MSG))
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
