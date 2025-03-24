---
title: แปลง PSD เป็น PDF
linktitle: แปลง PSD เป็น PDF
second_title: GroupDocs.Conversion .NET API
description: เรียนรู้วิธีแปลงไฟล์ PSD เป็น PDF ได้อย่างง่ายดายโดยใช้ GroupDocs.Conversion สำหรับ .NET ปฏิบัติตามคำแนะนำทีละขั้นตอนของเรา
weight: 10
url: /th/net/file-format-conversion-convert-psd-to-pdf/
---

# แปลง PSD เป็น PDF

## การแนะนำ
ในบทช่วยสอนนี้ เราจะแนะนำคุณตลอดขั้นตอนการแปลงไฟล์ PSD (เอกสาร Photoshop) เป็นรูปแบบ PDF โดยใช้ไลบรารี GroupDocs.Conversion สำหรับ .NET ด้วยการทำตามคำแนะนำทีละขั้นตอนเหล่านี้ คุณจะสามารถแปลงไฟล์ PSD ของคุณเป็น PDF ได้อย่างราบรื่น
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าข้อกำหนดเบื้องต้นต่อไปนี้:
1.  การติดตั้งไลบรารี GroupDocs.Conversion: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งไลบรารี GroupDocs.Conversion สำหรับ .NET คุณสามารถดาวน์โหลดได้จาก[เว็บไซต์](https://releases.groupdocs.com/conversion/net/).
2. การเข้าถึงไฟล์ PSD: เข้าถึงไฟล์ PSD ที่คุณต้องการแปลงเป็น PDF

## นำเข้าเนมสเปซ
ก่อนที่จะเข้าสู่กระบวนการแปลง ให้นำเข้าเนมสเปซที่จำเป็น:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## ขั้นตอนที่ 1: กำหนดโฟลเดอร์เอาท์พุตและไฟล์
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "psd-converted-to.pdf");
```
 ในขั้นตอนนี้ ให้ระบุโฟลเดอร์เอาท์พุตที่คุณต้องการบันทึกไฟล์ PDF ที่แปลงแล้ว ตรวจสอบให้แน่ใจว่าคุณเปลี่ยน`"Your Document Directory"` ด้วยเส้นทางไดเร็กทอรีจริง
## ขั้นตอนที่ 2: โหลดไฟล์ PSD ต้นฉบับ
```csharp
using (var converter = new GroupDocs.Conversion.Converter("Path_to_your_PSD_file.psd"))
{
    var options = new PdfConvertOptions();
    // บันทึกไฟล์ PDF ที่แปลงแล้ว
    converter.Convert(outputFile, options);
}
```
 ที่นี่ คุณจะเริ่มต้นการ`Converter` วัตถุที่มีเส้นทางไปยังไฟล์ PSD ของคุณ แทนที่`"Path_to_your_PSD_file.psd"` พร้อมเส้นทางจริงไปยังไฟล์ PSD ของคุณ จากนั้นสร้างอินสแตนซ์ของ`PdfConvertOptions` เพื่อระบุการตั้งค่าการแปลง สุดท้ายโทรหา.`Convert` วิธีการแปลงไฟล์ PSD เป็น PDF และบันทึกลงในไฟล์เอาต์พุตที่ระบุ
## ขั้นตอนที่ 3: ตรวจสอบความสมบูรณ์ของการแปลง
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```
ขั้นตอนนี้เพียงพิมพ์ข้อความไปยังคอนโซลเพื่อยืนยันความสำเร็จของกระบวนการแปลงและระบุตำแหน่งที่บันทึกไฟล์ PDF ที่แปลงแล้ว

## บทสรุป
ในบทช่วยสอนนี้ เราได้สาธิตวิธีการแปลงไฟล์ PSD เป็นรูปแบบ PDF โดยใช้ไลบรารี GroupDocs.Conversion สำหรับ .NET ด้วยการทำตามขั้นตอนที่ให้ไว้ คุณสามารถแปลงไฟล์ PSD ของคุณเป็น PDF ได้อย่างง่ายดาย ทำให้สามารถแชร์และดูเอกสารของคุณได้ง่ายขึ้น
## คำถามที่พบบ่อย

### ฉันสามารถแปลงไฟล์ PSD หลายไฟล์พร้อมกันโดยใช้ GroupDocs.Conversion ได้หรือไม่
ได้ คุณสามารถแปลงไฟล์ PSD หลายไฟล์เป็น PDF หรือรูปแบบอื่นเป็นชุดได้โดยใช้ GroupDocs.Conversion

### GroupDocs.Conversion รองรับรูปแบบเอาต์พุตอื่นนอกเหนือจาก PDF หรือไม่
ใช่ GroupDocs.Conversion รองรับรูปแบบเอาต์พุตที่หลากหลาย รวมถึง DOCX, XLSX, PPTX, JPEG, PNG และอื่นๆ

### GroupDocs.Conversion เข้ากันได้กับ .NET เวอร์ชันต่างๆ หรือไม่
ใช่ GroupDocs.Conversion เข้ากันได้กับ .NET เวอร์ชันต่างๆ รวมถึง .NET Core และ .NET Framework

### ฉันสามารถปรับแต่งตัวเลือกการแปลงเพื่อให้ควบคุมเอาต์พุตได้มากขึ้นหรือไม่
ใช่ GroupDocs.Conversion มีตัวเลือกการปรับแต่งมากมาย เช่น การระบุขนาดหน้า การวางแนว คุณภาพ และอื่นๆ

### มีรุ่นทดลองให้ทดสอบก่อนซื้อหรือไม่?
ใช่ คุณสามารถรับ GroupDocs.Conversion เวอร์ชันทดลองใช้ฟรีได้จาก[เว็บไซต์](https://releases.groupdocs.com/conversion/net/) เพื่อทดสอบคุณสมบัติก่อนตัดสินใจซื้อ