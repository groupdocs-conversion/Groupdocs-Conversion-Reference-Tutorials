---
"description": "แปลง JPG เป็น PDF ได้อย่างง่ายดายโดยใช้ GroupDocs.Conversion สำหรับ .NET ทำตามบทช่วยสอนทีละขั้นตอนนี้เพื่อการแปลงเอกสารอย่างราบรื่น"
"linktitle": "แปลง JPG เป็น PDF"
"second_title": "API การแปลง GroupDocs .NET"
"title": "แปลง JPG เป็น PDF"
"url": "/th/net/document-conversion/convert-jpg-to-pdf/"
"weight": 14
---

# แปลง JPG เป็น PDF

## การแนะนำ

คุณกำลังมองหาวิธีแปลงไฟล์ JPG เป็น PDF โดยไม่ต้องใช้ความพยายามใดๆ โดยใช้ GroupDocs.Conversion สำหรับ .NET หรือไม่ บทช่วยสอนนี้จะแนะนำคุณตลอดขั้นตอนต่างๆ GroupDocs.Conversion สำหรับ .NET เป็น API ที่มีประสิทธิภาพที่ช่วยให้คุณแปลงเอกสารในรูปแบบต่างๆ รวมถึงรูปภาพเป็น PDF ได้อย่างราบรื่นและง่ายดาย มาเริ่มกันเลย!

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม ให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:

1. GroupDocs.Conversion สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง GroupDocs.Conversion สำหรับ .NET แล้ว คุณสามารถดาวน์โหลดได้จาก [ที่นี่](https://releases-groupdocs.com/conversion/net/).
2. สภาพแวดล้อมการพัฒนา: มีการตั้งค่าสภาพแวดล้อมการพัฒนา เช่น Visual Studio ร่วมกับ .NET Framework หรือ .NET Core
3. ไฟล์ตัวอย่าง JPG: เตรียมไฟล์ตัวอย่าง JPG ที่คุณต้องการแปลงเป็น PDF

## นำเข้าเนมสเปซ

ก่อนอื่นให้เราทำการนำเข้าเนมสเปซที่จำเป็น:

```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```

ตอนนี้เรามาแบ่งกระบวนการแปลงเป็นขั้นตอนง่าย ๆ กัน:

## ขั้นตอนที่ 1: กำหนดไดเรกทอรีเอาต์พุตและชื่อไฟล์

```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "jpg-converted-to.pdf");
```

ตรวจสอบให้แน่ใจว่าระบุไดเร็กทอรีที่คุณต้องการบันทึกไฟล์ PDF ที่แปลงแล้ว และชื่อไฟล์เอาท์พุตที่ต้องการ

## ขั้นตอนที่ 2: โหลดไฟล์ JPG ต้นฉบับและแปลงเป็น PDF

```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_JPG))
{
    var options = new PdfConvertOptions();
    converter.Convert(outputFile, options);
}
```

เริ่มต้นการใช้งาน `Converter` วัตถุที่มีเส้นทางไปยังไฟล์ JPG ตัวอย่างของคุณ จากนั้นกำหนดค่าตัวเลือกการแปลง เช่น ระบุตัวเลือกการแปลง PDF สุดท้าย เรียกใช้ `Convert` วิธีการส่งเส้นทางไฟล์เอาท์พุตและตัวเลือกการแปลง

## ขั้นตอนที่ 3: แสดงข้อความเสร็จสิ้นการแปลง

```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```

หลังจากการแปลงเสร็จสิ้นแล้ว แสดงข้อความแจ้งการแปลงสำเร็จและตำแหน่งของไฟล์ PDF ที่ถูกแปลง

## บทสรุป

การแปลงไฟล์ JPG เป็น PDF โดยใช้ GroupDocs.Conversion สำหรับ .NET นั้นทำได้ง่าย ๆ ด้วยโค้ดเพียงไม่กี่บรรทัด เมื่อทำตามบทช่วยสอนนี้แล้ว คุณจะสามารถผสานรวมความสามารถในการแปลงเอกสารเข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างราบรื่น

## คำถามที่พบบ่อย

### ถาม: ฉันสามารถแปลงไฟล์ JPG หลายไฟล์เป็น PDF พร้อมกันได้หรือเปล่า?

A: ใช่ คุณสามารถแปลงไฟล์ JPG หลายไฟล์เป็น PDF ได้โดยการทำซ้ำในแต่ละไฟล์และดำเนินการแปลงตามที่อธิบายไว้ในบทช่วยสอน

### ถาม: GroupDocs.Conversion รองรับรูปแบบรูปภาพอื่นนอกเหนือจาก JPG หรือไม่

ตอบ ใช่ GroupDocs.Conversion รองรับรูปแบบรูปภาพต่างๆ เช่น PNG, TIFF, BMP และ GIF เป็นต้น

### ถาม: ฉันสามารถปรับแต่งไฟล์ PDF เอาท์พุตโดยใช้ตัวเลือกการแปลงได้หรือไม่

A: แน่นอน! GroupDocs.Conversion มีตัวเลือกการแปลงข้อมูลมากมาย ช่วยให้คุณปรับแต่งผลลัพธ์ PDF ตามความต้องการของคุณได้

### ถาม: มีเวอร์ชันทดลองใช้งานสำหรับ GroupDocs.Conversion สำหรับ .NET หรือไม่

A: ใช่ คุณสามารถเข้าถึงรุ่นทดลองใช้งานฟรีของ GroupDocs.Conversion สำหรับ .NET ได้จาก [ที่นี่](https://releases-groupdocs.com/).

### ถาม: ฉันสามารถขอความช่วยเหลือได้ที่ไหน หากพบปัญหาใดๆ ระหว่างขั้นตอนการแปลง

A: หากคุณพบปัญหาหรือมีคำถามเกี่ยวกับ GroupDocs.Conversion สำหรับ .NET โปรดเยี่ยมชม [ฟอรั่ม GroupDocs.Conversion](https://forum.groupdocs.com/c/conversion/11) เพื่อขอความช่วยเหลือ