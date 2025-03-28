---
title: แปลงเว็บเพจ HTML เป็น PDF
linktitle: แปลงเว็บเพจ HTML เป็น PDF
second_title: GroupDocs.Conversion .NET API
description: แปลงหน้าเว็บ HTML เป็นรูปแบบ PDF ได้อย่างง่ายดายโดยใช้ GroupDocs.Conversion สำหรับ .NET ปฏิบัติตามคำแนะนำทีละขั้นตอนของเราเพื่อการแปลงรูปแบบเอกสารที่ราบรื่น
weight: 22
url: /th/net/convert-files-to-pdf/convert-html-to-pdf/
---

# แปลงเว็บเพจ HTML เป็น PDF

## การแนะนำ
ในยุคดิจิทัลปัจจุบัน ความสามารถในการแปลงรูปแบบเอกสารต่างๆ ได้อย่างราบรื่นถือเป็นสิ่งสำคัญสำหรับธุรกิจและบุคคลทั่วไป ไม่ว่าจะเป็นการแปลงหน้าเว็บ HTML เป็น PDF เพื่อการแชร์หรือการเก็บถาวรที่ง่ายดาย การมีเครื่องมือที่เหมาะสมสามารถสร้างความแตกต่างได้ ในบทช่วยสอนนี้ เราจะสำรวจวิธีใช้ GroupDocs.Conversion สำหรับ .NET เพื่อแปลงหน้าเว็บ HTML เป็นรูปแบบ PDF ได้อย่างมีประสิทธิภาพ
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเจาะลึกบทช่วยสอน ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1.  การติดตั้ง: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง GroupDocs.Conversion สำหรับ .NET ในสภาพแวดล้อมการพัฒนาของคุณ คุณสามารถดาวน์โหลดไฟล์ที่จำเป็นได้จาก[ลิ้งค์ดาวน์โหลด](https://releases.groupdocs.com/conversion/net/).
2. ไฟล์ HTML ตัวอย่าง: เตรียมไฟล์ HTML ตัวอย่างที่คุณต้องการแปลงเป็น PDF ให้พร้อม สิ่งนี้จะทำหน้าที่เป็นไฟล์ต้นฉบับสำหรับการแปลง
3. สภาพแวดล้อม .NET: ความคุ้นเคยขั้นพื้นฐานกับการพัฒนา .NET และการใช้ไลบรารีผ่านแพ็คเกจ NuGet

## นำเข้าเนมสเปซ
ก่อนที่เราจะเริ่มกระบวนการแปลง เรามานำเข้าเนมสเปซที่จำเป็นก่อน:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```

## ขั้นตอนที่ 1: กำหนดโฟลเดอร์เอาท์พุตและเส้นทางไฟล์
ขั้นแรก ระบุโฟลเดอร์เอาท์พุตที่คุณต้องการบันทึกไฟล์ PDF ที่แปลงแล้ว คุณสามารถเลือกไดเร็กทอรีใดก็ได้ในระบบของคุณ
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "html-converted-to.pdf");
```
## ขั้นตอนที่ 2: โหลดไฟล์ HTML ต้นฉบับ
จากนั้น โหลดไฟล์ HTML ต้นฉบับที่คุณต้องการแปลงเป็น PDF โดยใช้คลาส Converter ของ GroupDocs.Conversion
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_HTML))
```
## ขั้นตอนที่ 3: กำหนดค่าตัวเลือกการแปลง
กำหนดค่าตัวเลือกการแปลงตามความต้องการของคุณ ในกรณีนี้ เราจะใช้ PdfConvertOptions ในการแปลง HTML เป็น PDF
```csharp
var options = new PdfConvertOptions();
```
## ขั้นตอนที่ 4: ทำการแปลง
ตอนนี้ ทำการแปลงจริงโดยการเรียกเมธอด Convert ของคลาส Converter และส่งเส้นทางไฟล์เอาต์พุตและตัวเลือกการแปลง
```csharp
converter.Convert(outputFile, options);
```
## ขั้นตอนที่ 5: แสดงข้อความแสดงความสำเร็จ
สุดท้ายนี้ แจ้งให้ผู้ใช้ทราบว่ากระบวนการแปลงเสร็จสมบูรณ์แล้ว และระบุเส้นทางในการบันทึกไฟล์ PDF ที่แปลงแล้ว
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```

## บทสรุป
ด้วย GroupDocs.Conversion สำหรับ .NET การแปลงหน้าเว็บ HTML เป็นรูปแบบ PDF กลายเป็นเรื่องง่าย ด้วยการทำตามขั้นตอนง่ายๆ ที่อธิบายไว้ในบทช่วยสอนนี้ คุณสามารถจัดการการแปลงรูปแบบเอกสารในแอปพลิเคชัน .NET ของคุณได้อย่างมีประสิทธิภาพ
## คำถามที่พบบ่อย
### GroupDocs.Conversion สำหรับ .NET เข้ากันได้กับ .NET ทุกเวอร์ชันหรือไม่
ใช่ GroupDocs.Conversion สำหรับ .NET เข้ากันได้กับ .NET Framework 4.6 และเวอร์ชันที่ใหม่กว่า
### ฉันสามารถแปลงไฟล์ HTML หลายไฟล์เป็น PDF พร้อมกันได้หรือไม่
อย่างแน่นอน! คุณสามารถวนซ้ำรายการไฟล์ HTML และทำการแปลงไฟล์แต่ละไฟล์ทีละไฟล์ได้
### GroupDocs.Conversion รองรับการแปลงเป็นรูปแบบอื่นนอกเหนือจาก PDF หรือไม่
ใช่ GroupDocs.Conversion รองรับรูปแบบเอกสารที่หลากหลายสำหรับการแปลง รวมถึง DOCX, XLSX, PPTX และอื่นๆ
### มีรุ่นทดลองใช้สำหรับ GroupDocs.Conversion สำหรับ .NET หรือไม่
 ใช่ คุณสามารถดาวน์โหลดเวอร์ชันทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนได้ที่ไหนหากฉันพบปัญหาใดๆ ระหว่างการใช้งาน
 คุณสามารถขอความช่วยเหลือได้จากฟอรัมชุมชน GroupDocs.Conversion[ที่นี่](https://forum.groupdocs.com/c/conversion/11).