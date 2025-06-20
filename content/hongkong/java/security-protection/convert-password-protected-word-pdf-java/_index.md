---
"date": "2025-04-28"
"description": "學習如何使用 GroupDocs.Conversion for Java 將受密碼保護的 Word 文件轉換為 PDF。掌握如何指定頁面、調整 DPI 以及旋轉內容。"
"title": "使用 GroupDocs.Conversion 在 Java 中將受密碼保護的 Word 轉換為 PDF"
"url": "/zh-hant/java/security-protection/convert-password-protected-word-pdf-java/"
"weight": 1
---

# 使用 GroupDocs.Conversion 在 Java 中將受密碼保護的 Word 轉換為 PDF

這份全面的指南將指導您如何使用 Java 中的 GroupDocs.Conversion 庫，輕鬆將受保護的 Word 文件轉換為 PDF 格式。了解如何指定特定頁面、設定自訂尺寸、調整解析度以及最佳化效能，以實現無縫文件轉換。

## 您將學到什麼：
- 使用 GroupDocs.Conversion for Java 轉換受密碼保護的 Word 檔案。
- 指定文件的確切頁面或部分以進行 PDF 轉換。
- 在轉換為 PDF 之前旋轉文件內容。
- 在 PDF 轉換期間調整自訂解析度的 DPI 設定。
- 利用 Java 記憶體管理的最佳實踐來提高效能。

## 先決條件
在繼續操作之前，請確保您已滿足以下先決條件：

### 所需的庫和依賴項
若要使用 GroupDocs.Conversion，請新增必要的程式庫。如果使用 Maven，請將儲存庫和依賴項新增至您的 `pom.xml`：

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

### 環境設定
確保您的電腦上已安裝並設定 Java 開發工具包 (JDK)。建議您對 Java 程式設計有基本的了解。

### 許可證獲取
GroupDocs.Conversion 提供免費試用版，方便您測試各項功能。如需長期使用，請考慮從以下平台取得臨時或完整許可證： [GroupDocs 購買](https://purchase。groupdocs.com/buy).

## 為 Java 設定 GroupDocs.Conversion
若要開始使用 GroupDocs.Conversion，請在專案中執行一些初始設定。

### Maven 設定
包含前面提到的必要的 Maven 依賴項，以確保所有必要的程式庫都已下載並可供使用。

### 基本初始化
透過建立以下實例來初始化 GroupDocs.Conversion `Converter` 類。這是一個基本設定：

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.load.WordProcessingLoadOptions;

WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
// 如果需要，請為受保護的文件設定密碼：
loadOptions.setPassword("your_password_here");

Converter converter = new Converter("path_to_your_document.docx", () -> loadOptions);
```

此程式碼片段初始化文件的轉換。 `loadOptions` 類別有助於管理密碼保護和其他設定。

## 實施指南
讓我們來探索如何使用 Java 中的 GroupDocs.Conversion 來實現關鍵功能。

### 將受密碼保護的文件轉換為 PDF
**概述：**
將受密碼保護的 Word 文件無縫轉換為 PDF 檔案。

#### 逐步實施
##### 使用密碼初始化載入選項
設定存取受保護文件的密碼：

```java
WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
loadOptions.setPassword("12345"); // 替換為您的實際密碼。
```

##### 設定轉換器並轉換
初始化 `Converter` 類，定義PDF轉換選項，並執行轉換：

```java
import com.groupdocs.conversion.options.convert.PdfConvertOptions;

String convertedFile = "YOUR_OUTPUT_DIRECTORY/ConvertedDocument.pdf";
PdfConvertOptions options = new PdfConvertOptions();

Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/SampleProtectedDocx.docx", () -> loadOptions);
converter.convert(convertedFile, options);
```

**解釋：**
這 `loadOptions` 物件對於處理受密碼保護的文件至關重要。正確設定密碼可確保成功存取和轉換。

#### 故障排除提示
- 仔細檢查密碼的準確性；拼字錯誤是常見問題。
- 驗證文件路徑以防止 `FileNotFoundException`。

### 指定要轉換的 PDF 頁面
**概述：**
選擇文件的特定頁面進行 PDF 轉換。

#### 逐步實施
##### 設定頁面範圍
定義要轉換的頁面：

```java
PdfConvertOptions options = new PdfConvertOptions();
options.setPageNumber(2); // 從第 2 頁開始。
options.setPagesCount(1); // 僅轉換一頁。
```

##### 轉換過程
使用指定的設定 `options` 轉換：

```java
String convertedFile = "YOUR_OUTPUT_DIRECTORY/SelectedPagesPdf.pdf";
Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/SampleDocx.docx", () -> loadOptions);
converter.convert(convertedFile, options);
```

**解釋：**
這 `setPageNumber()` 和 `setPagesCount()` 方法可以精確控制要轉換的文件部分。

### PDF轉換中旋轉頁面
**概述：**
在轉換過程中旋轉頁面以實現所需的方向。

#### 逐步實施
##### 設定旋轉選項
指定旋轉設定：

```java
import com.groupdocs.conversion.options.convert.Rotation;

PdfConvertOptions options = new PdfConvertOptions();
options.setRotate(Rotation.On180); // 將頁面旋轉 180 度。
```

##### 執行轉換
使用指定的旋轉選項進行初始化和轉換：

```java
String convertedFile = "YOUR_OUTPUT_DIRECTORY/RotatedPagesPdf.pdf";
Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/SampleDocx.docx", () -> loadOptions);
converter.convert(convertedFile, options);
```

**解釋：**
旋轉頁面對於修正方向或滿足特定的佈局要求很有用。

### 設定 PDF 轉換的 Dpi
**概述：**
調整轉換後的 PDF 的解析度 (DPI) 以滿足品質需求。

#### 逐步實施
##### 配置 DPI 設定
設定所需的 DPI 值：

```java
PdfConvertOptions options = new PdfConvertOptions();
options.setDpi(300); // 將 DPI 設定為 300 以獲得高解析度。
```

##### 使用自訂 DPI 執行轉換
使用以下設定繼續轉換：

```java
String convertedFile = "YOUR_OUTPUT_DIRECTORY/HighResolutionPdf.pdf";
Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/SampleDocx.docx", () -> loadOptions);
converter.convert(convertedFile, options);
```

**解釋：**
較高的 DPI 值可提升影像質量，但可能會增加檔案大小。請根據您的需求進行調整。

### 設定 PDF 轉換的寬度和高度
**概述：**
在轉換過程中自訂產生的 PDF 的尺寸。

#### 逐步實施
##### 定義維度
設定寬度和高度參數：

```java
PdfConvertOptions options = new PdfConvertOptions();
options.setWidth(1024); // 將寬度設定為 1024 像素。
options.setHeight(768); // 將高度設定為 768 像素。
```

##### 使用自訂尺寸進行轉換
使用以下尺寸繼續轉換：

```java
String convertedFile = "YOUR_OUTPUT_DIRECTORY/SizedPdf.pdf";
Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/SampleDocx.docx", () -> loadOptions);
converter.convert(convertedFile, options);
```

**解釋：**
自訂尺寸有助於根據特定的顯示或列印要求自訂輸出 PDF。