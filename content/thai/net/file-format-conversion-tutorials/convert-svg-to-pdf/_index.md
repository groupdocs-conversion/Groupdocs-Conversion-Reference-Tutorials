---
title: แปลง SVG เป็น PDF
linktitle: แปลง SVG เป็น PDF
second_title: GroupDocs.Conversion .NET API
description: เรียนรู้วิธีแปลง SVG เป็น PDF โดยใช้ GroupDocs.Conversion สำหรับ .NET ได้อย่างง่ายดาย ปรับปรุงกระบวนการจัดการเอกสารของคุณ
weight: 15
url: /th/net/file-format-conversion-convert-svg-to-pdf/
---

# แปลง SVG เป็น PDF

## การแนะนำ
ในโลกของการเขียนโปรแกรม การแปลงไฟล์จากรูปแบบหนึ่งไปเป็นอีกรูปแบบหนึ่งถือเป็นงานทั่วไป ไม่ว่าคุณจะจัดการกับรูปภาพ เอกสาร หรือสื่ออื่นๆ ความสามารถในการแปลงระหว่างรูปแบบต่างๆ ได้อย่างราบรื่นถือเป็นสิ่งสำคัญ ในบทช่วยสอนนี้ เราจะเจาะลึกวิธีการแปลงไฟล์ SVG (Scalable Vector Graphics) เป็น PDF (Portable Document Format) โดยใช้ GroupDocs.Conversion สำหรับ .NET
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเข้าสู่กระบวนการแปลง ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าข้อกำหนดเบื้องต้นต่อไปนี้:
### 1. ติดตั้ง GroupDocs.Conversion สำหรับ .NET
ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง GroupDocs.Conversion สำหรับ .NET ในสภาพแวดล้อมการพัฒนาของคุณ หากคุณยังไม่มี คุณสามารถดาวน์โหลดได้จาก[เว็บไซต์](https://releases.groupdocs.com/conversion/net/).
### 2. รับไฟล์ SVG ตัวอย่าง
คุณจะต้องมีไฟล์ SVG ตัวอย่างเพื่อแปลงเป็น PDF หากคุณไม่มี คุณสามารถค้นหาไฟล์ SVG ทางออนไลน์ได้อย่างง่ายดาย หรือสร้างไฟล์โดยใช้เครื่องมือออกแบบกราฟิกต่างๆ
### 3. ความเข้าใจพื้นฐานเกี่ยวกับ C#
ทำความคุ้นเคยกับพื้นฐานภาษาการเขียนโปรแกรม C# เนื่องจากเราจะใช้เพื่อเขียนโค้ด Conversion

## นำเข้าเนมสเปซ
ขั้นแรก เรามานำเข้าเนมสเปซที่จำเป็น:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## ขั้นตอนที่ 1: กำหนดโฟลเดอร์เอาท์พุตและไฟล์
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "svg-converted-to.pdf");
```
 ให้แน่ใจว่าจะเปลี่ยน`"Your Document Directory"` พร้อมเส้นทางไปยังไดเร็กทอรีเอาต์พุตที่คุณต้องการ
## ขั้นตอนที่ 2: โหลดไฟล์ SVG ต้นฉบับ
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_SVG))
{
    // รหัส Conversion อยู่ที่นี่
}
```
 แทนที่`Constants.SAMPLE_SVG` พร้อมเส้นทางไปยังไฟล์ SVG ของคุณ
## ขั้นตอนที่ 3: ตั้งค่าตัวเลือกการแปลง
```csharp
var options = new PdfConvertOptions();
```
ที่นี่ เรากำลังตั้งค่าตัวเลือกการแปลงสำหรับเอาต์พุต PDF โดยเฉพาะ คุณสามารถปรับแต่งตัวเลือกเหล่านี้ได้ตามความต้องการของคุณ
## ขั้นตอนที่ 4: ทำการแปลง
```csharp
converter.Convert(outputFile, options);
```
บรรทัดนี้ดำเนินการกระบวนการแปลง โดยนำไฟล์ SVG ต้นฉบับมาแปลงเป็น PDF ด้วยตัวเลือกที่ระบุ
## ขั้นตอนที่ 5: ตรวจสอบความสมบูรณ์ของการแปลง
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
บรรทัดนี้จะแสดงข้อความยืนยันความสำเร็จของกระบวนการแปลง พร้อมด้วยไดเร็กทอรีที่มีไฟล์ PDF ที่แปลงแล้ว

## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีแปลงไฟล์ SVG เป็น PDF โดยใช้ GroupDocs.Conversion สำหรับ .NET ด้วยการทำตามคำแนะนำทีละขั้นตอนและให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้น คุณจะสามารถรวมความสามารถในการแปลงรูปแบบไฟล์เข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างราบรื่น
## คำถามที่พบบ่อย
### GroupDocs.Conversion สำหรับ .NET เข้ากันได้กับกรอบงาน .NET ทั้งหมดหรือไม่
ใช่ GroupDocs.Conversion สำหรับ .NET รองรับเฟรมเวิร์ก .NET หลายเฟรม รวมถึง .NET Core และ .NET Framework
### ฉันสามารถปรับแต่งตัวเลือกการแปลงสำหรับรูปแบบเอาต์พุตเฉพาะได้หรือไม่
อย่างแน่นอน! GroupDocs.Conversion สำหรับ .NET มีตัวเลือกการปรับแต่งที่ครอบคลุมสำหรับรูปแบบเอาต์พุตที่รองรับแต่ละรูปแบบ
### GroupDocs.Conversion สำหรับ .NET รองรับการแปลงเป็นชุดหรือไม่
ได้ คุณสามารถแปลงไฟล์หลายไฟล์พร้อมกันได้โดยใช้ GroupDocs.Conversion สำหรับ .NET
### มีรุ่นทดลองใช้สำหรับการทดสอบหรือไม่?
 ใช่ คุณสามารถเข้าถึงเวอร์ชันทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนทางเทคนิคสำหรับ GroupDocs.Conversion สำหรับ .NET ได้ที่ไหน
คุณสามารถดูการสนับสนุนทางเทคนิคและความช่วยเหลือได้ในฟอรัม GroupDocs[ที่นี่](https://forum.groupdocs.com/c/conversion/11).