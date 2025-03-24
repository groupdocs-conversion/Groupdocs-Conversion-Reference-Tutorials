---
title: แปลง JPG เป็น PDF
linktitle: แปลง JPG เป็น PDF
second_title: GroupDocs.Conversion .NET API
description: แปลง JPG เป็น PDF ได้อย่างง่ายดายโดยใช้ GroupDocs.Conversion สำหรับ .NET ปฏิบัติตามบทช่วยสอนทีละขั้นตอนนี้เพื่อการแปลงเอกสารที่ราบรื่น
weight: 14
url: /th/net/document-conversion/convert-jpg-to-pdf/
---
## การแนะนำ

คุณต้องการแปลงไฟล์ JPG เป็น PDF ได้อย่างง่ายดายโดยใช้ GroupDocs.Conversion สำหรับ .NET หรือไม่? บทช่วยสอนนี้จะแนะนำคุณตลอดกระบวนการทีละขั้นตอน GroupDocs.Conversion สำหรับ .NET เป็น API ที่มีประสิทธิภาพซึ่งช่วยให้คุณสามารถแปลงรูปแบบเอกสารต่างๆ รวมถึงรูปภาพเป็น PDF ได้อย่างราบรื่น มาดำน้ำกันเถอะ!

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:

1.  GroupDocs.Conversion สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง GroupDocs.Conversion สำหรับ .NET แล้ว คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.groupdocs.com/conversion/net/).
2. สภาพแวดล้อมการพัฒนา: ตั้งค่าสภาพแวดล้อมการพัฒนา เช่น Visual Studio พร้อมด้วย .NET Framework หรือ .NET Core
3. ไฟล์ JPG ตัวอย่าง: เตรียมไฟล์ JPG ตัวอย่างที่คุณต้องการแปลงเป็น PDF

## นำเข้าเนมสเปซ

ขั้นแรก เรามานำเข้าเนมสเปซที่จำเป็น:

```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```

ตอนนี้ เรามาแบ่งกระบวนการแปลงเป็นขั้นตอนง่ายๆ กัน:

## ขั้นตอนที่ 1: กำหนดไดเรกทอรีผลลัพธ์และชื่อไฟล์

```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "jpg-converted-to.pdf");
```

ตรวจสอบให้แน่ใจว่าได้ระบุไดเร็กทอรีที่คุณต้องการบันทึกไฟล์ PDF ที่แปลงแล้วและชื่อไฟล์เอาต์พุตที่ต้องการ

## ขั้นตอนที่ 2: โหลดไฟล์ JPG ต้นฉบับและแปลงเป็น PDF

```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_JPG))
{
    var options = new PdfConvertOptions();
    converter.Convert(outputFile, options);
}
```

 เริ่มต้น`Converter` วัตถุที่มีเส้นทางไปยังไฟล์ JPG ตัวอย่างของคุณ จากนั้น กำหนดค่าตัวเลือกการแปลง เช่น การระบุตัวเลือกการแปลง PDF สุดท้ายโทรหา.`Convert` วิธีการส่งผ่านเส้นทางไฟล์เอาต์พุตและตัวเลือกการแปลง

## ขั้นตอนที่ 3: แสดงข้อความเสร็จสิ้นการแปลง

```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```

หลังจากการแปลงเสร็จสมบูรณ์ ให้แสดงข้อความระบุการแปลงสำเร็จและตำแหน่งของไฟล์ PDF ที่แปลงแล้ว

## บทสรุป

การแปลงไฟล์ JPG เป็น PDF โดยใช้ GroupDocs.Conversion สำหรับ .NET นั้นตรงไปตรงมาโดยใช้โค้ดเพียงไม่กี่บรรทัด เมื่อทำตามบทช่วยสอนนี้ คุณจะสามารถรวมความสามารถในการแปลงเอกสารเข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างราบรื่น

## คำถามที่พบบ่อย

### ถาม: ฉันสามารถแปลงไฟล์ JPG หลายไฟล์เป็น PDF พร้อมกันได้หรือไม่

ตอบ: ได้ คุณสามารถแปลงไฟล์ JPG หลายไฟล์เป็น PDF ได้โดยการวนซ้ำแต่ละไฟล์และดำเนินการตามขั้นตอนการแปลงที่อธิบายไว้ในบทช่วยสอน

### ถาม: GroupDocs.Conversion รองรับรูปแบบรูปภาพอื่นนอกเหนือจาก JPG หรือไม่

ตอบ: ใช่ GroupDocs.Conversion รองรับรูปแบบรูปภาพที่หลากหลาย เช่น PNG, TIFF, BMP และ GIF และอื่นๆ

### ถาม: ฉันสามารถปรับแต่งไฟล์ PDF เอาต์พุตโดยใช้ตัวเลือกการแปลงได้หรือไม่

ตอบ: แน่นอน! GroupDocs.Conversion มีตัวเลือกการแปลงที่หลากหลาย ซึ่งช่วยให้คุณปรับแต่งเอาต์พุต PDF ตามความต้องการของคุณได้

### ถาม: GroupDocs.Conversion สำหรับ .NET มีเวอร์ชันทดลองใช้งานหรือไม่

ตอบ: ได้ คุณสามารถเข้าถึง GroupDocs.Conversion สำหรับ .NET เวอร์ชันทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).

### ถาม: ฉันจะขอความช่วยเหลือได้ที่ไหนหากฉันประสบปัญหาใดๆ ในระหว่างกระบวนการแปลง

 ตอบ: หากคุณพบปัญหาใดๆ หรือมีคำถามเกี่ยวกับ GroupDocs.Conversion สำหรับ .NET โปรดไปที่[ฟอรัม GroupDocs.Conversion](https://forum.groupdocs.com/c/conversion/11) สำหรับความช่วยเหลือ.