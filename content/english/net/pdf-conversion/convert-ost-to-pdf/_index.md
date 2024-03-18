---
title: Convert OST to PDF
linktitle: Convert OST to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 12
url: /net/pdf-conversion/convert-ost-to-pdf/
---

## Complete Source Code
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.FileTypes;
using GroupDocs.Conversion.Options.Convert;
using GroupDocs.Conversion.Options.Load;

namespace GroupDocs.Conversion.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to convert OST file into PDF format.
    /// For more details about Outlook Offline Storage File (.ost) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-ost-to-pdf
    /// </summary>
    internal static class ConvertOstToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "ost-converted-{0}-to.pdf");
            
            // Load the source OST file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_OST, fileType => fileType == EmailFileType.Ost
                                                                                                                ? new PersonalStorageLoadOptions()
                                                                                                                : null))
	        {
                var options = new PdfConvertOptions();
		        var counter = 1;
                // Save converted PDF file
                converter.Convert(
		            (FileType fileType) => new FileStream(string.Format(outputFile, counter++), FileMode.Create),
                    options
                );            
	        }

            Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
        }
    }
}

```
