---
date: '2025-12-21'
description: เรียนรู้วิธีแปลงไฟล์ DOCX เป็น PDF จากสตรีมโดยใช้ GroupDocs.Conversion
  สำหรับ Java เหมาะสำหรับแอปพลิเคชันเว็บและการจัดการข้อยกเว้นไฟล์ไม่พบ
keywords:
- convert docx to pdf
- how to convert stream
- handle file notfound exception
- load document from stream
- GroupDocs.Conversion for Java
title: แปลง DOCX เป็น PDF จากสตรีมใน Java ด้วย GroupDocs
type: docs
url: /th/java/document-operations/convert-documents-streams-java-groupdocs/
weight: 1
---

# แปลง DOCX เป็น PDF จาก Streams ใน Java ด้วย GroupDocs

คุณกำลังมองหา **การแปลง DOCX เป็น PDF** โดยตรงจาก streams ในแอปพลิเคชัน Java ของคุณหรือไม่? ความต้องการนี้มักเกิดขึ้นเมื่อจัดการไฟล์ที่ไม่ได้อยู่บนดิสก์โดยตรง—เช่น การอัปโหลดจากฟอร์มเว็บหรือข้อมูลที่รับมาจากการเชื่อมต่อเครือข่าย ในบทแนะนำนี้คุณจะได้เรียนรู้วิธีโหลดเอกสารจาก stream, จัดการ `FileNotFoundException` ที่อาจเกิดขึ้น, และสร้าง PDF ด้วย GroupDocs.Conversion สำหรับ Java

## คำตอบสั้น

- **“การแปลง DOCX เป็น PDF จาก streams” หมายถึงอะไร?** หมายถึงการอ่านไฟล์ DOCX จาก `InputStream` แล้วเขียน PDF ที่แปลงแล้วโดยตรงไปยังไฟล์หรือ stream อื่นโดยไม่ต้องบันทึก DOCX ดั้งเดิมบนดิสก์  
- **ไลบรารีที่ทำการแปลงคืออะไร?** GroupDocs.Conversion สำหรับ Java มี API ที่ง่ายต่อการแปลงแบบใช้ stream  
- **ต้องมีลิขสิทธิ์สำหรับการใช้งานใน production หรือไม่?** ต้องมีลิขสิทธิ์เชิงพาณิชย์สำหรับการใช้งานใน production; มีรุ่นทดลองฟรีสำหรับการประเมินผล  
- **จะจัดการไฟล์ต้นทางที่หายไปอย่างไร?** ห่อการสร้าง `FileInputStream` ด้วยบล็อก try‑catch และจัดการ `FileNotFoundException` อย่างเหมาะสม  

## บทนำ

การแปลง DOCX เป็น PDF จาก streams มีประโยชน์เป็นพิเศษในแอปพลิเคชันเว็บที่คุณต้องการหลีกเลี่ยงไฟล์ชั่วคราว, ลดภาระ I/O, และทำให้กระบวนการใช้หน่วยความจำอย่างมีประสิทธิภาพ ด้านล่างเราจะเดินผ่านการตั้งค่าครบถ้วน ตั้งแต่การกำหนดค่า Maven จนถึงเมธอด Java ที่สามารถรันได้ซึ่งทำการแปลง

## ข้อกำหนดเบื้องต้น

- **Java Development Kit (JDK)** 8 หรือสูงกว่า  
- **Maven** สำหรับการจัดการ dependencies  
- ความเข้าใจพื้นฐานเกี่ยวกับ **Java streams** (เช่น `InputStream`, `FileInputStream`)  

### การตั้งค่าสภาพแวดล้อม

เพื่อใช้งาน GroupDocs.Conversion สำหรับ Java ก่อนอื่นให้เพิ่มไลบรารีลงในโปรเจกต์ Maven ของคุณ

## การตั้งค่า GroupDocs.Conversion สำหรับ Java

เพิ่ม repository ของ GroupDocs และ dependency ของ conversion ลงในไฟล์ `pom.xml` ของคุณ:

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/conversion/java/</url>
   </repository>
</repositories>

<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-conversion</artifactId>
      <version>25.2</version>
   </dependency>
</dependencies>
```

### การรับลิขสิทธิ์

คุณสามารถเริ่มต้นด้วยรุ่นทดลองฟรีเพื่อสำรวจ GroupDocs.Conversion สำหรับ Java สำหรับการใช้งานใน production ให้ซื้อไลเซนส์หรือขอไลเซนส์ชั่วคราวสำหรับการทดสอบที่ขยายเวลา

## คู่มือการทำงาน

ด้านล่างเป็นขั้นตอนแบบทีละขั้นที่แสดง **วิธีแปลงไฟล์ DOCX เป็น PDF จาก stream**  

### โหลดเอกสารจาก Stream

ฟีเจอร์นี้ช่วยให้คุณแปลงเอกสารโดยตรงจาก input stream โดยไม่ต้องเก็บไว้บนดิสก์ก่อน

#### ขั้นตอนที่ 1: นำเข้าแพ็กเกจที่จำเป็น

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.exceptions.GroupDocsConversionException;
import com.groupdocs.conversion.options.convert.PdfConvertOptions;

import java.io.FileInputStream;
import java.io.FileNotFoundException;
```

#### ขั้นตอนที่ 2: กำหนดเมธอดการแปลง

```java
public class LoadDocumentFromStream {
    public static void run() {
        // Specify the output path for the converted PDF
        String convertedFile = "YOUR_OUTPUT_DIRECTORY/LoadDocumentFromStream.pdf";
        
        try {
            // Initialize a Converter instance with a lambda that supplies the input stream
            Converter converter = new Converter(() -> {
                try {
                    return new FileInputStream("YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX");
                } catch (FileNotFoundException e) {
                    // Handle file notfound exception gracefully
                    throw new RuntimeException("Source DOCX file not found.", e);
                }
            });
            
            // Set up PDF conversion options (default settings)
            PdfConvertOptions options = new PdfConvertOptions();
            
            // Perform the conversion and save the PDF
            converter.convert(convertedFile, options);
        } catch (Exception e) {
            // Wrap any conversion errors in a GroupDocsConversionException
            throw new GroupDocsConversionException(e.getMessage());
        }
    }
}
```

#### คำอธิบาย

- **การเริ่มต้น Converter** – คลาส `Converter` ถูกสร้างด้วย lambda ที่คืนค่า `FileInputStream` รูปแบบนี้ทำให้คุณส่ง `InputStream` ใด ๆ (เช่น จาก HTTP request) ไปยังเอนจินการแปลงได้  
- **การจัดการ `FileNotFoundException`** – Lambda จะจับ `FileNotFoundException` แล้วโยนใหม่เป็น `RuntimeException` พร้อมข้อความที่ชัดเจน เพื่อตอบสนองคีย์เวิร์ดรอง *handle file notfound exception*  
- **ตัวเลือกการแปลงเป็น PDF** – `PdfConvertOptions` ให้คุณปรับแต่ง PDF ที่ออก (เช่น ขนาดหน้า, การบีบอัด) การตั้งค่าเริ่มต้นทำงานได้ดีในหลายกรณี  

### เคล็ดลับการแก้ปัญหา

- ตรวจสอบว่า **พาธของไฟล์ DOCX ต้นทาง** และ **ไดเรกทอรีผลลัพธ์** ถูกต้อง; การพิมพ์ผิดจะทำให้เกิด `FileNotFoundException`  
- หากคุณได้รับ `GroupDocsConversionException` ให้ตรวจสอบข้อความของ inner exception เพื่อหาสาเหตุ (เช่น รูปแบบไฟล์ที่ไม่รองรับ)  
- สำหรับเอกสารขนาดใหญ่ ควรห่อ `FileInputStream` ด้วย `BufferedInputStream` เพื่อเพิ่มประสิทธิภาพ I/O  

## การประยุกต์ใช้ในเชิงปฏิบัติ

การแปลง DOCX เป็น PDF จาก streams ด้วย GroupDocs.Conversion มีคุณค่าในหลายสถานการณ์จริง:

1. **การจัดการไฟล์ในเว็บแอปพลิเคชัน** – แปลงไฟล์ DOCX ที่ผู้ใช้อัปโหลดเป็น PDF ทันทีโดยไม่ต้องบันทึกไฟล์ต้นฉบับ  
2. **การประมวลผลข้อมูลจากเครือข่าย** – แปลงเอกสารที่รับมาจาก socket หรือ REST API โดยตรงจาก stream  
3. **ระบบประมวลผลแบบแบตช์** – ส่งคิวของ input stream ให้กับ worker ที่ทำการแปลงเป็น PDF จำนวนมาก  

## พิจารณาด้านประสิทธิภาพ

- **Buffered I/O** – ห่อ stream ด้วย `BufferedInputStream` สำหรับไฟล์ขนาดใหญ่เพื่อลดภาระการอ่าน  
- **การจัดการหน่วยความจำ** – ปล่อยอ็อบเจกต์ `Converter` ทันทีหลังการแปลงเพื่อคืนทรัพยากร native  
- **ความปลอดภัยของเธรด** – สร้าง `Converter` แยกสำหรับแต่ละเธรด; คลาสนี้ไม่รองรับการใช้งานหลายเธรดพร้อมกัน  

## สรุป

ในบทแนะนำนี้คุณได้เรียนรู้วิธี **แปลง DOCX เป็น PDF จาก streams** ด้วย GroupDocs.Conversion สำหรับ Java โดยการโหลดเอกสารโดยตรงจาก `InputStream`, จัดการ `FileNotFoundException` ที่อาจเกิดขึ้น, และใช้ API `Converter` ที่เรียบง่าย คุณสามารถสร้าง pipeline การแปลงที่มีประสิทธิภาพและไม่มีไฟล์ชั่วคราวสำหรับแอปพลิเคชัน Java สมัยใหม่ได้แล้ว

## ส่วนคำถามที่พบบ่อย (FAQ)

1. **ฟอร์แมตไฟล์ใดบ้างที่สามารถแปลงได้ด้วย GroupDocs.Conversion สำหรับ Java?**  
   - GroupDocs.Conversion รองรับฟอร์แมตหลากหลาย รวมถึง DOCX, XLSX, PPTX, PDF และอื่น ๆ อีกมากมาย  

2. **ฉันสามารถใช้ GroupDocs.Conversion ในแอปพลิเคชันเชิงพาณิชย์ได้หรือไม่?**  
   - ได้, แต่ต้องมีไลเซนส์เชิงพาณิชย์ที่ถูกต้องสำหรับการใช้งานใน production  

3. **จะจัดการข้อผิดพลาดในการแปลงอย่างไร?**  
   - ห่อโลจิกการแปลงด้วยบล็อก `try‑catch` และจับ `GroupDocsConversionException` เพื่อทำการจัดการข้อผิดพลาดอย่างราบรื่น  

4. **สามารถทำการแปลงแบบแบตช์ได้หรือไม่?**  
   - แน่นอน คุณสามารถวนลูปผ่านหลาย input stream และเรียก `converter.convert` สำหรับแต่ละเอกสารได้  

5. **สามารถปรับแต่งการตั้งค่า PDF ได้หรือไม่?**  
   - ได้, `PdfConvertOptions` มีตัวเลือกสำหรับขนาดหน้า, การบีบอัด, และอื่น ๆ  

## คำถามที่พบบ่อยเพิ่มเติม

**ถาม: จะทำอย่างไรถ้าต้องแปลงไฟล์ DOCX ที่เก็บใน BLOB ของฐานข้อมูล?**  
ตอบ: ดึง BLOB เป็น `InputStream` แล้วส่งให้ lambda ของ `Converter` ตามตัวอย่างที่แสดง  

**ถาม: ถ้า stream ต้นทางมีขนาดใหญ่ (หลายร้อย MB) จะทำอย่างไร?**  
ตอบ: ใช้ `BufferedInputStream` และพิจารณาประมวลผลการแปลงในเธรดพื้นหลังเพื่อหลีกเลี่ยงการบล็อกการทำงานของแอปพลิเคชันหลัก  

**ถาม: GroupDocs.Conversion รองรับเอกสารที่มีรหัสผ่านหรือไม่?**  
ตอบ: รองรับ คุณสามารถส่งรหัสผ่านผ่าน `LoadOptions` เมื่อสร้าง `Converter`  

**ถาม: สามารถแปลงโดยตรงไปยัง `OutputStream` แทนพาธไฟล์ได้หรือไม่?**  
ตอบ: API ปัจจุบันส่วนใหญ่เขียนไปยังพาธไฟล์ แต่คุณสามารถเขียนไปยังไฟล์ชั่วคราวแล้วสตรีมกลับ, หรือใช้ overload ของ `convert` ที่รับ `ByteArrayOutputStream`  

**ถาม: มีวิธีใดในการติดตามความคืบหน้าการแปลงบ้าง?**  
ตอบ: GroupDocs.Conversion มี event callbacks ที่คุณสามารถผูกเพื่อรับข้อมูลอัปเดตความคืบหน้า  

## แหล่งข้อมูล

- [Documentation](https://docs.groupdocs.com/conversion/java/)  
- [API Reference](https://reference.groupdocs.com/conversion/java/)  
- [Download GroupDocs.Conversion for Java](https://releases.groupdocs.com/conversion/java/)  
- [Purchase License](https://purchase.groupdocs.com/buy)  
- [Free Trial](https://releases.groupdocs.com/conversion/java/)  
- [Temporary License Request](https://purchase.groupdocs.com/temporary-license/)  
- [Support Forum](https://forum.groupdocs.com/c/conversion/10)  

---

**Last Updated:** 2025-12-21  
**Tested With:** GroupDocs.Conversion 25.2  
**Author:** GroupDocs