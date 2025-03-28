---
title: แปลง MHT เป็น PDF
linktitle: แปลง MHT เป็น PDF
second_title: GroupDocs.Conversion .NET API
description: แปลงไฟล์ MHT เป็น PDF ได้อย่างง่ายดายโดยใช้ GroupDocs.Conversion สำหรับ .NET ปฏิบัติตามคำแนะนำทีละขั้นตอนของเราเพื่อการผสานรวมเข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างราบรื่น
weight: 21
url: /th/net/document-conversion/convert-mht-to-pdf/
---

# แปลง MHT เป็น PDF

## การแนะนำ
ในโลกของการพัฒนา .NET การแปลงไฟล์จากรูปแบบหนึ่งไปเป็นอีกรูปแบบหนึ่งถือเป็นงานทั่วไป ไม่ว่าคุณจะจัดการกับเอกสาร รูปภาพ หรือไฟล์ประเภทอื่นๆ ความสามารถในการแปลงระหว่างรูปแบบต่างๆ ได้อย่างราบรื่นนั้นมีคุณค่าอย่างเหลือเชื่อ เครื่องมืออันทรงพลังอย่างหนึ่งที่เปิดใช้งานฟังก์ชันนี้คือ GroupDocs.Conversion สำหรับ .NET
ในบทช่วยสอนนี้ เราจะเน้นไปที่งานการแปลงงานหนึ่ง: การแปลงไฟล์ MHT (MIME HTML) เป็น PDF (Portable Document Format) โดยใช้ GroupDocs.Conversion สำหรับ .NET เราจะอธิบายกระบวนการทีละขั้นตอน โดยแบ่งแต่ละตัวอย่างออกเป็นส่วนๆ ที่สามารถจัดการได้เพื่อให้แน่ใจว่ามีความเข้าใจที่ชัดเจน
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเจาะลึกบทช่วยสอน ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1.  GroupDocs.Conversion สำหรับ .NET Library: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งไลบรารี GroupDocs.Conversion สำหรับ .NET ในสภาพแวดล้อมการพัฒนาของคุณ คุณสามารถดาวน์โหลดได้จาก[เว็บไซต์](https://releases.groupdocs.com/conversion/net/).
2. สภาพแวดล้อมการพัฒนา .NET: คุณจะต้องมีสภาพแวดล้อมการทำงานสำหรับการพัฒนา .NET รวมถึง Visual Studio หรือ IDE อื่นๆ ที่คุณเลือก
3. ความเข้าใจพื้นฐานของ C#: บทช่วยสอนนี้ถือว่าคุณมีความเข้าใจพื้นฐานเกี่ยวกับภาษาการเขียนโปรแกรม C#
4. ไฟล์ MHT ตัวอย่าง: เตรียมไฟล์ MHT ตัวอย่างที่คุณจะใช้สำหรับการแปลง คุณสามารถใช้ไฟล์ MHT ใดก็ได้เพื่อการทดสอบ

## นำเข้าเนมสเปซ
เพื่อเริ่มต้นกระบวนการแปลง คุณต้องนำเข้าเนมสเปซที่จำเป็นลงในโค้ด C# ของคุณ เนมสเปซเหล่านี้ให้การเข้าถึงฟังก์ชันที่จำเป็นสำหรับการแปลงไฟล์
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## ขั้นตอนที่ 1: กำหนดตำแหน่งไฟล์เอาท์พุต
ขั้นแรก กำหนดตำแหน่งที่คุณต้องการบันทึกไฟล์ PDF ที่แปลงแล้ว นี่จะเป็นไดเร็กทอรีที่เก็บเอกสารของคุณ
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "mht-converted-to.pdf");
```
 แทนที่`"Your Document Directory"` พร้อมเส้นทางไปยังไดเร็กทอรีเอาต์พุตที่คุณต้องการ
## ขั้นตอนที่ 2: โหลดไฟล์ MHT ต้นทาง
ถัดไป คุณต้องโหลดไฟล์ MHT ต้นทางที่คุณต้องการแปลง ขั้นตอนนี้จะเตรียมใช้งานตัวแปลง GroupDocs.Conversion ด้วยไฟล์ MHT ที่ระบุ
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_MHT))
{
    // รหัสการแปลงจะไปที่นี่
}
```
ตรวจสอบให้แน่ใจว่าได้เปลี่ยน`Constants.SAMPLE_MHT` พร้อมเส้นทางไปยังไฟล์ MHT ของคุณ
## ขั้นตอนที่ 3: ตั้งค่าตัวเลือกการแปลง
 ในขั้นตอนนี้ คุณจะต้องตั้งค่าตัวเลือกการแปลง สำหรับการแปลง MHT เป็น PDF คุณจะใช้`PdfConvertOptions`.
```csharp
var options = new PdfConvertOptions();
```
## ขั้นตอนที่ 4: ทำการแปลง
 ตอนนี้ได้เวลาทำการแปลงจริงจาก MHT เป็น PDF แล้ว ใช้`Convert()` วิธีการของวัตถุตัวแปลงและส่งเส้นทางไฟล์เอาต์พุตพร้อมกับตัวเลือกการแปลง
```csharp
converter.Convert(outputFile, options);
```
## ขั้นตอนที่ 5: แสดงข้อความแสดงความสำเร็จ
สุดท้าย แสดงข้อความแสดงความสำเร็จที่ระบุว่ากระบวนการแปลงเสร็จสมบูรณ์แล้ว
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้กล่าวถึงกระบวนการแปลงไฟล์ MHT เป็น PDF โดยใช้ GroupDocs.Conversion สำหรับ .NET ด้วยการทำตามคำแนะนำทีละขั้นตอนและใช้ส่วนย่อยของโค้ดที่ให้มา คุณจะสามารถรวมฟังก์ชันการแปลงไฟล์เข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างราบรื่น
## คำถามที่พบบ่อย
### ฉันสามารถแปลงไฟล์ MHT หลายไฟล์พร้อมกันโดยใช้ GroupDocs.Conversion สำหรับ .NET ได้หรือไม่
ได้ คุณสามารถแปลงไฟล์ MHT หลายไฟล์เป็น PDF หรือรูปแบบอื่นที่รองรับเป็นชุดได้โดยใช้ GroupDocs.Conversion สำหรับ .NET
### GroupDocs.Conversion สำหรับ .NET รองรับการแปลงเป็นรูปแบบอื่นที่ไม่ใช่ PDF หรือไม่
ใช่ GroupDocs.Conversion สำหรับ .NET รองรับการแปลงเป็นรูปแบบต่างๆ รวมถึง DOCX, XLSX, PPTX, JPG และอื่นๆ
### GroupDocs.Conversion สำหรับ .NET เข้ากันได้กับ .NET Core หรือไม่
ใช่ GroupDocs.Conversion สำหรับ .NET เข้ากันได้กับทั้ง .NET Framework และ .NET Core
### ฉันสามารถปรับแต่งตัวเลือกการแปลง เช่น คุณภาพและความละเอียดได้หรือไม่
ใช่ GroupDocs.Conversion สำหรับ .NET มีตัวเลือกมากมายสำหรับกำหนดการตั้งค่าการแปลงตามความต้องการของคุณ
### มีการทดลองใช้ GroupDocs.Conversion สำหรับ .NET ฟรีหรือไม่
 ใช่ คุณสามารถทดลองใช้ GroupDocs.Conversion สำหรับ .NET ได้ฟรีจาก[เว็บไซต์](https://releases.groupdocs.com/).