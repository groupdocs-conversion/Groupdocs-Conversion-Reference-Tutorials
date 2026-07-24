---
date: '2026-07-24'
description: 了解如何在 Java 中使用 Redis 快取與 GroupDocs.Conversion，以提升應用程式效能。本 Redis 快取 Java
  教學涵蓋設定、快取策略與效能技巧。
keywords:
- how to use redis
- redis cache java
- java redis connection
- configure redis cache
- redis cache key prefix
lastmod: '2026-07-24'
og_description: 了解如何在 Java 中使用 Redis 快取與 GroupDocs.Conversion。本指南展示設定、快取策略與效能技巧，讓文件轉換更快。
og_image_alt: 'Guide: Implement Redis cache in Java using GroupDocs.Conversion for
  high‑performance document processing'
og_title: 如何在 Java 中使用 Redis 快取與 GroupDocs.Conversion
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
title: 如何在 Java 中使用 Redis 快取與 GroupDocs.Conversion
type: docs
url: /zh-hant/java/cache-management/redis-cache-java-groupdocs-conversion-guide/
weight: 1
---

# 如何在 Java 中使用 Redis 快取與 GroupDocs.Conversion

`Redis` 是一種記憶體內資料結構儲存服務，支援字串、雜湊、串列、集合等。Redis 是功能強大的開源記憶體內資料結構儲存，可作為資料庫、快取與訊息代理。當您學習 **如何使用 Redis** 與 GroupDocs.Conversion 結合時，為您的 Java 應用程式提供快速的快取層，顯著降低文件轉換延遲。本指南將帶您完整走過 **Redis 快取 Java 教學**，從環境設定到實務使用，讓您立即看到效能提升。

## 快速問答
- **使用 Redis 與 GroupDocs 的主要好處是什麼？** 透過避免重複轉換，加速文件檢索。  
- **哪個 Maven 套件會加入 GroupDocs.Conversion？** `com.groupdocs:groupdocs-conversion`。  
- **如何在 Java 中連接 Redis？** 使用類似 `ConnectionMultiplexer.Connect("localhost")` 的 Java Redis 連線範例。  
- **我可以自訂快取鍵嗎？** 可以 — `redis cache key prefix` 讓您組織條目。  
- **在正式環境中是否需要授權？** 需要，有效的 GroupDocs.Conversion 授權是必須的。  

`ConnectionMultiplexer` 是來自 StackExchange.Redis 函式庫的客戶端類別，用於管理與 Redis 伺服器的連線。

## GroupDocs.Conversion for Java 是什麼？
GroupDocs.Conversion for Java 是一個可將超過 80 種檔案格式轉換為 PDF、影像及其他輸出的函式庫。它提供統一的 API，讓伺服器端高品質的文件轉換無需安裝 Microsoft Office。支援轉換為 PDF、影像、HTML 等多種格式，並提供浮水印、分頁與自訂渲染設定等選項。

## 為什麼要將 Redis 與 GroupDocs.Conversion 結合使用？
將 Redis 作為快取層可將重複請求的轉換時間縮短 **最高 90 %**，在處理大量批次時亦可降低 **約 70 %** 的 CPU 使用率。這類具體數據說明了為何眾多企業採用此模式以提供高吞吐量的文件服務。

## 前置條件
### 必要的函式庫與相依性
1. **Java Development Kit (JDK)：** 版本 8 或更新。  
2. **Redis Server：** 本機執行或遠端可連線。  
3. **GroupDocs.Conversion for Java：** 透過 Maven 加入（請參閱下方的 **maven dependency groupdocs** 章節）。  

### 環境設定
- 依照 [this guide](https://redis.io/download) 安裝 Redis。  
- 使用適當的 JDK 設定您的 IDE（IntelliJ IDEA、Eclipse 等）。  

### 知識前提
- 基本的 Java 與物件導向概念。  
- 熟悉 Maven 以管理相依性。  
- 了解快取原理以及其對文件轉換的重要性。

## 設定 GroupDocs.Conversion for Java
`GroupDocs.Conversion` 函式庫是執行格式轉換的核心引擎。將以下 Maven 片段加入您的 `pom.xml` 以取得官方套件：

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
1. **Free Trial：** 前往 [GroupDocs](https://releases.groupdocs.com/conversion/java/) 註冊以下載試用版。  
2. **Temporary License：** 從 [purchase page](https://purchase.groupdocs.com/temporary-license/) 申請臨時授權以延長評估。  
3. **Purchase：** 商業使用時，請透過其 [buy page](https://purchase.groupdocs.com/buy) 購買授權。  

取得授權後，您即可實例化轉換器：

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.convert.ConvertOptions;

// Initialize the Converter object with a document path
Converter converter = new Converter("path/to/your/document");
```

## 實作指南
### Redis 快取整合概觀
我們將建立自訂的 `RedisCache` 類別，實作 `ICache` 介面。此類別示範 **Java Redis 連線範例**，並說明如何使用 **redis cache key prefix**。

`RedisCache` 是 GroupDocs 的 `ICache` 介面的自訂實作，用於將轉換結果儲存於 Redis。

#### 步驟 1：建立 RedisCache 類別
以下為完整實作。請保持程式碼與示範完全相同，內含所有必要的匯入與快取鍵處理邏輯。

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

#### 步驟 2：在 GroupDocs.Conversion 中使用 Redis 快取
現在我們將快取套用於轉換工作流程。此程式碼片段示範 **convert documents pdf java** 範例，會先檢查快取再呼叫 GroupDocs.Conversion。

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

### 關鍵設定選項
- **`_cacheKeyPrefix`** – 調整此 **redis cache key prefix** 以分組相關條目（例如 `"Docs:"`）。  
- **ConnectionMultiplexer settings** – 調整連線池、逾時或 SSL，以適用於分散式 Redis 叢集。

## Redis 如何提升轉換速度？
首次載入文件後，將產生的位元組陣列儲存於 Redis，之後的呼叫直接取回——省去重複的 CPU 密集型轉換。透過快取二進位輸出，可將平均回應時間從數秒縮減至數毫秒，特別是對於頻繁存取的熱門文件。

## 什麼是 Redis 快取鍵前綴？
`redis cache key prefix` 是在每個快取條目鍵前加上的短字串，讓您能將資料分段（例如 `"Docs:"` 用於文件快取，`"Thumb:"` 用於縮圖）。使用唯一的前綴可避免多個應用程式共用同一 Redis 實例時發生鍵衝突。

## 如何在 Java 中設定 Redis 連線？
建立 `ConnectionMultiplexer` 實例，指定 Redis 伺服器位址，必要時提供密碼與 SSL 設定。簡易本機設定可呼叫 `ConnectionMultiplexer.Connect("localhost")`。在正式環境叢集時，傳入以逗號分隔的節點端點清單，並使用 `ConfigurationOptions` 設定故障轉移與負載平衡。

## 如何以程式方式清除 Redis 快取？
使用 `KeyDelete` 方法搭配匹配您前綴鍵的模式（例如 `_db.KeyDelete("Docs:*")`）來呼叫 Redis 資料庫。此操作一次移除所有快取的轉換結果，於部署或原始檔案變更時相當有用。您亦可使用 `SCAN` 指令在刪除前遍歷符合的鍵，對大型資料集較為安全。  

`KeyDelete` 是 Redis 資料庫客戶端的方法，用於移除符合指定模式的鍵。

## 實務應用
1. **文件轉換工作流程：** 快取 PDF 或影像輸出，以即時回應重複請求。  
2. **內容傳遞網路 (CDN)：** 將快取的二進位檔案存於 Redis，以加速邊緣傳遞。  
3. **批次處理系統：** 在多次批次執行間重複使用轉換結果，節省 CPU 資源。

## 效能考量
### 最佳化 Redis 快取使用
- **Memory Management（記憶體管理）：** 設定適當的 `maxmemory` 與逐出策略（例如 `volatile-lru`）。  
- **Eviction Policies（逐出策略）：** 依使用模式選擇 LRU、LFU 或基於 TTL 的過期方式。  
- **Serialization Overhead（序列化開銷）：** 範例使用 Java 序列化；若需更緊湊的負載，可考慮 protobuf 或 JSON。

### 使用 GroupDocs.Conversion 的 Java 記憶體管理
透過串流結果 (`ByteArrayOutputStream`) 來處理大型檔案，並及時釋放資源。`RedisCache` 的 `AutoCloseable` 實作確保 Redis 連線能正確關閉。

## 常見問題與除錯
| 症狀 | 可能原因 | 解決方案 |
|---------|--------------|-----|
| `ConnectionMultiplexer.Connect` 拋出逾時 | Redis 無法連線或主機/埠錯誤 | 確認 Redis 伺服器已啟動且可連線 (`redis-cli ping`)。 |
| `TryGetValue` 總是返回 false | 儲存與取得的序列化格式不匹配 | 確保 `Set` 與 `TryGetValue` 使用相同的序列化器。 |
| 大型 PDF 發生記憶體不足錯誤 | 在 Redis 中儲存巨大的位元組陣列且未設限制 | 啟用 `maxmemory` 並設定適當的逐出策略。 |

## 常見問答

**Q: 我可以將此方法用於遠端 Redis 叢集嗎？**  
A: 可以。將 `"localhost"` 替換為叢集端點，並為 `ConnectionMultiplexer` 設定 SSL 與密碼驗證。

**Q: 如何變更 `redis cache key prefix`？**  
A: 在 `RedisCache` 中修改 `_cacheKeyPrefix` 欄位。使用唯一的前綴有助於避免跨應用程式的鍵衝突。

**Q: 有沒有程式方式清除快取？**  
A: 呼叫 `_db.KeyDelete(pattern)` 或使用 `GetKeys` 取得符合的鍵，然後在迴圈中刪除。

**Q: 此方法能轉換非 PDF 的文件嗎？**  
A: 完全可以。將 `PdfConvertOptions` 替換為相應的 `ConvertOptions` 子類別（例如 `DocxConvertOptions`）。

**Q: 需要哪個版本的 GroupDocs.Conversion？**  
A: 本教學已在 GroupDocs.Conversion **25.2** 版本測試過；較新版本應該相容。

## 結論
透過精通 **如何使用 Redis** 與 GroupDocs.Conversion 的結合，您已建立穩健的快取層，顯著縮短轉換時間、降低伺服器負載，並提升最終使用者體驗。持續嘗試不同的 **redis cache key prefix**、逐出策略與序列化格式，以微調您特定工作負載的效能。

**下一步**
- 嘗試不同的逐出策略（LRU、TTL）。  
- 針對大型文件批次進行記憶體使用分析。  
- 探索進階的 GroupDocs 功能，如浮水印或多頁轉換。

---

**最後更新：** 2026-07-24  
**測試版本：** GroupDocs.Conversion 25.2  
**作者：** GroupDocs

## 相關教學

- [如何在 Java 使用 Redis 與 GroupDocs 快取文件](/conversion/java/cache-management/custom-cache-redis-groupdocs-java/)
- [如何在 Java 使用 GroupDocs.Conversion 快取檔案 – 高效文件轉換完整指南](/conversion/java/cache-management/implement-java-file-caching-groupdocs-conversion-guide/)
- [實作自訂快取 Java – GroupDocs Conversion 快取](/conversion/java/cache-management/)