---
date: '2026-07-24'
description: 'การแปลงภาพด้วย Java ง่ายขึ้น: เรียนรู้วิธีแปลงไฟล์ CAD เป็น TIFF ด้วยขนาดที่กำหนดเองโดยใช้
  GroupDocs Conversion Java. คู่มือขั้นตอนต่อขั้นสำหรับนักพัฒนา.'
keywords:
- java image conversion
- custom width height
- set image dimensions java
lastmod: '2026-07-24'
og_description: การแปลงภาพด้วย Java ง่ายขึ้น. แปลงไฟล์ CAD เป็นภาพ TIFF คุณภาพสูงด้วยความกว้างและความสูงที่กำหนดเองโดยใช้
  GroupDocs Conversion Java. ติดตามคู่มือโดยละเอียดของเรา.
og_image_alt: 'Guide: Convert CAD to TIFF with custom dimensions using GroupDocs Conversion
  Java'
og_title: 'การแปลงภาพด้วย Java: จาก CAD ไปเป็น TIFF พร้อมขนาดที่กำหนดเอง'
schemas:
- author: GroupDocs
  dateModified: '2026-07-24'
  description: 'Java image conversion made easy: learn how to convert CAD files to
    TIFF with custom dimensions using GroupDocs Conversion Java. Step‑by‑step guide
    for developers.'
  headline: 'Java Image Conversion: CAD to TIFF with Custom Dimensions'
  type: TechArticle
- questions:
  - answer: GroupDocs Conversion Java, a robust Java image conversion library.
    question: What library should I use for Java image conversion?
  - answer: Use `CadLoadOptions` and specify `setWidth()` and `setHeight()`.
    question: How do I set custom dimensions for a CAD file?
  - answer: Yes—load the CAD, set dimensions, then convert with `ImageConvertOptions`.
    question: Can I convert DWG to TIFF in one step?
  - answer: A free trial works for evaluation; a full license unlocks all features.
    question: Do I need a license?
  - answer: Any Java 8+ runtime is supported.
    question: What Java version is required?
  type: FAQPage
tags:
- convert CAD
- GroupDocs Conversion
- Java image conversion
- TIFF
- CAD processing
title: 'การแปลงภาพด้วย Java: จาก CAD ไปเป็น TIFF พร้อมขนาดที่กำหนดเอง'
type: docs
url: /th/java/cad-formats/cad-conversion-tiff-custom-dimensions-groupdocs-java/
weight: 1
---

# การแปลงภาพ Java: CAD เป็น TIFF พร้อมขนาดกำหนดเอง

หากคุณต้องการแปลงภาพวาด CAD ให้เป็นไฟล์ TIFF ความละเอียดสูงพร้อมควบคุมความกว้างและความสูงของพิกเซลอย่างแม่นยำ, **java image conversion** คือกุญแจสำคัญ. ด้วย GroupDocs Conversion Java, คุณสามารถทำ rasterization ของรูปแบบ CAD ที่รองรับทั้งหมด (DWG, DGN, DXF ฯลฯ) ให้เป็นไฟล์ TIFF ที่พอดีกับรายงาน, พอร์ทัลเว็บ, หรือเลย์เอาต์การพิมพ์. คู่มือนี้จะพาคุณผ่านทุกขั้นตอน—ตั้งแต่การตั้งค่าโปรเจกต์จนถึงการแปลงขั้นสุดท้าย—เพื่อให้คุณสามารถรวมกระบวนการนี้เข้าไปในเวิร์กโฟลว์ Java ใดก็ได้.

## คำตอบด่วน
- **ควรใช้ไลบรารีอะไรสำหรับการแปลงภาพ Java?** GroupDocs Conversion Java, ไลบรารีการแปลงภาพ Java ที่แข็งแกร่ง.  
- **วิธีตั้งขนาดกำหนดเองสำหรับไฟล์ CAD?** ใช้ `CadLoadOptions` และระบุ `setWidth()` และ `setHeight()`.  
- **สามารถแปลง DWG เป็น TIFF ได้ในขั้นตอนเดียวหรือไม่?** ได้—โหลด CAD, ตั้งขนาด, แล้วแปลงด้วย `ImageConvertOptions`.  
- **ต้องมีไลเซนส์หรือไม่?** การทดลองใช้ฟรีทำงานสำหรับการประเมิน; ไลเซนส์เต็มจะปลดล็อกคุณสมบัติทั้งหมด.  
- **ต้องใช้เวอร์ชัน Java ใด?** รองรับ Java 8+ ทุกเวอร์ชัน.

## GroupDocs Conversion Java คืออะไร?
ไลบรารี `GroupDocs Conversion Java` เป็นโซลูชัน **java image conversion** ที่รองรับรูปแบบเข้าและออกกว่า 110 รูปแบบ, รวมถึง CAD และรูปภาพเรสเตอร์หลักทั้งหมด.  
คลาส `Converter` เป็นคอมโพเนนต์หลักที่เริ่มต้นการดำเนินการแปลงไฟล์.  
มันให้การเรนเดอร์ฝั่งเซิร์ฟเวอร์, การสเกล, และตัวเลือกเฉพาะรูปแบบ, ช่วยให้นักพัฒนาสามารถแปลงไฟล์ได้โดยไม่ต้องติดตั้งโปรแกรมดูไฟล์ของบุคคลที่สาม.

## ทำไมต้องแปลง CAD เป็น TIFF พร้อมขนาดกำหนดเอง?
การกำหนดความกว้างและความสูงอย่างชัดเจนรับประกันว่าภาพ TIFF ที่ได้จะพอดีกับข้อจำกัดของเลย์เอาต์ในระบบ downstream. โดยกำหนดขนาดพิกเซลก่อนการ rasterization, คุณจะหลีกเลี่ยงการสเกลที่ทำให้เกิดศิลปะบิดเบือน, รักษาความสม่ำเสมอของความหนาของเส้น, และทำให้ภาพรวมเข้ากันได้อย่างราบรื่นกับ PDF, หน้าเว็บ, หรือสื่อพิมพ์โดยไม่ต้องทำการประมวลผลเพิ่มเติม. วิธีนี้ยังช่วยทำให้ไพป์ไลน์อัตโนมัติที่ต้องการขนาดภาพที่กำหนดไว้ล่วงหน้าง่ายขึ้น.

- **รักษาความคมชัดของภาพ:** การ rasterize ที่ 1920 × 1080 px (หรือขนาดใดที่คุณเลือก) จะทำให้เส้นและลายเส้นคมชัด.  
- **รับประกันเลย์เอาต์สม่ำเสมอ:** ภาพฝังลงใน PDF, HTML, หรือเทมเพลตการพิมพ์โดยไม่มีการปรับขนาดเพิ่มเติม.  
- **เพิ่มความเข้ากันได้:** TIFF เป็นฟอร์แมตที่ได้รับการยอมรับทั่วโลกบน Windows, macOS, Linux, และเครื่องมือออกแบบส่วนใหญ่, ลดปัญหาแปลงฟอร์แมต.

## ข้อกำหนดเบื้องต้น
ก่อนเริ่ม, โปรดตรวจสอบว่าคุณมี:

1. **GroupDocs Conversion Java** เวอร์ชัน 25.2 หรือใหม่กว่า (แนะนำให้ใช้รุ่นล่าสุด).  
2. IDE สำหรับ Java เช่น IntelliJ IDEA หรือ Eclipse.  
3. Maven ติดตั้งเพื่อจัดการ dependency.  
4. ความรู้พื้นฐานการเขียนโปรแกรม Java และความคุ้นเคยกับ `pom.xml` ของ Maven.  

## การตั้งค่า GroupDocs Conversion Java

เพิ่ม dependency ของ GroupDocs ลงใน `pom.xml` ของคุณ:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-conversion</artifactId>
    <version>25.2</version>
</dependency>
```

**การจัดหาไลเซนส์:** คุณสามารถรับการทดลองใช้ฟรี, ขอไลเซนส์ชั่วคราวเพื่อฟังก์ชันเต็ม, หรือซื้อไลเซนส์ถาวรเพื่อปลดล็อกคุณสมบัติของ GroupDocs Conversion อย่างเต็มที่.

เมื่อโปรเจกต์ Java ของคุณเชื่อมโยงกับ dependency เหล่านี้อย่างถูกต้อง, คุณก็พร้อมเริ่มแปลงไฟล์ CAD แล้ว!

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

## วิธีแปลง CAD เป็น TIFF พร้อมขนาดกำหนดเอง?

การแปลงไฟล์ CAD เป็น TIFF ด้วยขนาดที่แม่นยำต้องทำการโหลดภาพวาดต้นฉบับ, ตั้งค่าตัวเลือกการเรนเดอร์, และเรียกใช้ API การแปลง. ด้วยการทำตามลำดับขั้นตอนเชิงเส้น—ตั้งความกว้างและความสูง, เลือก TIFF เป็นรูปแบบผลลัพธ์, และดำเนินการแปลง—คุณจะมั่นใจว่าภาพที่สร้างขึ้นตรงตามข้อกำหนดขนาดของแอปพลิเคชัน downstream, พร้อมคงรายละเอียดและคุณภาพของภาพวาดต้นฉบับ.

1. **นำเข้าคลาสที่จำเป็น** (ดูขั้นตอนต่อไป).  
2. **สร้างอินสแตนซ์ `CadLoadOptions`** และตั้งค่า `width` และ `height` ให้เป็นขนาดเป้าหมายของคุณ.  
3. **สร้างอินสแตนซ์ `ImageConvertOptions`**, ระบุ `ImageFileType.Tiff`.  
4. **เรียกเมธอด `convert`** บนอ็อบเจกต์ `Converter`, ส่งพาธต้นทาง, ตัวเลือกการโหลด, และตัวเลือกการแปลง.

### การโหลดเอกสาร CAD ด้วยขนาดกำหนดเอง (วิธีตั้งขนาด)

คลาส `CadLoadOptions` บอก GroupDocs ว่าจะทำ rasterization ของภาพวาดอย่างไรก่อนการแปลง.

`CadLoadOptions` เป็นอ็อบเจกต์การกำหนดค่าที่ระบุพารามิเตอร์การเรนเดอร์เช่น ความกว้าง, ความสูง, และ DPI สำหรับไฟล์ CAD.

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
*Explanation:* By configuring `CadLoadOptions`, you tell **GroupDocs Conversion Java** to rasterize the CAD drawing at 1920 × 1080 pixels before any further processing.

### การแปลง CAD เป็นภาพ TIFF (Convert CAD to TIFF)

`ImageConvertOptions` กำหนดให้ไลบรารีสร้างไฟล์ TIFF ตามการตั้งค่าที่คุณระบุ.

`ImageConvertOptions` รวมพารามิเตอร์การแปลงเฉพาะภาพทั้งหมด, รวมถึงรูปแบบผลลัพธ์, ความละเอียด, และระดับการบีบอัด.

#### ขั้นตอนที่ 3: กำหนดค่าตัวเลือกการแปลง
```java
String convertedFilePath = "YOUR_OUTPUT_DIRECTORY/ConvertCadAndSpecifyWidthAndHeight.tiff";
ImageConvertOptions options = new ImageConvertOptions();
options.setFormat(ImageFileType.Tiff); // Set the conversion target to TIFF format
```

#### ขั้นตอนที่ 4: ดำเนินการแปลง
```java
converter.convert(convertedFilePath, options);
```
*Explanation:* Setting `ImageFileType.Tiff` directs **GroupDocs Conversion Java** to output a high‑quality TIFF file that respects the width and height you defined earlier.

## เคล็ดลับการแก้ไขปัญหาและข้อผิดพลาดทั่วไป
- **File Path Issues:** Verify that both source and destination paths are correct and that the application has read/write permissions.  
- **Unsupported Formats:** Ensure the CAD file is one of the supported formats (DWG, DGN, DXF, etc.).  
- **Memory Constraints:** Large drawings may require increasing the JVM heap size (`-Xmx2g` or higher).  
- **Quality Concerns:** Adjust `ImageConvertOptions` resolution settings if the default DPI does not meet your quality standards.  

## การประยุกต์ใช้งานจริง
1. **Architectural Visualization:** Export floor plans as TIFF for high‑resolution presentations.  
2. **Engineering Documentation:** Generate standardized images for inclusion in technical manuals.  
3. **Automated Reporting:** Embed CAD‑derived TIFFs into PDF or HTML reports via a CI pipeline.  

## ข้อควรพิจารณาด้านประสิทธิภาพ
- **Optimize Memory Usage:** Release the `Converter` instance after conversion (`converter.close()` if applicable).  
- **Batch Processing:** Loop through a list of CAD files and reuse a single `Converter` configuration to reduce overhead.  
- **Stay Updated:** Regularly upgrade to the latest GroupDocs Conversion Java release to benefit from performance enhancements and bug fixes.  

## คำถามที่พบบ่อย

**Q:** What file formats does GroupDocs Conversion support?  
**A:** It supports over 110 formats, including CAD files like DWG, DGN, DXF, as well as common image, document, and archive types.

**Q:** Can I convert multiple CAD files at once?  
**A:** Yes—implement a simple loop that creates a new `Converter` for each file or reuse the same instance with different source paths.

**Q:** How do I handle large file sizes during conversion?  
**A:** Increase the JVM heap size, process files in smaller batches, or use streaming options provided by the library.

**Q:** What if the output image quality is not satisfactory?  
**A:** Adjust the DPI or scaling settings in `ImageConvertOptions` to increase resolution.

**Q:** Is support available if I encounter issues?  
**A:** GroupDocs offers extensive documentation, community forums, and direct support for licensed customers.

## แหล่งข้อมูล
- [เอกสาร GroupDocs](https://docs.groupdocs.com/conversion/java/)
- [อ้างอิง API](https://reference.groupdocs.com/conversion/java/)
- [ดาวน์โหลดรุ่นล่าสุด](https://releases.groupdocs.com/conversion/java/)
- [ซื้อไลเซนส์](https://purchase.groupdocs.com/buy)
- [เข้าถึงการทดลองใช้ฟรี](https://releases.groupdocs.com/conversion/java/)
- [ขอไลเซนส์ชั่วคราว](https://purchase.groupdocs.com/temporary-license/)
- [ฟอรั่มสนับสนุน](https://forum.groupdocs.com/c/conversion/10)

---

**อัปเดตล่าสุด:** 2026-07-24  
**ทดสอบด้วย:** GroupDocs Conversion Java 25.2  
**ผู้เขียน:** GroupDocs  

## บทแนะนำที่เกี่ยวข้อง

- [convert cad pdf java – CAD Formats Conversion Tutorials for GroupDocs.Conversion Java](/conversion/java/cad-formats/)
- [convert pdf to jpg java using GroupDocs.Conversion – Guide](/conversion/java/document-operations/convert-pdf-to-jpg-groupdocs-java/)
- [How to Set License for GroupDocs.Conversion Java - Step‑By‑Step Guide](/conversion/java/getting-started/groupdocs-conversion-java-license-setup-file-path/)