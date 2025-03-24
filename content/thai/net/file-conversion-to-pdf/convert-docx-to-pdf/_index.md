---
title: แปลงเอกสาร Word DOCX เป็น PDF
linktitle: แปลงเอกสาร Word DOCX เป็น PDF
second_title: GroupDocs.Conversion .NET API
description: เรียนรู้วิธีแปลงเอกสาร DOCX Word เป็น PDF ได้อย่างง่ายดายโดยใช้ GroupDocs.Conversion สำหรับ .NET ปรับปรุงความสามารถในการจัดการเอกสารของคุณ
weight: 24
url: /th/net/file-conversion-to-pdf/convert-docx-to-pdf/
---
## การแนะนำ
ในด้านการจัดการเอกสาร การแปลงไฟล์จากรูปแบบหนึ่งไปเป็นอีกรูปแบบหนึ่งมักเป็นสิ่งจำเป็น ไม่ว่าจะเป็นเพราะเหตุผลด้านความเข้ากันได้ วัตถุประสงค์ในการเก็บข้อมูล หรือเพียงแค่การตั้งค่า ความสามารถในการแปลงระหว่างรูปแบบต่างๆ ได้อย่างราบรื่นถือเป็นสิ่งสำคัญ ในบทช่วยสอนนี้ เราจะเจาะลึกวิธีการแปลงเอกสาร DOCX Word เป็น PDF ได้อย่างง่ายดายโดยใช้ไลบรารี GroupDocs.Conversion สำหรับ .NET ด้วยการทำตามคำแนะนำทีละขั้นตอนเหล่านี้ คุณจะพร้อมที่จะจัดการกับการแปลงดังกล่าวได้อย่างง่ายดาย
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเข้าสู่กระบวนการแปลง ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1.  GroupDocs.Conversion สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งไลบรารีในสภาพแวดล้อมการพัฒนาของคุณ หากไม่ใช่คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.groupdocs.com/conversion/net/).
2. .NET Framework: ตรวจสอบให้แน่ใจว่าคุณมีความรู้ในการทำงานเกี่ยวกับการพัฒนา .NET และมีการตั้งค่าสภาพแวดล้อมที่จำเป็น

## นำเข้าเนมสเปซ
ในการเริ่มต้น ให้นำเข้าเนมสเปซที่จำเป็นในโค้ด C# ของคุณ:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## ขั้นตอนที่ 1: กำหนดโฟลเดอร์เอาท์พุตและไฟล์
ขั้นแรก ระบุโฟลเดอร์เอาท์พุตที่คุณต้องการบันทึกไฟล์ PDF ที่แปลงแล้ว และกำหนดชื่อไฟล์เอาท์พุต:
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "docx-converted-to.pdf");
```
 แทนที่`"Your Document Directory"` ด้วยเส้นทางไดเรกทอรีที่คุณต้องการบันทึกไฟล์ PDF ที่แปลงแล้ว
## ขั้นตอนที่ 2: โหลดไฟล์ DOCX ซอร์ส
จากนั้น โหลดไฟล์ DOCX ต้นฉบับโดยใช้ไลบรารี GroupDocs.Conversion:
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_DOCX))
{
    // รหัสการแปลงจะไปที่นี่
}
```
 แทนที่`Constants.SAMPLE_DOCX` พร้อมเส้นทางไปยังไฟล์ DOCX ต้นฉบับของคุณ
## ขั้นตอนที่ 3: ระบุตัวเลือกการแปลง
กำหนดตัวเลือกการแปลง ในกรณีนี้ เราจะใช้ PdfConvertOptions เนื่องจากเรากำลังแปลงเป็น PDF:
```csharp
var options = new PdfConvertOptions();
```
## ขั้นตอนที่ 4: ทำการแปลง
ทำการแปลงจริงและบันทึกไฟล์ PDF ที่แปลงแล้ว:
```csharp
converter.Convert(outputFile, options);
```
## ขั้นตอนที่ 5: แสดงข้อความแสดงความสำเร็จ
สุดท้าย แจ้งให้ผู้ใช้ทราบว่ากระบวนการแปลงเสร็จสมบูรณ์แล้ว:
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```

## บทสรุป
โดยสรุป การแปลงเอกสาร DOCX Word เป็นรูปแบบ PDF นั้นเป็นงานที่ตรงไปตรงมาด้วยไลบรารี GroupDocs.Conversion สำหรับ .NET ด้วยการทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ คุณสามารถดำเนินการแปลงดังกล่าวภายในแอปพลิเคชัน .NET ของคุณได้อย่างราบรื่น ซึ่งช่วยเพิ่มความสามารถในการจัดการเอกสาร
## คำถามที่พบบ่อย
### GroupDocs.Conversion เข้ากันได้กับ .NET ทุกเวอร์ชันหรือไม่
ใช่ GroupDocs.Conversion เข้ากันได้กับ .NET เวอร์ชันต่างๆ เพื่อให้นักพัฒนามีความยืดหยุ่น
### ฉันสามารถแปลงไฟล์รูปแบบอื่นนอกเหนือจาก DOCX เป็น PDF โดยใช้ GroupDocs.Conversion ได้หรือไม่
อย่างแน่นอน! GroupDocs.Conversion รองรับรูปแบบไฟล์ที่หลากหลายสำหรับการแปลง รวมถึง DOCX, XLSX, PPTX และอื่นๆ
### GroupDocs.Conversion มีเวอร์ชันทดลองใช้งานหรือไม่
 ใช่ คุณสามารถทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนสำหรับข้อความค้นหาที่เกี่ยวข้องกับ GroupDocs.Conversion ได้อย่างไร
 คุณสามารถขอความช่วยเหลือได้จากฟอรัมชุมชน GroupDocs[ที่นี่](https://forum.groupdocs.com/c/conversion/11).
### ฉันจะขอรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Conversion ได้ที่ไหน
 คุณสามารถขอรับใบอนุญาตชั่วคราวได้จาก[ที่นี่](https://purchase.groupdocs.com/temporary-license/).