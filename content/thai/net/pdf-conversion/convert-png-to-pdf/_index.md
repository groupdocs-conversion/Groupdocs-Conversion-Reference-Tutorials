---
title: แปลง PNG เป็น PDF
linktitle: แปลง PNG เป็น PDF
second_title: GroupDocs.Conversion .NET API
description: แปลงภาพ PNG เป็นเอกสาร PDF ได้อย่างง่ายดายโดยใช้ GroupDocs.Conversion สำหรับ .NET ขั้นตอนง่ายๆ สำหรับการแปลงรูปแบบไฟล์อย่างราบรื่น
type: docs
weight: 20
url: /th/net/pdf-conversion/convert-png-to-pdf/
---
## การแนะนำ
ในยุคดิจิทัลปัจจุบัน การแปลงรูปแบบไฟล์อย่างมีประสิทธิภาพเป็นสิ่งสำคัญสำหรับแอปพลิเคชันต่างๆ ไม่ว่าจะเป็นการจัดการเอกสาร การเก็บถาวร หรือการแชร์ ความสามารถในการแปลงไฟล์จากรูปแบบหนึ่งไปเป็นอีกรูปแบบหนึ่งได้อย่างราบรื่นนั้นมีคุณค่าอย่างยิ่ง ในบทช่วยสอนนี้ เราจะสำรวจวิธีแปลงรูปภาพ PNG เป็นเอกสาร PDF โดยใช้ GroupDocs.Conversion สำหรับ .NET GroupDocs.Conversion เป็น API การแปลงเอกสารอันทรงพลังที่ให้นักพัฒนามีเครื่องมือที่จำเป็นในการแปลงไฟล์ระหว่างรูปแบบต่างๆ ได้อย่างง่ายดาย
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเจาะลึกกระบวนการแปลง ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1.  GroupDocs.Conversion สำหรับ .NET SDK: ดาวน์โหลดและติดตั้ง SDK จาก[หน้าดาวน์โหลด](https://releases.groupdocs.com/conversion/net/)- ปฏิบัติตามคำแนะนำในการติดตั้งที่ให้ไว้เพื่อตั้งค่า SDK ในสภาพแวดล้อมการพัฒนาของคุณ
2. สภาพแวดล้อมการพัฒนา: ตั้งค่าสภาพแวดล้อมการพัฒนา .NET บนเครื่องของคุณ ซึ่งอาจเป็น Visual Studio หรือ IDE อื่นๆ ที่รองรับการพัฒนา .NET
3. ไฟล์ PNG ต้นฉบับ: เตรียมไฟล์รูปภาพ PNG ที่คุณต้องการแปลงเป็น PDF ตรวจสอบให้แน่ใจว่าคุณมีไฟล์ที่จัดเก็บไว้ในไดเร็กทอรีที่แอปพลิเคชัน .NET ของคุณสามารถเข้าถึงได้

## นำเข้าเนมสเปซ
เพื่อเริ่มกระบวนการแปลง ตรวจสอบให้แน่ใจว่าได้นำเข้าเนมสเปซที่จำเป็นลงในแอปพลิเคชัน .NET ของคุณ เนมสเปซเหล่านี้ให้การเข้าถึงฟังก์ชันที่จำเป็นสำหรับการแปลงไฟล์
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```

## ขั้นตอนที่ 1: กำหนดโฟลเดอร์เอาท์พุตและชื่อไฟล์
ขั้นแรก ระบุโฟลเดอร์เอาท์พุตที่จะบันทึกไฟล์ PDF ที่แปลงแล้ว และกำหนดชื่อของไฟล์เอาท์พุต
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "png-converted-to.pdf");
```
 แทนที่`"Your Document Directory"` พร้อมเส้นทางไปยังไดเร็กทอรีที่คุณต้องการบันทึกไฟล์ PDF ที่แปลงแล้ว
## ขั้นตอนที่ 2: โหลดไฟล์ PNG ต้นฉบับ
จากนั้น โหลดไฟล์ PNG ต้นฉบับที่คุณต้องการแปลงเป็น PDF โดยใช้ GroupDocs.Conversion
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PNG))
{
    // รหัสการแปลงจะไปที่นี่
}
```
 แทนที่`Constants.SAMPLE_PNG` พร้อมเส้นทางไปยังไฟล์ PNG ของคุณ
## ขั้นตอนที่ 3: กำหนดค่าตัวเลือกการแปลง
กำหนดค่าตัวเลือกการแปลงตามความต้องการของคุณ ในกรณีนี้ เราจะใช้ PdfConvertOptions ในการแปลง PNG เป็น PDF
```csharp
var options = new PdfConvertOptions();
```
คุณสามารถปรับแต่งตัวเลือกการแปลง เช่น การวางแนวหน้า ระยะขอบ คุณภาพ ฯลฯ ตามความต้องการของคุณ
## ขั้นตอนที่ 4: ทำการแปลง
 ตอนนี้เริ่มต้นกระบวนการแปลงโดยการเรียก`Convert` วิธีการของอ็อบเจ็กต์ Converter และส่งผ่านเส้นทางไฟล์เอาต์พุตพร้อมกับตัวเลือกการแปลง
```csharp
converter.Convert(outputFile, options);
```
วิธีนี้จะแปลงรูปภาพ PNG เป็นเอกสาร PDF และบันทึกลงในเส้นทางไฟล์เอาต์พุตที่ระบุ
## ขั้นตอนที่ 5: แสดงข้อความเสร็จสิ้นการแปลง
สุดท้าย แจ้งให้ผู้ใช้ทราบว่ากระบวนการแปลงเสร็จสมบูรณ์แล้ว และระบุเส้นทางไปยังไฟล์ PDF ที่ส่งออก
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```
ข้อความนี้ช่วยให้แน่ใจว่าผู้ใช้รู้ว่าจะหาไฟล์ PDF ที่แปลงแล้วได้จากที่ไหน

## บทสรุป
โดยสรุป GroupDocs.Conversion สำหรับ .NET มอบโซลูชันที่เรียบง่ายแต่ทรงพลังสำหรับการแปลงภาพ PNG เป็นเอกสาร PDF ได้อย่างราบรื่น ด้วยการทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ คุณสามารถแปลงไฟล์ PNG ของคุณเป็นรูปแบบ PDF ได้อย่างง่ายดาย เปิดโลกแห่งความเป็นไปได้ในการจัดการและแบ่งปันเอกสาร
## คำถามที่พบบ่อย
### GroupDocs.Conversion เข้ากันได้กับรูปแบบไฟล์อื่นนอกเหนือจาก PNG และ PDF หรือไม่
 ใช่ GroupDocs.Conversion รองรับรูปแบบไฟล์ที่หลากหลายสำหรับการแปลง รวมถึง DOCX, XLSX, PPTX, JPG, TIFF และอื่นๆ อ้างถึง[เอกสารประกอบ](https://reference.groupdocs.com/conversion/net/) สำหรับรายการรูปแบบที่รองรับทั้งหมด
### ฉันสามารถปรับแต่งการตั้งค่าการแปลงตามความต้องการเฉพาะของฉันได้หรือไม่?
อย่างแน่นอน! GroupDocs.Conversion นำเสนอตัวเลือกการปรับแต่งที่ครอบคลุม ซึ่งช่วยให้คุณปรับแต่งกระบวนการแปลงให้ตรงตามความต้องการของคุณได้ คุณสามารถปรับพารามิเตอร์ต่างๆ เช่น ขนาดหน้า การวางแนว คุณภาพ และอื่นๆ ได้
### GroupDocs.Conversion เหมาะสำหรับงานแปลงเอกสารขนาดใหญ่หรือไม่
ใช่ GroupDocs.Conversion ได้รับการออกแบบมาเพื่อจัดการงานการแปลงเอกสารขนาดใหญ่อย่างมีประสิทธิภาพ สถาปัตยกรรมที่แข็งแกร่งช่วยให้มั่นใจถึงประสิทธิภาพและความน่าเชื่อถือสูงสุดแม้ว่าจะต้องจัดการกับไฟล์จำนวนมากก็ตาม
### GroupDocs.Conversion ให้การสนับสนุนและช่วยเหลือนักพัฒนาหรือไม่
 ใช่ GroupDocs ให้การสนับสนุนอย่างครอบคลุมแก่นักพัฒนาผ่านทางบริการเฉพาะของตน[ฟอรั่ม](https://forum.groupdocs.com/c/conversion/11) ซึ่งคุณสามารถถามคำถาม ขอคำแนะนำ และโต้ตอบกับนักพัฒนาคนอื่นๆ
### ฉันสามารถลองใช้ GroupDocs.Conversion ก่อนตัดสินใจซื้อได้หรือไม่
 อย่างแน่นอน! คุณสามารถทดลองใช้ GroupDocs.Conversion ฟรีได้โดยไปที่[เว็บไซต์](https://releases.groupdocs.com/) และดาวน์โหลดเวอร์ชันทดลอง สิ่งนี้ช่วยให้คุณสำรวจคุณสมบัติและฟังก์ชันการทำงานก่อนตัดสินใจ