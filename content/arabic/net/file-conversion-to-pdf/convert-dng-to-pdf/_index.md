---
title: تحويل صور DNG إلى PDF
linktitle: تحويل صور DNG إلى PDF
second_title: GroupDocs.Conversion .NET API
description: تعرف على كيفية تحويل صور DNG إلى PDF بسهولة باستخدام GroupDocs.Conversion for .NET. اتبع دليلنا خطوة بخطوة للتحويل السلس.
weight: 21
url: /ar/net/file-conversion-to-pdf/convert-dng-to-pdf/
---
## مقدمة
في هذا البرنامج التعليمي، سنرشدك خلال عملية تحويل صور DNG إلى PDF باستخدام GroupDocs.Conversion for .NET. DNG (Digital Negative) هو تنسيق ملف يستخدم للتصوير الرقمي. من خلال تحويل صور DNG إلى PDF، يمكنك بسهولة مشاركتها أو تخزينها بتنسيق أكثر قبولًا عالميًا.
## المتطلبات الأساسية
قبل أن تبدأ، تأكد من أن لديك ما يلي:
1.  GroupDocs.Conversion لـ .NET: قم بتنزيل وتثبيت مكتبة GroupDocs.Conversion لـ .NET من[هنا](https://releases.groupdocs.com/conversion/net/).
2. ملف DNG المصدر: أنت بحاجة إلى ملف صورة DNG الذي تريد تحويله إلى PDF.
3. بيئة التطوير: تأكد من إعداد بيئة تطوير .NET.

## استيراد مساحات الأسماء
أولاً، تحتاج إلى استيراد مساحات الأسماء الضرورية لمشروعك. أضف ما يلي باستخدام التوجيهات إلى ملف التعليمات البرمجية الخاص بك:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## الخطوة 1: قم بتحميل ملف DNG المصدر
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "dng-converted-to.pdf");
// قم بتحميل ملف DNG المصدر
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_DNG))
{
    // تابع عملية التحويل
}
```
 في هذه الخطوة، يمكنك تحديد مجلد الإخراج حيث سيتم حفظ ملف PDF المحول. تأكد من الاستبدال`"Your Document Directory"` مع المسار إلى الدليل المطلوب. ثم تقوم بتحديد اسم ومسار ملف PDF الناتج.
## الخطوة 2: تحويل DNG إلى PDF
```csharp
var options = new PdfConvertOptions();
// حفظ ملف PDF المحول
converter.Convert(outputFile, options);
```
 هنا، يمكنك إنشاء مثيل لـ`PdfConvertOptions` لتعيين أي خيارات محددة لتحويل PDF، إذا لزم الأمر. ثم تقوم بالاتصال على`Convert` طريقة`converter`كائن، وتمرير مسار ملف الإخراج وخيارات التحويل.
## الخطوة 3: التعامل مع اكتمال التحويل
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
بعد اكتمال عملية التحويل، تقوم بعرض رسالة نجاح مع الدليل الذي يوجد به ملف PDF المحول.

## خاتمة
في الختام، يمكن تحويل صور DNG إلى PDF بسهولة باستخدام GroupDocs.Conversion for .NET. باتباع الخطوات البسيطة الموضحة في هذا البرنامج التعليمي، يمكنك تحويل ملفات DNG بكفاءة إلى تنسيق PDF، مما يجعلها أكثر سهولة في الوصول إليها ومشاركتها.
## الأسئلة الشائعة
### هل يتوافق GroupDocs.Conversion for .NET مع كافة إصدارات .NET؟
نعم، GroupDocs.Conversion for .NET متوافق مع .NET Framework 4.6.1 والإصدارات الأحدث، بالإضافة إلى .NET Core 2.0 والإصدارات الأحدث.
### هل يمكنني تحويل ملفات DNG متعددة إلى PDF في وقت واحد؟
نعم، يمكنك تحويل ملفات DNG متعددة إلى PDF عن طريق تكرار كل ملف وإجراء عملية التحويل لكل ملف.
### هل هناك أي قيود على حجم ملفات DNG التي يمكن تحويلها؟
ليس لدى GroupDocs.Conversion for .NET أي قيود محددة على حجم ملفات DNG التي يمكن تحويلها. ومع ذلك، قد يختلف الأداء بناءً على حجم وتعقيد ملفات الإدخال.
### هل يمكنني تخصيص خيارات التحويل لمخرجات PDF؟
 نعم، يمكنك تخصيص خيارات متنوعة مثل حجم الصفحة والاتجاه والضغط والمزيد باستخدام`PdfConvertOptions`فئة مقدمة من GroupDocs.Conversion لـ .NET.
### هل يتوفر الدعم الفني لـ GroupDocs.Conversion لـ .NET؟
 نعم، يتوفر الدعم الفني من خلال منتدى GroupDocs[هنا](https://forum.groupdocs.com/c/conversion/11)حيث يمكنك طرح الأسئلة والحصول على المساعدة من الخبراء.