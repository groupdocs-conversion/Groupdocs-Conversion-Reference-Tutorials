---
title: แปลง ODP เป็น PDF
linktitle: แปลง ODP เป็น PDF
second_title: GroupDocs.Conversion .NET API
description: เรียนรู้วิธีแปลง ODP เป็น PDF โดยใช้ GroupDocs.Conversion สำหรับ .NET ปฏิบัติตามคำแนะนำทีละขั้นตอนของเราเพื่อการแปลงเอกสารที่ราบรื่น
weight: 28
url: /th/net/document-conversion/convert-odp-to-pdf/
---

# แปลง ODP เป็น PDF

## การแนะนำ
GroupDocs.Conversion สำหรับ .NET เป็น API ที่ทรงพลังซึ่งช่วยให้นักพัฒนาสามารถแปลงรูปแบบเอกสารต่างๆ ในแอปพลิเคชัน .NET ของตนได้อย่างราบรื่น ในบทช่วยสอนนี้ เราจะแนะนำคุณตลอดขั้นตอนการแปลงไฟล์ ODP (OpenDocument Presentation) เป็นรูปแบบ PDF โดยใช้ GroupDocs.Conversion สำหรับ .NET
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
1.  GroupDocs.Conversion สำหรับ .NET SDK: ตรวจสอบให้แน่ใจว่าคุณได้ดาวน์โหลดและติดตั้ง GroupDocs.Conversion สำหรับ .NET SDK แล้ว คุณสามารถดาวน์โหลดได้จาก[หน้าดาวน์โหลด](https://releases.groupdocs.com/conversion/net/).
2. สภาพแวดล้อมการพัฒนา .NET: คุณควรตั้งค่าสภาพแวดล้อมการพัฒนา .NET บนเครื่องของคุณ
3. ไฟล์ ODP ต้นฉบับ: เตรียมไฟล์ ODP ที่คุณต้องการแปลงเป็น PDF

## นำเข้าเนมสเปซ
ขั้นแรก นำเข้าเนมสเปซที่จำเป็นไปยังโค้ด C# ของคุณ:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## ขั้นตอนที่ 1: กำหนดเส้นทางไฟล์เอาท์พุต
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "odp-converted-to.pdf");
```
 แทนที่`"Your Document Directory"` ด้วยเส้นทางที่คุณต้องการบันทึกไฟล์ PDF ที่แปลงแล้ว
## ขั้นตอนที่ 2: โหลดไฟล์ ODP ต้นฉบับ
```csharp
using (var converter = new GroupDocs.Conversion.Converter("path/to/your/source.odp"))
{
    // รหัสการแปลงจะไปที่นี่
}
```
 แทนที่`"path/to/your/source.odp"` ด้วยเส้นทางจริงไปยังไฟล์ ODP ต้นทางของคุณ
## ขั้นตอนที่ 3: ตั้งค่าตัวเลือกการแปลง
```csharp
var options = new PdfConvertOptions();
```
ที่นี่ คุณสามารถปรับแต่งตัวเลือกการแปลงตามความต้องการของคุณได้ ตัวอย่างเช่น คุณสามารถตั้งค่าการตั้งค่าการแปลง PDF เช่น ขนาดหน้า ระยะขอบ คุณภาพ ฯลฯ
## ขั้นตอนที่ 4: ทำการแปลง
```csharp
converter.Convert(outputFile, options);
```
บรรทัดโค้ดนี้เริ่มกระบวนการแปลงจาก ODP เป็น PDF โดยใช้ตัวเลือกที่ระบุ
## ขั้นตอนที่ 5: แสดงข้อความแสดงความสำเร็จ
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```
บรรทัดนี้จะแสดงข้อความแสดงความสำเร็จพร้อมกับโฟลเดอร์เอาต์พุตที่บันทึกไฟล์ PDF ที่แปลงแล้ว

## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีแปลงไฟล์ ODP เป็น PDF โดยใช้ GroupDocs.Conversion สำหรับ .NET ด้วยการทำตามขั้นตอนที่ให้ไว้ คุณสามารถรวมความสามารถในการแปลงเอกสารเข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างง่ายดาย
## คำถามที่พบบ่อย
### GroupDocs.Conversion สำหรับ .NET สามารถรองรับรูปแบบเอกสารอื่นๆ ได้หรือไม่
ใช่ GroupDocs.Conversion สำหรับ .NET รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง Word, Excel, PowerPoint, PDF และอื่นๆ
### มีการทดลองใช้ GroupDocs.Conversion สำหรับ .NET ฟรีหรือไม่
 ใช่ คุณสามารถทดลองใช้ฟรีได้จาก[เว็บไซต์](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนทางเทคนิคสำหรับ GroupDocs.Conversion สำหรับ .NET ได้อย่างไร
 คุณสามารถรับการสนับสนุนทางเทคนิคได้จาก[ฟอรั่มการสนับสนุน](https://forum.groupdocs.com/c/conversion/11).
### ฉันสามารถปรับแต่งตัวเลือกการแปลงตามความต้องการของฉันได้หรือไม่?
ใช่ GroupDocs.Conversion สำหรับ .NET มีตัวเลือกมากมายสำหรับการปรับแต่งให้ตรงกับความต้องการเฉพาะของคุณ
### ฉันจะซื้อใบอนุญาตสำหรับ GroupDocs.Conversion สำหรับ .NET ได้ที่ไหน
 คุณสามารถซื้อใบอนุญาตได้จาก[หน้าซื้อ](https://purchase.groupdocs.com/buy).