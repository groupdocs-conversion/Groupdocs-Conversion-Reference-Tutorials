---
title: แปลงรูปภาพ BMP เป็น PDF
linktitle: แปลงรูปภาพ BMP เป็น PDF
second_title: GroupDocs.Conversion .NET API
description: แปลงรูปภาพ BMP เป็น PDF ได้อย่างราบรื่นโดยใช้ GroupDocs.Conversion สำหรับ .NET ตัวเลือกที่ปรับแต่งได้เพื่อผลลัพธ์ที่ดีที่สุด
weight: 11
url: /th/net/file-conversion-to-pdf/convert-bmp-to-pdf/
---

# แปลงรูปภาพ BMP เป็น PDF

## การแนะนำ
GroupDocs.Conversion สำหรับ .NET มอบโซลูชันอันทรงพลังสำหรับการแปลงรูปภาพ BMP เป็นรูปแบบ PDF ได้อย่างราบรื่น บทช่วยสอนนี้จะแนะนำคุณตลอดกระบวนการทีละขั้นตอน
### ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่ม ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
1.  GroupDocs.Conversion สำหรับ .NET: ติดตั้งไลบรารีโดยการดาวน์โหลดจากไฟล์[ลิ้งค์ดาวน์โหลด](https://releases.groupdocs.com/conversion/net/).
2. ไฟล์ BMP ต้นฉบับ: เตรียมไฟล์รูปภาพ BMP ที่คุณต้องการแปลง

## นำเข้าเนมสเปซ
ขั้นแรก นำเข้าเนมสเปซที่จำเป็นเพื่อเข้าถึงคลาสและวิธีการที่จำเป็น:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## ขั้นตอนที่ 1: ตั้งค่าโฟลเดอร์เอาท์พุตและชื่อไฟล์
กำหนดเส้นทางโฟลเดอร์เอาท์พุตและชื่อของไฟล์ PDF ที่แปลงแล้ว:
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "bmp-converted-to.pdf");
```
## ขั้นตอนที่ 2: โหลดไฟล์ BMP ซอร์ส
 โหลดไฟล์ BMP ต้นทางโดยใช้ไฟล์`Converter` ระดับ:
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_BMP))
{
    // ตรรกะการแปลงอยู่ที่นี่
}
```
## ขั้นตอนที่ 3: กำหนดค่าตัวเลือกการแปลง
 ระบุตัวเลือกการแปลง ในกรณีนี้เราจะใช้`PdfConvertOptions` สำหรับการแปลงเป็นรูปแบบ PDF:
```csharp
var options = new PdfConvertOptions();
```
## ขั้นตอนที่ 4: แปลง BMP เป็น PDF
ทำการแปลงและบันทึกไฟล์ PDF ที่แปลงแล้ว:
```csharp
converter.Convert(outputFile, options);
```
## ขั้นตอนที่ 5: ตรวจสอบการแปลง
ตรวจสอบว่าการแปลงสำเร็จหรือไม่และแสดงเส้นทางโฟลเดอร์เอาต์พุต:
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
ยินดีด้วย! คุณได้แปลงรูปภาพ BMP เป็น PDF โดยใช้ GroupDocs.Conversion สำหรับ .NET สำเร็จแล้ว

## บทสรุป
โดยสรุป GroupDocs.Conversion สำหรับ .NET นำเสนอโซลูชันที่เรียบง่ายแต่ทรงพลังสำหรับการแปลงรูปภาพ BMP เป็นรูปแบบ PDF ด้วยการทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ คุณสามารถรวมฟังก์ชันการทำงานนี้เข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างราบรื่น
## คำถามที่พบบ่อย
### GroupDocs.Conversion สำหรับ .NET เข้ากันได้กับรูปแบบภาพ BMP ทั้งหมดหรือไม่
GroupDocs.Conversion สำหรับ .NET รองรับรูปแบบภาพ BMP ที่หลากหลาย จึงรับประกันความเข้ากันได้กับไฟล์ BMP ส่วนใหญ่
### ฉันสามารถปรับแต่งตัวเลือกการแปลงเพื่อให้ควบคุมเอาต์พุต PDF ได้มากขึ้นได้หรือไม่
ใช่ คุณสามารถปรับแต่งตัวเลือกการแปลงต่างๆ เช่น DPI ขนาดหน้า การวางแนว และอื่นๆ อีกมากมาย เพื่อปรับแต่งเอาต์พุต PDF ตามความต้องการของคุณ
### GroupDocs.Conversion สำหรับ .NET จำเป็นต้องมีการขึ้นต่อกันเพิ่มเติมหรือไม่
ไม่ GroupDocs.Conversion สำหรับ .NET เป็นไลบรารีแบบสแตนด์อโลนที่ไม่จำเป็นต้องมีการอ้างอิงเพิ่มเติมสำหรับงานการแปลงพื้นฐาน
### มีรุ่นทดลองให้ทดสอบก่อนซื้อหรือไม่?
 ใช่ คุณสามารถดาวน์โหลดเวอร์ชันทดลองใช้ฟรีได้จาก[หน้าเผยแพร่](https://releases.groupdocs.com/) เพื่อประเมินคุณสมบัติของห้องสมุดก่อนตัดสินใจซื้อ
### ฉันจะรับการสนับสนุนหรือความช่วยเหลือได้ที่ไหน หากฉันประสบปัญหาใดๆ
 ท่านสามารถเยี่ยมชมได้ที่[ฟอรัม GroupDocs.Conversion](https://forum.groupdocs.com/c/conversion/11) เพื่อขอความช่วยเหลือจากชุมชนหรือติดต่อฝ่ายสนับสนุนโดยตรงเพื่อขอความช่วยเหลือส่วนบุคคล