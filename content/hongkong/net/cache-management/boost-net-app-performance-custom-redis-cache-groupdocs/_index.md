---
"date": "2025-04-28"
"description": "了解如何使用 GroupDocs.Conversion 實作自訂 Redis 緩存，用於文件轉換，從而提升 .NET 應用效能。立即提升效率和速度！"
"title": "提升 .NET 應用程式效能 &#58; 使用 GroupDocs.Conversion 實作自訂 Redis 快取"
"url": "/zh-hant/net/cache-management/boost-net-app-performance-custom-redis-cache-groupdocs/"
"weight": 1
type: docs
---
# 使用 GroupDocs.Conversion 透過自訂 Redis 快取提升 .NET 應用程式效能

## 介紹

您的 .NET 應用程式中的文件轉換過程是否緩慢？結合使用自訂 Redis 快取和 GroupDocs.Conversion for .NET，提升效能和效率。本教學將引導您完成快取操作，以加快文件渲染速度。

**您將學到什麼：**
- 為 .NET 設定 GroupDocs.Conversion
- 實作自訂 Redis 快取以進行文件轉換
- 透過有效的快取策略優化效能

我們將指導您使用這些強大的工具來提升應用程式的效率。在開始之前，請確保您了解先決條件。

## 先決條件

要遵循本教程，請確保您已具備：

### 所需的庫和版本：
- **GroupDocs.Conversion for .NET** （版本 25.3.0）
- **StackExchange.Redis** Redis 操作庫
- Redis 伺服器正在執行的實例（例如， `192.168.222.4:6379`)

### 環境設定要求：
- Visual Studio 或其他支援 C# 的相容 IDE
- 已安裝 .NET Framework 或 .NET Core

### 知識前提：
- 對 C# 和 .NET 程式設計有基本的了解
- 熟悉 Redis 作為快取解決方案
- 具有軟體應用程式中文件轉換過程的經驗

## 為 .NET 設定 GroupDocs.Conversion

要開始使用 GroupDocs.Conversion，請透過 NuGet 套件管理器控制台或 .NET CLI 安裝它。

**NuGet 套件管理器控制台：**
```bash
Install-Package GroupDocs.Conversion -Version 25.3.0
```

**.NET CLI：**
```bash
dotnet add package GroupDocs.Conversion --version 25.3.0
```

### 許可證取得步驟：
- **免費試用：** 使用臨時許可證測試特性和功能。
- **臨時執照：** 不受限制地獲得擴展評估。
- **購買：** 為了長期使用，請考慮購買完整許可證。

安裝後，在您的 C# 應用程式中初始化 GroupDocs.Conversion：

```csharp
using GroupDocs.Conversion;
```

## 實施指南

### 使用 Redis 實作自訂緩存

本節示範如何使用 Redis 建立自訂緩存，用於文件渲染操作，以提高轉換速度和效率。

#### 概述
我們將實作基於 Redis 的快取機制來儲存渲染的文檔，避免冗餘處理並顯著加快轉換時間。

##### 步驟1：定義RedisCache類

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

    // 使用特定鍵在快取中設定數據
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

    // 嘗試使用密鑰從快取中檢索數據
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

    // 從快取中檢索所有符合過濾模式的鍵
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

**解釋：**
- **設定方法：** 使用特定的快取鍵將資料保存在 Redis 中。
- **TryGetValue 方法：** 如果可用，則檢索快取資料。
- **GetKeys 方法：** 取得與指定模式匹配的鍵。

##### 步驟2：使用自訂快取實現文件轉換

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

**解釋：**
- **RedisCache初始化：** 使用鍵前綴設定快取。
- **轉換器設定：** 將自訂快取整合到 GroupDocs.Conversion 設定中。
- **轉換過程：** 透過快取轉換結果來衡量並展示效能改進。

## 實際應用

### 用例：
1. **企業文件管理系統：** 提高大型應用程式的文件渲染速度。
2. **Web 服務：** 增強處理頻繁 PDF 轉換的 API 的回應時間。
3. **內容傳遞網路 (CDN)：** 快速快取並傳送預先轉換的文件。
4. **數據分析平台：** 加速涉及將資料轉換為可視格式的報告產生。
5. **電子商務網站：** 透過快取轉換後的圖像或文件預覽來優化產品目錄處理。

### 整合可能性：
- 與其他 .NET 框架（如 ASP.NET Core）結合用於 Web 應用程式。
- 使用 Docker 和 Kubernetes 整合到微服務架構中。

## 性能考慮

為了優化效能，請考慮以下事項：

- **快取大小管理：** 定期清除舊條目以防止記憶體溢出。
- **連接池：** 使用 Redis 中的連線池來有效管理資源。
- **資料序列化：** 選擇高效的序列化格式（例如，協定緩衝區）在 Redis 中儲存資料。

## 結論

使用 GroupDocs.Conversion for .NET 實作自訂 Redis 快取可以顯著提升應用程式的文件轉換效能。本教程提供了有關如何設定和使用這些強大工具來優化操作的逐步指導。

**後續步驟：**
- 嘗試不同的快取配置。
- 探索 GroupDocs.Conversion 的高級功能，以適應更複雜的用例。

準備好提升應用程式效率了嗎？立即開始實施此解決方案！

## 常見問題部分

1. **如何在本機上安裝 Redis？**
   - 按照適合您作業系統的官方 Redis 安裝指南進行操作： [Redis 下載](https://redis。io/download).
2. **使用 GroupDocs.Conversion 的自訂快取有哪些好處？**
   - 減少冗餘處理，加快轉換時間，降低資源使用率。
3. **我可以在雲端環境中使用此設定嗎？**
   - 當然！確保您的應用程式環境可以存取您的 Redis 實例。