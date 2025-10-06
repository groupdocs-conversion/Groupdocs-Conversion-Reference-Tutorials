---
"date": "2025-04-28"
"description": "เรียนรู้วิธีปรับปรุงประสิทธิภาพแอปพลิเคชัน .NET ของคุณโดยการใช้แคช Redis แบบกำหนดเองสำหรับการแปลงเอกสารโดยใช้ GroupDocs.Conversion ปรับปรุงประสิทธิภาพและความเร็วได้แล้ววันนี้!"
"title": "เพิ่มประสิทธิภาพการทำงานของแอปพลิเคชัน .NET ด้วยการใช้ Redis Cache แบบกำหนดเองด้วย GroupDocs.Conversion"
"url": "/th/net/cache-management/boost-net-app-performance-custom-redis-cache-groupdocs/"
"weight": 1
type: docs
---
# เพิ่มประสิทธิภาพแอปพลิเคชัน .NET ของคุณด้วย Redis Caching แบบกำหนดเองโดยใช้ GroupDocs.Conversion

## การแนะนำ

คุณประสบปัญหากระบวนการแปลงเอกสารที่ช้าในแอปพลิเคชัน .NET ของคุณหรือไม่ เพิ่มประสิทธิภาพและประสิทธิผลด้วยการใช้แคช Redis แบบกำหนดเองควบคู่ไปกับ GroupDocs.Conversion สำหรับ .NET บทช่วยสอนนี้จะแนะนำคุณเกี่ยวกับการดำเนินการแคชเพื่อเพิ่มความเร็วในการแสดงผลเอกสาร

**สิ่งที่คุณจะได้เรียนรู้:**
- การตั้งค่า GroupDocs.Conversion สำหรับ .NET
- การนำแคช Redis แบบกำหนดเองมาใช้งานในการแปลงเอกสาร
- เพิ่มประสิทธิภาพการทำงานด้วยกลยุทธ์แคชที่มีประสิทธิภาพ

เราจะแนะนำคุณเกี่ยวกับการเพิ่มประสิทธิภาพแอปพลิเคชันของคุณโดยใช้เครื่องมืออันทรงพลังเหล่านี้ ก่อนที่เราจะเริ่ม ตรวจสอบให้แน่ใจว่าคุณเข้าใจข้อกำหนดเบื้องต้นแล้ว

## ข้อกำหนดเบื้องต้น

หากต้องการทำตามบทช่วยสอนนี้ ให้แน่ใจว่าคุณมี:

### ไลบรารีและเวอร์ชันที่จำเป็น:
- **GroupDocs.การแปลงสำหรับ .NET** (เวอร์ชัน 25.3.0)
- **แลกเปลี่ยน StackExchange** ห้องสมุดสำหรับการดำเนินงาน Redis
- อินสแตนซ์ที่กำลังทำงานของเซิร์ฟเวอร์ Redis (เช่น `192.168.222.4:6379`-

### ข้อกำหนดการตั้งค่าสภาพแวดล้อม:
- Visual Studio หรือ IDE อื่นที่เข้ากันได้ที่รองรับ C#
- ติดตั้ง .NET Framework หรือ .NET Core แล้ว

### ข้อกำหนดเบื้องต้นของความรู้:
- ความเข้าใจพื้นฐานเกี่ยวกับการเขียนโปรแกรม C# และ .NET
- ความคุ้นเคยกับ Redis ในฐานะโซลูชันแคช
- ประสบการณ์เกี่ยวกับกระบวนการแปลงเอกสารในแอปพลิเคชันซอฟต์แวร์

## การตั้งค่า GroupDocs.Conversion สำหรับ .NET

หากต้องการเริ่มใช้ GroupDocs.Conversion ให้ติดตั้งผ่านคอนโซลตัวจัดการแพ็กเกจ NuGet หรือ .NET CLI

**คอนโซลตัวจัดการแพ็กเกจ NuGet:**
```bash
Install-Package GroupDocs.Conversion -Version 25.3.0
```

**.NET CLI:**
```bash
dotnet add package GroupDocs.Conversion --version 25.3.0
```

### ขั้นตอนการรับใบอนุญาต:
- **ทดลองใช้งานฟรี:** ทดสอบคุณสมบัติและฟังก์ชันด้วยใบอนุญาตชั่วคราว
- **ใบอนุญาตชั่วคราว:** รับการประเมินขยายแบบไม่มีข้อจำกัด
- **ซื้อ:** หากต้องการใช้ในระยะยาว ควรพิจารณาซื้อใบอนุญาตเต็มรูปแบบ

หลังจากการติดตั้ง ให้เริ่มต้น GroupDocs.Conversion ในแอปพลิเคชัน C# ของคุณ:

```csharp
using GroupDocs.Conversion;
```

## คู่มือการใช้งาน

### การใช้งานแคชแบบกำหนดเองโดยใช้ Redis

หัวข้อนี้สาธิตการสร้างแคชแบบกำหนดเองโดยใช้ Redis สำหรับการดำเนินการแสดงผลเอกสารเพื่อปรับปรุงความเร็วและประสิทธิภาพในการแปลง

#### ภาพรวม
เราจะนำกลไกการแคชที่ใช้ Redis มาใช้ในการจัดเก็บเอกสารที่แสดงผล โดยหลีกเลี่ยงการประมวลผลซ้ำซ้อน และเพิ่มความเร็วของเวลาในการแปลงได้อย่างมาก

##### ขั้นตอนที่ 1: กำหนดคลาส RedisCache

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using StackExchange.Redis;

public class RedisCache : IDisposable
{
    private readonly string _cacheKeyPrefix;
    private readonly ConnectionMultiplexer _redis;
    private readonly IDatabase _db;
    private readonly string _host = "192.168.222.4:6379";

    public RedisCache(string cacheKeyPrefix)
    {
        _cacheKeyPrefix = cacheKeyPrefix;
        _redis = ConnectionMultiplexer.Connect(_host);
        _db = _redis.GetDatabase();
    }

    // ตั้งค่าข้อมูลในแคชด้วยคีย์เฉพาะ
    public void Set(string key, object data)
    {
        if (data == null) return;

        string prefixedKey = GetPrefixedKey(key);
        using (MemoryStream stream = new MemoryStream())
        {
            ((Stream)data).CopyTo(stream);
            _db.StringSet(prefixedKey, RedisValue.CreateFrom(stream));
        }
    }

    // ลองดึงข้อมูลจากแคชโดยใช้คีย์
    public bool TryGetValue(string key, out object value)
    {
        var prefixedKey = GetPrefixedKey(key);
        var redisValue = _db.StringGet(prefixedKey);

        if (redisValue.HasValue)
        {
            value = new MemoryStream(redisValue);
            return true;
        }

        value = default;
        return false;
    }

    // ดึงคีย์ทั้งหมดที่ตรงกับรูปแบบตัวกรองจากแคช
    public IEnumerable<string> GetKeys(string filter)
    {
        return _redis.GetServer(_host).Keys(pattern: $"*{filter}*")
            .Select(x => x.ToString().Replace(_cacheKeyPrefix, string.Empty))
            .Where(x => x.StartsWith(filter, StringComparison.InvariantCultureIgnoreCase))
            .ToList();
    }

    private string GetPrefixedKey(string key) => $"{_cacheKeyPrefix}{key}";

    public void Dispose()
    {
        _redis.Dispose();
    }
}
```

**คำอธิบาย:**
- **วิธีการตั้งค่า:** บันทึกข้อมูลใน Redis โดยใช้คีย์แคชเฉพาะ
- **วิธีการ TryGetValue:** ดึงข้อมูลแคช หากมี
- **วิธีการ GetKeys:** ดึงคีย์ที่ตรงกับรูปแบบที่ระบุ

##### ขั้นตอนที่ 2: นำการแปลงเอกสารไปใช้ด้วยแคชที่กำหนดเอง

```csharp
using System;
using System.Diagnostics;
using GroupDocs.Conversion.Options.Convert;
using GroupDocs.Conversion.Caching;

public class HowToUseCustomCacheImplementation
{
    public static void Run()
    {
        string outputDirectory = "YOUR_OUTPUT_DIRECTORY";
        
        RedisCache cache = new RedisCache("sample_");
        Func<ConverterSettings> settingsFactory = () => new ConverterSettings
        {
            Cache = cache
        };

        using (Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/SAMPLE_PDF", settingsFactory))
        {
            PdfConvertOptions options = new PdfConvertOptions();
            
            Stopwatch stopWatch = Stopwatch.StartNew();
            converter.Convert($"{outputDirectory}/converted.pdf", options);
            stopWatch.Stop();

            stopWatch.Restart();
            converter.Convert($"{outputDirectory}/converted-1.pdf", options);
            stopWatch.Stop();
        }
    }
}
```

**คำอธิบาย:**
- **การเริ่มต้น RedisCache:** ตั้งค่าแคชด้วยคำนำหน้าคีย์
- **การตั้งค่าตัวแปลง:** รวมแคชแบบกำหนดเองลงในการตั้งค่า GroupDocs.Conversion
- **กระบวนการแปลง:** วัดและสาธิตการปรับปรุงประสิทธิภาพด้วยการแคชผลลัพธ์การแปลง

## การประยุกต์ใช้งานจริง

### กรณีการใช้งาน:
1. **ระบบบริหารจัดการเอกสารองค์กร:** ปรับปรุงความเร็วในการเรนเดอร์เอกสารสำหรับแอปพลิเคชันขนาดใหญ่
2. **บริการเว็บไซต์:** ปรับปรุงเวลาตอบสนองสำหรับ API ที่ต้องจัดการกับการแปลง PDF บ่อยครั้ง
3. **เครือข่ายการจัดส่งเนื้อหา (CDN):** แคชและส่งมอบเอกสารที่แปลงไว้ล่วงหน้าได้อย่างรวดเร็ว
4. **แพลตฟอร์มการวิเคราะห์ข้อมูล:** เร่งการสร้างรายงานที่เกี่ยวข้องกับการแปลงข้อมูลเป็นรูปแบบภาพ
5. **เว็บไซต์อีคอมเมิร์ซ:** เพิ่มประสิทธิภาพการประมวลผลแค็ตตาล็อกผลิตภัณฑ์โดยการแคชรูปภาพที่แปลงแล้วหรือตัวอย่างเอกสาร

### ความเป็นไปได้ในการบูรณาการ:
- รวมกับกรอบงาน .NET อื่นๆ เช่น ASP.NET Core สำหรับแอปพลิเคชันเว็บ
- รวมเข้ากับสถาปัตยกรรมไมโครเซอร์วิสโดยใช้ Docker และ Kubernetes

## การพิจารณาประสิทธิภาพ

เพื่อเพิ่มประสิทธิภาพการทำงาน โปรดพิจารณาสิ่งต่อไปนี้:

- **การจัดการขนาดแคช:** ล้างรายการเก่าเป็นประจำเพื่อป้องกันหน่วยความจำล้น
- **การรวมการเชื่อมต่อ:** ใช้การรวมการเชื่อมต่อใน Redis เพื่อจัดการทรัพยากรอย่างมีประสิทธิภาพ
- **การจัดลำดับข้อมูล:** เลือกฟอร์แมตการจัดลำดับที่มีประสิทธิภาพ (เช่น บัฟเฟอร์โปรโตคอล) เพื่อจัดเก็บข้อมูลใน Redis

## บทสรุป

การนำแคช Redis แบบกำหนดเองมาใช้กับ GroupDocs.Conversion สำหรับ .NET สามารถเพิ่มประสิทธิภาพการแปลงเอกสารของแอปพลิเคชันของคุณได้อย่างมาก บทช่วยสอนนี้ให้คำแนะนำทีละขั้นตอนเกี่ยวกับการตั้งค่าและใช้เครื่องมืออันทรงพลังเหล่านี้เพื่อเพิ่มประสิทธิภาพการทำงาน

**ขั้นตอนต่อไป:**
- ทดลองใช้การกำหนดค่าแคชที่แตกต่างกัน
- สำรวจคุณลักษณะขั้นสูงของ GroupDocs.Conversion สำหรับกรณีการใช้งานที่ซับซ้อนมากขึ้น

พร้อมที่จะเพิ่มประสิทธิภาพแอปพลิเคชันของคุณหรือยัง เริ่มใช้งานโซลูชันนี้วันนี้!

## ส่วนคำถามที่พบบ่อย

1. **ฉันจะติดตั้ง Redis บนเครื่องของฉันได้อย่างไร?**
   - ทำตามคู่มือการติดตั้ง Redis อย่างเป็นทางการสำหรับระบบปฏิบัติการของคุณ: [ดาวน์โหลด Redis](https://redis-io/download).
2. **ประโยชน์จากการใช้แคชแบบกำหนดเองกับ GroupDocs.Conversion มีอะไรบ้าง**
   - ลดการประมวลผลซ้ำซ้อน เร่งเวลาในการแปลง และลดการใช้ทรัพยากร
3. **ฉันสามารถใช้การตั้งค่านี้ในสภาพแวดล้อมคลาวด์ได้หรือไม่**
   - แน่นอน! ตรวจสอบให้แน่ใจว่าสามารถเข้าถึงอินสแตนซ์ Redis ของคุณได้จากสภาพแวดล้อมแอปพลิเคชันของคุณ