---
"description": "เรียนรู้วิธีการแปลงงานนำเสนอ PowerPoint (PPTX) เป็นรูปแบบ PDF โดยใช้ GroupDocs.Conversion สำหรับ .NET กระบวนการแปลงที่ง่ายและมีประสิทธิภาพ"
"linktitle": "แปลง PPTX เป็น PDF"
"second_title": "API การแปลง GroupDocs .NET"
"title": "แปลง PPTX เป็น PDF"
"url": "/th/net/pdf-conversion/convert-pptx-to-pdf/"
"weight": 29
type: docs
---
# แปลง PPTX เป็น PDF

## การแนะนำ
ในบทช่วยสอนนี้ เราจะแนะนำขั้นตอนการแปลงไฟล์งานนำเสนอ PowerPoint (PPTX) เป็น Portable Document Format (PDF) โดยใช้ไลบรารี GroupDocs.Conversion สำหรับ .NET ทำตามขั้นตอนด้านล่างเพื่อแปลงไฟล์ดังกล่าว
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่ม ให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
1. GroupDocs.Conversion สำหรับไลบรารี .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งไลบรารี GroupDocs.Conversion สำหรับ .NET แล้ว คุณสามารถดาวน์โหลดได้จาก [ที่นี่](https://releases-groupdocs.com/conversion/net/).
2. สภาพแวดล้อมการพัฒนา: ตั้งค่าสภาพแวดล้อมการพัฒนาด้วยเครื่องมือที่จำเป็น เช่น Visual Studio หรือ .NET IDE อื่นๆ

## นำเข้าเนมสเปซ
รวมเนมสเปซที่จำเป็นในโครงการของคุณเพื่อเข้าถึงฟังก์ชันการทำงานของ GroupDocs.Conversion
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## ขั้นตอนที่ 1: ตั้งค่าโฟลเดอร์ผลลัพธ์และชื่อไฟล์
ขั้นแรก ให้กำหนดโฟลเดอร์เอาต์พุตที่จะบันทึกไฟล์ PDF ที่แปลงแล้ว และระบุชื่อไฟล์ PDF เอาต์พุต
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "pptx-converted-to.pdf");
```
## ขั้นตอนที่ 2: โหลดไฟล์ PPTX ต้นฉบับ
โหลดไฟล์งานนำเสนอ PowerPoint ต้นฉบับ (PPTX) โดยใช้ไลบรารี GroupDocs.Conversion
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PPTX))
{
    // ตรรกะการแปลงจะถูกวางไว้ที่นี่
}
```
## ขั้นตอนที่ 3: ระบุตัวเลือกการแปลง
กำหนดตัวเลือกการแปลง ในกรณีนี้ เราจะแปลงเป็นรูปแบบ PDF ดังนั้นให้สร้างอินสแตนซ์ของ `PdfConvertOptions`-
```csharp
var options = new PdfConvertOptions();
```
## ขั้นตอนที่ 4: ดำเนินการแปลง
ดำเนินการกระบวนการแปลงโดยใช้ `Convert` วิธีการและส่งผ่านเส้นทางไฟล์เอาท์พุตพร้อมกับตัวเลือกการแปลง
```csharp
converter.Convert(outputFile, options);
```
## ขั้นตอนที่ 5: ตรวจสอบผลลัพธ์
หลังจากการแปลงเสร็จสมบูรณ์แล้ว ให้แสดงข้อความแจ้งการเสร็จสมบูรณ์และตำแหน่งของไฟล์เอาต์พุต
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีการแปลงไฟล์งานนำเสนอ PowerPoint (PPTX) เป็น Portable Document Format (PDF) โดยใช้ไลบรารี GroupDocs.Conversion สำหรับ .NET คุณสามารถดำเนินการแปลงไฟล์นี้ในแอปพลิเคชัน .NET ได้อย่างง่ายดายโดยทำตามขั้นตอนที่ระบุไว้ข้างต้น
## คำถามที่พบบ่อย
### ถาม: GroupDocs.Conversion เข้ากันได้กับ .NET ทุกเวอร์ชันหรือไม่
ตอบ: ใช่ GroupDocs.Conversion รองรับ .NET Framework 2.0 ขึ้นไป รวมถึง .NET Core และ .NET Standard
### ถาม: ฉันสามารถแปลงไฟล์เป็นรูปแบบอื่นนอกเหนือจาก PDF ได้หรือไม่?
ตอบ: ใช่ GroupDocs.Conversion รองรับรูปแบบเอกสารต่างๆ มากมายสำหรับการแปลง รวมถึง Word, Excel, HTML และอื่นๆ อีกมากมาย
### ถาม: GroupDocs.Conversion มีการทดลองใช้ฟรีหรือไม่
A: ใช่ คุณสามารถเข้าถึงรุ่นทดลองใช้งานฟรีของ GroupDocs.Conversion ได้จาก [ที่นี่](https://releases-groupdocs.com/).
### ถาม: ฉันจะได้รับการสนับสนุนสำหรับ GroupDocs.Conversion ได้อย่างไร
A: คุณสามารถรับการสนับสนุนจากฟอรัมชุมชน GroupDocs ได้ [ที่นี่](https://forum-groupdocs.com/c/conversion/11).
### ถาม: มีใบอนุญาตชั่วคราวสำหรับ GroupDocs.Conversion หรือไม่
A: ใช่ คุณสามารถขอรับใบอนุญาตชั่วคราวสำหรับ GroupDocs ได้ การแปลงจาก [ที่นี่](https://purchase-groupdocs.com/temporary-license/).