---
title: تحويل XLSM إلى PDF
linktitle: تحويل XLSM إلى PDF
second_title: GroupDocs.Conversion .NET API
description: تعرف على كيفية تحويل ملفات XLSM إلى تنسيق PDF بسهولة باستخدام GroupDocs.Conversion for .NET. يتضمن دليل خطوة بخطوة.
weight: 23
url: /ar/net/converting-file-types-to-pdf/convert-xlsm-to-pdf/
---
## مقدمة
في هذا البرنامج التعليمي، سوف نتعمق في عملية تحويل ملفات XLSM إلى تنسيق PDF باستخدام مكتبة GroupDocs.Conversion القوية لـ .NET. يعد تحويل الملفات مهمة شائعة في العديد من التطبيقات، ويعمل GroupDocs.Conversion على تبسيط هذه العملية، مما يوفر إمكانات تحويل فعالة وموثوقة.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من توفر المتطلبات الأساسية التالية:
### 1. قم بتثبيت GroupDocs.Conversion لـ .NET
يمكنك تنزيل مكتبة GroupDocs.Conversion for .NET من موقع الويب.[حمل هنا](https://releases.groupdocs.com/conversion/net/)
### 2. الحصول على ترخيص أو استخدام ترخيص مؤقت
 لاستخدام GroupDocs.Conversion لـ .NET، تحتاج إلى ترخيص صالح. إذا لم يكن لديك ترخيص، يمكنك الحصول على ترخيص مؤقت لأغراض الاختبار.[الحصول على ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/)
### 3. قم بإعداد بيئة التطوير الخاصة بك
تأكد من إعداد بيئة تطوير لبرمجة .NET. يمكنك استخدام Visual Studio أو أي بيئة تطوير متكاملة أخرى مفضلة.

## استيراد مساحات الأسماء
أولاً، لنستورد مساحات الأسماء الضرورية إلى مشروعنا:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```

الآن، دعونا نقسم عملية التحويل إلى خطوات متعددة:
## الخطوة 1: تحديد مجلد الإخراج ومسار الملف
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "xlsm-converted-to.pdf");
```
 تأكد من الاستبدال`"Your Document Directory"` باستخدام مسار الدليل حيث تريد حفظ ملف PDF المحول.
## الخطوة 2: قم بتحميل ملف XLSM المصدر
```csharp
using (var converter = new GroupDocs.Conversion.Converter("Path_to_your_XLSM_file"))
{
	// منطق التحويل سوف يذهب هنا
}
```
 يستبدل`"Path_to_your_XLSM_file"` بالمسار الفعلي لملف XLSM الخاص بك.
## الخطوة 3: احفظ ملف PDF المحول
بعد إعداد خيارات التحويل، احفظ ملف PDF المحول إلى مسار الإخراج المحدد.
```csharp
// خيارات التحويل
var options = new PdfConvertOptions();

// إجراء التحويل
converter.Convert(outputFile, options);
```
## الخطوة 4: عرض رسالة إتمام التحويل
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```
تُعلم هذه الخطوة المستخدم بإكمال عملية التحويل بنجاح وتوفر الموقع الذي يمكن العثور فيه على ملف PDF المحول.

## خاتمة
يعد تحويل ملفات XLSM إلى تنسيق PDF عملية مباشرة باستخدام GroupDocs.Conversion for .NET. باتباع الخطوات الموضحة في هذا البرنامج التعليمي، يمكنك دمج وظيفة تحويل الملفات بسلاسة في تطبيقات .NET الخاصة بك.
## الأسئلة الشائعة
### هل يتوافق GroupDocs.Conversion for .NET مع كافة إصدارات .NET؟
نعم، GroupDocs.Conversion for .NET متوافق مع .NET Framework 4.6.1 والإصدارات الأحدث.
### هل يمكنني تحويل ملفات XLSM متعددة في وقت واحد؟
نعم، يمكنك تحويل ملفات XLSM متعددة إلى PDF أو تنسيقات أخرى مدعومة.
### هل يدعم GroupDocs.Conversion for .NET ملفات XLSM المشفرة؟
نعم، يدعم GroupDocs.Conversion for .NET تحويل ملفات XLSM المشفرة، بشرط أن يكون لديك بيانات الاعتماد اللازمة.
### هل هناك نسخة تجريبية متاحة لأغراض الاختبار؟
نعم، يمكنك الحصول على نسخة تجريبية مجانية من GroupDocs.Conversion لـ .NET لتقييم ميزاته قبل إجراء عملية شراء.
### كيف يمكنني الحصول على الدعم الفني لـ GroupDocs.Conversion لـ .NET؟
 يمكنك زيارة منتدى GroupDocs.Conversion للحصول على الدعم الفني والمساعدة.[قم بزيارة منتدى الدعم](https://forum.groupdocs.com/c/conversion/11)