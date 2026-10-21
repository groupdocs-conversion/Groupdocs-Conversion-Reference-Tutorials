---
date: '2026-10-21'
description: เรียนรู้วิธีสร้าง cache key Java และรวม Redis กับ GroupDocs.Conversion
  เพื่อเพิ่ม rendering performance, ลด conversion time, และกำหนดค่า TTLs ในโครงการ
  Java อย่างง่าย
images:
- /java/cache-management/custom-cache-redis-groupdocs-java/og-image.png
keywords:
- create cache key java
- java redis caching
- groupdocs conversion cache
- redis ttl java
lastmod: '2026-10-21'
og_description: สร้าง cache key Java ในคู่มือแบบขั้นตอนต่อขั้นตอนนี้ที่แสดงวิธีรวม
  Redis กับ GroupDocs.Conversion เพื่อ cache document bytes, boost rendering performance,
  และลด conversion time. กำหนดค่า TTLs และวัดการเพิ่มความเร็ว.
og_image_alt: 'Developer guide: create cache key Java using Redis and GroupDocs'
og_title: สร้าง cache key Java – cache docs with Redis and GroupDocs
schemas:
- author: GroupDocs
  dateModified: '2026-10-21'
  description: Learn how to create cache key Java and integrate Redis with GroupDocs.Conversion
    to boost rendering performance, reduce conversion time, and configure TTLs.
  headline: Create cache key Java – cache docs with Redis and GroupDocs
  type: TechArticle
- description: Learn how to create cache key Java and integrate Redis with GroupDocs.Conversion
    to boost rendering performance, reduce conversion time, and configure TTLs.
  name: Create cache key Java – cache docs with Redis and GroupDocs
  steps:
  - name: '**High‑traffic portals** – Serve frequently requested PDFs (catalogs, whitepapers)
      instantly.'
    text: '**High‑traffic portals** – Serve frequently requested PDFs (catalogs, whitepapers)
      instantly.'
  - name: '**Enterprise DMS** – Reduce load when users repeatedly view the same contracts
      or policy documents.'
    text: '**Enterprise DMS** – Reduce load when users repeatedly view the same contracts
      or policy documents.'
  - name: '**E‑commerce** – Cache generated invoices or product catalogs to speed
      up checkout.'
    text: '**E‑commerce** – Cache generated invoices or product catalogs to speed
      up checkout.'
  - name: '**Learning platforms** – Deliver lecture notes and e‑books without re‑rendering
      on every student request.'
    text: '**Learning platforms** – Deliver lecture notes and e‑books without re‑rendering
      on every student request.'
  - name: '**Legal services** – Accelerate distribution of case files while keeping
      storage costs low.'
    text: '**Legal services** – Accelerate distribution of case files while keeping
      storage costs low.'
  type: HowTo
- questions:
  - answer: Absolutely. The same caching pattern works for DOCX, HTML, images, and
      more – just change the `ConvertOptions` type.
    question: Can I use this approach with other GroupDocs output formats?
  - answer: Combine the source file path, conversion options, and any version identifiers.
      This guarantees uniqueness per configuration.
    question: How do I choose a good cache key?
  - answer: Invalidate the cache manually (e.g., delete the key) or use a shorter
      TTL so stale data expires quickly.
    question: What if a document changes after it’s cached?
  - answer: No, but Redis offers low latency, built‑in TTL, and wide Java client support,
      making it a popular choice for this scenario.
    question: Is Redis the only option for caching?
  - answer: Minimal. The heavy lifting is done by Redis; the app only holds short‑lived
      connections via Jedis.
    question: Does this increase memory usage on the application server?
  type: FAQPage
tags:
- create cache key java
- java redis cache
- groupdocs conversion
- document rendering
title: สร้าง cache key Java – cache docs in Java with Redis
type: docs
url: /th/java/cache-management/custom-cache-redis-groupdocs-java/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# สร้างคีย์แคชใน Java – แคชเอกสารใน Java ด้วย Redis

ในแอปพลิเคชันเว็บสมัยใหม่ การให้บริการเอกสารที่แปลงแล้วซ้ำ ๆ สามารถทำให้ใช้ CPU อย่างไม่มีประสิทธิภาพและทำให้เวลาในการตอบสนองเพิ่มขึ้น. **การสร้างคีย์แคชใน Java** ช่วยให้คุณเก็บผลลัพธ์การแปลงไว้ครั้งเดียวและดึงคืนได้ทันทีในคำขอถัดไป. บทแนะนำนี้จะแสดงวิธีเชื่อม Redis เข้ากับกระบวนการทำงานของ GroupDocs.Conversion, สร้างคีย์แคชที่เชื่อถือได้, กำหนดค่า TTLs, และวัดผลการปรับปรุงประสิทธิภาพที่คุณคาดหวัง.

## คำตอบอย่างรวดเร็ว
- **บทแนะนำนี้ครอบคลุมอะไร?** การสอนการแคช java redis อย่างครบถ้วนที่รวม Redis กับ GroupDocs.Conversion.  
- **ทำไมต้องใช้ Redis?** มันให้ความหน่วงต่ำระดับมิลลิวินาที, รองรับการหมดอายุ TTL, และสามารถขยายแนวนอนได้หลายอินสแตนซ์ของแอปพลิเคชัน.  
- **ฉันต้องการไลเซนส์ GroupDocs หรือไม่?** ไลเซนส์ทดลองหรือชั่วคราวก็พอสำหรับการทดสอบ; ไลเซนส์เต็มจำเป็นสำหรับการใช้งานในสภาพแวดล้อมการผลิต.  
- **ขั้นตอนหลักคืออะไร?** เพิ่ม dependencies ของ Maven, กำหนดค่า `JedisPool`, สร้างเมธอดช่วยเหลือแคช, และเชื่อมแคชเข้ากับ pipeline การแปลง.  
- **เวอร์ชัน Java ที่รองรับคืออะไร?** Java 8+ (เข้ากันได้กับรุ่นล่าสุดของ GroupDocs.Conversion).

## การแคชเอกสารด้วย Redis คืออะไร?
การแคชเอกสารด้วย Redis หมายถึงการเก็บผลลัพธ์ไบนารีของการแปลง (เช่น อาเรย์ไบต์ PDF) ไว้ใน Redis เพื่อให้คำขอในอนาคตที่เหมือนกันสามารถดึงไบต์ที่แคชไว้แทนการรันเอนจินการแปลงใหม่. วิธีนี้ขจัดการทำงานของ CPU ที่ซ้ำซ้อน, ลดแบนด์วิธของเครือข่าย, และมอบประสบการณ์ผู้ใช้ที่ราบรื่นยิ่งขึ้น.

## ทำไมต้องใช้แคช Redis ใน Java?
การโหลดเอกสารครั้งเดียว, เก็บผลลัพธ์, และให้บริการทันทีเมื่อมีการเข้าถึงซ้ำสามารถ **ลดเวลาแปลงได้ถึง 90 %** สำหรับไฟล์ที่เข้าถึงบ่อย, **ลดค่าใช้จ่ายโครงสร้างพื้นฐาน** ด้วยการใช้ CPU น้อยลง, และ **ให้แหล่งข้อมูลที่เป็นความจริงเดียว** สำหรับโหนดแอปพลิเคชันทั้งหมดในสภาพแวดล้อมคลัสเตอร์. Redis สามารถประมวลผลมากกว่า 200 k การดำเนินการต่อวินาทีบนโหนดเดียว, รับประกันการค้นหาในระดับมิลลิวินาที.

## ข้อกำหนดเบื้องต้น
- **GroupDocs.Conversion** – เวอร์ชัน 25.2 หรือใหม่กว่า (รองรับ **120+** ฟอร์แมตเข้าและออก).  
- **Jedis** (ไคลเอนต์ Redis อย่างเป็นทางการสำหรับ Java).  
- อินสแตนซ์ Redis ที่กำลังทำงาน (การพัฒนาท้องถิ่นสามารถใช้ค่าเริ่มต้น `localhost:6379`).  
- Maven สำหรับการจัดการ dependencies.  
- ความคุ้นเคยพื้นฐานกับการจัดการข้อยกเว้นใน Java และสตรีม I/O.

## การตั้งค่า GroupDocs.Conversion สำหรับ Java

`GroupDocs.Conversion` เป็นไลบรารี Java ที่แปลงและเรนเดอร์เอกสารเป็นรูปแบบหลากหลาย, จัดการการรักษาเลย์เอาต์, ฝังฟอนต์, และการสกัดภาพโดยอัตโนมัติ.

เพิ่มรีโพซิทอรีของ GroupDocs และ dependency ลงใน `pom.xml` ของคุณ:

```xml
<repositories>
    <repository>
        <id>groupdocs-maven</id>
        <url>https://repo.groupdocs.com/maven</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-conversion</artifactId>
        <version>25.2.0</version>
    </dependency>
    <dependency>
        <groupId>redis.clients</groupId>
        <artifactId>jedis</artifactId>
        <version>4.2.3</version>
    </dependency>
</dependencies>
```

### การรับไลเซนส์
คุณสามารถเริ่มต้นด้วย **Free Trial**, ขอ **Temporary License** เพื่อการประเมิน, หรือซื้อ **License** เต็มรูปแบบสำหรับการใช้งานในสภาพแวดล้อมการผลิต.

เริ่มต้น GroupDocs.Conversion ในโค้ด Java ของคุณ:

```java
import com.groupdocs.conversion.*;

ConversionConfig config = new ConversionConfig();
config.setLicensePath("path/to/license/file.lic");
ConversionApi conversionApi = new ConversionApi(config);
```

## คู่มือการดำเนินการ

### การสร้างแคชแบบกำหนดเองโดยใช้ Redis

#### ภาพรวม
แคช Redis แบบกำหนดเองจะเก็บไบต์ของเอกสารที่เรนเดอร์ไว้, ทำให้สามารถดึงคืนได้ทันทีเมื่อมีการร้องขอซ้ำ.

#### การตั้งค่า JedisPool
JedisPool เป็นพูลที่ปลอดภัยต่อเธรดของการเชื่อมต่อ Redis ที่สามารถนำกลับมาใช้ใหม่ได้, ช่วยลดภาระของซ็อกเก็ตและเพิ่มอัตราการทำงาน.

```java
import redis.clients.jedis.JedisPool;
import redis.clients.jedis.JedisPoolConfig;

JedisPoolConfig poolConfig = new JedisPoolConfig();
poolConfig.setMaxTotal(20);               // maximum active connections
poolConfig.setMaxIdle(10);                // maximum idle connections
poolConfig.setMinIdle(2);                 // minimum idle connections
JedisPool jedisPool = new JedisPool(poolConfig, "localhost", 6379);
```

#### การจัดเก็บและดึงข้อมูลแคช
เมธอดช่วยเหลือต่อไปนี้จะทำการซีเรียลไลซ์อาเรย์ไบต์เป็นสตริง Base64 เพื่อการจัดเก็บที่ปลอดภัยและดึงกลับมาเป็นอาเรย์ไบต์อีกครั้ง.

```java
import java.util.Base64;
import redis.clients.jedis.Jedis;

public class RedisCacheHelper {

    private final JedisPool pool;
    private final int ttlSeconds; // time‑to‑live for cached entries

    public RedisCacheHelper(JedisPool pool, int ttlSeconds) {
        this.pool = pool;
        this.ttlSeconds = ttlSeconds;
    }

    public void put(String key, byte[] data) {
        try (Jedis jedis = pool.getResource()) {
            String encoded = Base64.getEncoder().encodeToString(data);
            jedis.setex(key, ttlSeconds, encoded); // configure redis ttl
        }
    }

    public byte[] get(String key) {
        try (Jedis jedis = pool.getResource()) {
            String encoded = jedis.get(key);
            return encoded != null ? Base64.getDecoder().decode(encoded) : null;
        }
    }
}
```

#### การรวมกับ GroupDocs.Conversion
ตอนนี้เชื่อมแคชเข้ากับกระบวนการแปลง. เมธอดจะตรวจสอบแคชก่อน; หากไม่พบ (miss) จะทำการแปลง, เก็บผลลัพธ์, และคืนค่าไบต์.

```java
import com.groupdocs.conversion.options.convertoptions.PdfConvertOptions;

public class DocumentService {

    private final ConversionApi conversionApi;
    private final RedisCacheHelper cacheHelper;

    public DocumentService(ConversionApi conversionApi, RedisCacheHelper cacheHelper) {
        this.conversionApi = conversionApi;
        this.cacheHelper = cacheHelper;
    }

    public byte[] convertToPdf(String sourcePath, PdfConvertOptions options) throws Exception {
        // Build a deterministic cache key
        String cacheKey = "pdf:" + sourcePath + ":" + options.hashCode();

        // Attempt to fetch from Redis
        byte[] cached = cacheHelper.get(cacheKey);
        if (cached != null) {
            // Cache hit – return stored bytes
            return cached;
        }

        // Cache miss – perform conversion
        byte[] result = conversionApi.convert(sourcePath, options).toByteArray();

        // Store result for future calls
        cacheHelper.put(cacheKey, result);
        return result;
    }
}
```

## วิธีสร้างคีย์แคชใน Java สำหรับการแคช Redis?
สร้างคีย์ที่กำหนดได้โดยการต่อเส้นทางไฟล์ต้นทาง, ค่าที่เลือกจาก `ConvertOptions`, และแท็กเวอร์ชันเสริม (ถ้ามี), จากนั้นแฮชสตริงด้วย SHA‑256. คีย์นี้ระบุการกำหนดค่าการแปลงแต่ละชุดอย่างเฉพาะเจาะจง, ทำให้คำขอที่เหมือนกันเข้าถึงแคชได้ในขณะที่ตัวเลือกที่ต่างกันสร้างรายการแยกกัน.

คลาส `ConversionApi` เป็นส่วนประกอบหลักใน GroupDocs.Conversion ที่ดำเนินการแปลงเอกสาร. คุณสามารถสร้างคีย์แคช, ค้นหาใน Redis, และเรียก `ConversionApi.convert` เฉพาะเมื่อคีย์ไม่มีอยู่, ลดเวลาแปลงและภาระเซิร์ฟเวอร์อย่างมาก.

## วิธีการทำแคช Redis ด้วย Java?
`ConversionApi` เป็นคลาสหลักใน GroupDocs.Conversion ที่ดำเนินการแปลงเอกสาร. โหลดเอกสารต้นทาง, สร้างคีย์แคชที่กำหนดได้, ค้นหาใน Redis, และเรียก `ConversionApi` เฉพาะเมื่อคีย์ไม่มีอยู่. รูปแบบนี้รับประกันว่าการแปลงที่เป็นเอกลักษณ์แต่ละครั้งจะทำเพียงครั้งเดียว, จากนั้นให้บริการจากแคชตามระยะเวลาที่กำหนดใน TTL.

## เคล็ดลับการแก้ไขปัญหา
- ตรวจสอบว่าเซิร์ฟเวอร์ Redis สามารถเข้าถึงได้ (`redis-cli ping` ควรคืนค่า `PONG`).  
- ตรวจสอบให้แน่ใจว่าโฮสต์และพอร์ตของ `JedisPool` ตรงกับการปรับใช้ Redis ของคุณ.  
- ห่อการเรียกแคชในบล็อก try‑catch เพื่อจัดการกับการขัดข้องของการเชื่อมต่อโดยไม่ทำให้กระบวนการแปลงหยุดชะงัก.  
- ตรวจสอบหน่วยความจำของ Redis (`INFO memory`) และตั้งนโยบาย `maxmemory` (เช่น `volatile-lru`) เพื่อกำจัดรายการเก่าอย่างราบรื่น.  
- หากพบ `OutOfMemoryError` บน JVM, เพิ่มขนาด heap หรือเปิดใช้งาน `-XX:+UseCompressedOops`.

## การประยุกต์ใช้งานจริง

1. **พอร์ทัลที่มีการเข้าชมสูง** – ให้บริการ PDF ที่ร้องขอบ่อย (แคตาล็อก, whitepapers) อย่างทันที.  
2. **Enterprise DMS** – ลดภาระเมื่อผู้ใช้ดูสัญญาหรือเอกสารนโยบายเดียวกันหลายครั้ง.  
3. **E‑commerce** – แคชใบแจ้งหนี้หรือแคตาล็อกสินค้าเพื่อเร่งการชำระเงิน.  
4. **Learning platforms** – ส่งมอบบันทึกการบรรยายและอี‑บุ๊คโดยไม่ต้องเรนเดอร์ใหม่ในแต่ละคำขอของนักเรียน.  
5. **Legal services** – เร่งการแจกจ่ายไฟล์คดีขณะรักษาต้นทุนการจัดเก็บให้ต่ำ.

## ข้อควรพิจารณาด้านประสิทธิภาพ

- **ปรับจูน Redis** – ปรับ `maxmemory`, เลือกนโยบายการกำจัดเช่น `allkeys-lru`, และตั้งค่า `timeout` ที่เหมาะสมตามรูปแบบการจราจรของคุณ.  
- **ติดตามอัตราการ hit/miss ของแคช** – ใช้ `INFO stats` หรือคานเตอร์ `keyspace_hits` / `keyspace_misses` ของ Redis เพื่อปรับ TTL ให้เหมาะสม.  
- **การกำหนดขนาด heap ของ JVM** – ตรวจสอบให้แน่ใจว่า heap สามารถรองรับบัฟเฟอร์ของ GroupDocs; กฎโดยประมาณคือ 1 GB heap ต่อ 100 MB ของ payload การแปลงพร้อมกัน.  
- **การแปลงแบบแบตช์** – เมื่อแปลงไฟล์หลายไฟล์, ใช้ `Jedis` อินสแตนซ์เดียวต่อเธรดเพื่อให้การใช้ซ็อกเก็ตน้อยที่สุด.

## คำถามที่พบบ่อย

**Q: สามารถใช้วิธีนี้กับฟอร์แมตผลลัพธ์ของ GroupDocs อื่นได้หรือไม่?**  
A: แน่นอน. รูปแบบแคชเดียวกันทำงานได้กับ DOCX, HTML, ภาพ, และอื่น ๆ – เพียงเปลี่ยนประเภท `ConvertOptions`.

**Q: จะเลือกคีย์แคชที่ดีอย่างไร?**  
A: รวมเส้นทางไฟล์ต้นทาง, ตัวเลือกการแปลง, และตัวระบุเวอร์ชันใด ๆ. วิธีนี้รับประกันความเป็นเอกลักษณ์ตามการกำหนดค่า.

**Q: ถ้าเอกสารมีการเปลี่ยนแปลงหลังจากที่แคชแล้วจะทำอย่างไร?**  
A: ทำการลบแคชด้วยตนเอง (เช่น ลบคีย์) หรือใช้ TTL ที่สั้นกว่าเพื่อให้ข้อมูลที่ล้าสมัยหมดอายุเร็วขึ้น.

**Q: Redis เป็นตัวเลือกเดียวสำหรับการแคชหรือไม่?**  
A: ไม่, แต่ Redis มีความหน่วงต่ำ, มี TTL ในตัว, และรองรับไคลเอนต์ Java อย่างกว้างขวาง, ทำให้เป็นตัวเลือกยอดนิยมสำหรับสถานการณ์นี้.

**Q: วิธีนี้ทำให้การใช้หน่วยความจำบนเซิร์ฟเวอร์แอปพลิเคชันเพิ่มขึ้นหรือไม่?**  
A: น้อยมาก. งานหนักทำโดย Redis; แอปเพียงเก็บการเชื่อมต่อสั้น ๆ ผ่าน Jedis.

## สรุป
คุณมีบทแนะนำ **java redis caching** ครบถ้วนที่แสดงวิธีแคชเอกสารด้วย Redis และ GroupDocs.Conversion. โดยการเก็บผลลัพธ์ที่เรนเดอร์ไว้ใน Redis, คุณจะ **เพิ่มประสิทธิภาพการเรนเดอร์**, **ลดเวลาแปลง**, และมอบประสบการณ์ที่ราบรื่นให้กับผู้ใช้ปลายทาง. ทดลองกับค่า TTL ต่าง ๆ, ตรวจสอบเมตริกของแคช, และขยายรูปแบบนี้ไปยังฟอร์แมตเอกสารอื่น ๆ ตามการเติบโตของแอปพลิเคชันของคุณ.

---

**อัปเดตล่าสุด:** 2026-10-21  
**ทดสอบกับ:** GroupDocs.Conversion 25.2, Jedis 4.2.3  
**ผู้เขียน:** GroupDocs

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

```java
import redis.clients.jedis.JedisPool;

public class CacheManager {
    private static JedisPool jedisPool = new JedisPool("localhost", 6379);
    
    public static void main(String[] args) {
        // Additional cache setup code here
    }
}
```

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

## บทแนะนำที่เกี่ยวข้อง

- [การสร้างแคชแบบกำหนดเองใน Java – แคช GroupDocs Conversion](/conversion/java/cache-management/)
- [วิธีใช้แคช Redis ใน Java กับ GroupDocs.Conversion](/conversion/java/cache-management/redis-cache-java-groupdocs-conversion-guide/)
- [วิธีแคชไฟล์ใน Java กับ GroupDocs.Conversion – คู่มือครบวงจรสำหรับการแปลงเอกสารอย่างมีประสิทธิภาพ](/conversion/java/cache-management/implement-java-file-caching-groupdocs-conversion-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}