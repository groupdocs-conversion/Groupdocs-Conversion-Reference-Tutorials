---
date: '2026-01-23'
description: เรียนรู้วิธีแคชเอกสารใน Java ด้วยการใช้ Redis cache ร่วมกับ GroupDocs.Conversion
  เพื่อเพิ่มประสิทธิภาพการแสดงผลและปรับปรุงประสิทธิภาพโดยรวม
keywords:
- Custom Caching Java
- GroupDocs.Conversion Java
- Redis Cache Implementation
title: วิธีแคชเอกสารใน Java ด้วย Redis และ GroupDocs
type: docs
url: /th/java/cache-management/custom-cache-redis-groupdocs-java/
weight: 1
---

# วิธีแคชเอกสารใน Java ด้วย Redis & GroupDocs

เมื่อคุณต้องการ **วิธีแคชเอกสาร** อย่างมีประสิทธิภาพ โดยเฉพาะในช่วงการแสดงผลเอกสารปริมาณมาก แคชที่ออกแบบดีสามารถลดเวลาในการประมวลผลได้อย่างมาก ในบทแนะนำนี้เราจะพาคุณผ่าน **java redis cache tutorial** ที่ครบถ้วนซึ่งผสานรวม Redis กับ GroupDocs.Conversion เพื่อช่วยคุณ **เพิ่มประสิทธิภาพการแสดงผล** สำหรับ PDF, DOCX และรูปแบบอื่น ๆ

## คำตอบอย่างรวดเร็ว
- **บทแนะนำนี้ครอบคลุมอะไร?** การทำแคชที่ใช้ Redis สำหรับ GroupDocs.Conversion ใน Java.  
- **ทำไมต้องใช้ Redis?** มันให้การจัดเก็บในหน่วยความจำที่เร็ว, รองรับ TTL, และขยายขนาดได้ง่าย.  
- **ฉันต้องการไลเซนส์ของ GroupDocs หรือไม่?** ไลเซนส์ทดลองหรือไลเซนส์ชั่วคราวใช้ได้สำหรับการทดสอบ; ไลเซนส์เต็มจำเป็นสำหรับการใช้งานจริง.  
- **ขั้นตอนหลักคืออะไร?** ตั้งค่า dependencies ของ Maven, กำหนดค่า Jedis, สร้างตัวช่วยแคช, และผสานแคชเข้ากับกระบวนการแปลง.  
- **รองรับเวอร์ชัน Java ใด?** Java 8+ (เข้ากันได้กับรุ่นล่าสุดของ GroupDocs.Conversion).

## การแคชเอกสารด้วย Redis คืออะไร?
การแคชเก็บผลลัพธ์ของการแปลงเอกสาร (เช่น PDF ที่สร้างขึ้น) ไว้ใน Redis เพื่อให้คำขอต่อ ๆ ไปสำหรับไฟล์ต้นฉบับเดียวกันสามารถให้บริการได้ทันทีโดยไม่ต้องประมวลผลใหม่ สิ่งนี้ช่วยลดภาระ CPU, ปริมาณการจราจรเครือข่าย, และปรับปรุงประสบการณ์ของผู้ใช้

## ทำไมต้องใช้แคช Redis ใน Java?
- **เพิ่มประสิทธิภาพการแสดงผล** โดยหลีกเลี่ยงการแปลงซ้ำ.  
- **ลดค่าใช้จ่ายโครงสร้างพื้นฐาน** – ใช้ CPU น้อยลงและความกดดันของหน่วยความจำน้อยลง.  
- **ขยายได้หลายอินสแตนซ์ของแอปพลิเคชัน** เนื่องจาก Redis เป็นที่เก็บศูนย์กลาง.  
- **การควบคุมละเอียด** ของนโยบายการหมดอายุ ช่วยให้คุณสมดุลระหว่างความสดใหม่และความเร็ว.

 dependencies.ความเพิ่มรีโพซิทอรีของ GroupDocs และ dependency ลงใน `pom.xml` ของคุณ:

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

### การรับไลเซนส์
คุณสามารถเริ่มต้นด้วย **Free Trial**, ขอ **Temporary License** เพื่อการประเมิน, หรือซื้อ **License** เต็มรูปแบบสำหรับการใช้งานจริง.

เริ่มต้น GroupDocs.Conversion ในโค้ด Java ของคุณ:

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.convert.PdfConvertOptions;

public class DocumentConversion {
    public static void main(String[] args) {
        // Initialize the Converter with a document path
        Converter converter = new Converter("input.docx");
        
        // Set up conversion options for PDF
        PdfConvertOptions options = new PdfConvertOptions();
        converter.convert("output.pdf", options);
    }
}
```

## คู่มือการนำไปใช้

### การสร้างแคชแบบกำหนดเองโดยใช้ Redis

#### ภาพรวม
แคช Redis แบบกำหนดเองจะเก็บไบต์ของเอกสารที่แสดงผลแล้ว ทำให้สามารถดึงข้อมูลได้ทันทีเมื่อมีการร้องขอซ้ำ.

#### การตั้งค่า JedisPool
ขั้นแรก สร้างพูลการเชื่อมต่อเพื่อจัดการการเชื่อมต่อ Redis อย่างมีประสิทธิภาพ:

```java
import redis.clients.jedis.JedisPool;

public class CacheManager {
    private static JedisPool jedisPool = new JedisPool("localhost", 6379);
    
    public static void main(String[] args) {
        // Additional cache setup code here
    }
}
```

#### การจัดเก็บและดึงข้อมูลแคช
ใช้เมธอดช่วยเหลือแบบง่ายเพื่อใส่และดึงเอกสารจาก Redis:

```java
import redis.clients.jedis.Jedis;

public class CacheManager {

    public static void storeDocument(String key, String documentContent) {
        try (Jedis jedis = jedisPool.getResource()) {
            // Set the content in Redis cache with an expiration time of one hour
            jedis.setex(key, 3600, documentContent);
        }
    }

    public static String retrieveDocument(String key) {
        try (Jedis jedis = jedisPool.getResource()) {
            return jedis.get(key); // Retrieve cached content if available
        }
    }
}
```

#### การผสานกับ GroupDocs.Conversion
ตอนนี้เชื่อมแคชเข้ากับกระบวนการแปลง:

```java
public class DocumentConversion {

    public static void convertWithCache(String inputPath, String outputPath) {
        Converter converter = new Converter(inputPath);
        PdfConvertOptions options = new PdfConvertOptions();

        // Generate a cache key based on the document path and conversion settings
        String cacheKey = "doc:" + inputPath;

        // Check if the converted document is already cached
        String cachedDocument = CacheManager.retrieveDocument(cacheKey);

        if (cachedDocument != null) {
            System.out.println("Using cached version of the document.");
            // Save cached content to output file
            Files.write(Paths.get(outputPath), cachedDocument.getBytes());
        } else {
            // Perform conversion and cache the result
            converter.convert(output -> {
                String documentContent = new String(output.toByteArray());
                CacheManager.storeDocument(cacheKey, documentContent);
                Files.write(Paths.get(outputPath), output.toByteArray());
            }, options);
        }
    }

    public static void main(String[] args) {
        convertWithCache("input.docx", "output.pdf");
    }
}
```

### เคล็ดลับการแก้ไขปัญหา
- ตรวจสอบว่าเซิร์ฟเวอร์ Redis สามารถเข้าถึงได้ (`ping` จากโฮสต์).  
- ยืนยันว่า host/port ของ `JedisPool` ตรงกับอินสแตนซ์ Redis ของคุณ.  
- ห่อการเรียกแคชในบล็อก try‑catch เพื่อจัดการปัญหาการเชื่อมต่ออย่างราบรื่น.  
- ตรวจสอบการใช้หน่วยความจำของ Redis; พิจารณานโยบาย `maxmemory` สำหรับการใช้งานจริง.

## การประยุกต์ใช้งานจริง
1. **พอร์ทัลที่มีการเข้าชมสูง** – ให้บริการ PDF ที่ร้องขอบ่อยอย่างทันที.  
2. **Enterprise DMS** – ลดภาระบนเซิร์ฟเวอร์แปลงเมื่อผู้ใช้ดูสัญญาเดียวกันหลายครั้ง.  
3. **E‑commerce** – แคชใบแจ้งหนี้หรือแคตาล็อกสินค้าที่สร้างขึ้น.  
4. **แพลตฟอร์มการเรียนรู้** – เร่งการส่งมอบบันทึกการบรรยายและอี‑บุ๊ค.  
5. **บริการด้านกฎหมาย** – เร่งการแจกจ่ายไฟล์คดีพร้อมคงต้นทุนการจัดเก็บให้ต่ำ.

## ปัจจัยที่ต้องพิจารณาด้านประสิทธิ** – ปรับ `maxmemory`, `eviction-policy`, และการตั้งค่า timeout ตามภาระงานของคุณ.  
- **ติดตามอัตราการฮิต/มิสของแคช** – ใช้สถิติ `INFO` ของ Redis เพื่อปรับค่า TTL ของคีย์อย่างละเอียด.  
- **ขนาด heap ของ JVM** – ตรวจสอบให้แน่ใจว่า heap สามารถรองรับไลบรารีการแปลงพร้อมบัฟเฟอร์ในกระบวนการได้.

## คำถามที่พบบ่อย

**Q: ฉันสามารถใช้วิธีนี้กับรูปแบบผลลัพธ์อื่นของ GroupDocs ได้หรือไม่?**  
A: แน่นอน. รูปแบบแคชเดียวกันทำงานได้กับ DOCX, HTML, รูปภาพ, และอื่น ๆ – เพียงเปลี่ยน้าเอกต้องโดยการลบคีย์ด้วยตนเอง (เช่น ลบคีย์) หรือใช้ TTL ที่สั้นลงเพื่อให้ข้อมูลเก่าหมดอายุอย่างรวดเร็ว.

**Q: Redis เป็นตัวเลือกเดียวสำหรับการแคชหรือไม่?**  
A: ไม่, แต่ Redis มีความหน่วงต่ำ, มี TTL ในตัว, และสนับสนุนไคลเอนต์ Java อย่างกว้างขวาง ทำให้เป็นตัวเลือกที่นิยมสำหรับสถานการณ์นี้.

**Q: วิธีนี้ทำให้การใช้หน่วยความจำบนเซิร์ฟเวอร์แอปพลิเคชันเพิ่มขึ้นหรือไม่?**  
A: น้อยมาก. งานหนักทำโดย Redis; แอปเพียงเก็บการเชื่อมต่อสั้น ๆ ผ่าน Jedis.

## สรุป
ตอนนี้คุณมี **java redis cacheกับผู้ TTL, ตรวจสอบเมตริกแคช, และขยายรูปแบบนี้ไปยังรูปแบบเอกสารอื่น ๆ ตามต้องการ.

---

**อัปเดตล่าสุด:** 2026-01-23  
**ทดสอบด้วย:** GroupDocs.Conversion 25.2, Jedis 4.2  
**ผู้เขียน:** GroupDocs