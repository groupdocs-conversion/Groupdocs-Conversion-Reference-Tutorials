---
date: '2026-01-26'
description: เรียนรู้วิธีแปลงไฟล์ CAD เป็น TIFF ด้วยขนาดที่กำหนดเองโดยใช้ GroupDocs
  Conversion Java ซึ่งเป็นไลบรารีการแปลงภาพ Java ชั้นนำ คู่มือแบบขั้นตอนต่อขั้นตอน
keywords:
- CAD Conversion
- TIFF Image
- Custom Dimensions
- GroupDocs.Conversion Java
title: 'แปลง CAD เป็น TIFF ด้วยขนาดกำหนดเองโดยใช้ GroupDocs Conversion Java: คู่มือฉบับสมบูรณ์'
type: docs
url: /th/java/cad-formats/cad-conversion-tiff-custom-dimensions-groupdocs-java/
weight: 1
---

ดิเคชันของคุณ ด้วย **groupdocs conversion java** กระบวนการนี้จะกลัตยกรรมหรือแผนผังวิศวกรรม การแปลงเอกสารเหล่านี้เป็นรูปแบบ TIFF พร้อมการตั้งค่าความกว้างและความสูงที่ามาก

## คำตอบสั้น
- **ควรใช้ไลบรารีใดสำหรับการแปลงภาพใน Java?** GroupDocs Conversion Java, ไลบรารีการแปลงภาพ java ที่แข็งแรง  
- **จะตั้งค่าขนาดกำหนดเองสำหรับไฟล์ CAD อย่างไร?** ใช้ `CadLoadOptions` และระบุ `set** ได้—โหลด CADด? ทุกเวอร์ชัน

## GroupDocs Conversion Java คืออะไร?
GroupDocs Conversion Java เป็น **java image conversion library** ที่ทรงพลัง รองรับไฟล์มากกว่า 100 รูปแบบ รวมถึงเดอร์, การสเกล, และตัวเลือกเฉพาะรูปแบบ ทำให้เหมาะสำหรับงาน “how to convert CAD” ที่ต้องการการควบคุมละเอียดของขนาดผลลัพธ์

## ทำไมต้องแปลง CAD เป็น TIFF ด้วยขนาดกำหนดเอง?
- **รักษารายละเอียด:** TIFF เก็บข้อมูลเวกเตอร์ความละเอียดสูงเมื่อแปลงเป็นเรสเตอร์ที่ขนาดที่คุณต้องการ  
- **รูปแบบที่สอดคล้อง:** การระบุความกว้างและความสูงทำให้ภาพพทัล, หรือการพิมพ์ได้อย่างสมบูรณ์  
- **ความเข้ากันได้ข้ามแพลตฟอร์ม:** ไฟล์ TIFFใหม่กว่า (แนะนำให้ สำหรับฐานด้านการเขียนโปรแกรม Java และความคุ้นเคยกับ `pom.xml` ของ Maven  

## การตั้งค่า GroupDocs Conversion Java

เริ่มต้นโดยกำหนดค่า Maven ให้รวมไลบรารี GroupDocs ที่จำเป็นโดยเพิ่มส่วนต่อไปนี้ในไฟล์ `pom.xml` ของคุณ:

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

**การรับลิขสิทธิ์:** คุณสามารถขอทดลองใช้ฟรี, ขอรับลิขสิทธิ์ชั่วคราวเพื่อใช้งานเต็มรูปแบบ, หรือซื้อลิขสิทธิ์ถาวรเพื่อปลดล็อกคุณสมบัติของ GroupDocs Conversion อย่างเต็มที่

เมื่อโปรเจกต์ Java ของคุณเชื่อมโยงกับ dependencies เหล่านี้อย่างถูกต้อง คุณก็พร้อมเริ่มแปลงไฟล์ CAD แล้ว!

## คู่มือขั้นตอนโดยละเอียด

### โหลดเอกสาร CAD ด้วยขนาดกำหนดเอง (วิธีตั้งค่าขนาด)

**ภาพรวม:** ขั้นตอนนี้จะแสดงให้คุณเห็น *วิธีแปลง CAD* พร้อมระบุความกว้างและความสูงที่ต้องการอย่างแม่นยำ

#### ขั้นตอนที่ 1: นำเข้าไลบรารีที่จำเป็น
```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.filetypes.ImageFileType;
import com.groupdocs.conversion.options.convert.ImageConvertOptions;
import com.groupdocs.conversion.options.load.CadLoadOptions;
```

#### ขั้นตอนที่ 2: ตั้งค่า Load Options ด้วยขนาดกำหนดเอง
```java
String sourceDocumentPath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DWG_WITH_LAYOUTS_AND_LAYERS";
CadLoadOptions loadOptions = new CadLoadOptions();
loadOptions.setWidth(1920); // Specify the desired width in pixels
loadOptions.setHeight(1080); // Specify the desired height in pixels
Converter converter = new Converter(sourceDocumentPath, () -> loadOptions);
```
*คำอธิบาย:* โดยการกำหนด `CadLoadOptions` คุณบอก **groupdocs conversion java** ให้เรนเดอร์ภาพวาด CAD ที่ขนาด 1920 × 1080 พิกเซล ก่อนทำการประมวลผลต่อไป

### แปลง CAD เป็นภาพ TIFF (Convert CAD to TIFF)

**ภาพรวม:** หลังจากโหลดไฟล์ CAD ด้วยขนาดกำหนดเองแล้ว คุณสามารถแปลงโดยตรงเป็นภาพ TIFF ได้

#### ขั้นตอนที่ 3: กำหนดค่า Conversion Options
```java
String convertedFilePath = "YOUR_OUTPUT_DIRECTORY/ConvertCadAndSpecifyWidthAndHeight.tiff";
ImageConvertOptions options = new ImageConvertOptions();
options.setFormat(ImageFileType.Tiff); // Set the conversion target to TIFF format
```

#### ขั้นตอนที่ 4: ดำเนินการแปลง
```java
converter.convert(convertedFilePath, options);
```
*คำอธิบาย:* การตั้งค่า `ImageFileType.Tiff` จะสั่งให้ **groupdocs conversion java** ส่งออกไฟล์ TIFF คุณภาพสูงที่รักษาความกว้างและความสูงที่คุณกำหนดไว้ก่อนหน้า

## เคล็ดลับการแก้ไขปัญหาและข้อผิดพลาดทั่วไป
- **ปัญหาเส้นทางไฟล์:** ตรวจสอบให้แน่ใจว่าเส้นทางต้นทางและปลายทางถูกต้องและแอปพลิเคชันมีสิทธิ์อ่าน/เขียน  
- **รูปแบบที่ไม่รองรับ:** ยืนยันว่าไฟล์ CAD อยู่ในรูปแบบที่รองรับ (DWG, DGN, DXF ฯลฯ)  
- **ข้อจำกัดด้านหน่วยความจำ:** การวาดที่ใหญ่อาจต้องเพิ่มขนาด heap ของ JVM (`-Xmx2g` หรือมากกว่า)  
- **คุณภาพไม่พอ:** ปรับค่าการตั้งค่า resolution ใน `ImageConvertOptions` หาก DPI เริ่มต้นไม่ตรงตามมาตรฐานคุณภาพของคุณ  

## การประยุกต์ใช้งานจริง
1. **การแสดงผลสถาปัตยกรรม:** ส่งออกแผนผังเป็น TIFF สำหรับการนำเสนอความละเอียดสูง  
2. **เอกสารวิศวกรรม:** สร้างภาพมาตรฐานเพื่อใส่ในคู่มือเทคนิค  
3. **การรายงานอัตโนมัติ:** ฝัง TIFF ที่ได้จาก CAD ลงในรายงาน PDF หรือ HTML ผ่าน pipeline CI  

## พิจารณาด้านประสิทธิภาพ
- **เพิ่มประสิทธิภาพการใช้หน่วยความจำ:** ปิดอินสแตนซ์ `Converter` หลังการแปลง (`converter.close()` หากมี)  
- **การประมวลผลเป็นชุด:** วนลูปผ่านรายการไฟล์ CAD และใช้การตั้งค่า `Converter` ตัวเดียวเพื่อ ลดค่าโอเวอร์เฮด  
- **อัปเดตอยู่เสมอ:** ควรอัปเกรดเป็นรุ่นล่าสุดของ GroupDocs Conversion Java อย่างสม่ำเสมอเพื่อรับประโยชน์จากการปรับปรุงประสิทธิภาพและการแก้บั๊ก  

## สรุป
ด้วยการทำตามคู่มือนี้ คุณได้เรียนรู้ **วิธีแปลง CAD** เป็น TIFF ด้วยขนาดกำหนดเองโดยใช้ **groupdocs conversion java** ความสามารถนี้ช่วยทำให้เวิร์กโฟลว์ที่ต้องการขนาดภาพแม่นยำเป็นเรื่องง่าย ไม่ว่าจะเป็นการนำเสนอ, เอกสาร, หรือ pipeline อัตโนมัติ  

**ขั้นตอนต่อไป:** สำรวจตัวเลือกการแปลงเพิ่มเติม เช่น PDF, PNG, หรือ SVG และผสานตรรกะการแปลงเข้าไปในบริการ Java ของคุณเพื่อการอัตโนมัติแบบครบวงจร  

## คำถามที่พบบ่อย

**ถาม:** GroupDocs Conversion รองรับรูปแบบไฟล์อะไรบ้าง?  
**ตอบ:** รองรับกว่า 100 รูปแบบ รวมถึงไฟล์ CAD เช่น DWG, DGN, DXF รวมถึงรูปภาพ, เอกสาร, และไฟล์อาร์ไคฟ์ทั่วไป  

**ถาม:** สามารถแปลงไฟล์ CAD หลายไฟล์พร้อมกันได้หรือไม่?  
**ตอบ:** ได้—สร้างลูปง่าย ๆ ที่สร้าง `Converter` ใหม่สำหรับแต่ละไฟล์ หรือใช้อินสแตนซ์เดียวกับเส้นทางต้นทางที่ต่างกัน  

**ถาม:** จะจัดการกับไฟล์ขนาดใหญ่ระหว่างการแปลงอย่างไร?  
**ตอบ:** เพิ่มขนาด heap ของ JVM, ประมวลผลเป็นชุดย่อย, หรือใช้ตัวเลือกสตรีมมิ่งที่ไลบรารีให้มา  

**ถาม:** ถ้าคุณภาพภาพผลลัพธ์ไม่พอจะทำอย่างไร?  
**ตอบ:** ปรับค่า DPI หรือการสเกลใน `ImageConvertOptions` เพื่อเพิ่มความละเอียด  

**ถาม:** มีการสนับสนุนหากพบปัญหาหรือไม่?  
**ตอบ:** GroupDocs มีเอกสารประกอบ, ฟอรั่มชุมชน, และการสนับสนุนโดยตรงสำหรับลูกค้าที่มีลิขสิทธิ์  

## แหล่งข้อมูล
- [GroupDocs Documentation](https://docs.groupdocs.com/conversion/java/)
- [API Reference](https://reference.groupdocs.com/conversion/java/)
- [Download Latest Release](https://releases.groupdocs.com/conversion/java/)
- [Purchase Licenses](https://purchase.groupdocs.com/buy)
- [Free Trial Access](https://releases.groupdocs.com/conversion/java/)
- [Temporary License Request](https://purchase.groupdocs.com/temporary-license/)
- [Support Forum](https://forum.groupdocs.com/c/conversion/10)

---

**อัปเดตล่าสุด:** 2026-01-26  
**ทดสอบด้วย:** GroupDocs Conversion Java 25.2  
**ผู้เขียน:** GroupDocs  

---