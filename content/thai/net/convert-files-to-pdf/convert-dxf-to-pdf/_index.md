---
title: แปลงไฟล์แลกเปลี่ยน DXF CAD Drawing เป็น PDF
linktitle: แปลงไฟล์แลกเปลี่ยน DXF CAD Drawing เป็น PDF
second_title: GroupDocs.Conversion .NET API
description: แปลงไฟล์ DXF CAD Drawing Exchange เป็น PDF ได้อย่างง่ายดายด้วย GroupDocs.Conversion สำหรับ .NET
weight: 12
url: /th/net/convert-files-to-pdf/convert-dxf-to-pdf/
---

# แปลงไฟล์แลกเปลี่ยน DXF CAD Drawing เป็น PDF

## การแนะนำ
ในโลกของการพัฒนาซอฟต์แวร์ ความสามารถในการแปลงไฟล์จากรูปแบบหนึ่งไปเป็นอีกรูปแบบหนึ่งได้อย่างราบรื่นเป็นสิ่งที่ขาดไม่ได้ ไม่ว่าคุณจะจัดการกับเอกสาร รูปภาพ หรือแบบร่าง CAD การมีเครื่องมือการแปลงที่เชื่อถือได้สามารถช่วยประหยัดเวลาและความพยายามได้ ในบทช่วยสอนนี้ เราจะเจาะลึกกระบวนการแปลง DXF (ไฟล์ CAD Drawing Exchange) เป็น PDF โดยใช้ไลบรารี GroupDocs.Conversion สำหรับ .NET
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเจาะลึกกระบวนการแปลง ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:

## นำเข้าเนมสเปซ
ในการเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณได้นำเข้าเนมสเปซที่จำเป็นในโครงการของคุณ:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
ตอนนี้ เรามาแบ่งกระบวนการแปลงออกเป็นหลายขั้นตอน:
## ขั้นตอนที่ 1: โหลดไฟล์ Source DXF
ขั้นแรก คุณต้องโหลดไฟล์ DXF ที่คุณต้องการแปลง ต่อไปนี้คือวิธีที่คุณสามารถทำได้:
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "dxf-converted-to.pdf");
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_DXF))
{
```
## ขั้นตอนที่ 2: ตั้งค่าตัวเลือกการแปลง
เมื่อโหลดไฟล์ DXF แล้ว ก็ถึงเวลาตั้งค่าตัวเลือกการแปลง ในกรณีนี้ เรากำลังแปลงเป็น PDF ดังนั้น เรามากำหนดตัวเลือกการแปลง PDF กัน:
```csharp
	var options = new PdfConvertOptions();
```
## ขั้นตอนที่ 3: ทำการแปลง
เมื่อโหลดไฟล์ต้นฉบับและตั้งค่าตัวเลือกการแปลงแล้ว คุณสามารถดำเนินการขั้นตอนการแปลงต่อได้ ต่อไปนี้เป็นวิธีดำเนินการ:
```csharp
	converter.Convert(outputFile, options);
}
```
## ขั้นตอนที่ 4: แสดงข้อความแสดงความสำเร็จ
เมื่อการแปลงสำเร็จ การแสดงความคิดเห็นแก่ผู้ใช้จะเป็นประโยชน์เสมอ แจ้งให้พวกเขาทราบว่ากระบวนการแปลงเสร็จสมบูรณ์แล้ว และจะหาไฟล์ที่แปลงได้ที่ใด:
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
แค่นั้นแหละ! คุณได้แปลงไฟล์ DXF เป็น PDF โดยใช้ GroupDocs.Conversion สำหรับ .NET เรียบร้อยแล้ว

## บทสรุป
ในบทช่วยสอนนี้ เราได้สำรวจกระบวนการแปลงไฟล์ DXF CAD Drawing Exchange เป็น PDF โดยใช้ GroupDocs.Conversion สำหรับ .NET ด้วยการทำตามขั้นตอนง่ายๆ ที่อธิบายไว้ข้างต้น คุณสามารถจัดการการแปลงรูปแบบไฟล์ในแอปพลิเคชัน .NET ของคุณได้อย่างง่ายดาย ช่วยประหยัดเวลาและปรับปรุงขั้นตอนการทำงานของคุณ
## คำถามที่พบบ่อย
### GroupDocs.Conversion เข้ากันได้กับ .NET ทุกเวอร์ชันหรือไม่
ใช่ GroupDocs.Conversion เข้ากันได้กับ .NET ทุกเวอร์ชัน รวมถึง .NET Core และ .NET Framework
### ฉันสามารถแปลงหลายไฟล์พร้อมกันโดยใช้ GroupDocs.Conversion ได้หรือไม่
อย่างแน่นอน! GroupDocs.Conversion ช่วยให้คุณสามารถแปลงไฟล์หลายไฟล์พร้อมกัน ทำให้การแปลงเป็นชุดเป็นเรื่องง่าย
### GroupDocs.Conversion รองรับการแปลงเป็นรูปแบบอื่นนอกเหนือจาก PDF หรือไม่
ใช่ GroupDocs.Conversion รองรับรูปแบบเอาต์พุตที่หลากหลาย รวมถึง DOCX, XLSX, JPG, PNG และอื่นๆ อีกมากมาย
### GroupDocs.Conversion มีรุ่นทดลองใช้ฟรีหรือไม่
 ใช่ คุณสามารถใช้ GroupDocs.Conversion รุ่นทดลองใช้ฟรีเพื่อสำรวจคุณสมบัติและความสามารถของมันก่อนตัดสินใจซื้อ[เว็บไซต์](https://releases.groupdocs.com/).
### ฉันจะขอรับการสนับสนุนได้ที่ไหน หากฉันพบปัญหาใดๆ กับ GroupDocs.Conversion
 คุณสามารถค้นหาทรัพยากรสนับสนุนที่ครอบคลุม รวมถึงฟอรัมและเอกสารประกอบได้ใน GroupDocs[เว็บไซต์](https://forum.groupdocs.com/c/conversion/11).