---
title: แปลงไฟล์ DWG CAD เป็น PDF
linktitle: แปลงไฟล์ DWG CAD เป็น PDF
second_title: GroupDocs.Conversion .NET API
description: เรียนรู้วิธีแปลงไฟล์ DWG CAD เป็น PDF ได้อย่างราบรื่นโดยใช้ GroupDocs.Conversion สำหรับ .NET ปฏิบัติตามบทช่วยสอนทีละขั้นตอนของเราเพื่อการแปลงที่มีประสิทธิภาพ
weight: 10
url: /th/net/convert-files-to-pdf/convert-dwg-to-pdf/
---

# แปลงไฟล์ DWG CAD เป็น PDF

## การแนะนำ
ในบทช่วยสอนนี้ เราจะได้เรียนรู้วิธีแปลงไฟล์ DWG CAD เป็น PDF โดยใช้ GroupDocs.Conversion สำหรับ .NET GroupDocs.Conversion เป็นไลบรารีที่มีประสิทธิภาพซึ่งมีฟังก์ชันการแปลงเอกสารที่หลากหลาย
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่ม ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
1.  GroupDocs.Conversion สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งไลบรารี GroupDocs.Conversion คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.groupdocs.com/conversion/net/).
2. สภาพแวดล้อมการพัฒนา: ตั้งค่าสภาพแวดล้อมการพัฒนาของคุณด้วย Visual Studio หรือ IDE ที่ต้องการอื่นๆ
3. ไฟล์ DWG: เตรียมไฟล์ DWG ที่คุณต้องการแปลงให้พร้อมในไดเร็กทอรีในเครื่องของคุณ

## นำเข้าเนมสเปซ
ก่อนที่จะเข้าสู่กระบวนการแปลง ให้นำเข้าเนมสเปซที่จำเป็น:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## ขั้นตอนที่ 1: โหลดไฟล์ DWG ต้นฉบับ
 ขั้นแรก คุณต้องโหลดไฟล์ DWG ต้นฉบับ นี้จะกระทำโดยใช้`Converter` คลาสจัดทำโดย GroupDocs.Conversion 
```csharp
using (var converter = new GroupDocs.Conversion.Converter("Path_to_your_DWG_file"))
{
    // รหัสของคุณที่นี่
}
```
 แทนที่`"Path_to_your_DWG_file"` พร้อมเส้นทางจริงไปยังไฟล์ DWG ของคุณ
## ขั้นตอนที่ 2: แปลง DWG เป็น PDF
เมื่อคุณโหลดไฟล์ DWG แล้ว คุณสามารถระบุตัวเลือกการแปลงและแปลงเป็น PDF ได้ 
```csharp
var options = new PdfConvertOptions();
```
 ที่นี่เรากำลังสร้าง`PdfConvertOptions` ซึ่งมีการตั้งค่าต่างๆ สำหรับกระบวนการแปลง PDF
## ขั้นตอนที่ 3: บันทึกไฟล์ PDF ที่แปลงแล้ว
หลังจากระบุตัวเลือกการแปลงแล้ว ตอนนี้คุณสามารถแปลงไฟล์ DWG เป็น PDF และบันทึกได้
```csharp
string outputFolder = "Your_Document_Directory";
string outputFile = Path.Combine(outputFolder, "dwg-converted-to.pdf");
converter.Convert(outputFile, options);
```
 แทนที่`"Your_Document_Directory"` ด้วยไดเร็กทอรีที่คุณต้องการบันทึกไฟล์ PDF ที่แปลงแล้ว
## ขั้นตอนที่ 4: แสดงข้อความเสร็จสิ้น
เมื่อการแปลงเสร็จสมบูรณ์ คุณสามารถแสดงข้อความเพื่อแจ้งให้ผู้ใช้ทราบเกี่ยวกับตำแหน่งของไฟล์ PDF ที่แปลงแล้ว
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```
ข้อความนี้จะช่วยให้ผู้ใช้ค้นหาไฟล์ที่แปลงแล้วได้อย่างง่ายดาย

## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีแปลงไฟล์ DWG CAD เป็น PDF โดยใช้ GroupDocs.Conversion สำหรับ .NET ด้วยการทำตามขั้นตอนง่ายๆ เหล่านี้ คุณสามารถแปลงไฟล์ DWG ของคุณเป็นรูปแบบ PDF ได้อย่างราบรื่น
## คำถามที่พบบ่อย
### ฉันสามารถแปลงไฟล์ DWG หลายไฟล์พร้อมกันโดยใช้ GroupDocs.Conversion ได้หรือไม่
ใช่ GroupDocs.Conversion รองรับการแปลงเป็นชุด ทำให้คุณสามารถแปลงไฟล์หลายไฟล์ได้ในคราวเดียว
### มีข้อ จำกัด เกี่ยวกับขนาดของไฟล์ DWG สำหรับการแปลงหรือไม่?
GroupDocs.Conversion สามารถจัดการไฟล์ DWG ขนาดใหญ่ได้โดยไม่มีข้อจำกัดใดๆ จึงรับประกันการแปลงที่มีประสิทธิภาพ
### GroupDocs.Conversion จะรักษาการจัดรูปแบบและคุณภาพของไฟล์ DWG ต้นฉบับในระหว่างการแปลงหรือไม่
ใช่ GroupDocs.Conversion รับประกันการแปลงที่มีความแม่นยำสูง โดยรักษาการจัดรูปแบบและคุณภาพของไฟล์ต้นฉบับ
### ฉันสามารถปรับแต่งตัวเลือกการแปลงตามความต้องการของฉันได้หรือไม่?
GroupDocs.Conversion มีตัวเลือกการแปลงที่หลากหลายซึ่งสามารถปรับแต่งให้ตรงตามความต้องการเฉพาะของคุณได้
### มีการสนับสนุนใดบ้างหากฉันประสบปัญหาในระหว่างกระบวนการแปลง?
 ใช่ คุณสามารถขอความช่วยเหลือได้จากฟอรัมชุมชน GroupDocs.Conversion[ที่นี่](https://forum.groupdocs.com/c/conversion/11).