---
date: '2026-01-23'
description: 學習如何在 Java 中透過實作 Redis 快取與 GroupDocs.Conversion 來快取文件，提升渲染效能並改善效率。
keywords:
- Custom Caching Java
- GroupDocs.Conversion Java
- Redis Cache Implementation
title: 如何在 Java 中使用 Redis 與 GroupDocs 快取文件
type: docs
url: /zh-hant/java/cache-management/custom-cache-redis-groupdocs-java/
weight: 1
---

# 如何在 Java 中使用 Redis 與 GroupDocs 快取文件

當您需要**快取文件**時，特別是在高流量的文件渲染情況下，一個設計良好的快取可以大幅縮短處理時間。在本教學中，我們將逐步說明一個完整的**java redis cache tutorial**，將 Redis 與 GroupDocs.Conversion 結合，協助您**提升渲染效能**，支援 PDF、DOCX 以及其他格式。

## 快速回答
- **本教學涵蓋什麼內容？** 在 Java 中為 GroupDocs.Conversion 實作基於 Redis 的快取。  
- **為什麼使用 Redis？** 它提供快速的記憶體儲存、TTL 支援，以及易於擴展的特性。  
- **我需要 GroupDocs 授權嗎？** 試用或臨時授權可用於測試；正式環境則需完整授權。  
- **主要步驟是什麼？** 設定 Maven 相依性、配置 Jedis、建立快取輔助工具，並將快取整合到轉換流程中。  
- **支援哪個 Java 版本？** Java 8 以上（相容於最新的 GroupDocs.Conversion 版本）。

## 使用 Redis 快取文件是什麼？
快取會將文件轉換的輸出（例如產生的 PDF）儲存於 Redis 中，讓後續對相同來源檔案的請求能即時回應，無需重新處理。這可降低 CPU 負載、網路流量，並提升最終使用者體驗。

## 為什麼在 Java 中實作 Redis 快取？
- **提升渲染效能**，避免重複轉換。  
- **降低基礎設施成本**——減少 CPU 週期與記憶體壓力。  
- **可跨多個應用實例擴展**，因為 Redis 為集中式儲存。  
- **細緻的過期策略控制**，讓您在新鮮度與速度之間取得平衡。

## 前置條件
- **GroupDocs.Conversion** – 版本 25.2 或更新。  
- **Jedis**（Java 用的 Redis 客戶端）。  
- 正在執行的 Redis 伺服器（開發時本機 localhost 即可）。  
- 用於相依性管理的 Maven。  
- 基本的 Java 知識與文件轉換概念的了解。

## 為 Java 設定 GroupDocs.Conversion

將 GroupDocs 倉庫與相依性加入您的 `pom.xml`：

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

### 取得授權
您可以先使用**免費試用**、申請**臨時授權**以進行評估，或購買完整的**授權**以供正式環境使用。

在您的 Java 程式碼中初始化 GroupDocs.Conversion：

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

## 實作指南

### 使用 Redis 建立自訂快取

#### 概觀
自訂的 Redis 快取會保存已渲染的文件位元組，讓重複請求時能即時取得。

#### 設定 JedisPool
首先，建立連線池以有效管理 Redis 連線：

```java
import redis.clients.jedis.JedisPool;

public class CacheManager {
    private static JedisPool jedisPool = new JedisPool("localhost", 6379);
    
    public static void main(String[] args) {
        // Additional cache setup code here
    }
}
```

#### 儲存與取得快取資料
使用簡單的輔助方法將文件寫入或讀取自 Redis：

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

#### 與 GroupDocs.Conversion 整合
現在將快取結合到轉換工作流程中：

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

### 疑難排解技巧
- 確認 Redis 伺服器可連線（從主機執行 `ping`）。  
- 確認 `JedisPool` 的主機與埠號與您的 Redis 實例相符。  
- 將快取呼叫包在 try‑catch 區塊中，以優雅地處理連線問題。  
- 監控 Redis 記憶體使用情況；在正式環境考慮 `maxmemory` 策略。

## 實務應用
1. **高流量入口網站** – 即時提供常被請求的 PDF。  
2. **企業文件管理系統 (DMS)** – 當使用者重複檢視相同合約時，減輕轉換伺服器負載。  
3. **電子商務** – 快取產生的發票或產品目錄。  
4. **學習平台** – 加速課程筆記與電子書的傳遞。  
5. **法律服務** – 加速案件檔案分發，同時降低儲存成本。

## 效能考量
- **調校 Redis** – 根據工作負載調整 `maxmemory`、`eviction-policy` 與逾時設定。  
- **追蹤快取命中/未命中比例** – 使用 Redis `INFO` 統計資料微調鍵的 TTL。  
- **JVM 堆積大小** – 確保堆積能容納轉換函式庫及任何程式內緩衝區。

## 常見問答

**Q: 我可以將此方法套用於其他 GroupDocs 輸出格式嗎？**  
A: 當然可以。相同的快取模式適用於 DOCX、HTML、圖片等，只需更改 `ConvertOptions` 類型。

**Q: 我該如何選擇合適的快取鍵？**  
A: 結合來源檔案路徑、轉換選項以及任何版本識別碼。這樣可確保每個設定的唯一性。

**Q: 若文件在快取後被修改，該怎麼辦？**  
A: 手動使快取失效（例如刪除鍵）或使用較短的 TTL，使過期資料快速失效。

**Q: Redis 是唯一的快取選項嗎？**  
A: 不是，但 Redis 具備低延遲、內建 TTL 與廣泛的 Java 客戶端支援，使其在此情境下相當受歡迎。

**Q: 這會增加應用伺服器的記憶體使用嗎小。主要工作由 Redis現在已掌握完整的 **java redis cache tutorial**，展示如何使用 Redis 與 GroupDocs.Conversion **快取文件**。透過將渲染結果儲存於 Redis，您可以 **提升渲染效能**、降低伺服器負載，並為最終使用者提供更順暢的體驗。可嘗試不同的 TTL 值、監控快取指標，並文件格式。

---

**最後更新：** 2026-01-23  
**測試環境：** GroupDocs.Conversion 25.2, Jed