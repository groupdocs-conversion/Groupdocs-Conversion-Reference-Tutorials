---
"description": ".NET के लिए GroupDocs.Conversion का उपयोग करके PowerPoint प्रस्तुतियों (PPTX) को PDF प्रारूप में परिवर्तित करना सीखें। आसान और कुशल रूपांतरण प्रक्रिया।"
"linktitle": "PPTX को PDF में बदलें"
"second_title": "GroupDocs.Conversion .NET एपीआई"
"title": "PPTX को PDF में बदलें"
"url": "/hi/net/pdf-conversion/convert-pptx-to-pdf/"
"weight": 29
type: docs
---
# PPTX को PDF में बदलें

## परिचय
इस ट्यूटोरियल में, हम .NET के लिए GroupDocs.Conversion लाइब्रेरी का उपयोग करके एक PowerPoint प्रस्तुति (PPTX) फ़ाइल को पोर्टेबल डॉक्यूमेंट फ़ॉर्मेट (PDF) में बदलने की प्रक्रिया से गुजरेंगे। इस रूपांतरण को प्राप्त करने के लिए नीचे दिए गए चरणों का पालन करें।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ हैं:
1. .NET लाइब्रेरी के लिए GroupDocs.Conversion: सुनिश्चित करें कि आपने .NET लाइब्रेरी के लिए GroupDocs.Conversion स्थापित किया है। आप इसे यहाँ से डाउनलोड कर सकते हैं [यहाँ](https://releases.groupdocs.com/conversion/net/).
2. विकास परिवेश: विजुअल स्टूडियो या किसी अन्य .NET IDE जैसे आवश्यक उपकरणों के साथ विकास परिवेश स्थापित करें।

## नामस्थान आयात करें
GroupDocs.Conversion कार्यात्मकताओं तक पहुँचने के लिए अपने प्रोजेक्ट में आवश्यक नामस्थान शामिल करें।
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## चरण 1: आउटपुट फ़ोल्डर और फ़ाइल नाम सेट करें
सबसे पहले, आउटपुट फ़ोल्डर को परिभाषित करें जहां परिवर्तित पीडीएफ फाइल को सहेजा जाएगा, और आउटपुट पीडीएफ फाइल का नाम निर्दिष्ट करें।
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "pptx-converted-to.pdf");
```
## चरण 2: स्रोत PPTX फ़ाइल लोड करें
GroupDocs.Conversion लाइब्रेरी का उपयोग करके स्रोत PowerPoint प्रस्तुति (PPTX) फ़ाइल लोड करें।
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PPTX))
{
    // रूपांतरण तर्क यहां रखा जाएगा
}
```
## चरण 3: रूपांतरण विकल्प निर्दिष्ट करें
रूपांतरण विकल्प परिभाषित करें। इस मामले में, हम PDF प्रारूप में रूपांतरण कर रहे हैं, इसलिए इसका एक उदाहरण बनाएँ `PdfConvertOptions`.
```csharp
var options = new PdfConvertOptions();
```
## चरण 4: रूपांतरण करें
रूपांतरण प्रक्रिया को निष्पादित करने के लिए निम्न का उपयोग करें: `Convert` विधि का उपयोग करें और रूपांतरण विकल्पों के साथ आउटपुट फ़ाइल पथ को पास करें।
```csharp
converter.Convert(outputFile, options);
```
## चरण 5: आउटपुट जांचें
रूपांतरण सफलतापूर्वक पूरा हो जाने के बाद, एक संदेश प्रदर्शित करें जो पूरा होने और आउटपुट फ़ाइल के स्थान को इंगित करता है।
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```

## निष्कर्ष
इस ट्यूटोरियल में, हमने .NET के लिए GroupDocs.Conversion लाइब्रेरी का उपयोग करके PowerPoint प्रेजेंटेशन (PPTX) फ़ाइल को पोर्टेबल डॉक्यूमेंट फ़ॉर्मेट (PDF) में बदलना सीखा। ऊपर बताए गए चरणों का पालन करके, आप आसानी से अपने .NET अनुप्रयोगों में यह रूपांतरण कर सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### प्रश्न: क्या GroupDocs.Conversion .NET के सभी संस्करणों के साथ संगत है?
A: हां, GroupDocs.Conversion .NET Framework 2.0 और उच्चतर का समर्थन करता है, जिसमें .NET Core और .NET मानक शामिल है।
### प्रश्न: क्या मैं फ़ाइलों को पीडीएफ के अलावा अन्य प्रारूपों में परिवर्तित कर सकता हूँ?
A: हां, GroupDocs.Conversion रूपांतरण के लिए दस्तावेज़ प्रारूपों की एक विस्तृत श्रृंखला का समर्थन करता है, जिसमें Word, Excel, HTML और बहुत कुछ शामिल है।
### प्रश्न: क्या GroupDocs.Conversion कोई निःशुल्क परीक्षण प्रदान करता है?
A: हां, आप GroupDocs.Conversion के निःशुल्क परीक्षण को यहां से एक्सेस कर सकते हैं [यहाँ](https://releases.groupdocs.com/).
### प्रश्न: मैं GroupDocs.Conversion के लिए समर्थन कैसे प्राप्त कर सकता हूं?
उत्तर: आप ग्रुपडॉक्स समुदाय फोरम से सहायता प्राप्त कर सकते हैं [यहाँ](https://forum.groupdocs.com/c/conversion/11).
### प्रश्न: क्या GroupDocs.Conversion के लिए कोई अस्थायी लाइसेंस उपलब्ध है?
A: हां, आप GroupDocs.Conversion के लिए एक अस्थायी लाइसेंस प्राप्त कर सकते हैं [यहाँ](https://purchase.groupdocs.com/temporary-license/).