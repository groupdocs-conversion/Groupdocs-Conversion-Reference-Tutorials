---
date: '2026-01-26'
description: 學習如何在 Java 中使用 Redis 快取與 GroupDocs.Conversion 以提升應用程式效能。此 Redis 快取 Java
  教學涵蓋設定、快取策略及效能技巧。
keywords:
- Redis Cache Java
- GroupDocs.Conversion for Java
- Java caching
title: 如何在 Java 中使用 Redis 快取與 GroupDocs.Conversion
type: docs
url: /zh-hant/java/cache-management/redis-cache-java-groupdocs-conversion-guide/
weight: 1
---

# 如何在 Java 中使用 Redis 快取與 GroupDocs.Conversion

Redis 是一個功能強大的開源、記憶體內資料結構存儲，可作為資料庫、快取和訊息代理。當您學習 **如何使用 Redis** 與 GroupDocs.Conversion 結合時，您為 Java 應用程式提供了一個快速的快取層，顯著降低文件轉換延遲。在本指南中，我們將完整走過 **redis cache java tutorial**，從環境設定到實務使用，讓您立即看到效能提升。

## 快速答案
- **使用 Redis 與 GroupDocs 的主要好處是什麼？** 透過避免重複轉換，加快文件檢索速度。  
- **哪個 Maven 套件會加入 GroupDocs.Conversion？** `com.groupdocs:groupdocs-conversion`。  
- **如何在 Java 中連接 Redis？** 使用類似 `ConnectionMultiplexer.Connect("localhost")` 的 Java Redis 連接範例。  
- **我可以自訂快取鍵嗎？** 可以 — `redis cache key prefix` 讓您組織條目。  
- **生產環境是否需要授權？** 需要，必須擁有有效的 GroupDocs.Conversion 授權。

## 介紹

想像一個高流量入口網站，根據需求即時提供由 Word 或 Excel 檔案產生的 PDF。若未使用快取，每個請求都會觸發全新轉換，耗用 CPU 與 I/O。透過學習 **如何使用 Redis**，您可以將已轉換的位元組陣列儲存一次，之後的請求即可即時取回。這不僅加快回應時間，亦減輕伺服器負載，提升使用者體驗。

**您將學會**
- 在 Java 中設定 Redis 快取  
- 實作自訂 `RedisCache` 類別（**java redis connection example**）  
- 使用 GroupDocs.Conversion 轉換文件並快取結果  
- 調整 **redis cache key prefix** 以更佳組織  
- 生產環境的效能調校技巧  

讓我們從先決條件開始。

## 先決條件
### 必要的函式庫與相依性
1. **Java Development Kit (JDK)：** 版本 8 或更新。  
2. **Redis Server：** 本機執行或可遠端存取。  
3. **GroupDocs.Conversion for Java：** 透過 Maven 加入（請參閱下方的 **maven dependency groupdocs** 章節）。

### 環境設定
- 依照 [this guide](https://redis.io/download) 安裝 Redis。  
- 使用適當的 JDK 設定您的 IDE（IntelliJ IDEA、Eclipse 等）。

### 知識先備
- 基本的 Java 與物件導向概念。  
- 熟悉 Maven 以管理相依性。  
- 了解快取原理以及其對文件轉換的重要性。

## 設定 GroupDocs.Conversion for Java

首先，將 GroupDocs.Conversion 函式庫加入您的專案。以下的 Maven 片段即為您需要的官方 **maven dependency groupdocs**。

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
1. **免費試用：** 前往 [GroupDocs](https://releases.groupdocs.com/conversion/java/) 註冊以下載試用版。  
2. **臨時授權：** 從 [purchase page](https://purchase.groupdocs.com/temporary-license/) 申請臨時授權以延長評估。  
3. **購買：** 商業使用請透過其 [buy page](https://purchase.groupdocs.com/buy) 購買授權。

取得授權後，您即可實例化轉換器：

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.convert.ConvertOptions;

// Initialize the Converter object with a document path
Converter converter = new Converter("path/to/your/document");
```

## 實作指南
### Redis 快取整合概觀

我們將建立一個實作 `ICache` 的自訂 `RedisCache` 類別。此類別示範 **java redis connection example**，並說明如何使用 **redis cache key prefix**。

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
現在我們將快取套入轉換工作流程。此片段展示一個 **convert documents pdf java** 範例，會先檢查快取再呼叫 GroupDocs.Conversion。

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

### 鍵值設定選項
- **`_cacheKeyPrefix`** – 調整此 **redis cache key prefix** 以分組相關條目（例如 `"Docs:"`）。  
- **ConnectionMultiplexer 設定** – 為分散式 Redis 叢集調校連線池、逾時或 SSL。

## 實務應用
1. **文件轉換工作流程：** 快取 PDF 或影像輸出，以即時回應重複請求。  
2. **內容傳遞網路 (CDN)：** 將快取的二進位檔存於 Redis，以快速在邊緣提供。  
3. **批次處理系統：** 在多次批次執行間重複使用轉換結果，節省 CPU 時間。

## 效能考量
### 最佳化 Redis 快取使用
- **記憶體管理：** 設定適當的 `maxmemory` 與逐出策略（例如 `volatile-lru`）。  
- **逐出策略：** 依使用模式選擇 LRU、LFU 或基於 TTL 的過期方式。  
- **序列化開銷：** 範例使用 Java 序列化；若需更小負載可考慮 protobuf 或 JSON。

### 使用 GroupDocs.Conversion 的 Java 記憶體管理
透過串流結果 (`ByteArrayOutputStream`) 來處理大型檔案，並即時釋放資源。`RedisCache` 的 `AutoCloseable` 實作可確保 Redis 連線正確關閉。

## 常見問題與除錯
| 症狀 | 可能原因 | 解決逾時 | Redis 無法連線或 確保 `Set` 與 `Try 此能轉換非 PDF 的文件嗎？**  
A: 當然可以。將 `PdfConvertOptions` 替換為相應的 `ConvertOptions` 子類別（例如 `DocxConvertOptions`）。

**Q: 需要哪個版本的 GroupDocs.Conversion？**  
A: 本教學以 GroupDocs.Conversion **25.2** 為測試版本；較新版本應該相容。

## 結論
透過 的結合，您已建立一個強韌的快取層，顯著縮短轉換時間、降低伺服器負載，並提升最終使用者體驗。持續嘗試不同的 **redis cache key prefixes**、逐出策略與序列化格式，以微調您特定工作負載的效能。

**下一步**
- 嘗試不同的逐出策略（LRU、TTL）。  
- 針對大型文件批次進行記憶體使用分析。  
- 探索進階的 GroupDocs 功能，如浮水印或多頁轉換。

---

**最後更新：** 2026-01-26  
**測試版本：** GroupDocs.Conversion 25.2  
**作者：** GroupDocs