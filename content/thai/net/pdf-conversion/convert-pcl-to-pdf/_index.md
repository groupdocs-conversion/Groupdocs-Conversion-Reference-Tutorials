---
title: แปลง PCL เป็น PDF
linktitle: แปลง PCL เป็น PDF
second_title: GroupDocs.Conversion .NET API
description: เรียนรู้วิธีแปลงไฟล์ PCL เป็น PDF ได้อย่างง่ายดายโดยใช้ GroupDocs.Conversion สำหรับ .NET ปฏิบัติตามคำแนะนำทีละขั้นตอนของเรา
weight: 18
url: /th/net/pdf-conversion/convert-pcl-to-pdf/
---

# แปลง PCL เป็น PDF

## การแนะนำ
ในบทช่วยสอนนี้ เราจะแนะนำคุณตลอดขั้นตอนการแปลงไฟล์ PCL (Printer Command Language) เป็น PDF โดยใช้ GroupDocs.Conversion สำหรับ .NET ทำตามขั้นตอนด้านล่างเพื่อให้บรรลุการแปลงนี้ได้อย่างราบรื่น
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
1. GroupDocs.Conversion สำหรับไลบรารี .NET: ตรวจสอบให้แน่ใจว่าคุณได้ดาวน์โหลดและติดตั้งไลบรารี GroupDocs.Conversion สำหรับ .NET แล้ว คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.groupdocs.com/conversion/net/).
2. การเข้าถึงไฟล์ PCL: คุณควรมีไฟล์ PCL ที่คุณต้องการแปลงเป็น PDF
3. สภาพแวดล้อมการพัฒนา: ตั้งค่าสภาพแวดล้อมการพัฒนาของคุณด้วย .NET Framework หรือ .NET Core

## นำเข้าเนมสเปซ
ขั้นแรก คุณต้องนำเข้าเนมสเปซที่จำเป็นไปยังโปรเจ็กต์ของคุณ เนมสเปซเหล่านี้ประกอบด้วย:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## ขั้นตอนที่ 1: โหลดไฟล์ Source PCL
เริ่มต้นด้วยการโหลดไฟล์ PCL ต้นทางที่คุณต้องการแปลง คุณสามารถทำได้โดยการระบุเส้นทางไปยังไฟล์ PCL ของคุณ
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "pcl-converted-to.pdf");
// โหลดไฟล์ PCL ต้นทาง
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PCL))
{
```
## ขั้นตอนที่ 2: ระบุตัวเลือกการแปลง
 ถัดไป ระบุตัวเลือกการแปลง ในกรณีนี้ เรากำลังแปลงเป็น PDF ดังนั้นให้สร้างอินสแตนซ์ของ`PdfConvertOptions`.
```csharp
	var options = new PdfConvertOptions();
```
## ขั้นตอนที่ 3: ทำการแปลง
 ทำการแปลงจริงจาก PCL เป็น PDF โดยการเรียก`Convert` วิธีการของวัตถุตัวแปลงและส่งผ่านเส้นทางไฟล์เอาต์พุตและตัวเลือกการแปลง
```csharp
	// บันทึกไฟล์ PDF ที่แปลงแล้ว
	converter.Convert(outputFile, options);
```
## ขั้นตอนที่ 4: ตรวจสอบความสมบูรณ์ของการแปลง
สุดท้าย เมื่อการแปลงเสร็จสมบูรณ์แล้ว ให้แสดงข้อความแจ้งว่าเสร็จสิ้นพร้อมกับเส้นทางโฟลเดอร์เอาท์พุต
```csharp
	Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
}
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้อธิบายขั้นตอนการแปลงไฟล์ PCL เป็น PDF โดยใช้ GroupDocs.Conversion สำหรับ .NET แล้ว ด้วยการทำตามขั้นตอนที่อธิบายไว้ข้างต้น คุณสามารถแปลงเอกสาร PCL ของคุณเป็นรูปแบบ PDF ได้อย่างราบรื่น ช่วยให้เข้าถึงและแบ่งปันได้ง่ายขึ้น
## คำถามที่พบบ่อย
### GroupDocs.Conversion สำหรับ .NET เข้ากันได้กับ .NET ทุกเวอร์ชันหรือไม่
ใช่ GroupDocs.Conversion สำหรับ .NET เข้ากันได้กับทั้ง .NET Framework และ .NET Core
### ฉันสามารถแปลงไฟล์ PCL หลายไฟล์พร้อมกันโดยใช้ไลบรารีนี้ได้หรือไม่
ได้ คุณสามารถแปลงไฟล์ PCL หลายไฟล์เป็น PDF หรือรูปแบบอื่นๆ ที่รองรับเป็นชุดได้
### GroupDocs.Conversion สำหรับ .NET ต้องใช้อินเทอร์เน็ตในการแปลงหรือไม่
ไม่ GroupDocs.Conversion สำหรับ .NET ดำเนินการแปลงทั้งหมดภายในเครื่องโดยไม่ต้องใช้อินเทอร์เน็ต
### มีรุ่นทดลองให้ทดสอบก่อนซื้อหรือไม่?
 ใช่ คุณสามารถดาวน์โหลดเวอร์ชันทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนหรือขอความช่วยเหลือสำหรับปัญหาใดๆ ที่เกี่ยวข้องกับ GroupDocs.Conversion สำหรับ .NET ได้ที่ไหน
 คุณสามารถเยี่ยมชมฟอรัม GroupDocs.Conversion[ที่นี่](https://forum.groupdocs.com/c/conversion/11) สำหรับการสนับสนุนและความช่วยเหลือ