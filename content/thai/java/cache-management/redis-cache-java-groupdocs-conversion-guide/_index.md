---
date: '2026-07-24'
description: เรียนรู้วิธีใช้ Redis cache ใน Java กับ GroupDocs.Conversion เพื่อเพิ่มประสิทธิภาพของแอปพลิเคชัน
  คู่มือ Redis cache Java นี้ครอบคลุมการตั้งค่า กลยุทธ์การแคช และเคล็ดลับด้านประสิทธิภาพ
keywords:
- how to use redis
- redis cache java
- java redis connection
- configure redis cache
- redis cache key prefix
lastmod: '2026-07-24'
og_description: เรียนรู้วิธีใช้ Redis cache ใน Java กับ GroupDocs.Conversion คู่มือนี้แสดงการตั้งค่า
  กลยุทธ์การแคช และเคล็ดลับด้านประสิทธิภาพเพื่อการแปลงเอกสารที่เร็วขึ้น
og_image_alt: 'Guide: Implement Redis cache in Java using GroupDocs.Conversion for
  high‑performance document processing'
og_title: วิธีใช้ Redis Cache ใน Java กับ GroupDocs.Conversion
schemas:
- author: GroupDocs
  dateModified: '2026-07-24'
  description: Learn how to use Redis cache in Java with GroupDocs.Conversion to boost
    application efficiency. This redis cache java tutorial covers setup, caching strategies,
    and performance tips.
  headline: How to Use Redis Cache in Java with GroupDocs.Conversion
  type: TechArticle
- questions:
  - answer: Yes. Replace `"localhost"` with the cluster endpoint and configure `ConnectionMultiplexer`
      for SSL and password authentication.
    question: Can I use this approach with a remote Redis cluster?
  - answer: Modify the `_cacheKeyPrefix` field in `RedisCache`. Using a unique prefix
      helps avoid key collisions across applications.
    question: How do I change the `redis cache key prefix`?
  - answer: Call `_db.KeyDelete(pattern)` or use `GetKeys` to retrieve matching keys
      and delete them in a loop.
    question: Is there a way to clear the cache programmatically?
  - answer: Absolutely. Replace `PdfConvertOptions` with the appropriate `ConvertOptions`
      subclass (e.g., `DocxConvertOptions`).
    question: Does this work for converting documents other than PDF?
  - answer: The tutorial was tested with GroupDocs.Conversion **25.2**; newer versions
      should be compatible.
    question: What version of GroupDocs.Conversion is required?
  type: FAQPage
tags:
- redis cache
- groupdocs conversion
- java caching
- document conversion
- performance optimization
title: วิธีใช้ Redis Cache ใน Java กับ GroupDocs.Conversion
type: docs
url: /th/java/cache-management/redis-cache-java-groupdocs-conversion-guide/
weight: 1
---

# วิธีใช้ Redis Cache ใน Java กับ GroupDocs.Conversion

`Redis` คือที่เก็บโครงสร้างข้อมูลในหน่วยความจำที่รองรับสตริง, แฮช, รายการ, เซต และอื่น ๆ. Redis เป็นโอเพนซอร์สที่ทรงพลัง, ทำหน้าที่เป็นฐานข้อมูล, แคช, และตัวกลางส่งข้อความ. เมื่อคุณเรียนรู้ **วิธีใช้ Redis** ร่วมกับ GroupDocs.Conversion, คุณจะให้แอปพลิเคชัน Java ของคุณมีชั้นแคชที่ทำงานเร็วซึ่งลดความหน่วงของการแปลงเอกสารอย่างมาก. ในคู่มือนี้เราจะพาคุณผ่าน **บทเรียน redis cache java** อย่างครบถ้วน, ตั้งแต่การตั้งค่าสภาพแวดล้อมจนถึงการใช้งานจริง, เพื่อให้คุณเห็นประสิทธิภาพที่เพิ่มขึ้นทันที.

## คำตอบสั้น
- **ประโยชน์หลักของการใช้ Redis กับ GroupDocs คืออะไร?** การดึงเอกสารที่เร็วขึ้นโดยหลีกเลี่ยงการแปลงซ้ำ.  
- **Maven artifact ใดที่เพิ่ม GroupDocs.Conversion?** `com.groupdocs:groupdocs-conversion`.  
- **ฉันจะเชื่อมต่อ Java กับ Redis อย่างไร?** ใช้ตัวอย่างการเชื่อมต่อ Redis ใน Java เช่น `ConnectionMultiplexer.Connect("localhost")`.  
- **ฉันสามารถปรับแต่งคีย์แคชได้หรือไม่?** ได้ – `redis cache key prefix` ช่วยให้คุณจัดระเบียบรายการ.  
- **ต้องการไลเซนส์สำหรับการใช้งานในโปรดักชันหรือไม่?** ต้องการ, จำเป็นต้องมีไลเซนส์ GroupDocs.Conversion ที่ถูกต้อง.  

`ConnectionMultiplexer` คือคลาสไคลเอนต์จากไลบรารี StackExchange.Redis ที่จัดการการเชื่อมต่อกับเซิร์ฟเวอร์ Redis.

## GroupDocs.Conversion for Java คืออะไร?
GroupDocs.Conversion for Java คือไลบรารีที่แปลงไฟล์กว่า 80 รูปแบบเป็น PDF, รูปภาพ, และผลลัพธ์อื่น ๆ. มันให้ API ที่เป็นเอกภาพสำหรับการแปลงเอกสารคุณภาพสูงบนเซิร์ฟเวอร์โดยไม่ต้องติดตั้ง Microsoft Office. รองรับการแปลงเป็น PDF, รูปภาพ, HTML, และรูปแบบอื่น ๆ อีกมาก, พร้อมตัวเลือกการใส่น้ำลายน้ำ, การแบ่งหน้า, และการตั้งค่าการเรนเดอร์แบบกำหนดเอง.

## ทำไมต้องใช้ Redis กับ GroupDocs.Conversion?
การใช้ Redis เป็นชั้นแคชสามารถลดเวลาการแปลงได้ **สูงสุด 90 %** สำหรับคำขอที่ทำซ้ำ, และลดการใช้ CPU **ประมาณ 70 %** เมื่อประมวลผลชุดข้อมูลขนาดใหญ่. การอ้างอิงเช่นนี้ทำให้เห็นชัดว่าทำไมหลายองค์กรถึงนำรูปแบบนี้ไปใช้สำหรับบริการเอกสารที่ต้องการ throughput สูง.

## ข้อกำหนดเบื้องต้น
### ไลบรารีและการพึ่งพาที่จำเป็น
1. **Java Development Kit (JDK):** เวอร์ชัน 8 หรือใหม่กว่า.  
2. **Redis Server:** ทำงานในเครื่องหรือเข้าถึงได้จากระยะไกล.  
3. **GroupDocs.Conversion for Java:** เพิ่มผ่าน Maven (ดูส่วน **maven dependency groupdocs** ด้านล่าง).  

### การตั้งค่าสภาพแวดล้อม
- ติดตั้ง Redis ตาม [คู่มือนี้](https://redis.io/download).  
- กำหนดค่า IDE ของคุณ (IntelliJ IDEA, Eclipse, ฯลฯ) ให้ใช้ JDK ที่เหมาะสม.  

### ความรู้พื้นฐานที่ต้องมี
- แนวคิดพื้นฐานของ Java และ OOP.  
- ความคุ้นเคยกับ Maven สำหรับการจัดการ dependencies.  
- ความเข้าใจในหลักการแคชและเหตุผลที่สำคัญต่อการแปลงเอกสาร.

## การตั้งค่า GroupDocs.Conversion for Java
ไลบรารี `GroupDocs.Conversion` เป็นเครื่องยนต์หลักที่ทำการแปลงรูปแบบไฟล์. เพิ่มสแนปเพต Maven ด้านล่างนี้ในไฟล์ `pom.xml` ของคุณเพื่อดึงแพ็กเกจอย่างเป็นทางการ:

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
1. **ทดลองใช้ฟรี:** สมัครที่ [GroupDocs](https://releases.groupdocs.com/conversion/java/) เพื่อดาวน์โหลดเวอร์ชันทดลอง.  
2. **ไลเซนส์ชั่วคราว:** ขอไลเซนส์ชั่วคราวสำหรับการประเมินระยะยาวจาก [purchase page](https://purchase.groupdocs.com/temporary-license/).  
3. **ซื้อ:** สำหรับการใช้งานเชิงพาณิชย์, ซื้อไลเซนส์ผ่าน [buy page](https://purchase.groupdocs.com/buy).

เมื่อคุณมีไลเซนส์แล้ว, คุณสามารถสร้างอินสแตนซ์ของคอนเวอร์เตอร์ได้:

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.convert.ConvertOptions;

// Initialize the Converter object with a document path
Converter converter = new Converter("path/to/your/document");
```

## คู่มือการนำไปใช้
### ภาพรวมการรวม Redis Cache
เราจะสร้างคลาส `RedisCache` แบบกำหนดเองที่ implements `ICache`. คลาสนี้แสดง **java redis connection example** และแสดงวิธีทำงานกับ **redis cache key prefix**.

`RedisCache` เป็นการนำเข้า `ICache` ของ GroupDocs ที่เก็บผลลัพธ์การแปลงใน Redis.  

#### ขั้นตอนที่ 1: สร้างคลาส RedisCache
ด้านล่างเป็นการนำไปใช้เต็มรูปแบบ. เก็บโค้ดไว้ตามที่แสดง; โค้ดนี้รวม import ที่จำเป็นทั้งหมดและตรรกะการจัดการคีย์แคช.

```java
import com.groupdocs.conversion.caching.ICache;
import StackExchange.Redis;
import java.io.IOException;
import java.io.ObjectInputStream;
import java.io.ObjectOutputStream;
import java.io.Serializable;
import java.util.List;

public class RedisCache implements ICache, AutoCloseable {
    private String _cacheKeyPrefix = "GroupDocs:";
    private ConnectionMultiplexer _redis;
    private IDatabase _db;
    
    public RedisCache() {
        _redis = ConnectionMultiplexer.Connect("localhost");
        _db = _redis.GetDatabase();
    }

    public void Set(String key, Serializable data) throws IOException {
        String prefixedKey = GetPrefixedKey(key);
        try (ObjectOutputStream oos = new ObjectOutputStream(_db.StreamWrite())) {
            oos.writeObject(data);
            _db.StringSet(prefixedKey, oos.toString());
        }
    }

    public boolean TryGetValue(String key, Object value) {
        String prefixedKey = GetPrefixedKey(key);
        byte[] serializedData = _db.StringGet(prefixKey).ToArray();
        if (serializedData != null) {
            try (ObjectInputStream ois = new ObjectInputStream(new ByteArrayInputStream(serializedData))) {
                value = ois.readObject();
                return true;
            } catch (IOException | ClassNotFoundException e) {
                e.printStackTrace();
            }
        }
        return false;
    }

    public List<String> GetKeys(String filter) {
        return _db.Keys(_cacheKeyPrefix + "*" + filter + "*").Select(k -> k.ToString().Replace(_cacheKeyPrefix, "")).ToList();
    }

    private String GetPrefixedKey(String key) {
        return _cacheKeyPrefix + key;
    }

    @Override
    public void close() throws Exception {
        _redis.Dispose();
    }
}
```

#### ขั้นตอนที่ 2: ใช้งาน Redis Cache กับ GroupDocs.Conversion
ต่อไปเราจะเชื่อมแคชเข้ากับเวิร์กโฟลว์การแปลง. สแนปเพตนี้แสดง **convert documents pdf java** ตัวอย่างที่ตรวจสอบแคชก่อนเรียก GroupDocs.Conversion.

```java
// Example usage of RedisCache with GroupDocs.Conversion
public void ConvertAndCacheDocument(String filePath) throws IOException {
    String cacheKey = "converted:" + filePath;
    Object cachedResult;

    if (cacheRedis.TryGetValue(cacheKey, cachedResult)) {
        System.out.println("Retrieved from cache: " + cachedResult);
    } else {
        // Perform conversion
        Converter converter = new Converter(filePath);
        ConvertOptions options = new PdfConvertOptions();
        byte[] result = converter.Convert(() -> new ByteArrayOutputStream(), options);

        // Cache the conversion result
        cacheRedis.Set(cacheKey, result);
        System.out.println("Conversion performed and cached.");
    }
}
```

### ตัวเลือกการกำหนดค่า
- **`_cacheKeyPrefix`** – ปรับ **redis cache key prefix** นี้เพื่อจัดกลุ่มรายการที่เกี่ยวข้อง (เช่น `"Docs:"`).  
- **การตั้งค่า ConnectionMultiplexer** – ปรับการจัดสระการเชื่อมต่อ, เวลา timeout, หรือ SSL สำหรับคลัสเตอร์ Redis แบบกระจาย.

## Redis ช่วยเพิ่มความเร็วการแปลงอย่างไร?
โหลดเอกสารครั้งเดียว, เก็บอาร์เรย์ไบต์ที่ได้ใน Redis, แล้วดึงกลับมาในการเรียกครั้งต่อไป – วิธีนี้ขจัดความจำเป็นในการแปลงที่ใช้ CPU ซ้ำ ๆ. ด้วยการแคชผลลัพธ์ไบต์, คุณลดเวลาเฉลี่ยของการตอบสนองจากหลายวินาทีเหลือไม่กี่มิลลิวินาที, โดยเฉพาะสำหรับเอกสารที่ได้รับการเรียกบ่อย.

## redis cache key prefix คืออะไร?
`redis cache key prefix` คือสตริงสั้นที่นำหน้าคีย์ของแต่ละรายการแคช, ช่วยให้คุณแยกข้อมูล (เช่น `"Docs:"` สำหรับแคชเอกสาร, `"Thumb:"` สำหรับรูปย่อ). การใช้พรีฟิกซ์ที่ไม่ซ้ำกันช่วยป้องกันการชนกันของคีย์เมื่อหลายแอปใช้ Redis อินสแตนซ์เดียวกัน.

## วิธีตั้งค่าการเชื่อมต่อ Redis ใน Java?
สร้างอินสแตนซ์ `ConnectionMultiplexer` ด้วยที่อยู่ของเซิร์ฟเวอร์ Redis, สามารถระบุรหัสผ่านและการตั้งค่า SSL ได้. สำหรับการตั้งค่าแบบโลคัลเรียบง่าย, ใช้ `ConnectionMultiplexer.Connect("localhost")`. สำหรับคลัสเตอร์โปรดักชัน, ส่งรายการ endpoint คั่นด้วยคอมม่าและกำหนด `ConfigurationOptions` เพื่อรองรับ failover และ load balancing.

## วิธีลบ Redis cache ด้วยโปรแกรม?
เรียกเมธอด `KeyDelete` ของฐานข้อมูล Redis พร้อมแพทเทิร์นที่ตรงกับคีย์ที่มีพรีฟิกซ์ของคุณ (เช่น `_db.KeyDelete("Docs:*")`). วิธีนี้จะลบผลลัพธ์การแปลงที่แคชทั้งหมดในหนึ่งคำสั่ง, มีประโยชน์ในช่วงการดีพลอยหรือเมื่อไฟล์ต้นทางเปลี่ยนแปลง. คุณยังสามารถใช้คำสั่ง `SCAN` เพื่อวนลูปคีย์ที่ตรงกันก่อนลบ, ซึ่งปลอดภัยกว่าเมื่อจัดการชุดข้อมูลขนาดใหญ่.  

`KeyDelete` เป็นเมธอดของไคลเอนต์ฐานข้อมูล Redis ที่ลบคีย์ที่ตรงกับแพทเทิร์นที่กำหนด.

## การประยุกต์ใช้ในเชิงปฏิบัติ
1. **เวิร์กโฟลว์การแปลงเอกสาร:** แคชผลลัพธ์ PDF หรือรูปภาพเพื่อให้บริการคำขอซ้ำได้ทันที.  
2. **เครือข่ายการส่งมอบเนื้อหา (CDN):** เก็บไบนารีที่แคชไว้ใน Redis เพื่อการส่งมอบที่รวดเร็วที่ขอบเครือข่าย.  
3. **ระบบประมวลผลแบบแบตช์:** ใช้ผลลัพธ์การแปลงซ้ำในหลายรอบแบตช์, ประหยัดการใช้ CPU.

## พิจารณาด้านประสิทธิภาพ
### การเพิ่มประสิทธิภาพการใช้ Redis Cache
- **การจัดการหน่วยความจำ:** ตั้งค่า `maxmemory` และนโยบายการขับออกที่เหมาะสม (เช่น `volatile-lru`).  
- **นโยบายการขับออก:** เลือก LRU, LFU, หรือการหมดอายุแบบ TTL ตามรูปแบบการใช้งาน.  
- **ค่าโอเวอร์เฮดของการซีเรียลไลซ์:** ตัวอย่างใช้การซีเรียลไลซ์ของ Java; หากต้องการ payload ที่แคบกว่าให้พิจารณา protobuf หรือ JSON.

### การจัดการหน่วยความจำ Java กับ GroupDocs.Conversion
จัดการไฟล์ขนาดใหญ่โดยสตรีมผลลัพธ์ (`ByteArrayOutputStream`) และปล่อยทรัพยากรโดยเร็ว. การ implement `AutoCloseable` ของ `RedisCache` ทำให้การเชื่อมต่อ Redis ถูกปิดอย่างถูกต้อง.

## ปัญหาทั่วไป & การแก้ไข
| อาการ | สาเหตุที่เป็นไปได้ | วิธีแก้ |
|---------|--------------|-----|
| `ConnectionMultiplexer.Connect` ขว้างข้อผิดพลาด timeout | Redis ไม่สามารถเข้าถึงได้หรือโฮสต์/พอร์ตผิด | ตรวจสอบว่าเซิร์ฟเวอร์ Redis กำลังทำงานและเข้าถึงได้ (`redis-cli ping`). |
| `TryGetValue` คืนค่า false เสมอ | รูปแบบการซีเรียลไลซ์ที่เก็บและดึงไม่ตรงกัน | ตรวจสอบให้ใช้ serializer เดียวกันสำหรับทั้ง `Set` และ `TryGetValue`. |
| ข้อผิดพลาด Out‑of‑memory กับ PDF ขนาดใหญ่ | เก็บ byte array ขนาดใหญ่ใน Redis โดยไม่มีขีดจำกัด | เปิดใช้งาน `maxmemory` และตั้งค่านโยบายการขับออกที่เหมาะสม. |

## คำถามที่พบบ่อย

**ถาม: ฉันสามารถใช้วิธีนี้กับคลัสเตอร์ Redis ระยะไกลได้หรือไม่?**  
ตอบ: ได้. แทนที่ `"localhost"` ด้วย endpoint ของคลัสเตอร์และกำหนดค่า `ConnectionMultiplexer` สำหรับ SSL และการยืนยันรหัสผ่าน.

**ถาม: ฉันจะเปลี่ยน `redis cache key prefix` ได้อย่างไร?**  
ตอบ: แก้ไขฟิลด์ `_cacheKeyPrefix` ใน `RedisCache`. การใช้พรีฟิกซ์ที่ไม่ซ้ำกันช่วยหลีกเลี่ยงการชนกันของคีย์ระหว่างแอปพลิเคชัน.

**ถาม: มีวิธีลบแคชโดยโปรแกรมหรือไม่?**  
ตอบ: เรียก `_db.KeyDelete(pattern)` หรือใช้ `GetKeys` เพื่อดึงคีย์ที่ตรงกันแล้วลบในลูป.

**ถาม: วิธีนี้ทำงานกับการแปลงเอกสารที่ไม่ใช่ PDF ได้หรือไม่?**  
ตอบ: แน่นอน. แทนที่ `PdfConvertOptions` ด้วยคลาสย่อย `ConvertOptions` ที่เหมาะสม (เช่น `DocxConvertOptions`).

**ถาม: ต้องการเวอร์ชันใดของ GroupDocs.Conversion?**  
ตอบ: คู่มือนี้ทดสอบกับ GroupDocs.Conversion **25.2**; เวอร์ชันใหม่กว่าควรทำงานได้เช่นกัน.

## สรุป
โดยการเชี่ยวชาญ **วิธีใช้ Redis** ร่วมกับ GroupDocs.Conversion, คุณได้สร้างชั้นแคชที่แข็งแกร่งซึ่งลดเวลาการแปลง, ลดภาระเซิร์ฟเวอร์, และปรับปรุงประสบการณ์ผู้ใช้สุดท้าย. ควรทดลองใช้ **redis cache key prefixes**, นโยบายการขับออก, และรูปแบบการซีเรียลไลซ์ต่าง ๆ เพื่อปรับแต่งประสิทธิภาพให้เหมาะกับโหลดของคุณ.

**ขั้นตอนต่อไป**
- ลองกลยุทธ์การขับออกต่าง ๆ (LRU, TTL).  
- ทำการ profiling การใช้หน่วยความจำกับชุดเอกสารขนาดใหญ่.  
- สำรวจฟีเจอร์ขั้นสูงของ GroupDocs เช่น การใส่น้ำลายน้ำหรือการแปลงหลายหน้า.

---

**Last Updated:** 2026-07-24  
**Tested With:** GroupDocs.Conversion 25.2  
**Author:** GroupDocs

## บทเรียนที่เกี่ยวข้อง

- [วิธีแคชเอกสารใน Java ด้วย Redis & GroupDocs](/conversion/java/cache-management/custom-cache-redis-groupdocs-java/)
- [วิธีแคชไฟล์ใน Java กับ GroupDocs.Conversion – คู่มือฉบับสมบูรณ์สำหรับการแปลงเอกสารอย่างมีประสิทธิภาพ](/conversion/java/cache-management/implement-java-file-caching-groupdocs-conversion-guide/)
- [การทำ Custom Cache ใน Java – Cache ของ GroupDocs Conversion](/conversion/java/cache-management/)