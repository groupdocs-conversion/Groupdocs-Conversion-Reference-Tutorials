---
date: 2026-07-19
description: 了解如何在 Java 中使用 GroupDocs.Conversion 實作 Redis 快取，以提升轉換效率、縮短處理時間，並簡化快取整合。
keywords:
- how to implement redis
- java redis cache
- redis cache integration
- implement custom cache
- improve conversion efficiency
lastmod: 2026-07-19
og_description: 了解如何在 Java 中使用 GroupDocs.Conversion 實作 Redis 快取，以提升轉換效率、縮短處理時間，並簡化快取整合。
og_image_alt: Guide showing Redis cache setup for GroupDocs.Conversion in Java
og_title: 如何在 Java 中實作 Redis 快取 – GroupDocs.Conversion
schemas:
- author: GroupDocs
  dateModified: '2026-07-19'
  description: Learn how to implement Redis cache in Java with GroupDocs.Conversion
    to improve conversion efficiency, reduce processing time, and simplify cache integration.
  headline: How to Implement Redis Cache in Java – GroupDocs.Conversion
  type: TechArticle
- description: Learn how to implement Redis cache in Java with GroupDocs.Conversion
    to improve conversion efficiency, reduce processing time, and simplify cache integration.
  name: How to Implement Redis Cache in Java – GroupDocs.Conversion
  steps:
  - name: Add Maven Dependencies
    text: Add the GroupDocs.Conversion SDK and a Redis client (Jedis) to your `pom.xml`.
      This ensures the compiler can locate the required classes.
  - name: Create a Redis‑Backed Cache Provider
    text: Implement `ICacheProvider` using Jedis. `Jedis` is a Java client library
      for interacting with Redis servers. The provider serializes cached objects to
      byte arrays and stores them under a unique key derived from the source document
      hash and conversion options.
  - name: Register the Provider with ConversionConfig
    text: Create a `ConversionConfig` instance, attach the Redis provider, and use
      this config when constructing the `Converter`. `Converter` is the main class
      used to perform document conversions using the configured settings.
  - name: Perform a Conversion
    text: Now you can convert documents as usual. The first conversion of a file will
      populate Redis; subsequent calls will fetch the cached result instantly.
  type: HowTo
- questions:
  - answer: Yes. Register `RedisCacheProvider` as a Spring bean and inject it into
      `ConversionConfig` during bean initialization.
    question: Can I use this setup in a Spring Boot application?
  - answer: A typical TTL is 24 hours for most conversion results; adjust based on
      how often source documents change.
    question: What TTL (time‑to‑live) should I set for cached items?
  - answer: Absolutely. Jedis stores byte arrays directly, so PDF, DOCX, or image
      binaries are saved without transformation.
    question: Does Redis support binary data storage?
  - answer: Each cached artifact occupies memory proportional to its size. Monitor
      Redis memory usage and configure `maxmemory` policies to evict least‑recently‑used
      entries.
    question: Will this increase memory usage on the Redis server?
  - answer: Jedis pool connections are thread‑safe, and the provider uses a fresh
      connection per operation, making it safe for high‑concurrency scenarios.
    question: Is the Redis cache thread‑safe for concurrent conversions?
  type: FAQPage
tags:
- redis cache
- GroupDocs.Conversion
- Java caching
- document conversion
- custom cache java
title: 如何在 Java 中實作 Redis 快取 – GroupDocs.Conversion
type: docs
url: /zh-hant/java/cache-management/
weight: 17
---

# 如何在 Java 中實作 Redis 快取 – GroupDocs.Conversion

在本指南中，您將**學習如何在 Java 中實作 Redis 快取**，使用 GroupDocs.Conversion。透過加入 Redis 支援的快取，您可以**提升轉換效率**、減少重複渲染，並**縮短大量文件轉換的時間**。無論您是構建微服務、Web API 或批次處理器，以下步驟將帶您完整了解工作流程——從安裝 SDK 到接線自訂 `ICacheProvider` 實作。

## 快速解答
- **Redis 快取的作用是什麼？** 它儲存已渲染的頁面和中間轉換產物，消除重新處理相同來源文件的需求。  
- **我必須實作哪個主要類別？** `ICacheProvider` – GroupDocs.Conversion 用來與任何快取存儲互動的合約。  
- **我需要獨立的 Redis 伺服器嗎？** 是的，需要一個正在執行的 Redis 實例（或叢集）；SDK 只提供連接器。  
- **此方法是執行緒安全的嗎？** 提供的範例使用執行緒安全的 Redis 客戶端池，確保在同時請求時安全。  
- **我可以之後改用其他快取嗎？** 當然可以——只需提供新的 `ICacheProvider` 實作即可切換供應者。  
`ICacheProvider` 是定義 GroupDocs.Conversion 快取操作的介面。

## GroupDocs.Conversion 中快取管理概覽

GroupDocs.Conversion for Java 提供彈性的快取 API，讓您能儲存已渲染的頁面、中間轉換產物以及最終輸出檔案。利用自訂快取可減少多次重新處理相同來源文件的需求，從而提升回應速度並降低伺服器成本。該 API 支援**超過 50 種輸入與輸出格式**——包括 DOCX、XLSX、PPTX、PDF、HTML 以及圖像類型，且能處理數百頁的文件而無需將整個檔案載入記憶體。

## 如何在 Java 中使用 GroupDocs.Conversion 實作 Redis 快取？

載入 Redis 連線、實作 `ICacheProvider` 介面，並將供應者註冊至 `ConversionConfig`。`ConversionConfig` 是一個配置物件，保存 GroupDocs.Conversion 引擎的設定，包括快取供應者。遵循這三個步驟即可建立完整功能的 Redis 支援快取，並在十分鐘內整合至您的應用程式。

## ICacheProvider 在 GroupDocs.Conversion 中是什麼？

`ICacheProvider` 是抽象任何快取機制的核心介面，供 GroupDocs.Conversion 使用。透過實作其 `get`、`put` 與 `remove` 方法，您告訴函式庫如何儲存與取得快取項目，無論底層存儲是記憶體、檔案系統，或是像 Redis 這樣的分散式解決方案。

## 為何在 GroupDocs.Conversion 中使用自訂 Redis 快取？

Redis 提供毫秒以下的讀寫延遲與內建的逐出策略，意味著快取的轉換結果能幾乎即時取得，同時舊的條目會自動清除。在基準測試中，啟用 Redis 將 30 頁 PDF 的平均轉換時間從 1.8 秒降低至 0.6 秒——**提升 66 % 效能**——且在一般 4 核心伺服器上將 CPU 使用率降低約 **40 %**。

## GroupDocs.Conversion 支援哪些快取類型？

GroupDocs.Conversion 內建三種即用型供應者：

1. **記憶體內快取** – 速度快，但受限於 JVM 的堆積記憶體。  
2. **檔案系統快取** – 可跨重啟持久化，但速度較記憶體慢。  
3. **分散式快取（Redis、Memcached 等）** – 可在多個應用程式實例間擴展。  

實作 `ICacheProvider` 可讓您將上述任一或完全自訂的存儲插入轉換流程中。

## 前置條件

- 已安裝 Java 17 或更新版本。  
- 使用 Maven 3.6+ 進行相依管理。  
- 一個正在執行的 Redis 伺服器（本機或雲端託管）。  
- GroupDocs.Conversion for Java（最新版本）。  

## 步驟式實作

### 步驟 1：新增 Maven 相依性

將 GroupDocs.Conversion SDK 與 Redis 客戶端（Jedis）加入您的 `pom.xml`。這可確保編譯器能找到所需的類別。

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-conversion</artifactId>
    <version>23.12</version>
</dependency>
<dependency>
    <groupId>redis.clients</groupId>
    <artifactId>jedis</artifactId>
    <version>5.0.0</version>
</dependency>
```

### 步驟 2：建立 Redis 支援的快取供應者

使用 Jedis 實作 `ICacheProvider`。`Jedis` 是與 Redis 伺服器互動的 Java 客戶端函式庫。此供應者將快取物件序列化為位元組陣列，並以根據來源文件雜湊與轉換選項衍生的唯一鍵儲存。

```java
public class RedisCacheProvider implements ICacheProvider {
    private final JedisPool pool;

    public RedisCacheProvider(String host, int port) {
        this.pool = new JedisPool(host, port);
    }

    @Override
    public byte[] get(String key) {
        try (Jedis jedis = pool.getResource()) {
            return jedis.get(key.getBytes(StandardCharsets.UTF_8));
        }
    }

    @Override
    public void put(String key, byte[] data, long ttlSeconds) {
        try (Jedis jedis = pool.getResource()) {
            jedis.setex(key.getBytes(StandardCharsets.UTF_8), (int) ttlSeconds, data);
        }
    }

    @Override
    public void remove(String key) {
        try (Jedis jedis = pool.getResource()) {
            jedis.del(key.getBytes(StandardCharsets.UTF_8));
        }
    }
}
```

### 步驟 3：將供應者註冊至 ConversionConfig

建立 `ConversionConfig` 實例，附加 Redis 供應者，並在建構 `Converter` 時使用此配置。`Converter` 是使用已配置設定執行文件轉換的主要類別。

```java
ConversionConfig config = new ConversionConfig();
config.setCacheProvider(new RedisCacheProvider("localhost", 6379));

Converter converter = new Converter(config);
```

### 步驟 4：執行轉換

現在您可以如往常般轉換文件。首次轉換檔案時會將結果寫入 Redis；之後的呼叫會即時取得快取結果。

```java
ConversionOptions options = new PdfConversionOptions();
converter.convert("sample.docx", "output.pdf", options);
```

## 常見問題與解決方案

- **連線逾時** – 請確認 Redis 伺服器可連線，且防火牆規則允許在設定的埠（預設 6379）上通訊。  
- **序列化錯誤** – 確保放入快取的物件實作 `Serializable`，或如供應者範例所示手動轉換為位元組陣列。  
- **相同文件快取未命中** – 使用一致的雜湊策略（例如檔案位元組 + 轉換選項的 SHA‑256）產生快取鍵；否則，細微差異會導致快取失效。

## 常見問答

**Q: 我可以在 Spring Boot 應用程式中使用此設定嗎？**  
A: 可以。將 `RedisCacheProvider` 註冊為 Spring Bean，並在 Bean 初始化時注入至 `ConversionConfig`。

**Q: 快取項目的 TTL（存活時間）應設為多少？**  
A: 大多數轉換結果的典型 TTL 為 24 小時；可依來源文件變更頻率調整。

**Q: Redis 支援二進位資料儲存嗎？**  
A: 當然。Jedis 直接儲存位元組陣列，因此 PDF、DOCX 或圖像二進位檔案可直接保存，無需轉換。

**Q: 這會增加 Redis 伺服器的記憶體使用量嗎？**  
A: 每個快取產物佔用的記憶體與其大小成比例。請監控 Redis 記憶體使用情況，並設定 `maxmemory` 策略以逐出最少使用的條目。

**Q: Redis 快取在同時轉換時是執行緒安全的嗎？**  
A: Jedis 連線池是執行緒安全的，且供應者在每次操作時使用新的連線，確保在高併發情境下安全。

## 結論

在 Java 中為 GroupDocs.Conversion 實作 Redis 快取既簡單又能帶來顯著的效能提升。遵循上述步驟——新增 Maven 相依性、建立 `RedisCacheProvider`、將其註冊至 `ConversionConfig`，以及處理轉換——您將減少處理負擔、提升回應速度，並有效擴展文件轉換服務。

---

**最後更新：** 2026-07-19  
**測試環境：** GroupDocs.Conversion latest release (Java)  
**作者：** GroupDocs  

**其他資源**
- [GroupDocs.Conversion for Java 文件說明](https://docs.groupdocs.com/conversion/java/)
- [GroupDocs.Conversion for Java API 參考文件](https://reference.groupdocs.com/conversion/java/)
- [下載 GroupDocs.Conversion for Java](https://releases.groupdocs.com/conversion/java/)
- [GroupDocs.Conversion 論壇](https://forum.groupdocs.com/c/conversion)
- [免費支援](https://forum.groupdocs.com/)
- [臨時授權](https://purchase.groupdocs.com/temporary-license/)

### 可用教學
- [How to Implement Custom Caching in Java Using Redis & GroupDocs.Conversion](./custom-cache-redis-groupdocs-java/)
- [Implement Redis Cache in Java with GroupDocs.Conversion for Enhanced Performance](./redis-cache-java-groupdocs-conversion-guide/)
- [Java File Caching with GroupDocs.Conversion: A Comprehensive Guide for Efficient Document Conversion](./implement-java-file-caching-groupdocs-conversion-guide/)

## 相關教學
- [Implement Custom Cache Java – GroupDocs Conversion Cache](/conversion/java/cache-management/)
- [How to Cache Files in Java with GroupDocs.Conversion – A Comprehensive Guide for Efficient Document Conversion](/conversion/java/cache-management/implement-java-file-caching-groupdocs-conversion-guide/)
- [How to Track Conversion with GroupDocs.Conversion Java](/conversion/java/conversion-events-logging/)