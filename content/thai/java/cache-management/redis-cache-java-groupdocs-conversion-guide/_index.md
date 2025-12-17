---
date: '2025-12-17'
description: เรียนรู้ตัวอย่างการใช้แคช Redis ใน Java ที่ช่วยเพิ่มประสิทธิภาพของแอปพลิเคชัน
  Java ของคุณโดยการผสานแคช Redis กับ GroupDocs.Conversion รวมถึงการกำหนดคีย์พรีฟิกซ์ของแคช
  Redis, การตั้งค่า, กลยุทธ์การแคช, และเคล็ดลับด้านประสิทธิภาพ.
keywords:
- Redis Cache Java
- GroupDocs.Conversion for Java
- Java caching
title: ตัวอย่างแคช Redis ใน Java พร้อมคู่มือ GroupDocs.Conversion
type: docs
url: /th/java/cache-management/redis-cache-java-groupdocs-conversion-guide/
weight: 1
---

# ตัวอย่าง Java Redis Cache กับคู่มือ GroupDocs.Conversion

Redis เป็นที่เก็บข้อมูลแบบ in‑memory ที่สามารถทำหน้าที่เป็นฐานข้อมูล, แคช, และ message broker ได้ เมื่อคุณผสานมันกับ GroupDocs.Conversion สำหรับ Java คุณจะได้การผสานที่ทรงพลังซึ่งทำให้การแปลงเอกสารเร็วขึ้นอย่างมาก ในบทแนะนำนี้คุณจะได้เห็น **java redis cache example** ที่แสดงวิธีตั้งค่า Redis, เชื่อมต่อกับ GroupDocs.Conversion, และปรับแต่งแคชโดยใช้ **redis cache key prefix** เมื่อจบคุณจะเข้าใจว่ารูปแบบนี้สำคัญอย่างไรและจะนำไปใช้ในโครงการจริงได้อย่างไร

## Quick Answers
- **What is the primary benefit?** ลดการแปลงเอกสารซ้ำซ้อนและลดเวลาตอบสนอง  
- **Do I need a license?** ใช่, GroupDocs.Conversion ต้องการใบอนุญาตที่ถูกต้องสำหรับการใช้งานในสภาพแวดล้อมการผลิต  
- **Which Redis client is used?** ตัวอย่างนี้ใช้ไลบรารี StackExchange.Redis (แสดงในโค้ด)  
- **Can I run Redis locally?** แน่นอน—ติดตั้งบนเครื่องพัฒนาของคุณหรือใช้อินสแตนซ์ระยะไกล  
- **Is the cache thread‑safe?** คลาส `RedisCache` ที่ให้มาจัดการการเชื่อมต่ออย่างปลอดภัยสำหรับสถานการณ์เว็บทั่วไป  

## Introduction

ลองนึกภาพพอร์ทัลที่มีการเข้าชมสูงที่ให้ผู้ใช้ดูไฟล์ PDF ที่สร้างจากไฟล์ Word, Excel หรือ PowerPoint หากไม่มีการแคช ทุกคำขอจะทำให้ GroupDocs.Conversion ต้องประมวลผลเอกสารต้นฉบับเดียวกันใหม่ซ้ำ ทำให้ใช้ CPU มากและเพิ่มความล่าช้า โดยการใส่ **java redis cache example** เข้าไปในขั้นตอนการแปลง คุณจะเก็บอาร์เรย์ไบต์ที่ได้ไว้ครั้งเดียวและให้บริการทันทีในคำขอถัดไป สิ่งนี้ไม่เพียงปรับปรุงประสบการณ์ผู้ใช้ แต่ยังลดค่าใช้จ่ายโครงสร้างพื้นฐาน  

## What is a java redis cache example?

**java redis cache example** แสดงให้เห็นว่าโค้ด Java สามารถโต้ตอบกับเซิร์ฟเวอร์ Redis เพื่อจัดเก็บและดึงอ็อบเจ็กต์—ในกรณีของเราเป็นผลลัพธ์ของการแปลงเอกสาร รูปแบบนี้มักประกอบด้วย:

1. สร้างคีย์แคชที่ไม่ซ้ำ (มักอิงจากชื่อไฟล์, ตัวเลือกการแปลง, และ **redis cache key prefix**)  
2. ตรวจสอบ Redis ว่ามีรายการที่มีอยู่หรือไม่ก่อนเรียกใช้เอนจินการแปลง  
3. บันทึกผลลัพธ์การแปลงกลับไปยัง Redis เพื่อใช้ในครั้งต่อไป  

## Why use Redis with GroupDocs.Conversion?

- **Speed:** การอ่านจากหน่วยความจำเร็วกว่าการอ่านจากดิสก์หลายระดับคำสั่ง  
- **Scalability:** อินสแตนซ์แอปพลิเคชันหลายตัวสามารถแชร์แคชเดียวกัน ทำให้สามารถสเกลแนวนอนได้  
- **Flexibility:** Redis รองรับนโยบายการขับออก (LRU, TTL) ที่ช่วยควบคุมขนาดแคช  

## Prerequisites

### Required Libraries and Dependencies
1. **Java Development Kit (JDK):** เวอร์ชัน 8 หรือใหม่กว่า  
2. **Redis Server:** ทำงานบนเครื่องท้องถิ่น (`localhost:6379`) หรือเข้าถึงได้จากระยะไกล  
3. **GroupDocs.Conversion for Java:** เพิ่มผ่าน Maven (ดูส่วนต่อไป)  

### Environment Setup
- ติดตั้ง Redis ตาม [this guide](https://redis.io/download).  
- ตั้งค่า IDE ของคุณ (IntelliJ IDEA, Eclipse ฯลฯ) ให้ใช้ JDK ที่เหมาะสม  

### Knowledge Prerequisites
- แนวคิดพื้นฐานของ Java และ OOP  
- ความคุ้นเคยกับ Maven สำหรับการจัดการ dependencies  
- ความเข้าใจพื้นฐานของการแคช  

## Setting Up GroupDocs.Conversion for Java

### Maven Setup
เพิ่ม repository และ dependency ลงในไฟล์ `pom.xml` ของคุณ:

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

### License Acquisition
1. **Free Trial:** ลงทะเบียนที่ [GroupDocs](https://releases.groupdocs.com/conversion/java/) เพื่อดาวน์โหลดเวอร์ชันทดลอง  
2. **Temporary License:** ขอใบอนุญาตชั่วคราวสำหรับการประเมินระยะยาวจาก [purchase page](https://purchase.groupdocs.com/temporary-license/)  
3. **Purchase:** สำหรับการใช้งานเชิงพาณิชย์ ให้ซื้อใบอนุญาตผ่าน [buy page](https://purchase.groupdocs.com/buy)  

### Initializing the Converter
```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.convert.ConvertOptions;

// Initialize the Converter object with a document path
Converter converter = new Converter("path/to/your/document");
```

## Implementation Guide

### Redis Cache Integration Overview
เราจะสร้างคลาส `RedisCache` แบบกำหนดเองที่ implements `ICache`. คลาสนี้จะจัดการการ serialization, การจัดการคีย์ (รวมถึง **redis cache key prefix**), และการดำเนินการ CRUD พื้นฐานต่อ Redis  

#### Step 1: Create RedisCache Class
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

#### Step 2: Using Redis Cache with GroupDocs.Conversion
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

### Configuring redis cache key prefix
ฟิลด์ `_cacheKeyPrefix` ให้คุณจัดกลุ่มรายการที่เกี่ยวข้อง (เช่น `"GroupDocs:"`). ปรับค่าตามแนวทางการตั้งชื่อของคุณหรือความต้องการแบบหลายผู้เช่า  

## Key Configuration Options
- **_cacheKeyPrefix:** ปรับแต่งเพื่อจัดระเบียบคีย์แคชอย่างมีประสิทธิภาพ  
- **ConnectionMultiplexer settings:** ปรับให้เหมาะสมสำหรับการ pool การเชื่อมต่อ, SSL, หรือคลัสเตอร์ Redis แบบกระจาย  

## Practical Applications
1. **Document Conversion Workflows:** แคช PDF, รูปภาพ หรือ HTML ที่แปลงแล้วเพื่อหลีกเลี่ยงการประมวลผลซ้ำ  
2. **Content Delivery Networks (CDNs):** ให้บริการเอกสารที่แคชจากตำแหน่ง edge เพื่อการเข้าถึงที่เร็วขึ้น  
3. **Batch Processing Systems:** เก็บผลลัพธ์ระหว่างขั้นตอน ทำให้ pipeline สามารถทำต่อได้  

## Performance Considerations

### Optimizing Redis Cache Usage
- **Memory Management:** ตั้งค่า `maxmemory` และนโยบายการขับออกที่เหมาะสม (เช่น `volatile-lru`)  
- **Eviction Policies:** เลือก LRU, LFU หรือ TTL ตามรูปแบบการใช้งานของคุณ  
- **Serialization Overhead:** พิจารณาใช้ binary serializer (เช่น Kryo) สำหรับ payload ขนาดใหญ่  

### Java Memory Management with GroupDocs.Conversion
จัดการไฟล์ขนาดใหญ่โดยสตรีมการแปลงโดยตรงไปยัง `ByteArrayOutputStream` และทำลาย `Converter` อย่างทันท่วงทีเพื่อปล่อยทรัพยากรเนทีฟ  

## Frequently Asked Questions

**Q: What if the Redis server goes down?**  
A: โค้ดจะย้อนกลับไปทำการแปลงใหม่เมื่อ `TryGetValue` คืนค่า false เพื่อให้การทำงานต่อเนื่อง  

**Q: Can I use a different Redis client library?**  
A: ใช่, คลาส `RedisCache` เป็นตัวอย่างง่าย ๆ; คุณสามารถแทนที่ `StackExchange.Redis` ด้วย Lettuce, Jedis หรือไคลเอนต์ Redis ของ Java ใดก็ได้  

**Q: How do I set an expiration time for cached items?**  
A: ใช้ overload ของ `StringSet` ของ Redis ที่รับ `TimeSpan`/`Duration` เพื่อกำหนด TTL ให้กับแต่ละรายการ  

**Q: Is the cache thread‑safe in a web application?**  
A: `ConnectionMultiplexer` พื้นฐานออกแบบมาสำหรับการใช้พร้อมกัน ทำให้แคชปลอดภัยสำหรับคอนเทนเนอร์ servlet ทั่วไป  

**Q: Do I need to serialize objects manually?**  
A: ตัวอย่างใช้การ serialization ในตัวของ Java. สำหรับการผลิต ควรพิจารณาใช้รูปแบบที่มีประสิทธิภาพมากขึ้นเช่น Protocol Buffers หรือ JSON  

## Conclusion
คุณได้สร้าง **java redis cache example** ที่ผสาน Redis กับ GroupDocs.Conversion, เรียนรู้วิธีตั้งค่า **redis cache key prefix**, และสำรวจแนวทางปฏิบัติที่ดีที่สุดสำหรับการปรับจูนหน่วยความจำและประสิทธิภาพ รูปแบบนี้สามารถขยายไปยังรูปแบบการแปลงอื่น ๆ, สถาปัตยกรรมหลายผู้เช่า, หรือการปรับใช้แบบคลาวด์เนทีฟ  

**Next Steps**  
- ทดลองใช้นโยบายการขับออกและค่า TTL ที่แตกต่างกัน  
- ทำ profiling แอปพลิเคชันเพื่อระบุคอขวดเพิ่มเติม  
- สำรวจ Redis Cluster สำหรับสถานการณ์ที่ต้องการความพร้อมใช้งานสูง  

---

**Last Updated:** 2025-12-17  
**Tested With:** GroupDocs.Conversion 25.2  
**Author:** GroupDocs