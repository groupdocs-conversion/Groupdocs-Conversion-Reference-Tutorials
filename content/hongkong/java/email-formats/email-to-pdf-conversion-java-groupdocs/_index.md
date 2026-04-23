---
date: '2026-02-26'
description: 學習如何在 Java 中使用 GroupDocs.Conversion 進行帶時區偏移的電子郵件轉 PDF 轉換，適用於存檔及跨時區協作。
keywords:
- Email to PDF Conversion
- Timezone Offset in Java
- GroupDocs.Conversion for Java
title: 在 Java 中使用 GroupDocs.Conversion 進行 Email 轉 PDF 轉換並處理時區偏移
type: docs
url: /zh-hant/java/email-formats/email-to-pdf-conversion-java-groupdocs/
weight: 1
---

: none.

Now produce final content.# 如何在 Java 中使用 GroupDocs.Conversion 將電子郵件轉換為 PDF 並套用時區偏移

將電子郵件文件轉換為 PDF 可能相當具挑戰性，尤其在必須維持正確的時區資訊時更是如此。在本教學中，您將學習 **如何將電子郵件轉換為 PDF**，並使用 GroupDocs.Conversion for Java 以自訂時區偏移。此指南會逐步說明從專案設定到最終轉換的每個步驟，讓您能快速且有信心地實作可靠的 **電子郵件轉 PDF 轉換** 解決方案。

## 快速解答
- **哪個函式庫負責轉換？** GroupDocs.Conversion for Java.  
- **哪個主要方法設定時區？** `EmailLoadOptions.setTimeZoneOffset`.  
- **我需要授權嗎？** 免費試用版可用於測試；正式環境需購買完整授權。  
- **我可以批次處理多封電子郵件嗎？** 是的——將轉換迴圈包裝在批次程序中。  
- **需要哪個 Java 版本？** JDK 8 或更新版本。  

## 電子郵件轉 PDF 轉換概述
當您將電子郵件（`.eml`、`.msg` 等）轉換為 PDF 時，原始的時間戳記會原樣複製。如果該電子郵件來自不同的時區，這些時間戳記在其他地區的讀者看來可能會產生誤導。透過套用 **時區偏移**，您可確保 PDF 顯示正確的本地時間，保留通訊的情境。這就是有效 **電子郵件轉 PDF 轉換** 的核心。

## 為何使用 GroupDocs.Conversion for Java？
- **廣泛的格式支援** – 支援 `.eml`、`.msg` 以及許多其他電子郵件類型。  
- **內建時區處理** – `EmailLoadOptions` 允許您以毫秒設定偏移。  
- **高效能** – 基於串流的轉換降低記憶體占用。  
- **企業級授權** – 提供彈性的試用與購買選項。  

## 前置條件
在開始之前，請確保您具備以下條件：

1. **函式庫與相依性**  
   - GroupDocs.Conversion for Java 版本 25.2 或更新版本。  

2. **環境設定**  
   - 已安裝 Java Development Kit (JDK 8+)。  
   - Maven 作為建置工具。  

3. **知識需求**  
   - 基本的 Java 程式設計與檔案 I/O。  
   - 熟悉 Maven 相依性管理。  

## 設定 GroupDocs.Conversion for Java

### 安裝資訊
將 GroupDocs 套件庫與轉換相依性加入您的 `pom.xml` 中：

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
您可以先使用免費試用版，或申請臨時授權以測試完整功能：

- **免費試用** – 下載函式庫並探索基本功能。  
- **臨時授權** – 前往[此處](https://purchase.groupdocs.com/temporary-license/)申請臨時授權。  
- **購買** – 長期使用時，請考慮從[官方網站](https://purchase.groupdocs.com/buy)購買授權。  

### 基本初始化
以下為建立 `Converter` 實例並載入帶有時區偏移之電子郵件所需的最小程式碼：

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.load.EmailLoadOptions;

// Initialize GroupDocs.Conversion with necessary load options for email files
EmailLoadOptions loadOptions = new EmailLoadOptions();
loadOptions.setTimeZoneOffset(7200000.0); // Set timezone offset in milliseconds (e.g., 2 hours)
```

## 實作指南

### 電子郵件文件的載入選項
設定時區偏移可確保 PDF 顯示正確的本地時間。

#### 步驟 1 – 設定時區偏移
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
loadOptions.setTimeZoneOffset(7200000.0); // Set to 2 hours ahead (in milliseconds)
```

*說明*：`setTimeZoneOffset` 會依指定的毫秒數調整文件的時間戳記。

### 轉換設定與執行

#### 步驟 2 – 初始化 Converter 物件
```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.convert.PdfConvertOptions;

String sourceFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.eml"; // Path to the email document.
String outputPattern = "YOUR_OUTPUT_DIRECTORY/ConvertEmailWithTimezoneOffset-%d.pdf";

List<OutputStream> streamPool = new ArrayList<>();
Converter converter = new Converter(sourceFilePath, () -> loadOptions);
PdfConvertOptions options = new PdfConvertOptions();
```

*說明*：`Converter` 以來源檔案路徑以及提供先前定義的 `loadOptions` 的 lambda 建立。此設定將時區設定與轉換流程結合。

#### 步驟 3 – 執行轉換
```java
try {
    converter.convert((SaveDocumentStreamForFileType) t -> {
        try {
            OutputStream outputStream = Files.newOutputStream(Paths.get(String.format(outputPattern, streamPool.size())));
            streamPool.add(outputStream);
            return outputStream;
        } catch (IOException e) {
            throw new RuntimeException(e);
        }
    }, options);
} finally {
    for (OutputStream outputStream : streamPool) {
        if (outputStream != null) {
            outputStream.close();
        }
    }
}
```

*說明*：`convert` 方法會將每個 PDF 頁面串流至唯一命名的檔案。`try‑finally` 區塊確保所有串流皆被關閉，防止資源泄漏。

## 實務應用
- **電子郵件歸檔** – 將 PDF 以正確的時間戳記儲存，用於法律或稽核目的。  
- **跨時區協作** – 全球團隊在轉換後的文件中看到相同的本地時間。  
- **電子郵件報告** – 產生保留原始發送/接收時間的 PDF 報告。  

您可以將此工作流程整合至 CRM 系統、文件管理平台或自動化批次作業，以簡化文件處理流程。

## 效能考量
- **資源管理** – 及時關閉串流（如範例所示），釋放記憶體。  
- **批次處理** – 迭代 `.eml` 檔案集合，盡可能重複使用同一個 `Converter` 實例。  
- **JVM 調校** – 為大型批次調整堆積大小（`-Xmx`），避免 `OutOfMemoryError`。  

## 常見問題與解決方案

| 症狀 | 可能原因 | 解決方法 |
|---------|--------------|-----|
| `NullPointerException` at `loadOptions` | 未正確傳遞載入選項 | 確保在建立 `Converter` 時使用 lambda `() -> loadOptions`。 |
| PDF 輸出為空白 | 輸入檔案路徑不正確或檔案遺失 | 確認 `sourceFilePath` 指向現有的 `.eml` 檔案。 |
| 時區未反映 | 偏移值錯誤（例如使用秒而非毫秒） | 以 **毫秒** 提供偏移值（例如 +2 小時 為 `7200000`）。 |

## 常見問答
**Q: 什麼是 GroupDocs.Conversion for Java？**  
A: 它是一個功能強大的函式庫，可在數十種格式之間進行文件轉換，亦支援電子郵件轉 PDF。

**Q: 如何為電子郵件設定時區偏移？**  
A: 使用 `EmailLoadOptions.setTimeZoneOffset(milliseconds)`，於初始化 `Converter` 前設定。

**Q: 這個設定能轉換多種電子郵件格式嗎？**  
A: 可以，函式庫支援 `.eml`、`.msg` 以及其他常見的電子郵件檔案類型。

**Q: 轉換過程中常見的陷阱是什麼？**  
A: 缺少相依性、檔案路徑不正確，以及以錯誤單位（秒而非毫秒）提供偏移值。

**Q: 在哪裡可以找到更多關於 GroupDocs.Conversion 的資源？**  
A: 請參閱[官方文件](https://docs.groupdocs.com/conversion/java/)，獲取詳細指南與 API 參考。

## 資源
- **文件說明**：前往[GroupDocs Documentation](https://docs.groupdocs.com/conversion/java/) 瞭解更多。  
- **API 參考**：詳細的 API 參考可在[此處](https://reference.groupdocs.com/conversion/java/)取得。  
- **下載 GroupDocs.Conversion**：從[此處](https://releases.groupdocs.com/conversion/java/)開始使用函式庫。  
- **購買**：長期使用請於[GroupDocs Purchase Page](https://purchase.groupdocs.com/buy)購買授權。  
- **免費試用與授權**：可免費試用或於[GroupDocs Free Trial](https://releases.groupdocs.com/conversion/java/)與[Temporary License](https://purchase.groupdocs.com/temporary-license/) 申請臨時授權。  
- **支援**：如需協助，請造訪[GroupDocs Forum](https://forum.groupdocs.com/c/conversion/10)。  

善用 GroupDocs.Conversion 為您的 Java 應用程式帶來強大功能，立即體驗精確且具時區感知的 PDF 轉換！

---

**最後更新：** 2026-02-26  
**測試版本：** GroupDocs.Conversion 25.2  
**作者：** GroupDocs