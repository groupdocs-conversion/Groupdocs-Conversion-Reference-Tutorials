---
title: แปลง XLSM เป็น PDF
linktitle: แปลง XLSM เป็น PDF
second_title: GroupDocs.Conversion .NET API
description: เรียนรู้วิธีแปลงไฟล์ XLSM เป็นรูปแบบ PDF ได้อย่างง่ายดายโดยใช้ GroupDocs.Conversion สำหรับ .NET รวมคำแนะนำทีละขั้นตอน
weight: 23
url: /th/net/converting-file-types-to-pdf/convert-xlsm-to-pdf/
---

# แปลง XLSM เป็น PDF

## การแนะนำ
ในบทช่วยสอนนี้ เราจะเจาะลึกกระบวนการแปลงไฟล์ XLSM เป็นรูปแบบ PDF โดยใช้ GroupDocs.Conversion สำหรับไลบรารี .NET อันทรงพลัง การแปลงไฟล์เป็นงานทั่วไปในหลายๆ แอปพลิเคชัน และ GroupDocs.Conversion ช่วยให้กระบวนการนี้ง่ายขึ้น โดยนำเสนอความสามารถในการแปลงที่มีประสิทธิภาพและเชื่อถือได้
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
### 1. ติดตั้ง GroupDocs.Conversion สำหรับ .NET
คุณสามารถดาวน์โหลดไลบรารี GroupDocs.Conversion สำหรับ .NET ได้จากเว็บไซต์[ดาวน์โหลดได้ที่นี่](https://releases.groupdocs.com/conversion/net/)
### 2. รับใบอนุญาตหรือใช้ใบอนุญาตชั่วคราว
 หากต้องการใช้ GroupDocs.Conversion สำหรับ .NET คุณต้องมีใบอนุญาตที่ถูกต้อง หากคุณไม่มี คุณสามารถขอรับใบอนุญาตชั่วคราวเพื่อการทดสอบได้[รับใบอนุญาตชั่วคราว](https://purchase.groupdocs.com/temporary-license/)
### 3. ตั้งค่าสภาพแวดล้อมการพัฒนาของคุณ
ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าสภาพแวดล้อมการพัฒนาสำหรับการเขียนโปรแกรม .NET คุณสามารถใช้ Visual Studio หรือ IDE ที่ต้องการอื่นๆ ได้

## นำเข้าเนมสเปซ
ขั้นแรก เรามานำเข้าเนมสเปซที่จำเป็นเข้าสู่โปรเจ็กต์ของเรา:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```

ตอนนี้ เรามาแบ่งกระบวนการแปลงออกเป็นหลายขั้นตอน:
## ขั้นตอนที่ 1: กำหนดโฟลเดอร์เอาท์พุตและเส้นทางไฟล์
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "xlsm-converted-to.pdf");
```
 ให้แน่ใจว่าจะเปลี่ยน`"Your Document Directory"` ด้วยเส้นทางไดเรกทอรีที่คุณต้องการบันทึกไฟล์ PDF ที่แปลงแล้ว
## ขั้นตอนที่ 2: โหลดไฟล์ Source XLSM
```csharp
using (var converter = new GroupDocs.Conversion.Converter("Path_to_your_XLSM_file"))
{
	// ตรรกะการแปลงจะไปที่นี่
}
```
 แทนที่`"Path_to_your_XLSM_file"` ด้วยเส้นทางจริงไปยังไฟล์ XLSM ของคุณ
## ขั้นตอนที่ 3: บันทึกไฟล์ PDF ที่แปลงแล้ว
หลังจากตั้งค่าตัวเลือกการแปลงแล้ว ให้บันทึกไฟล์ PDF ที่แปลงแล้วไปยังเส้นทางเอาต์พุตที่ระบุ
```csharp
// ตัวเลือกการแปลง
var options = new PdfConvertOptions();

// ดำเนินการแปลง
converter.Convert(outputFile, options);
```
## ขั้นตอนที่ 4: แสดงข้อความเสร็จสิ้นการแปลง
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```
ขั้นตอนนี้จะแจ้งให้ผู้ใช้ทราบเกี่ยวกับความสำเร็จของกระบวนการแปลง และระบุตำแหน่งที่สามารถพบไฟล์ PDF ที่แปลงแล้วได้

## บทสรุป
การแปลงไฟล์ XLSM เป็นรูปแบบ PDF เป็นกระบวนการที่ไม่ซับซ้อนด้วย GroupDocs.Conversion สำหรับ .NET ด้วยการทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ คุณสามารถรวมฟังก์ชันการแปลงไฟล์เข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างราบรื่น
## คำถามที่พบบ่อย
### GroupDocs.Conversion สำหรับ .NET เข้ากันได้กับ .NET ทุกเวอร์ชันหรือไม่
ใช่ GroupDocs.Conversion สำหรับ .NET เข้ากันได้กับ .NET Framework 4.6.1 และเวอร์ชันที่ใหม่กว่า
### ฉันสามารถแปลงไฟล์ XLSM หลายไฟล์พร้อมกันได้หรือไม่
ได้ คุณสามารถแปลงไฟล์ XLSM หลายไฟล์เป็น PDF หรือรูปแบบอื่นๆ ที่รองรับเป็นชุดได้
### GroupDocs.Conversion สำหรับ .NET รองรับไฟล์ XLSM ที่เข้ารหัสหรือไม่
ใช่ GroupDocs.Conversion สำหรับ .NET รองรับการแปลงไฟล์ XLSM ที่เข้ารหัส โดยคุณต้องมีข้อมูลรับรองที่จำเป็น
### มีรุ่นทดลองใช้สำหรับการทดสอบหรือไม่?
ได้ คุณสามารถรับ GroupDocs.Conversion สำหรับ .NET เวอร์ชันทดลองใช้ฟรีเพื่อประเมินคุณลักษณะต่างๆ ก่อนตัดสินใจซื้อ
### ฉันจะรับการสนับสนุนทางเทคนิคสำหรับ GroupDocs.Conversion สำหรับ .NET ได้อย่างไร
 คุณสามารถไปที่ฟอรัม GroupDocs.Conversion เพื่อรับการสนับสนุนและความช่วยเหลือทางเทคนิค[เยี่ยมชมฟอรั่มการสนับสนุน](https://forum.groupdocs.com/c/conversion/11)