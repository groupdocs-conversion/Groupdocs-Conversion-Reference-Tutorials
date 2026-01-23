---
date: '2025-12-26'
description: 了解如何使用 GroupDocs.Conversion for Java 在處理時區偏移的同時將電子郵件轉換為 PDF。非常適合檔案保存與跨時區協作。
keywords:
- Email to PDF Conversion
- Timezone Offset in Java
- GroupDocs.Conversion for Java
title: 如何在 Java 中使用 GroupDocs.Conversion 將電子郵件轉換為 PDF 並套用時區偏移
type: docs
url: /zh-hant/java/email-formats/email-to-pdf-conversion-java-groupdocs/
weight: 1
---

# 如何在 Java 中使用 GroupDocs.Conversion 將電郵轉換為 PDF 並套用時區偏移

將電郵文件（.eml、.msg 等）轉換成 PDF 可能會遇到挑戰，尤其是必須保留正確的時區資訊時更是如此。在本教學中，你將學會 **如何使用 GroupDocs.Conversion for Java 以自訂時區偏移將電郵轉換為 PDF**。無論是為了合規保存電郵，或是與全球團隊共享，本文都會一步步說明從專案設定到最終轉換的完整流程，讓你能快速實作可靠的解決方案。

## 快速答覆
- **哪個函式庫負責轉換？** GroupDocs.Conversion for Java。  
- **哪個主要方法設定時區？** `EmailLoadOptions.setTimeZoneOffset`。  
- **需要授權嗎？** 免費試用可用於測試；正式環境需購買正式授權。  
- **可以批次處理多封電郵嗎？** 可以——將轉換迴圈包在批次程序中即可。  
- **需要哪個 Java 版本？** JDK 8 或以上。

## 什麼是「將電郵轉換為 PDF」以及為什麼時區很重要？

當你將電郵（`.eml`、`.msg` 等）轉換為 PDF 時，原始的時間戳記會原樣複製。如果電郵是從不同的時區發送，這些時間戳記在其他地區的讀者看來可能會產生誤導。透過套用 **時區偏移**，你可以確保 PDF 中顯示的時間為正確的本地時間，從而保留通訊的上下文。

## 為什麼選擇 GroupDocs.Conversion for Java？

- **廣泛的格式支援** – 支援 `.eml`、`.msg` 以及其他多種電郵類型。  
- **內建時區處理** – `EmailLoadOptions` 允許以毫秒為單位設定偏移。  
- **高效能** – 基於串流的轉換減少記憶體佔用。  
- **企業級授權** – 提供彈性的試用與購買方案。

## 前置條件

在開始之前，請確保你已具備以下條件：

1. **函式庫與相依性**  
   - GroupDocs.Conversion for Java 版本 25.2 或更新版本。  

2. **環境設定**  
   - 已安裝 Java Development Kit (JDK 8+)。  
   - 使用 Maven 作為建置工具。  

3. **基礎知識**  
   - 基本的 Java 程式設計與檔案 I/O。  
   - 熟悉 Maven 相依性管理。

## 設定 GroupDocs.Conversion for Java

### 安裝資訊

在 `pom.xml` 中加入 GroupDocs 儲存庫與轉換相依性：

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

你可以先使用免費試用，或申請臨時授權以測試完整功能：

- **免費試用** – 下載函式庫並探索基本功能。  
- **臨時授權** – 前往 [此處](https://purchase.groupdocs.com/temporary-license/) 申請臨時授權。  
- **購買** – 長期使用請考慮從[官方網站](https://purchase.groupdocs.com/buy)購買授權。

### 基本初始化

以下程式碼示範如何建立 `Converter` 實例，並以時區偏移載入電郵：

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.load.EmailLoadOptions;

// Initialize GroupDocs.Conversion with necessary load options for email files
EmailLoadOptions loadOptions = new EmailLoadOptions();
loadOptions.setTimeZoneOffset(7200000.0); // Set timezone offset in milliseconds (e.g., 2 hours)
```

## 實作指南

### 電郵文件的載入選項

設定時區偏移可確保 PDF 反映正確的本地時間。

#### 步驟 1 – 設定時區偏移

```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
loadOptions.setTimeZoneOffset(7200000.0); // Set to 2 hours ahead (in milliseconds)
```

*說明*：`setTimeZoneOffset` 會依指定的毫秒數調整文件的時間戳記。

### 轉換設定與執行

接下來我們會配置 `Converter` 並執行轉換。

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

*說明*：`Converter` 以來源檔案路徑與提供先前定義 `loadOptions` 的 lambda 建立。這樣即可將時區設定與轉換流程綁定。

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

*說明*：`convert` 方法會將每一頁 PDF 串流至唯一命名的檔案。`try‑finally` 區塊確保所有串流在結束時關閉，避免資源洩漏。

## 實務應用

- **電郵歸檔** – 以正確時間戳記存放 PDF，符合法律或稽核需求。  
- **跨時區協作** – 全球團隊在轉換後的文件中看到相同的本地時間。  
- **電郵報表** – 產生保留原始發送/接收時間的 PDF 報表。

此工作流程可與 CRM 系統、文件管理平台或自動化批次作業整合，提升文件處理效率。

## 效能考量

- **資源管理** – 如範例所示即時關閉串流以釋放記憶體。  
- **批次處理** – 針對多個 `.eml` 檔案迴圈時，盡量重複使用同一個 `Converter` 實例。  
- **JVM 調校** – 大批次時調整堆疊大小 (`-Xmx`) 以避免 `OutOfMemoryError`。

## 常見問題與解決方案

| 症狀 | 可能原因 | 解決方式 |
|------|----------|----------|
| `NullPointerException` 於 `loadOptions` | 載入選項未正確傳遞 | 確認在建立 `Converter` 時使用 `() -> loadOptions` lambda。 |
| PDF 輸出為空白 | 輸入檔案路徑錯誤或檔案不存在 | 檢查 `sourceFilePath` 是否指向實際存在的 `.eml` 檔案。 |
| 時區未反映 | 偏移值單位錯誤（例如使用秒而非毫秒） | 以 **毫秒** 提供偏移值（例如 `7200000` 代表 +2 小時）。 |

## 常見問答

**Q: 什麼是 GroupDocs.Conversion for Java？**  
A: 這是一套功能強大的函式庫，可在數十種格式之間進行文件轉換，亦支援電郵轉 PDF。

**Q: 如何為電郵設定時區偏移？**  
A: 在初始化 `Converter` 前，使用 `EmailLoadOptions.setTimeZoneOffset(milliseconds)` 設定。

**Q: 這套組合能轉換多種電郵格式嗎？**  
A: 能，函式庫支援 `.eml`、`.msg` 以及其他常見電郵檔案類型。

**Q: 轉換過程中常見的陷阱是什麼？**  
A: 缺少相依性、檔案路徑錯誤、以及將偏移單位寫成秒而非毫秒。

**Q: 哪裡可以找到更多 GroupDocs.Conversion 的資源？**  
A: 前往[官方文件](https://docs.groupdocs.com/conversion/java/)取得詳細指南與 API 參考。

## 資源

- **文件說明**：前往 [GroupDocs Documentation](https://docs.groupdocs.com/conversion/java/) 繼續探索  
- **API 參考**：完整 API 參考可在[此處](https://reference.groupdocs.com/conversion/java/)取得  
- **下載 GroupDocs.Conversion**：從[此處](https://releases.groupdocs.com/conversion/java/)開始使用函式庫  
- **購買授權**：長期使用請至[GroupDocs 購買頁面](https://purchase.groupdocs.com/buy)購買授權  
- **免費試用與授權**：可在[GroupDocs 免費試用](https://releases.groupdocs.com/conversion/java/)或[臨時授權](https://purchase.groupdocs.com/temporary-license/)取得  
- **支援**：如需協助，請造訪[GroupDocs 論壇](https://forum.groupdocs.com/c/conversion/10)

立即在你的 Java 應用程式中運用 GroupDocs.Conversion 的威力，享受準確且具時區感知的 PDF 轉換吧！

---

**最後更新：** 2025-12-26  
**測試環境：** GroupDocs.Conversion 25.2  
**作者：** GroupDocs