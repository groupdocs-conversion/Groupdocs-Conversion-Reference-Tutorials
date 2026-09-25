---
date: '2026-09-25'
description: 了解如何使用 GroupDocs.Conversion 將 eml 轉換為 pdf（Java），並套用時區偏移以保留正確的時間戳記。為 Java
  開發人員提供的逐步指南。
keywords:
- convert eml to pdf java
- email to pdf conversion
- timezone offset java
lastmod: '2026-09-25'
og_description: 了解如何使用 GroupDocs.Conversion 將 eml 轉換為 pdf（Java），並套用時區偏移以保留正確的時間戳記。為開發人員提供的詳細
  Java 指南。
og_image_alt: 'Java guide: convert eml to pdf with timezone offset using GroupDocs.Conversion'
og_title: 使用 GroupDocs 轉換 eml 為 pdf（Java）並套用時區偏移
schemas:
- author: GroupDocs
  dateModified: '2026-09-25'
  description: Learn how to convert eml to pdf java with GroupDocs.Conversion, applying
    a timezone offset to preserve correct timestamps. Step‑by‑step guide for Java
    developers.
  headline: How to convert eml to pdf java with timezone offset
  type: TechArticle
- description: Learn how to convert eml to pdf java with GroupDocs.Conversion, applying
    a timezone offset to preserve correct timestamps. Step‑by‑step guide for Java
    developers.
  name: How to convert eml to pdf java with timezone offset
  steps:
  - name: '**Libraries & dependencies**'
    text: '**Libraries & dependencies**'
  - name: '**Environment**'
    text: '**Environment**'
  - name: '**Knowledge**'
    text: '**Knowledge**'
  type: HowTo
- questions:
  - answer: It’s a powerful library that enables document conversion across dozens
      of formats, including email to PDF, with built‑in timezone handling.
    question: What is GroupDocs.Conversion for Java?
  - answer: Use `EmailLoadOptions.setTimeZoneOffset(milliseconds)` before initializing
      the `Converter`.
    question: How do I set the timezone offset for emails?
  - answer: Yes, the library supports `.eml`, `.msg`, and other common email file
      types.
    question: Can I convert multiple email formats with this setup?
  - answer: Missing dependencies, incorrect file paths, and providing the offset in
      the wrong unit (seconds vs. milliseconds).
    question: What are common pitfalls during conversion?
  - answer: Visit the [official documentation](https://docs.groupdocs.com/conversion/java/)
      for detailed guides and API references.
    question: Where can I find more resources on GroupDocs.Conversion?
  type: FAQPage
tags:
- convert eml
- GroupDocs.Conversion
- Java email conversion
- timezone offset
- PDF generation
title: 如何在 Java 中將 eml 轉換為 pdf 並套用時區偏移
type: docs
url: /zh-hant/java/email-formats/email-to-pdf-conversion-java-groupdocs/
weight: 1
---

# 如何在 Java 中將 eml 轉換為 pdf 並調整時區偏移

在本教學中，您將學會如何 **convert eml to pdf java**，同時正確調整任何時區差異的時間戳記。使用 GroupDocs.Conversion for Java，您將看到完整的端到端工作流程——從 Maven 設定、載入帶有自訂偏移的電子郵件，到串流產生的 PDF 檔案。此步驟適用於 Java 8+ 開發者，需產出可靠、可存檔的 PDF，且顯示正確的本地時間。

## 快速回答
- **什麼函式庫負責轉換？** GroupDocs.Conversion for Java.  
- **哪個主要方法設定時區？** `EmailLoadOptions.setTimeZoneOffset`.  
- **需要授權嗎？** 免費試用可用於測試；正式上線需購買完整授權。  
- **可以批次處理多封電子郵件嗎？** 可以——將轉換迴圈包在批次程序中。  
- **需要哪個 Java 版本？** JDK 8 或更新版本。  

## 什麼是 convert eml to pdf java？
「convert eml to pdf java」描述的是使用 Java 程式碼將電子郵件檔案（通常為 `.eml` 或 `.msg`）產生 PDF 文件的過程。此轉換對於歸檔、法律合規以及跨平台分享非常重要，因為 PDF 能保留版面且可在任何裝置上檢視。

## 為什麼使用 GroupDocs.Conversion for Java？
GroupDocs.Conversion 支援 **70+** 種輸入與輸出格式，包括 `.eml`、`.msg`、`.pdf`、`.docx` 以及各類影像。其內建的 `EmailLoadOptions` 允許您以毫秒為單位指定時區偏移，確保 PDF 的時間戳記符合目標本地時間。函式庫以串流方式處理檔案，較載入整個文件至記憶體可降低高達 **80 %** 的記憶體使用量。

## 前置條件
在開始之前，請確保您已具備：

1. **函式庫與相依性**  
   - GroupDocs.Conversion for Java 版本 **25.2** 或更新。  

2. **環境**  
   - 已安裝並設定 JDK 8+。  
   - Maven 作為建置自動化工具。  

3. **知識**  
   - 基本的 Java 程式設計，尤其是檔案 I/O。  
   - 熟悉 Maven 的 `pom.xml` 結構。

## 設定 GroupDocs.Conversion for Java

### 安裝資訊
將 GroupDocs 倉庫與轉換相依性加入您的 `pom.xml`：

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
您可以先使用免費試用，或申請臨時授權以測試完整功能：

- **免費試用** – 下載函式庫並探索基本功能。  
- **臨時授權** – 申請臨時授權 [臨時授權頁面](https://purchase.groupdocs.com/temporary-license/)。  
- **購買** – 若長期使用，請考慮從 [官方網站](https://purchase.groupdocs.com/buy) 購買授權。

### 基本初始化
以下是建立 `Converter` 實例並以時區偏移載入電子郵件的最小程式碼：

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.load.EmailLoadOptions;

// Initialize GroupDocs.Conversion with necessary load options for email files
EmailLoadOptions loadOptions = new EmailLoadOptions();
loadOptions.setTimeZoneOffset(7200000.0); // Set timezone offset in milliseconds (e.g., 2 hours)
```

## 如何設定時區偏移？
`EmailLoadOptions` 是一個設定類別，控制電子郵件檔案的載入方式。請在轉換前以自訂偏移載入電子郵件。`setTimeZoneOffset` 方法接受 **毫秒** 為單位的偏移值，例如 +2 小時的偏移即為 `7200000`。此調整會重新寫入產生 PDF 中的顯示時間戳記。提供偏移後，函式庫會重新計算顯示的寄送與接收時間，確保產出的 PDF 反映收件者的本地時區。此功能對於跨國團隊審閱已存檔通訊特別有用。

```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
loadOptions.setTimeZoneOffset(7200000.0); // Set to 2 hours ahead (in milliseconds)
```

## 如何初始化 Converter 物件？
`Converter` 是執行文件轉換的主要類別，使用提供的載入選項。透過傳入來源檔案路徑與回傳先前定義的 `loadOptions` 的 lambda 來建立 `Converter`。此做法將時區設定綁定至轉換流程。它會讀取來源電子郵件，套用 `EmailLoadOptions` 設定（包括時區偏移），並為 PDF 產生準備輸出串流。使用 lambda 可確保在轉換時評估選項，對於處理多個檔案且設定各異的情況特別有幫助。

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.convert.PdfConvertOptions;

String sourceFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.eml"; // Path to the email document.
String outputPattern = "YOUR_OUTPUT_DIRECTORY/ConvertEmailWithTimezoneOffset-%d.pdf";

List<OutputStream> streamPool = new ArrayList<>();
Converter converter = new Converter(sourceFilePath, () -> loadOptions);
PdfConvertOptions options = new PdfConvertOptions();
```

## 如何執行轉換並串流 PDF 頁面？
`PdfConvertOptions` 指定 PDF 輸出的設定，如頁面大小、壓縮與影像品質。呼叫 `convert` 方法，傳入 `PdfConvertOptions` 實例與每頁的輸出串流。`try‑finally` 區塊確保所有串流在完成後關閉，避免資源泄漏。設定完選項後，`convert` 方法會遍歷電子郵件的每一頁，將 PDF 資料寫入各自的輸出串流。此方式讓您能有效處理大型電子郵件，因為每頁會單獨處理與刷新，最大程度降低記憶體消耗。

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

## 實務應用
- **歸檔電子郵件** – 以正確時間戳記的 PDF 存檔，用於法律或稽核目的。  
- **跨時區協作** – 全球團隊在轉換文件中看到相同的本地時間。  
- **電子郵件報表** – 產生保留原始寄送/接收時間的 PDF 報表，以符合合規需求。

您可以將此工作流程嵌入 CRM 系統、文件管理平台或自動化批次作業，以簡化文件管道。

## 效能考量
- **資源管理** – 如範例所示，及時關閉串流以釋放記憶體。  
- **批次處理** – 迭代 `.eml` 檔案集合時，盡可能重複使用單一 `Converter` 實例。  
- **JVM 調校** – 為大型批次調整堆疊大小 (`-Xmx`) 以避免 `OutOfMemoryError`。  

## 常見問題與解決方案

| 症狀 | 可能原因 | 解決方法 |
|------|----------|----------|
| `NullPointerException` at `loadOptions` | 未正確傳遞載入選項 | 確保在建立 `Converter` 時使用 lambda `() -> loadOptions`。 |
| PDF 輸出為空白 | 輸入檔案路徑不正確或檔案遺失 | 確認 `sourceFilePath` 指向現有的 `.eml` 檔案。 |
| 時區未反映 | 偏移值錯誤（例如使用秒而非毫秒） | 提供 **毫秒** 為單位的偏移值（例如 +2 小時為 `7200000`）。 |

## 常見問答
**Q: 什麼是 GroupDocs.Conversion for Java？**  
A: 它是一個功能強大的函式庫，可在數十種格式之間進行文件轉換，包括電子郵件轉 PDF，並內建時區處理功能。

**Q: 如何為電子郵件設定時區偏移？**  
A: 在初始化 `Converter` 之前，使用 `EmailLoadOptions.setTimeZoneOffset(milliseconds)` 設定時區偏移。

**Q: 我可以使用此設定轉換多種電子郵件格式嗎？**  
A: 可以，該函式庫支援 `.eml`、`.msg` 以及其他常見的電子郵件檔案類型。

**Q: 轉換過程中常見的陷阱是什麼？**  
A: 缺少相依性、檔案路徑不正確，以及以錯誤單位（秒而非毫秒）提供偏移值。

**Q: 我可以在哪裡找到更多關於 GroupDocs.Conversion 的資源？**  
A: 請前往 [官方文件](https://docs.groupdocs.com/conversion/java/) 取得詳細指南與 API 參考。

## 其他資源
- **文件**：於 [GroupDocs 文件](https://docs.groupdocs.com/conversion/java/) 繼續探索。  
- **API 參考**：詳細的 API 參考可於 [API 參考](https://reference.groupdocs.com/conversion/java/) 取得。  
- **下載 GroupDocs.Conversion**：從 [GroupDocs.Conversion 下載頁面](https://releases.groupdocs.com/conversion/java/) 開始使用。  
- **購買**：長期使用請於 [GroupDocs 購買頁面](https://purchase.groupdocs.com/buy) 購買授權。  
- **免費試用與授權**：可於 [GroupDocs 免費試用](https://releases.groupdocs.com/conversion/java/) 或 [臨時授權](https://purchase.groupdocs.com/temporary-license/) 取得。  
- **支援**：如需協助，請造訪 [GroupDocs 論壇](https://forum.groupdocs.com/c/conversion/10)。

善用 GroupDocs.Conversion 的強大功能於您的 Java 應用程式，立即體驗準確且具時區感知的 PDF 轉換！

---

**最後更新:** 2026-09-25  
**測試版本:** GroupDocs.Conversion 25.2  
**作者:** GroupDocs

## 相關教學

- [msg 轉 pdf java – 使用 GroupDocs 的電子郵件格式轉換](/conversion/java/email-formats/)
- [eml 轉 pdf java – 使用 GroupDocs 轉換電子郵件為 PDF](/conversion/java/pdf-conversion/convert-emails-to-pdfs-groupdocs-java/)
- [使用 GroupDocs.Conversion Java 轉換多種檔案類型 – 完整指南](/conversion/java/document-operations/groupdocs-conversion-java-master-document-conversion/)