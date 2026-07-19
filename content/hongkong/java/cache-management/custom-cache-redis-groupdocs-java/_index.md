---
date: '2026-07-19'
description: 探索一步一步的 java redis 快取教學，將 Redis 與 GroupDocs.Conversion 整合，以提升渲染效能、縮短轉換時間，並簡化快取管理。
keywords:
- java redis caching
- boost rendering performance
- configure redis ttl
- reduce conversion time
- cache documents java
lastmod: '2026-07-19'
og_description: 學習使用 GroupDocs.Conversion 的 java redis 快取。本教學示範如何提升渲染效能、縮短轉換時間，並在簡易
  Java 專案中設定 Redis TTL。
og_image_alt: 'Guide: java redis caching with GroupDocs and Redis'
og_title: java redis 快取 – 在 Java 中使用 Redis 的 Cache Docs
schemas:
- author: GroupDocs
  dateModified: '2026-07-19'
  description: Discover a step‑by‑step java redis caching tutorial that integrates
    Redis with GroupDocs.Conversion to boost rendering performance, reduce conversion
    time, and simplify cache management.
  headline: 'java redis caching: Cache Docs in Java with Redis'
  type: TechArticle
- description: Discover a step‑by‑step java redis caching tutorial that integrates
    Redis with GroupDocs.Conversion to boost rendering performance, reduce conversion
    time, and simplify cache management.
  name: 'java redis caching: Cache Docs in Java with Redis'
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
- java redis cache
- GroupDocs.Conversion
- document rendering
- performance optimization
title: java redis 快取：在 Java 中使用 Redis 的 Cache Docs
type: docs
url: /zh-hant/java/cache-management/custom-cache-redis-groupdocs-java/
weight: 1
---

# java redis caching：在 Java 中使用 Redis 快取文件

在現代 Web 應用程式中，重複提供相同的已轉換文件會浪費 CPU 資源並延長回應時間。**java redis caching** 透過將轉換輸出儲存於快速的記憶體資料庫中，讓後續請求即時回應。本教學將說明如何將 Redis 整合至 GroupDocs.Conversion 工作流程、設定 TTL，並衡量可預期的效能提升。

## 快速答案
- **本教程涵蓋什麼內容？** 一個完整的 java redis caching 教程，將 Redis 與 GroupDocs.Conversion 整合。  
- **為什麼使用 Redis？** 它提供子毫秒級延遲，支援 TTL 過期，且可在多個應用實例間水平擴展。  
- **我需要 GroupDocs 授權嗎？** 試用或臨時授權可用於測試；正式環境需要完整授權。  
- **主要步驟是什麼？** 新增 Maven 依賴、配置 `JedisPool`、建立快取輔助方法，並將快取插入轉換流程。  
- **支援哪個 Java 版本？** Java 8 以上（相容於最新的 GroupDocs.Conversion 版本）。

## 什麼是使用 Redis 快取文件？
使用 Redis 快取文件是指將轉換的二進位輸出（例如 PDF 位元組陣列）持久化於 Redis，讓相同的未來請求能直接取得快取的位元組，而不必重新執行轉換引擎。這可消除重複的 CPU 工作、降低網路頻寬，並提供更流暢的使用者體驗。

## 為什麼在 Java 中實作 Redis 快取？
將文件載入一次，儲存結果，之後的請求即可即時提供。基於 Redis 的快取可為常被存取的檔案 **將轉換時間縮減最高達 90 %**，透過降低 CPU 使用率 **降低基礎設施成本**，並在叢集環境中 **提供單一真實來源** 給所有應用節點。

## 先決條件
- **GroupDocs.Conversion** – 版本 25.2 或更新（支援 **120+** 輸入與輸出格式）。  
- **Jedis**（官方的 Java Redis 客戶端）。  
- 一個正在執行的 Redis 實例（本機開發可使用預設的 `localhost:6379`）。  
- 用於依賴管理的 Maven。  
- 熟悉 Java 例外處理與 I/O 串流的基本知識。

## 設定 GroupDocs.Conversion（Java 版）

`GroupDocs.Conversion` 是一個 Java 函式庫，可將文件轉換與渲染為多種格式，並自動處理版面保存、字型嵌入與影像抽取。

Add the GroupDocs repository and dependency to your `pom.xml`:

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

### 取得授權
您可以先使用 **Free Trial**，申請 **Temporary License** 以進行評估，或購買完整的 **License** 用於正式環境。

Initialize GroupDocs.Conversion in your Java code:

```java
import com.groupdocs.conversion.*;

ConversionConfig config = new ConversionConfig();
config.setLicensePath("path/to/license/file.lic");
ConversionApi conversionApi = new ConversionApi(config);
```

## 實作指南

### 使用 Redis 建立自訂快取

#### 概觀
自訂的 Redis 快取會保存已渲染的文件位元組，讓重複請求能即時取得。

#### 設定 JedisPool
`JedisPool` 是一個執行緒安全的可重複使用 Redis 連線池，可減少 socket 開銷並提升吞吐量。

```java
import redis.clients.jedis.JedisPool;
import redis.clients.jedis.JedisPoolConfig;

JedisPoolConfig poolConfig = new JedisPoolConfig();
poolConfig.setMaxTotal(20);               // maximum active connections
poolConfig.setMaxIdle(10);                // maximum idle connections
poolConfig.setMinIdle(2);                 // minimum idle connections
JedisPool jedisPool = new JedisPool(poolConfig, "localhost", 6379);
```

#### 儲存與取得快取資料
以下輔助方法會將位元組陣列序列化為 Base64 字串以安全儲存，並再取回為位元組陣列。

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

#### 與 GroupDocs.Conversion 整合
現在將快取結合至轉換工作流程。此方法會先檢查快取；若未命中，則執行轉換、儲存結果，並回傳位元組。

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

## 如何實作 java redis 快取？
`ConversionApi` 是 GroupDocs.Conversion 中執行文件轉換的主要類別。

載入來源文件，產生確定性的快取鍵，於 Redis 中查找，僅在鍵不存在時才呼叫 `ConversionApi`。此模式確保每個唯一的轉換只執行一次，之後在設定的 TTL 期間從快取提供。

## 疑難排解技巧
- 確認 Redis 伺服器可連線（`redis-cli ping` 應回傳 `PONG`）。  
- 確保 `JedisPool` 的主機與埠號與您的 Redis 部署相符。  
- 將快取呼叫包在 try‑catch 區塊，以處理連線問題而不中斷轉換流程。  
- 監控 Redis 記憶體 (`INFO memory`) 並設定 `maxmemory` 策略（例如 `volatile-lru`）以優雅地逐出舊條目。  
- 若在 JVM 上遇到 `OutOfMemoryError`，請增大堆積大小或啟用 `-XX:+UseCompressedOops`。

## 實務應用

1. **高流量入口網站** – 即時提供常被請求的 PDF（目錄、白皮書）。  
2. **企業文件管理系統（DMS）** – 當使用者重複檢視相同合約或政策文件時降低負載。  
3. **電子商務** – 快取產生的發票或產品目錄，加速結帳流程。  
4. **學習平台** – 提供講義與電子書，無需在每位學生請求時重新渲染。  
5. **法律服務** – 加速案件檔案的分發，同時降低儲存成本。

## 效能考量

- **調校 Redis** – 調整 `maxmemory`、選擇如 `allkeys-lru` 的逐出策略，並根據流量模式設定適當的 `timeout` 值。  
- **追蹤快取命中/未命中比例** – 使用 `INFO stats` 或 Redis 的 `keyspace_hits` / `keyspace_misses` 計數器來微調 TTL。  
- **JVM 堆積大小** – 確保堆積能容納 GroupDocs 緩衝；一般經驗法則是每 100 MB 同時轉換負載配置 1 GB 堆積。  
- **批次轉換** – 轉換大量檔案時，於每個執行緒重複使用單一 `Jedis` 實例，以減少 socket 開銷。

## 常見問題

**Q: 我可以將此方法用於其他 GroupDocs 輸出格式嗎？**  
A: 當然可以。相同的快取模式適用於 DOCX、HTML、影像等，只需更改 `ConvertOptions` 類型。

**Q: 如何選擇合適的快取鍵？**  
A: 結合來源檔案路徑、轉換選項以及任何版本識別碼。這可保證每個設定的唯一性。

**Q: 若文件在快取後變更該怎麼辦？**  
A: 手動使快取失效（例如刪除鍵）或使用較短的 TTL，使過期資料快速失效。

**Q: Redis 是唯一的快取選項嗎？**  
A: 不是，但 Redis 提供低延遲、內建 TTL 以及廣泛的 Java 客戶端支援，使其在此情境下相當受歡迎。

**Q: 這會增加應用伺服器的記憶體使用嗎？**  
A: 影響極小。主要工作由 Redis 承擔，應用程式僅透過 Jedis 保持短暫連線。

## 結論
您現在已擁有完整的 **java redis caching** 教程，說明如何使用 Redis 與 GroupDocs.Conversion 快取文件。將渲染結果持久化於 Redis 後，您將 **提升渲染效能**、**縮短轉換時間**，並為最終使用者提供更流暢的體驗。可嘗試不同的 TTL 值、監控快取指標，並隨著應用成長將此模式擴展至其他文件格式。

---

**最後更新：** 2026-07-19  
**測試環境：** GroupDocs.Conversion 25.2, Jedis 4.2.3  
**作者：** GroupDocs

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

## 相關教學

- [實作自訂快取 Java – GroupDocs Conversion Cache](/conversion/java/cache-management/)
- [如何在 Java 中使用 Redis 快取與 GroupDocs.Conversion](/conversion/java/cache-management/redis-cache-java-groupdocs-conversion-guide/)
- [如何在 Java 中快取檔案與 GroupDocs.Conversion – 高效文件轉換的完整指南](/conversion/java/cache-management/implement-java-file-caching-groupdocs-conversion-guide/)