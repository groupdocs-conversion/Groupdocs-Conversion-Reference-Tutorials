---
title: แปลง XLS เป็น PDF
linktitle: แปลง XLS เป็น PDF
second_title: GroupDocs.Conversion .NET API
description: แปลงไฟล์ XLS เป็นรูปแบบ PDF ได้อย่างง่ายดายโดยใช้ GroupDocs.Conversion สำหรับ .NET การบูรณาการที่ราบรื่น เอกสารประกอบที่ครอบคลุม และการสนับสนุนที่พร้อมใช้งาน
weight: 24
url: /th/net/converting-file-types-to-pdf/convert-xls-to-pdf/
---
## การแนะนำ
GroupDocs.Conversion สำหรับ .NET เป็น API อันทรงพลังที่ช่วยให้นักพัฒนาสามารถแปลงเอกสารระหว่างรูปแบบต่างๆ ภายในแอปพลิเคชัน .NET ของตนได้อย่างง่ายดาย ในบทช่วยสอนนี้ เราจะเน้นที่การแปลงไฟล์ XLS (Microsoft Excel Spreadsheet) เป็น PDF (Portable Document Format) ซึ่งเป็นข้อกำหนดทั่วไปในแอปพลิเคชันทางธุรกิจจำนวนมาก
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเข้าสู่บทช่วยสอน ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
### 1. ติดตั้ง GroupDocs.Conversion สำหรับ .NET
 ดาวน์โหลดและติดตั้ง GroupDocs.Conversion สำหรับ .NET จาก[เว็บไซต์](https://releases.groupdocs.com/conversion/net/)- ปฏิบัติตามคำแนะนำในการติดตั้งที่ให้ไว้เพื่อรวมเข้ากับโครงการ .NET ของคุณ
### 2. รับไฟล์ XLS ตัวอย่าง
ตรวจสอบให้แน่ใจว่าคุณมีไฟล์ XLS ตัวอย่างที่คุณต้องการแปลงเป็น PDF หากคุณไม่มี คุณสามารถสร้างสเปรดชีต Excel แบบธรรมดาหรือดาวน์โหลดไฟล์ XLS ตัวอย่างจากอินเทอร์เน็ตได้
### 3. ตั้งค่าสภาพแวดล้อมการพัฒนา
ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าสภาพแวดล้อมการพัฒนาสำหรับการพัฒนา .NET รวมถึง Visual Studio หรือ IDE ที่ต้องการอื่นๆ

## นำเข้าเนมสเปซ
ในแอปพลิเคชัน .NET ของคุณ ให้นำเข้าเนมสเปซที่จำเป็นเพื่อเข้าถึงฟังก์ชัน GroupDocs.Conversion:

```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## ขั้นตอนที่ 1: กำหนดโฟลเดอร์เอาท์พุตและเส้นทางไฟล์
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "xls-converted-to.pdf");
```
 ให้แน่ใจว่าจะเปลี่ยน`"Your Document Directory"` พร้อมเส้นทางไปยังโฟลเดอร์ที่คุณต้องการบันทึกไฟล์ PDF ที่แปลงแล้ว
## ขั้นตอนที่ 2: โหลดไฟล์ XLS ต้นฉบับ
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_XLS))
{
    // ตรรกะการแปลงจะไปที่นี่
}
```
 แทนที่`Constants.SAMPLE_XLS` พร้อมเส้นทางไปยังไฟล์ XLS ต้นทางของคุณ
## ขั้นตอนที่ 3: ตั้งค่าตัวเลือกการแปลง
```csharp
var options = new PdfConvertOptions();
```
ในขั้นตอนนี้ คุณสามารถปรับแต่งตัวเลือกการแปลงได้ตามความต้องการของคุณ ตัวอย่างเช่น คุณสามารถตั้งค่าการป้องกันด้วยรหัสผ่าน ปรับการวางแนวหน้า หรือระบุคุณภาพการแปลง
## ขั้นตอนที่ 4: ทำการแปลงและบันทึกไฟล์ PDF
```csharp
converter.Convert(outputFile, options);
```
บรรทัดโค้ดนี้ดำเนินการกระบวนการแปลงและบันทึกไฟล์ PDF ที่เป็นผลลัพธ์ไปยังเส้นทางเอาต์พุตที่ระบุ
## ขั้นตอนที่ 5: แสดงข้อความเสร็จสิ้นการแปลง
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
ขั้นตอนนี้จะแสดงข้อความที่ระบุว่ากระบวนการแปลงเสร็จสมบูรณ์พร้อมกับตำแหน่งของโฟลเดอร์เอาท์พุต

## บทสรุป
โดยสรุป GroupDocs.Conversion สำหรับ .NET มอบวิธีที่ตรงไปตรงมาและมีประสิทธิภาพในการแปลงไฟล์ XLS เป็นรูปแบบ PDF ภายในแอปพลิเคชัน .NET ด้วยการทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ นักพัฒนาสามารถรวมฟังก์ชันการแปลงเอกสารเข้ากับโปรเจ็กต์ของตนได้อย่างราบรื่น
## คำถามที่พบบ่อย
### ถาม: GroupDocs.Conversion สำหรับ .NET สามารถแปลงไฟล์เป็นรูปแบบอื่นที่ไม่ใช่ PDF ได้หรือไม่
ตอบ: ใช่ GroupDocs.Conversion สำหรับ .NET รองรับการแปลงระหว่างรูปแบบเอกสารที่หลากหลาย รวมถึง DOCX, PPTX, HTML และอื่นๆ
### ถาม: GroupDocs.Conversion สำหรับ .NET เข้ากันได้กับทั้ง .NET Framework และ .NET Core หรือไม่
ตอบ: ใช่ GroupDocs.Conversion สำหรับ .NET เข้ากันได้กับทั้งสภาพแวดล้อม .NET Framework และ .NET Core
### ถาม: GroupDocs.Conversion สำหรับ .NET จำเป็นต้องมีการขึ้นต่อกันเพิ่มเติมหรือไม่
ตอบ: ไม่ GroupDocs.Conversion สำหรับ .NET ไม่มีการพึ่งพาภายนอก ทำให้ง่ายต่อการรวมเข้ากับโปรเจ็กต์ .NET ของคุณ
### ถาม: ฉันสามารถแปลงหลายไฟล์พร้อมกันโดยใช้ GroupDocs.Conversion สำหรับ .NET ได้หรือไม่
ตอบ: ได้ GroupDocs.Conversion สำหรับ .NET ช่วยให้สามารถแปลงไฟล์หลายไฟล์เป็นชุด ซึ่งช่วยเพิ่มประสิทธิภาพสำหรับงานแปลงเอกสารขนาดใหญ่
### ถาม: GroupDocs.Conversion สำหรับ .NET มีการสนับสนุนทางเทคนิคหรือไม่
 ตอบ: ได้ คุณสามารถเข้าถึงการสนับสนุนทางเทคนิคและความช่วยเหลือผ่านทางฟอรัม GroupDocs.Conversion[ที่นี่](https://forum.groupdocs.com/c/conversion/11).