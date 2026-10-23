---
date: '2026-10-21'
description: تعلم كيفية إنشاء مفتاح التخزين المؤقت Java وتكامل Redis مع GroupDocs.Conversion
  لتعزيز أداء العرض، وتقليل زمن التحويل، وتكوين TTLs في مشروع Java بسيط.
images:
- /java/cache-management/custom-cache-redis-groupdocs-java/og-image.png
keywords:
- create cache key java
- java redis caching
- groupdocs conversion cache
- redis ttl java
lastmod: '2026-10-21'
og_description: إنشاء مفتاح التخزين المؤقت Java في هذا الدليل خطوة بخطوة الذي يوضح
  كيفية دمج Redis مع GroupDocs.Conversion لتخزين بايتات المستند، وتعزيز أداء العرض،
  وتقليل زمن التحويل. قم بتكوين TTLs وقياس تحسين السرعة.
og_image_alt: 'Developer guide: create cache key Java using Redis and GroupDocs'
og_title: إنشاء مفتاح التخزين المؤقت Java – تخزين المستندات باستخدام Redis وGroupDocs
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
title: إنشاء مفتاح التخزين المؤقت Java – تخزين المستندات في Java باستخدام Redis
type: docs
url: /ar/java/cache-management/custom-cache-redis-groupdocs-java/
weight: 1
---

# إنشاء مفتاح ذاكرة التخزين المؤقت Java – تخزين مستندات الكاش في Java باستخدام Redis

في تطبيقات الويب الحديثة، قد يؤدي تقديم نفس المستند المحوَّل بشكل متكرر إلى إهدار دورات المعالج وزيادة أوقات الاستجابة. **إنشاء مفتاح ذاكرة تخزين مؤقت في Java** يتيح لك تخزين ناتج التحويل مرة واحدة واسترجاعه فورًا في الطلبات اللاحقة. يوضح هذا الدرس كيفية ربط Redis بسير عمل GroupDocs.Conversion، وإنشاء مفاتيح تخزين مؤقت موثوقة، وتكوين TTLs، وقياس تحسينات الأداء المتوقعة.

## إجابات سريعة
- **ماذا يغطي هذا الدرس؟** دليل كامل لتخزين Redis المؤقت في Java يدمج Redis مع GroupDocs.Conversion.  
- **لماذا نستخدم Redis؟** يوفر زمن استجابة أقل من الملي ثانية، يدعم انتهاء TTL، ويتوسع أفقياً عبر عدة نسخ من التطبيق.  
- **هل أحتاج إلى ترخيص GroupDocs؟** تجربة أو ترخيص مؤقت يكفي للاختبار؛ الترخيص الكامل مطلوب للنشر في بيئة الإنتاج.  
- **ما هي الخطوات الرئيسية؟** إضافة تبعيات Maven، تكوين `JedisPool`، بناء طرق مساعدة للتخزين المؤقت، وربط التخزين المؤقت بخط أنابيب التحويل.  
- **ما نسخة Java المدعومة؟** Java 8+ (متوافقة مع أحدث إصدارات GroupDocs.Conversion).

## ما هو تخزين المستندات في الذاكرة المؤقتة باستخدام Redis؟
يعني تخزين المستندات في الذاكرة المؤقتة باستخدام Redis حفظ الناتج الثنائي للتحويل (مثل مصفوفة بايتات PDF) في Redis بحيث يمكن للطلبات المستقبلية المتطابقة استرجاع البايتات المخزنة بدلاً من إعادة تشغيل محرك التحويل. هذا يلغي العمل المتكرر للمعالج، يقلل من استهلاك عرض النطاق الترددي، ويوفر تجربة مستخدم نهائية أكثر سلاسة.

## لماذا تنفيذ ذاكرة تخزين مؤقت Redis في Java؟
تحميل المستند مرة واحدة، تخزين النتيجة، وتقديمها فورًا عند الطلبات المتكررة يمكن أن **يقلل زمن التحويل بنسبة تصل إلى 90 %** للملفات التي يتم الوصول إليها بشكل متكرر، **يخفض تكاليف البنية التحتية** عبر تقليل استهلاك المعالج، و**يوفر مصدرًا موحدًا للبيانات** لجميع عقد التطبيق في بيئة عنقودية. يمكن لـ Redis معالجة أكثر من 200 ألف عملية في الثانية على عقدة واحدة، مما يضمن عمليات بحث بأقل من الملي ثانية.

## المتطلبات المسبقة
- **GroupDocs.Conversion** – الإصدار 25.2 أو أحدث (يدعم **120+** صيغة إدخال وإخراج).  
- **Jedis** (عميل Redis الرسمي لـ Java).  
- مثيل Redis يعمل (يمكن للتطوير المحلي استخدام الإعداد الافتراضي `localhost:6379`).  
- Maven لإدارة التبعيات.  
- إلمام أساسي بمعالجة الاستثناءات في Java وتدفقات الإدخال/الإخراج.

## إعداد GroupDocs.Conversion لـ Java

`GroupDocs.Conversion` هي مكتبة Java تقوم بتحويل وعرض المستندات إلى مجموعة واسعة من الصيغ، مع الحفاظ على التخطيط، تضمين الخطوط، واستخراج الصور تلقائيًا.

أضف مستودع GroupDocs والاعتماد إلى ملف `pom.xml` الخاص بك:

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

### الحصول على الترخيص
يمكنك البدء بـ **تجربة مجانية**، طلب **ترخيص مؤقت** للتقييم، أو شراء **ترخيص** كامل للاستخدام في بيئة الإنتاج.

ابدأ تهيئة GroupDocs.Conversion في كود Java الخاص بك:

```java
import com.groupdocs.conversion.*;

ConversionConfig config = new ConversionConfig();
config.setLicensePath("path/to/license/file.lic");
ConversionApi conversionApi = new ConversionApi(config);
```

## دليل التنفيذ

### إنشاء ذاكرة تخزين مؤقت مخصصة باستخدام Redis

#### نظرة عامة
تخزين مؤقت مخصص باستخدام Redis يحتفظ ببايتات المستند المعروض، مما يتيح استرجاعًا فوريًا عند الطلبات المتكررة.

#### إعداد JedisPool
`JedisPool` هو مجموعة آمنة للخطوط (thread‑safe) من اتصالات Redis القابلة لإعادة الاستخدام، يقلل من عبء المقابس ويحسن معدل النقل.

```java
import redis.clients.jedis.JedisPool;
import redis.clients.jedis.JedisPoolConfig;

JedisPoolConfig poolConfig = new JedisPoolConfig();
poolConfig.setMaxTotal(20);               // maximum active connections
poolConfig.setMaxIdle(10);                // maximum idle connections
poolConfig.setMinIdle(2);                 // minimum idle connections
JedisPool jedisPool = new JedisPool(poolConfig, "localhost", 6379);
```

#### تخزين واسترجاع البيانات المخزنة مؤقتًا
طرق المساعدة أدناه تقوم بتسلسل مصفوفة البايتات إلى سلسلة Base64 لتخزين آمن وتسترجعها مرة أخرى إلى مصفوفة بايتات.

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

#### التكامل مع GroupDocs.Conversion
الآن اربط التخزين المؤقت بسير عمل التحويل. تتحقق الطريقة من التخزين المؤقت أولاً؛ إذا لم توجد قيمة، تقوم بتنفيذ التحويل، تخزين النتيجة، وإرجاع البايتات.

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

## كيف تنشئ مفتاح ذاكرة التخزين المؤقت Java لتخزين Redis المؤقت؟
أنشئ مفتاحًا حتميًا عن طريق دمج مسار ملف المصدر، قيم `ConvertOptions` المختارة، وعلامة نسخة اختيارية، ثم احسب تجزئة السلسلة باستخدام SHA‑256. يحدد هذا المفتاح كل تكوين تحويل بشكل فريد، مما يضمن أن الطلبات المتطابقة تصل إلى التخزين المؤقت بينما تولد الخيارات المختلفة مدخلات منفصلة.

فئة `ConversionApi` هي المكون الأساسي في GroupDocs.Conversion الذي ينفذ تحويلات المستندات. يمكنك إنشاء مفتاح تخزين مؤقت، البحث عنه في Redis، واستدعاء `ConversionApi.convert` فقط عندما يكون المفتاح غير موجود، مما يقلل بشكل كبير من زمن التحويل وحمل الخادم.

## كيف تنفذ تخزين Redis المؤقت في Java؟
`ConversionApi` هي الفئة الأساسية في GroupDocs.Conversion التي تنفذ عمليات تحويل المستندات. حمّل مستند المصدر، أنشئ مفتاح تخزين مؤقت حتمي، ابحث عنه في Redis، واستدعِ `ConversionApi` فقط عندما يكون المفتاح غير موجود. يضمن هذا النمط أن كل تحويل فريد يتم مرة واحدة فقط، ثم يُقدَّم من التخزين المؤقت طوال مدة TTL المكوَّنة.

## نصائح استكشاف الأخطاء وإصلاحها
- تحقق من أن خادم Redis يمكن الوصول إليه (`redis-cli ping` يجب أن يُعيد `PONG`).  
- تأكد من أن مضيف ومنفذ `JedisPool` يتطابقان مع نشر Redis الخاص بك.  
- غلف استدعاءات التخزين المؤقت بكتل try‑catch للتعامل مع انقطاعات الاتصال دون إيقاف سير التحويل.  
- راقب ذاكرة Redis (`INFO memory`) واضبط سياسات `maxmemory` (مثل `volatile-lru`) لإزالة المدخلات القديمة بلطف.  
- إذا واجهت `OutOfMemoryError` على JVM، قم بزيادة حجم الـ heap أو فعّل `-XX:+UseCompressedOops`.

## تطبيقات عملية

1. **بوابات ذات حركة مرور عالية** – تقديم ملفات PDF المطلوبة بشكل متكرر (كتالوجات، الأوراق البيضاء) فورًا.  
2. **نظام إدارة المستندات المؤسسي** – تقليل الحمل عندما يعرض المستخدمون العقود أو وثائق السياسات نفسها بشكل متكرر.  
3. **التجارة الإلكترونية** – تخزين الفواتير أو كتالوجات المنتجات المولدة مؤقتًا لتسريع عملية الدفع.  
4. **منصات التعلم** – تقديم ملاحظات المحاضرات والكتب الإلكترونية دون إعادة العرض في كل طلب من الطلاب.  
5. **الخدمات القانونية** – تسريع توزيع ملفات القضايا مع الحفاظ على انخفاض تكاليف التخزين.

## اعتبارات الأداء

- **ضبط Redis** – تعديل `maxmemory`، اختيار سياسة إخلاء مثل `allkeys-lru`، وتعيين قيم `timeout` المناسبة بناءً على نمط حركة المرور.  
- **متابعة نسب الضربات/الفشل في التخزين المؤقت** – استخدم `INFO stats` أو عدادات `keyspace_hits` / `keyspace_misses` في Redis لضبط TTLs بدقة.  
- **حجم heap في JVM** – تأكد من أن الـ heap يمكنه استيعاب مخازن GroupDocs؛ القاعدة العامة هي 1 GB heap لكل 100 MB من حمولة التحويل المتزامنة.  
- **تحويلات دفعية** – عند تحويل العديد من الملفات، أعد استخدام مثيل `Jedis` واحد لكل خيط لتقليل استهلاك المقابس.

## الأسئلة المتكررة

**س: هل يمكنني استخدام هذا النهج مع صيغ إخراج GroupDocs أخرى؟**  
ج: بالتأكيد. نمط التخزين المؤقت نفسه يعمل مع DOCX، HTML، الصور، وأكثر – فقط غيّر نوع `ConvertOptions`.

**س: كيف أختار مفتاح تخزين مؤقت جيد؟**  
ج: دمج مسار ملف المصدر، خيارات التحويل، وأي معرفات نسخة. هذا يضمن التفرد لكل تكوين.

**س: ماذا لو تغير المستند بعد تخزينه مؤقتًا؟**  
ج: إبطال التخزين المؤقت يدويًا (مثلاً حذف المفتاح) أو استخدم TTL أقصر حتى تنتهي صلاحية البيانات القديمة بسرعة.

**س: هل Redis هو الخيار الوحيد للتخزين المؤقت؟**  
ج: لا، لكن Redis يوفر زمن استجابة منخفض، TTL مدمج، ودعم واسع لعملاء Java، مما يجعله خيارًا شائعًا لهذا السيناريو.

**س: هل يزيد هذا من استهلاك الذاكرة على خادم التطبيق؟**  
ج: الحد الأدنى. العملية الثقيلة تتم على Redis؛ التطبيق يحتفظ باتصالات قصيرة العمر عبر Jedis فقط.

## الخلاصة
أنت الآن تمتلك دليلًا كاملاً حول **java redis caching** يوضح كيفية تخزين المستندات مؤقتًا باستخدام Redis وGroupDocs.Conversion. من خلال حفظ الناتج المعروض في Redis، سـ **تحسن أداء العرض**، **تقلل زمن التحويل**، وتوفر تجربة أكثر سلاسة للمستخدمين النهائيين. جرب قيم TTL مختلفة، راقب مقاييس التخزين المؤقت، ووسع النمط إلى صيغ مستندات أخرى مع نمو تطبيقك.

**آخر تحديث:** 2026-10-21  
**تم الاختبار مع:** GroupDocs.Conversion 25.2، Jedis 4.2.3  
**المؤلف:** GroupDocs

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

## دروس ذات صلة

- [Implement Custom Cache Java – GroupDocs Conversion Cache](/conversion/java/cache-management/)
- [How to Use Redis Cache in Java with GroupDocs.Conversion](/conversion/java/cache-management/redis-cache-java-groupdocs-conversion-guide/)
- [How to Cache Files in Java with GroupDocs.Conversion – A Comprehensive Guide for Efficient Document Conversion](/conversion/java/cache-management/implement-java-file-caching-groupdocs-conversion-guide/)
