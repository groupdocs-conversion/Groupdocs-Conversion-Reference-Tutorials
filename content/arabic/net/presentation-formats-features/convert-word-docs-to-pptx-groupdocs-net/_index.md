---
"date": "2025-04-30"
"description": "تعلّم كيفية تحويل مستندات مايكروسوفت وورد بسلاسة إلى عروض تقديمية جذابة باستخدام GroupDocs.Conversion لـ .NET. حسّن إنتاجيتك ببضعة أسطر من التعليمات البرمجية."
"title": "تحويل مستندات Word إلى PowerPoint PPTX باستخدام GroupDocs.Conversion لـ .NET"
"url": "/ar/net/presentation-formats-features/convert-word-docs-to-pptx-groupdocs-net/"
"weight": 1
type: docs
---
# تحويل مستندات Word إلى PowerPoint PPTX باستخدام GroupDocs.Conversion لـ .NET

## مقدمة
في بيئة اليوم الرقمية سريعة التطور، يُمكن لتحويل المستندات بين الصيغ بكفاءة أن يُحسّن الإنتاجية بشكل ملحوظ. سيُرشدك هذا البرنامج التعليمي خلال استخدام **GroupDocs.Conversion لـ .NET**—مكتبة قوية تسهل التحويل السلس عبر أنواع المستندات المختلفة.

ستتعلم كيفية تحويل ملفات DOC إلى صيغة PPTX بفعالية وبأقل قدر من البرمجة. بنهاية هذا الدليل، ستتمكن من:
- إعداد بيئة التطوير الخاصة بك
- تثبيت GroupDocs.Conversion لـ .NET
- تنفيذ عملية التحويل في C#
- فهم التطبيقات العملية واعتبارات الأداء

دعونا نبدأ!

## المتطلبات الأساسية
قبل أن نبدأ، تأكد من أن لديك ما يلي:
1. **مكتبة GroupDocs.Conversion**:ستحتاج إلى الإصدار 25.3.0 أو إصدار أحدث لهذا البرنامج التعليمي.
2. **بيئة التطوير**:تأكد من إعداد بيئة .NET مع دعم C#.
3. **المعرفة الأساسية**:ستكون المعرفة بلغة C# ومعالجة الملفات ومفاهيم برمجة .NET الأساسية مفيدة.

## إعداد GroupDocs.Conversion لـ .NET
للبدء، نحتاج إلى تثبيت مكتبة GroupDocs.Conversion في مشروعك:

**وحدة تحكم مدير الحزم NuGet**
```shell
Install-Package GroupDocs.Conversion -Version 25.3.0
```

**\.NET CLI**
```bash
dotnet add package GroupDocs.Conversion --version 25.3.0
```

### الحصول على ترخيص
- **نسخة تجريبية مجانية**:ابدأ بالإصدار التجريبي المجاني لاختبار وظائف GroupDocs.
- **رخصة مؤقتة**:الحصول على ترخيص مؤقت للميزات والقدرات الموسعة أثناء التطوير.
- **شراء**:للاستخدام طويل الأمد، فكر في شراء ترخيص.

إليك كيفية تهيئة بيئتك وإعدادها:
```csharp
using GroupDocs.Conversion;

// قم بتهيئة كائن المحول باستخدام مسار المستند المصدر
var converter = new Converter("YOUR_DOCUMENT_DIRECTORY\sample.doc");
```

## دليل التنفيذ

### تحويل DOC إلى PPTX
توضح هذه الميزة كيفية تحويل مستند Microsoft Word (.doc) إلى عرض تقديمي مفتوح XML في PowerPoint (.pptx).

#### الخطوة 1: تحميل ملف DOC المصدر
أولاً، حدد مسار مستندك المصدر. يُهيئ هذا المقطع البرمجي المُحوِّل بالملف الذي ترغب في تحويله.
```csharp
using (var converter = new GroupDocs.Conversion.Converter("YOUR_DOCUMENT_DIRECTORY\sample.doc"))
{
    // قم بمتابعة خطوات التحويل هنا.
}
```

#### الخطوة 2: تحديد خيارات التحويل
حدّد خيارات تحويل مستند إلى تنسيق PowerPoint. تتيح لك هذه الخيارات تخصيص الإخراج.
```csharp
// إنشاء مثيل لـ PresentationConvertOptions
var options = new PresentationConvertOptions();
```

#### الخطوة 3: تحويل ملف PPTX وحفظه
أخيرًا، قم بتحويل ملف DOC إلى PPTX باستخدام خيارات التحويل المحددة واحفظه في الموقع المطلوب.
```csharp
string outputFolder = Path.Combine("YOUR_OUTPUT_DIRECTORY\