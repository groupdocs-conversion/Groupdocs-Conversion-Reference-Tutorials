---
date: '2025-12-19'
description: เรียนรู้วิธีติดตามการแปลงใน Java รวมถึงวิธีแปลงไฟล์ docx เป็น pdf ด้วย
  Java โดยใช้ GroupDocs.Conversion. สร้างตัวฟังที่แข็งแรงเพื่อการตรวจสอบที่ราบรื่น.
keywords:
- track document conversion progress Java
- GroupDocs.Conversion for Java
- conversion state and progress listener
title: 'วิธีติดตามความคืบหน้าการแปลงใน Java ด้วย GroupDocs - คู่มือฉบับสมบูรณ์'
type: docs
url: /th/java/conversion-events-logging/java-groupdocs-conversion-progress-listener/
weight: 1
---

# วิธีติดตามความคืบหน้าการแปลงใน Java ด้วย GroupDocs

หากคุณต้องการ **ทราบวิธีการติดตามการแปลง** ในแอปพลิเคชัน Java ของคุณ—โดยเฉพาะเมื่อคุณต้องการ **แปลง docx pdf java**—GroupDocs.Conversion มีวิธีการที่เรียบง่ายและขับเคลื่อนด้วยเหตุการณ์ การแนบ listener จะทำให้คุณได้รับข้อมูลตอบกลับแบบเรียลไทม์ในแต่ละขั้นตอนของ pipeline การแปลง ทำให้การทำงานแบบ batch, แถบความคืบหน้า UI, และการบันทึกข้อมูลเป็นเรื่องโปร่งใสมากขึ้น.

## คำตอบด่วน
- **Listener บันทึกอะไร?** รวมถึงรายงานเริ่มต้น, ความละเอียด (เปอร์เซ็นต์), เอกสารที่เกี่ยวข้อง
- **ฉันต้องการรูปแบบใดๆ บ้างหรือไม่** รองรับที่ GroupDocs.Conversion รองรับเช่น DOCX→PDF
- **ต้องการไลเซนส์หรือไม่?** ประโยชน์ของการใช้งานฟรีสำหรับการพัฒนา; ต้องมีเซนส์การชำระเงินแบบสมจริง
- **ต้องใช้ Maven ต้องใช้เวลา?** Maven คุณจะต้องจัดการกับการพึ่งพาอาศัย แต่คุณก็สามารถใช้ Gradle หรือ JAR แบบแมนนวลได้
- ** สามารถอยู่ในเว็บเซอร์วิสได้หรือเปล่า?** ได้—ห่อการเรียกแปลงในจุดสิ้นสุดของ REST จากนั้นสตรีมความคืบในนั้น

## “วิธีการติดตามการเปลี่ยนแปลง” ใน GroupDocs คืออะไร
GroupDocs.Conversion มีอยู่แล้ว `IConverterListener` สามารถนำมาใช้ทำให้โค้ดของคุณดีขึ้นเมื่อเครื่องมือแปลงสถานะ, ช่วยให้บันทึก, อัปเดตคอมโพเนนต์ UI, หรือเรียกเฟิร์มแวร์ต่อเนื่องได้

## ทำไมต้องติดตามความคืบหน้าของ Conversion?
- **ประสบการณ์ผู้ใช้:** แสดงเปอร์เซ็นต์ในส่วนต่างๆ ใน ​​UI หรือเครื่องมือ CLI
- **การจัดการความรู้สึก:** ต้องใช้การกำกับดูแลตั้งแต่ต้นและลองใหม่หรือยกเลิกอย่างสุภาพ
- ** กล่าวถึงทรัพยากร:** ในเวลาที่เห็นได้ชัดสำหรับแบทช์ขนาดใหญ่และแหล่งที่มาตามนั้น

## ข้อกำหนดเบื้องต้น
- **ชุดพัฒนา Java (JDK 8+)**
- **Maven** (หรือเครื่องมือสร้างสิ่งใด ๆ ที่สามารถแก้ไขที่เก็บ Maven ได้)
- **ไลบรารี GroupDocs.Conversion สำหรับ Java**
- ** เช่นเดียวกับเซนส์ GroupDocs ที่ถูกต้อง** (สมุนไพรใช้งานได้ฟรีสำหรับการทดสอบ)

## การตั้งค่า GroupDocs.Conversion สำหรับ Java
### ติดตั้ง GroupDocs.Conversion ผ่าน Maven
เพิ่มพื้นที่เก็บข้อมูลและการพึ่งพาใน `pom.xml` ของคุณ:

```xml
<repositories>
    <repository>
        <id>groupdocs-repo</id>
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

### การได้มาซึ่งใบอนุญาต
GroupDocs มีฟังก์ชั่นการใช้งานฟรี, ไลเซนส์ชั่วคราวสำหรับระบบ, และระบบควบคุมโดยตรง จากนั้น [หน้าการซื้อ](https://purchase.groupdocs.com/buy) เพื่อรับไลเซนส์ของคุณ

### การเริ่มต้นขั้นพื้นฐาน
เมื่อไลบรารีอยู่บน classpath ของคุณแล้ว คุณสามารถสร้างอินสแตนซ์ `ConverterSettings` ได้:

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.ConverterSettings;

public class InitializeGroupDocs {
    public static void main(String[] args) {
        ConverterSettings settings = new ConverterSettings();
        // Additional configurations can be set here.
    }
}
```

## คู่มือการใช้งาน
เราจะอธิบายคุณลักษณะแต่ละอย่างทีละขั้นตอน โดยเพิ่มบริบทก่อนข้อมูลโค้ดแต่ละรายการ

### คุณสมบัติ 1: สถานะการแปลงและผู้ฟังความคืบหน้า
#### ภาพรวม
Listener นี้จะบอกคุณเมื่อ Conversion เริ่มต้น ความคืบหน้าไปไกลแค่ไหน และสิ้นสุดเมื่อใด

#### การนำผู้ฟังไปใช้
สร้างคลาสที่ใช้ `IConverterListener`:

```java
import com.groupdocs.conversion.IConverterListener;

class ListenConversionStateAndProgress implements IConverterListener {
    public void started() {
        System.out.println("Conversion has begun.");
    }

    public void progress(byte current) {
        System.out.printf("Conversion Progress: %d%%\n", current);
    }

    public void completed() {
        System.out.println("Conversion has finished.");
    }
}
```

**คำอธิบาย**
- **started()** – สำหรับเรียกความสนใจในจีนเพื่อตรวจสอบ. การเริ่มต้นใหม่ตัวเตือนหรือคอมโพเนนต์ UI.
- **ความคืบหน้า(byte current)** – รับค่าตั้งแต่ 0 ถึง 100 แสดงเปอร์เซ็นต์ที่เป็นตัวอย่าง บางส่วนในขณะนี้.
- **completed()** – บันทึกการเรียกหลังจากไฟล์ผลลัพธ์ถูกเขียนเพิ่มเติม ทรัพยากรที่นี่.

### คุณสมบัติ 2: การตั้งค่าตัวแปลงพร้อม Listener
#### ภาพรวม
แนบ Listener ของคุณเข้ากับ `ConverterSettings` เพื่อให้กลไกรู้ว่าจะส่งเหตุการณ์ไปที่ใด

#### ขั้นตอนการกำหนดค่า
1. **สร้างตัวอย่างของผู้ฟังของคุณ**:

   ```java
   IConverterListener listener = new ListenConversionStateAndProgress();
   ```

2. **กำหนดค่าออบเจ็กต์ `ConverterSettings`**:

   ```java
   ConverterSettings settingsFactory = new ConverterSettings();
   settingsFactory.setListener(listener);
   ```

### คุณสมบัติที่ 3: การแปลงเอกสาร
#### ภาพรวม
ตอนนี้คุณจะได้เห็นการทำงานของ Listener ในระหว่างการแปลงไฟล์ DOCX เป็น PDF

#### ขั้นตอนการใช้งาน
1. **กำหนดเส้นทางอินพุตและเอาต์พุต** (แทนที่ด้วยไดเร็กทอรีจริงของคุณ):

   ```java
   String inputDocPath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX";
   String outputPath = "YOUR_OUTPUT_DIRECTORY/converted.pdf";
   ```

2. **เริ่มต้นตัวแปลงด้วยการตั้งค่าที่เปิดใช้งาน Listener** และเริ่มการแปลง:

   ```java
   try (Converter converter = new Converter(inputDocPath, settingsFactory)) {
       PdfConvertOptions options = new PdfConvertOptions();
       converter.convert(outputPath, options);
   }
   ```

**คำอธิบาย**
- **Converter** – คลาสหลักที่ประสานเสียง.
- **PdfConvertOptions** – บอก GroupDocs ที่ต้องการผลลัพธ์เป็น PDF เคยได้ยิน `PptxConvertOptions`, `HtmlConvertOptions` และอื่นๆ, และ Listener เดิมที่รายงานในวันนี้.

## วิธีแปลง docx pdf java ด้วย GroupDocs
โค้ดด้านบนได้แสดงรายการ **docx→pdf** แล้ว รูปแบบเป้าหมายอื่นๆ เพียงเปลี่ยน `PdfConvertOptions` เป็นคลาสตัวเลือกที่เหมาะสม (เช่น `HtmlConvertOptions` สำหรับ HTML) ผู้ฟังมีการเปลี่ยนแปลง ดังนั้นคุณยังคงได้รับไม่ว่าประเภทผลลัพธ์จะเป็นอะไรก็ตาม

## การใช้งานจริง
1. ** ระบบจัดการเอกสารอัตโนมัติ** – จะต้องระบุแบทช์ประเภทของไฟล์พร้อมแสดงคุณสมบัติของระบบโดยไม่คำนึงถึง
2. ** การให้ความรู้สำหรับระดับองค์กร** – ฝังศพไปป์ไลน์, เอกสารการวิจัย, หรือการเพิ่มเนื้อหา e-learning.
3. **เครื่องมือย้ายเนื้อหา** – ควบคุมจำนวนมากจากรูปแบบเก่าไปยัง PDF สมัยใหม่, ตรวจสอบความถูกต้องของการรวบรวมข้อมูลตั้งแต่ต้น.

## ข้อควรพิจารณาด้านประสิทธิภาพ
- **การจัดการคำอธิบาย:** ใช้ try‑with‑resources (ตามเพิ่มเติม) และ `Converter` จะปิดอย่างรวดเร็ว
- **การทำงานหลายอย่างพร้อมกัน:** สำหรับแบทช์ขนาดใหญ่, รันในความถี่แบบต่อเนื่อง, แต่ต้องจำไว้ว่าแต่ละส่วนต้องมีผู้ฟังในผลลัพธ์ที่ผสมกัน.
- ** คำเตือน:** ไม่มีการเรียก `System.out` ของ Listener ประกาศ; เราทราบจริง, ส่งต่อไปยังคณะกรรมการรวบรวมข้อมูลของผู้ชม (SLF4J, Log4j)

## ปัญหาทั่วไปและแนวทางแก้ไข
| ปัญหา | โซลูชั่น |
|-------|----------|
| **ไม่มีการแสดงเลย** | ไมโครโฟนสามารถเรียก `settingsFactory.setListener(listener);` ก่อนสร้าง `Converter`. |
| **OutOfMemoryError กับไฟล์ขนาดใหญ่** | ขนาดฮีปของ JVM (`-Xmx2g` หรืออื่นๆ) และพิจารณาว่าไฟล์นั้นเป็นเพียงชิ้นเล็ก ๆ เท่านั้น |
| **ผู้ฟังไม่ทำงานเมื่อเกิดเหตุการณ์** | ห่อ `converter.convert` ด้วยบล็อก try‑catch และเรียกเมธอด `errorภายใน(byte code)` วิธีที่มีประสิทธิภาพในการ Listener ของคุณ |

## คำถามที่พบบ่อย

**ถาม:** ติดตามเรื่องนี้เป็นหลักสำหรับรูปแบบอื่นๆ นอกเหนือจาก PDF ได้หรือไม่?
**ก:** ได้. `IConverterListener` เดียวกันกับรูปแบบของกลุ่มเป้าหมายใดๆ ที่ GroupDocs.Conversion รองรับ; เพียงเปลี่ยนตัวเลือกคลาส

**ถาม:** ฉันจัดการเอกสารจำนวนมากอย่างมีประสิทธิภาพได้อย่างไร?
**A:** ใช้ Java streaming APIs โดยเพิ่มขนาดฮีปของ JVM, ค้นหาของ Listener เพื่อจับขั้นตอนที่ตามปกติ

**ถาม:** จะเป็นเรื่องสำคัญหากเป็นจุดศูนย์กลางทาง?
**A:**เพื่อเพิ่มเมธอดเพิ่มเติมใน Listener ของคุณ (เช่น `error(byte code)`) และห่อการเรียก `convert` ด้วยการจัดการข้อมูลเพื่อบันทึกความล้มเหลว

**ถาม:** มีขีดจำกัดของขนาดหรือประเภทไฟล์หรือไม่?
**ตอบ:** ส่วนใหญ่มักจะกล่าวถึงการสนับสนุน, แต่ไฟล์ขนาดใหญ่มากอาจต้องการข้อมูลเพิ่มเติม ดูเอกสารอย่างเป็นทางการของ [เอกสารประกอบ GroupDocs](https://docs.groupdocs.com/conversion/java/) สำหรับกรุงโรม

**ถาม:** จะช่วยให้สิ่งนี้เกิดขึ้นในเว็บได้อย่างไร?
**A:** ห่อโลเจลจะมาในจุดสิ้นสุดของ REST (เช่น Spring Boot) และสตรีมอัปเดตตามปกติที่ Server‑Sent Events (SSE) หรือ WebSocket ส่งผลลัพธ์ของ Listener ของพวกเรา

## ทรัพยากร
- **เอกสาร:** [GroupDocs Conversion Documentation](https://docs.groupdocs.com/conversion/java/)
- **อ้างอิง API:** [API Reference](https://reference.groupdocs.com/conversion/java/)
- **ดาวน์โหลด:** [Download GroupDocs.Conversion](https://releases.groupdocs.com/conversion/java/)
- **ซื้อ:** [Buy License](https://purchase.groupdocs.com/buy)
- **ทดลองใช้งานฟรี:** [Try Free Trial](https://releases.groupdocs.com/conversion/java/)
- **ไลเซนส์ชั่วคราว:** [Get Temporary License](https://purchase.groupdocs.com/temporary-license/)
- **ฟอรั่มสนับสนุน:** [GroupDocs Support](https://forum.groupdocs.com/c/conversion/10)

---

**อัปเดตล่าสุด:** 2025-12-19  
**ทดสอบกับ:** GroupDocs.Conversion 25.2  
**ผู้เขียน:** GroupDocs  

---