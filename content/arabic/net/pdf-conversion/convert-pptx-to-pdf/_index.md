---
"description": "تعرّف على كيفية تحويل عروض PowerPoint التقديمية (PPTX) إلى صيغة PDF باستخدام GroupDocs.Conversion لـ .NET. عملية تحويل سهلة وفعّالة."
"linktitle": "تحويل PPTX إلى PDF"
"second_title": "GroupDocs.Conversion .NET API"
"title": "تحويل PPTX إلى PDF"
"url": "/ar/net/pdf-conversion/convert-pptx-to-pdf/"
"weight": 29
type: docs
---
# تحويل PPTX إلى PDF

## مقدمة
في هذا البرنامج التعليمي، سنشرح عملية تحويل ملف عرض تقديمي من PowerPoint (PPTX) إلى تنسيق مستند محمول (PDF) باستخدام مكتبة GroupDocs.Conversion لـ .NET. اتبع الخطوات التالية لتحقيق هذا التحويل.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من أن لديك المتطلبات الأساسية التالية:
1. مكتبة GroupDocs.Conversion لـ .NET: تأكد من تثبيت مكتبة GroupDocs.Conversion لـ .NET. يمكنك تنزيلها من [هنا](https://releases.groupdocs.com/conversion/net/).
2. بيئة التطوير: قم بإعداد بيئة تطوير بالأدوات اللازمة مثل Visual Studio أو أي .NET IDE آخر.

## استيراد مساحات الأسماء
قم بتضمين مساحات الأسماء الضرورية في مشروعك للوصول إلى وظائف GroupDocs.Conversion.
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## الخطوة 1: تعيين اسم المجلد والملف الناتج
أولاً، قم بتحديد مجلد الإخراج الذي سيتم حفظ ملف PDF المحول فيه، وحدد اسم ملف PDF الإخراج.
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "pptx-converted-to.pdf");
```
## الخطوة 2: تحميل ملف PPTX المصدر
قم بتحميل ملف العرض التقديمي المصدر PowerPoint (PPTX) باستخدام مكتبة GroupDocs.Conversion.
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PPTX))
{
    // سيتم وضع منطق التحويل هنا
}
```
## الخطوة 3: تحديد خيارات التحويل
حدّد خيارات التحويل. في هذه الحالة، نُحوّل إلى صيغة PDF، لذا أنشئ نسخة من `PdfConvertOptions`.
```csharp
var options = new PdfConvertOptions();
```
## الخطوة 4: تنفيذ التحويل
تنفيذ عملية التحويل باستخدام `Convert` الطريقة وتمرير مسار ملف الإخراج مع خيارات التحويل.
```csharp
converter.Convert(outputFile, options);
```
## الخطوة 5: التحقق من الناتج
بعد اكتمال التحويل بنجاح، قم بعرض رسالة تشير إلى اكتمال عملية التحويل وموقع ملف الإخراج.
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```

## خاتمة
في هذا البرنامج التعليمي، تعلمنا كيفية تحويل ملف عرض تقديمي من PowerPoint (PPTX) إلى تنسيق مستند محمول (PDF) باستخدام مكتبة GroupDocs.Conversion لـ .NET. باتباع الخطوات الموضحة أعلاه، يمكنك إجراء هذا التحويل بسهولة في تطبيقات .NET.
## الأسئلة الشائعة
### س: هل GroupDocs.Conversion متوافق مع كافة إصدارات .NET؟
ج: نعم، يدعم GroupDocs.Conversion .NET Framework 2.0 والإصدارات الأحدث، بما في ذلك .NET Core و.NET Standard.
### س: هل يمكنني تحويل الملفات إلى تنسيقات أخرى غير PDF؟
ج: نعم، يدعم GroupDocs.Conversion مجموعة واسعة من تنسيقات المستندات للتحويل، بما في ذلك Word وExcel وHTML والمزيد.
### س: هل يقدم GroupDocs.Conversion أي نسخة تجريبية مجانية؟
ج: نعم، يمكنك الوصول إلى نسخة تجريبية مجانية من GroupDocs.Conversion من [هنا](https://releases.groupdocs.com/).
### س: كيف يمكنني الحصول على الدعم لـ GroupDocs.Conversion؟
ج: يمكنك الحصول على الدعم من منتدى مجتمع GroupDocs [هنا](https://forum.groupdocs.com/c/conversion/11).
### س: هل هناك ترخيص مؤقت متاح لـ GroupDocs.Conversion؟
ج: نعم، يمكنك الحصول على ترخيص مؤقت لـ GroupDocs.Conversion من [هنا](https://purchase.groupdocs.com/temporary-license/).