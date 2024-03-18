---
title: Convert PST to PDF
linktitle: Convert PST to PDF
second_title: GroupDocs.Conversion .NET API
description: 
type: docs
weight: 12
url: /net/file-format-conversion-tutorials/convert-pst-to-pdf/
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
    /// This example demonstrates how to convert PST file into PDF format.
    /// For more details about Personal Storage File (.pst) to Portable Document (.pdf) conversion please check this documentation article 
    /// https://docs.groupdocs.com/conversion/net/convert-pst-to-pdf
    /// </summary>
    internal static class ConvertPstToPdf
    {
        public static void Run()
        {
            string outputFolder = "Your Document Directory";
            string outputFile = Path.Combine(outputFolder, "pst-converted-{0}-to.pdf");
            
            // Load the source PST file
            using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PST, fileType => fileType == EmailFileType.Pst
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
