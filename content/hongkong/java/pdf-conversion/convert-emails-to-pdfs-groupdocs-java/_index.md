---
date: '2026-01-18'
description: 學習使用 GroupDocs.Conversion for Java 進行電郵轉 PDF，並使用進階選項。控制電郵欄位的可見性，優化文件管理。
keywords:
- convert emails to PDFs with GroupDocs
- Java email conversion advanced options
- control visibility in email PDF conversion
title: 使用 GroupDocs.Conversion 在 Java 中將 Email 轉換為 PDF：進階選項指南
type: docs
url: /zh-hant/java/pdf-conversion/convert-emails-to-pdfs-groupdocs-java/
weight: 1
---

# 使用 GroupDocs.Conversion 的 Java 電子郵件轉 PDF 轉換：進階選項指南

將電子郵件訊息轉換為 PDF 是存檔、分享以及確保資料私隱的常見需求。在本教學中，您將掌握使用 GroupDocs.Conversion for Java 進行 **email to pdf conversion**，學習如何隱藏或顯示特定的電子郵件欄位，以及如何微調流程以獲得最佳效能。

## 快速解答
- **什麼函式庫負責 email to PDF 轉換？** GroupDocs.Conversion for Java。  
- **需要哪個 Maven 套件？** `com.groupdocs:groupdocs-conversion`。  
- **可以隱藏寄件者/收件者資訊嗎？** 可以 — 使用 `EmailLoadOptions` 來控制可見性。  
- **正式環境是否需要授權？** 非試用使用需具備有效的 GroupDocs 授權。  
- **支援的 Java 版本為何？** Java 8 或更高版本。

## 什麼是 Email to PDF 轉換？
Email to PDF 轉換會將 `.msg`、`.eml` 或其他電子郵件格式轉換為靜態、可攜帶的 PDF 文件。此過程會保留原始訊息的版面配置，同時讓您能夠編輯隱藏敏感資訊，如電子郵件地址、標頭或 CC/BCC 欄位。

## 為何使用 GroupDocs.Conversion for Java？
GroupDocs.Conversion 提供簡易的 API、強大的格式支援，以及細緻的載入選項，讓您能精確決定電子郵件的哪些部分會出現在最終 PDF 中。它亦能順利與 Maven 整合，使相依管理變得簡單。

## 前置條件
- **已安裝 Java Development Kit (JDK) 8+**。  
- **Maven** 用於相依管理（請參閱下方 *groupdocs conversion maven* 章節）。  
- 具備 Java 與 Maven 專案的基本知識。  

## 設定 GroupDocs.Conversion for Java

首先，將 GroupDocs 儲存庫與轉換相依項目加入您的 `pom.xml`。以下為您需要的 **groupdocs conversion maven** 設定。

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
- **免費試用** – 無償探索所有功能。  
- **臨時授權** – 申請短期金鑰以延長評估。  
- **購買** – 取得完整授權以用於正式部署。  

## 實作指南

### 使用進階選項將 Email 轉換為 PDF

以下為逐步說明，展示如何在自訂欄位可見性的同時 **convert msg to pdf**。

#### 步驟 1：設定 Email 載入選項
建立 `EmailLoadOptions` 實例，並關閉您不希望出現在 PDF 中的欄位。

```java
import com.groupdocs.conversion.options.load.EmailLoadOptions;

EmailLoadOptions loadOptions = new EmailLoadOptions();
loadOptions.setDisplayHeader(false);
loadOptions.setDisplayFromEmailAddress(false);
loadOptions.setDisplayToEmailAddress(false);
loadOptions.setDisplayEmailAddress(false);
loadOptions.setDisplayCcEmailAddress(false);
loadOptions.setDisplayBccEmailAddress(false);
loadOptions.setConvertOwned(false); // Prevent conversion of fields that are owned by the document
```

#### 步驟 2：初始化 Converter
在建立 `Converter` 物件時傳入已設定好的載入選項。

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.convert.PdfConvertOptions;

Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/SAMPLE_MSG", () -> loadOptions);
```

#### 步驟 3：設定 PDF 轉換選項
您可以使用 `PdfConvertOptions` 進一步自訂 PDF 輸出。此範例中，預設設定已足夠。

```java
PdfConvertOptions options = new PdfConvertOptions();
```

#### 步驟 4：執行轉換
呼叫 `convert` 方法，提供目標路徑與上述定義的選項。

```java
converter.convert("YOUR_OUTPUT_DIRECTORY/ConvertEmailWithAlteringFieldsVisibility.pdf", options);
```

### 依文件類型的載入選項
了解如何載入不同類型的文件對於彈性轉換至關重要。以下提供針對電子郵件的示例。

#### 步驟 1：設定 Email 載入選項（重複使用）

```java
import com.groupdocs.conversion.options.load.EmailLoadOptions;

EmailLoadOptions emailLoadOptions = new EmailLoadOptions();
emailLoadOptions.setDisplayHeader(false);
emailLoadOptions.setDisplayFromEmailAddress(false);
emailLoadOptions.setDisplayToEmailAddress(false);
emailLoadOptions.setDisplayEmailAddress(false);
emailLoadOptions.setDisplayCcEmailAddress(false);
emailLoadOptions.setDisplayBccEmailAddress(false);
emailLoadOptions.setConvertOwned(false); // Do not convert owned fields
```

#### 步驟 2：使用 Email 載入選項初始化 Converter

```java
Converter emailConverter = new Converter("EMAIL_FILE_PATH", () -> emailLoadOptions);
```

## 實務應用
以下列出三個 **email to pdf conversion** 發揮優勢的實際情境：

1. **法律文件** – 在與客戶分享電子郵件證據前，先編輯隱藏個人資料。  
2. **企業存檔** – 以標準化、唯讀的格式保存內部溝通。  
3. **個人整理** – 保留重要訊息的乾淨 PDF 檔案，同時不暴露不必要的地址。  

## 效能考量
- **優化檔案大小** – 以較小批次處理或在轉換後壓縮 PDF。  
- **記憶體管理** – 利用 Java 的垃圾回收機制，避免一次載入大型電子郵件至記憶體。  
- **保持更新** – 定期升級至最新的 GroupDocs.Conversion 版本，以獲得效能提升。  

## 常見問題與解決方案
| 問題 | 原因 | 解決方案 |
|------|------|----------|
| 大型 `.msg` 檔案導致 OutOfMemoryError | 整個檔案一次載入記憶體 | 串流電子郵件內容或增加 JVM 堆積大小（`-Xmx2g`）。 |
| PDF 中缺少電子郵件正文 | `displayHeader` 設為 `true` 而正文被隱藏 | 確認 `setDisplayHeader(false)` 只隱藏標頭，正文仍保持可見。 |
| 授權未被識別 | 在正式環境使用試用金鑰 | 改為使用有效的正式授權檔案或字串。 |

## 常見問答

**Q: 什麼是 GroupDocs.Conversion for Java？**  
A: 它是一個 Java 函式庫，可在超過 100 種檔案格式之間進行轉換，包含 email to PDF 轉換。

**Q: 如何在轉換過程中確保電子郵件的私隱？**  
A: 使用 `EmailLoadOptions` 在轉換前關閉寄件者、收件者以及 CC/BCC 地址等欄位。

**Q: 除了電子郵件外，我可以轉換其他文件類型嗎？**  
A: 可以，該函式庫支援 Word、Excel、PowerPoint、影像等多種格式。

**Q: 轉換大型電子郵件的記憶體需求為何？**  
A: 配置足夠的堆積空間（例如 `-Xmx2g`），並考慮分批處理檔案。

**Q: 我可以在哪裡取得更多關於 GroupDocs.Conversion 的資訊？**  
A: 前往[官方文件](https://docs.groupdocs.com/conversion/java/)與[API 參考](https://reference.groupdocs.com/conversion/java/)。

## 資源
- **文件**: [GroupDocs.Conversion for Java Docs](https://docs.groupdocs.com/conversion/java/)
- **API 參考**: [GroupDocs.Conversion API Reference](https://reference.groupdocs.com/conversion/java/)

---

**最後更新：** 2026-01-18  
**測試版本：** GroupDocs.Conversion 25.2  
**作者：** GroupDocs