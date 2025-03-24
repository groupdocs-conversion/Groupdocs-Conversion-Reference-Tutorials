---
title: تحويل PPTX إلى PDF
linktitle: تحويل PPTX إلى PDF
second_title: GroupDocs.Conversion .NET API
description: تعرف على كيفية تحويل عروض PowerPoint التقديمية (PPTX) إلى تنسيق PDF باستخدام GroupDocs.Conversion for .NET. عملية تحويل سهلة وفعالة.
weight: 29
url: /ar/net/pdf-conversion/convert-pptx-to-pdf/
---

# تحويل PPTX إلى PDF

## مقدمة
في هذا البرنامج التعليمي، سنتعرف على عملية تحويل ملف عرض تقديمي لـ PowerPoint (PPTX) إلى تنسيق مستند محمول (PDF) باستخدام مكتبة GroupDocs.Conversion لـ .NET. اتبع الخطوات أدناه لتحقيق هذا التحويل.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من توفر المتطلبات الأساسية التالية:
1.  GroupDocs.Conversion لمكتبة .NET: تأكد من تثبيت GroupDocs.Conversion لمكتبة .NET. يمكنك تنزيله من[هنا](https://releases.groupdocs.com/conversion/net/).
2. بيئة التطوير: قم بإعداد بيئة تطوير باستخدام الأدوات اللازمة مثل Visual Studio أو أي برنامج .NET IDE آخر.

## استيراد مساحات الأسماء
قم بتضمين مساحات الأسماء الضرورية في مشروعك للوصول إلى وظائف GroupDocs.Conversion.
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## الخطوة 1: تعيين مجلد الإخراج واسم الملف
أولاً، حدد مجلد الإخراج حيث سيتم حفظ ملف PDF المحول، وحدد اسم ملف PDF الناتج.
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "pptx-converted-to.pdf");
```
## الخطوة 2: قم بتحميل ملف PPTX المصدر
قم بتحميل ملف العرض التقديمي PowerPoint (PPTX) المصدر باستخدام مكتبة GroupDocs.Conversion.
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PPTX))
{
    // سيتم وضع منطق التحويل هنا
}
```
## الخطوة 3: تحديد خيارات التحويل
تحديد خيارات التحويل. في هذه الحالة، نقوم بالتحويل إلى تنسيق PDF، لذا قم بإنشاء مثيل لـ`PdfConvertOptions`.
```csharp
var options = new PdfConvertOptions();
```
## الخطوة 4: إجراء التحويل
 تنفيذ عملية التحويل باستخدام`Convert` الطريقة وتمرير مسار ملف الإخراج مع خيارات التحويل.
```csharp
converter.Convert(outputFile, options);
```
## الخطوة 5: التحقق من الإخراج
بعد اكتمال التحويل بنجاح، قم بعرض رسالة تشير إلى اكتمال التحويل وموقع ملف الإخراج.
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```

## خاتمة
في هذا البرنامج التعليمي، تعلمنا كيفية تحويل ملف عرض تقديمي لـ PowerPoint (PPTX) إلى تنسيق مستند محمول (PDF) باستخدام مكتبة GroupDocs.Conversion لـ .NET. باتباع الخطوات الموضحة أعلاه، يمكنك إجراء هذا التحويل بسهولة في تطبيقات .NET الخاصة بك.
## الأسئلة الشائعة
### س: هل GroupDocs.Conversion متوافق مع كافة إصدارات .NET؟
ج: نعم، يدعم GroupDocs.Conversion .NET Framework 2.0 والإصدارات الأحدث، بما في ذلك .NET Core و.NET Standard.
### س: هل يمكنني تحويل الملفات إلى صيغ أخرى غير PDF؟
ج: نعم، يدعم GroupDocs.Conversion نطاقًا واسعًا من تنسيقات المستندات للتحويل، بما في ذلك Word وExcel وHTML والمزيد.
### س: هل يقدم GroupDocs.Conversion أي نسخة تجريبية مجانية؟
 ج: نعم، يمكنك الوصول إلى النسخة التجريبية المجانية من GroupDocs.Conversion من[هنا](https://releases.groupdocs.com/).
### س: كيف يمكنني الحصول على الدعم لـ GroupDocs.Conversion؟
 ج: يمكنك الحصول على الدعم من منتدى مجتمع GroupDocs[هنا](https://forum.groupdocs.com/c/conversion/11).
### س: هل يتوفر ترخيص مؤقت لـ GroupDocs.Conversion؟
 ج: نعم، يمكنك الحصول على ترخيص مؤقت لـ GroupDocs.Conversion من[هنا](https://purchase.groupdocs.com/temporary-license/).