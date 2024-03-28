---
title: แปลง PPTX เป็น PDF
linktitle: แปลง PPTX เป็น PDF
second_title: GroupDocs.Conversion .NET API
description: เรียนรู้วิธีแปลงงานนำเสนอ PowerPoint (PPTX) เป็นรูปแบบ PDF โดยใช้ GroupDocs.Conversion สำหรับ .NET กระบวนการแปลงที่ง่ายและมีประสิทธิภาพ
type: docs
weight: 29
url: /th/net/pdf-conversion/convert-pptx-to-pdf/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะอธิบายขั้นตอนการแปลงไฟล์งานนำเสนอ PowerPoint (PPTX) ไปเป็น Portable Document Format (PDF) โดยใช้ไลบรารี GroupDocs.Conversion สำหรับ .NET ทำตามขั้นตอนด้านล่างเพื่อให้ได้การแปลงนี้
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
1.  GroupDocs.Conversion สำหรับไลบรารี .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งไลบรารี GroupDocs.Conversion สำหรับ .NET แล้ว คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.groupdocs.com/conversion/net/).
2. สภาพแวดล้อมการพัฒนา: ตั้งค่าสภาพแวดล้อมการพัฒนาด้วยเครื่องมือที่จำเป็น เช่น Visual Studio หรือ .NET IDE อื่น ๆ

## นำเข้าเนมสเปซ
รวมเนมสเปซที่จำเป็นในโครงการของคุณเพื่อเข้าถึงฟังก์ชัน GroupDocs.Conversion
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## ขั้นตอนที่ 1: ตั้งค่าโฟลเดอร์เอาท์พุตและชื่อไฟล์
ขั้นแรก กำหนดโฟลเดอร์เอาท์พุตที่จะบันทึกไฟล์ PDF ที่แปลงแล้ว และระบุชื่อของไฟล์ PDF เอาท์พุต
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "pptx-converted-to.pdf");
```
## ขั้นตอนที่ 2: โหลดไฟล์ PPTX ต้นฉบับ
โหลดไฟล์งานนำเสนอ PowerPoint (PPTX) ต้นทางโดยใช้ไลบรารี GroupDocs.Conversion
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PPTX))
{
    // ตรรกะการแปลงจะถูกวางไว้ที่นี่
}
```
## ขั้นตอนที่ 3: ระบุตัวเลือกการแปลง
กำหนดตัวเลือกการแปลง ในกรณีนี้ เรากำลังแปลงเป็นรูปแบบ PDF ดังนั้นให้สร้างอินสแตนซ์ของ`PdfConvertOptions`.
```csharp
var options = new PdfConvertOptions();
```
## ขั้นตอนที่ 4: ทำการแปลง
 ดำเนินการกระบวนการแปลงโดยใช้`Convert` วิธีการและส่งเส้นทางไฟล์เอาต์พุตพร้อมกับตัวเลือกการแปลง
```csharp
converter.Convert(outputFile, options);
```
## ขั้นตอนที่ 5: ตรวจสอบผลลัพธ์
หลังจากการแปลงเสร็จสมบูรณ์แล้ว ให้แสดงข้อความระบุความสมบูรณ์และตำแหน่งของไฟล์เอาต์พุต
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีแปลงไฟล์งานนำเสนอ PowerPoint (PPTX) เป็น Portable Document Format (PDF) โดยใช้ไลบรารี GroupDocs.Conversion สำหรับ .NET ด้วยการทำตามขั้นตอนที่อธิบายไว้ข้างต้น คุณสามารถทำการแปลงนี้ในแอปพลิเคชัน .NET ของคุณได้อย่างง่ายดาย
## คำถามที่พบบ่อย
### ถาม: GroupDocs.Conversion เข้ากันได้กับ .NET ทุกเวอร์ชันหรือไม่
ตอบ: ใช่ GroupDocs.Conversion รองรับ .NET Framework 2.0 และสูงกว่า รวมถึง .NET Core และ .NET Standard
### ถาม: ฉันสามารถแปลงไฟล์เป็นรูปแบบอื่นที่ไม่ใช่ PDF ได้หรือไม่
ตอบ: ใช่ GroupDocs.Conversion รองรับรูปแบบเอกสารที่หลากหลายสำหรับการแปลง รวมถึง Word, Excel, HTML และอื่นๆ
### ถาม: GroupDocs.Conversion ให้ทดลองใช้ฟรีหรือไม่
 ตอบ: ได้ คุณสามารถเข้าถึง GroupDocs.Conversion รุ่นทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ถาม: ฉันจะรับการสนับสนุนสำหรับ GroupDocs.Conversion ได้อย่างไร
 ตอบ: คุณสามารถรับการสนับสนุนจากฟอรัมชุมชน GroupDocs[ที่นี่](https://forum.groupdocs.com/c/conversion/11).
### ถาม: GroupDocs.Conversion มีใบอนุญาตชั่วคราวหรือไม่
 ตอบ: ได้ คุณสามารถขอรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Conversion ได้จาก[ที่นี่](https://purchase.groupdocs.com/temporary-license/).