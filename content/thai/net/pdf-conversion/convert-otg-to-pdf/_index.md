---
title: แปลง OTG เป็น PDF
linktitle: แปลง OTG เป็น PDF
second_title: GroupDocs.Conversion .NET API
description: เรียนรู้วิธีแปลงไฟล์ OTG เป็น PDF โดยใช้ GroupDocs.Conversion สำหรับ .NET การบูรณาการที่เรียบง่าย มีประสิทธิภาพ และราบรื่นสำหรับโครงการของคุณ
type: docs
weight: 13
url: /th/net/pdf-conversion/convert-otg-to-pdf/
---
## การแนะนำ
การแปลงไฟล์ OTG (OpenDocument Graphics) เป็นรูปแบบ PDF อาจเป็นงานที่สำคัญ โดยเฉพาะอย่างยิ่งเมื่อต้องจัดการกับระบบการจัดการเอกสาร หรือการแชร์ไฟล์บนแพลตฟอร์มต่างๆ ในบทช่วยสอนนี้ เราจะแนะนำคุณตลอดขั้นตอนการแปลงไฟล์ OTG เป็น PDF โดยใช้ไลบรารี GroupDocs.Conversion สำหรับ .NET มาดำน้ำกันเถอะ!
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
1. GroupDocs.Conversion สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งไลบรารี GroupDocs.Conversion สำหรับ .NET คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.groupdocs.com/conversion/net/).
2. ไฟล์ OTG: เตรียมไฟล์ OTG ที่คุณต้องการแปลงเป็น PDF ให้พร้อมในไดเร็กทอรีเอกสารของคุณ

## นำเข้าเนมสเปซ
ขั้นแรก คุณต้องนำเข้าเนมสเปซที่จำเป็นไปยังโปรเจ็กต์ .NET ของคุณ 
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## ขั้นตอนที่ 1: ตั้งค่าไดเร็กทอรีเอาต์พุตและชื่อไฟล์
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "otg-converted-to.pdf");
```
 ในขั้นตอนนี้ คุณจะกำหนดไดเร็กทอรีเอาต์พุตที่จะบันทึกไฟล์ PDF ที่แปลงแล้ว แทนที่`"Your Document Directory"` พร้อมเส้นทางไปยังไดเร็กทอรีเอาต์พุตที่คุณต้องการ
## ขั้นตอนที่ 2: โหลดไฟล์ OTG ต้นทางและแปลงเป็น PDF
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_OTG))
{
    var options = new PdfConvertOptions();
    // บันทึกไฟล์ PDF ที่แปลงแล้ว
    converter.Convert(outputFile, options);
}
```
 ที่นี่เรายกตัวอย่างใหม่`Converter` วัตถุจากไลบรารี GroupDocs.Conversion โดยส่งผ่านเส้นทางของไฟล์ OTG ต้นทาง จากนั้นเราก็สร้าง`PdfConvertOptions` เพื่อระบุตัวเลือกการแปลง ในที่สุดเราก็เรียกว่า`Convert` วิธีแปลงไฟล์ OTG เป็นรูปแบบ PDF
## ขั้นตอนที่ 3: ตรวจสอบความสมบูรณ์ของการแปลง
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
ขั้นตอนนี้จะแจ้งให้ผู้ใช้ทราบว่ากระบวนการแปลงเสร็จสมบูรณ์ และระบุเส้นทางในการบันทึกไฟล์ PDF ที่แปลงแล้ว

## บทสรุป
การแปลงไฟล์ OTG เป็นรูปแบบ PDF ทำได้ง่ายด้วยไลบรารี GroupDocs.Conversion สำหรับ .NET ด้วยการทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ คุณสามารถรวมฟังก์ชันการทำงานนี้เข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างราบรื่น ช่วยเพิ่มความสามารถในการทำงานร่วมกันและการเข้าถึงเอกสาร
## คำถามที่พบบ่อย
### GroupDocs.Conversion สามารถแปลงไฟล์รูปแบบอื่นนอกเหนือจาก OTG เป็น PDF ได้หรือไม่
ใช่ GroupDocs.Conversion รองรับรูปแบบไฟล์ที่หลากหลายสำหรับการแปลง รวมถึง DOCX, XLSX, PPTX, HTML และอื่นๆ
### GroupDocs.Conversion เหมาะสำหรับใช้ในเชิงพาณิชย์หรือไม่
อย่างแน่นอน! GroupDocs.Conversion นำเสนอใบอนุญาตเชิงพาณิชย์สำหรับธุรกิจและองค์กรที่ต้องการใช้ประโยชน์จากความสามารถในการแปลงเอกสารอันทรงพลัง
### GroupDocs.Conversion ให้การสนับสนุนทางเทคนิคหรือไม่
ใช่ GroupDocs ให้การสนับสนุนทางเทคนิคโดยเฉพาะเพื่อช่วยเหลือผู้ใช้ในการสอบถามหรือปัญหาใดๆ ที่อาจพบระหว่างการใช้งาน
### ฉันสามารถลองใช้ GroupDocs.Conversion ก่อนซื้อใบอนุญาตได้หรือไม่
ใช่ คุณสามารถใช้ GroupDocs.Conversion รุ่นทดลองใช้ฟรีเพื่อสำรวจคุณสมบัติและความเข้ากันได้กับความต้องการของคุณ
### ฉันจะขอรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Conversion ได้อย่างไร
คุณสามารถขอรับใบอนุญาตชั่วคราวจาก GroupDocs เพื่อวัตถุประสงค์ในการประเมินหรือโครงการระยะสั้นได้โดยไปที่ใบอนุญาตชั่วคราว[ใบอนุญาต](https://purchase.groupdocs.com/temporary-license/).