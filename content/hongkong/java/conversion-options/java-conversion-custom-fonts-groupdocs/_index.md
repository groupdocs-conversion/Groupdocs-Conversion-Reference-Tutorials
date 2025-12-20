---
date: '2025-12-20'
description: 了解如何使用 GroupDocs.Conversion for Java 將簡報轉換為 PDF，包括自訂字型替換以及 pptx 轉 PDF
  的 Java 支援。
keywords:
- Java document conversion
- custom fonts in Java
- GroupDocs.Conversion for Java
title: Java：使用 GroupDocs.Conversion 將簡報轉換為 PDF
type: docs
url: /zh-hant/java/conversion-options/java-conversion-custom-fonts-groupdocs/
weight: 1
---

# Java：使用 GroupDocs.Conversion 將簡報轉換為 PDF

在當今節奏快速的數位環境中，可靠地 **將簡報轉換為 PDF** 並保留原始外觀是必備功能。無論您是要分享給客戶的簡報、歸檔培訓資料，或是自動化報告產生，缺少字型都會破壞視覺體驗。本教學將指導您使用 GroupDocs.Conversion for Java 進行 **將簡報轉換為 PDF**，並使用自訂字型替代，確保輸出在任何裝置上都與原稿完全相同。

## 快速回答
- **「convert presentation to PDF」是什麼意思？** 它將 PowerPoint 檔案（例如 .pptx）轉換為 PDF 文件，同時保留版面配置、圖形和文字。  
- **哪個函式庫負責轉換？** GroupDocs.Conversion for Java。  
- **我需要 Maven 相依性嗎？** 是 – 在下方加入 **groupdocs maven dependency**。  
- **我可以替換缺少的字型嗎？** 當然可以，使用 `FontSubstitute` 將不可用的字型映射為替代字型。  
- **生產環境需要授權嗎？** 需要，商業使用必須擁有有效的 GroupDocs 授權。  

## 在 Java 中「convert presentation to PDF」是什麼？
將簡報轉換為 PDF 意味著取得 PowerPoint 檔案（通常為 .pptx），產生與原始投影片相同的 PDF 版本。此過程包括解析投影片內容、繪製圖形，並嵌入字型，使 PDF 在各平台上顯示一致。

## 為何在此任務使用 GroupDocs.Conversion？
- **高保真** – 保持精確的版面配置、動畫（作為靜態影像）以及向量圖形。  
- **自訂字型支援** – 讓您定義備援字型，消除「缺少字型」警告。  
- **Maven 友好** – 簡單整合 **groupdocs maven dependency**。  
- **跨平台** – 可在 Windows、Linux 與 macOS 上運作，無需額外本機二進位檔。  

## 前置條件
1. 已安裝 **Java Development Kit (JDK) 8+**。  
2. 用於相依性管理的 **Maven**（或您偏好的 Gradle）。  
3. 具備 Java 與 Maven 專案結構的基本知識。  
4. 取得 **GroupDocs.Conversion** 授權（試用或付費）。  

## 設定 GroupDocs.Conversion for Java

### Maven 設定（groupdocs maven dependency）

將儲存庫與相依性加入您的 `pom.xml`：

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

> **專業提示：** 請定期檢查 GroupDocs Maven 儲存庫，以保持版本號為最新。

### 取得授權
- **免費試用：** 從 GroupDocs 官方網站下載試用版。  
- **臨時授權：** 申請臨時金鑰以延長測試時間。  
- **正式授權：** 滿意後購買正式授權。  

## 實作指南

### 如何使用自訂字型替代將簡報轉換為 PDF

#### 步驟 1：使用字型替代定義 Presentation Load Options

建立輔助方法以準備 `PresentationLoadOptions`，並將缺少的字型映射至可用字型。

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.load.PresentationLoadOptions;
import com.groupdocs.conversion.contracts.FontSubstitute;
import java.util.ArrayList;
import java.util.List;

public PresentationLoadOptions definePresentationLoadOptionsWithFontSubstitution() {
    // Initialize PresentationLoadOptions
    PresentationLoadOptions loadOptions = new PresentationLoadOptions();
    
    // Create a list to hold font substitutes
    List<FontSubstitute> fontSubstitutes = new ArrayList<>();
    
    // Add font substitution mappings
    fontSubstitutes.add(FontSubstitute.create("Tahoma", "Arial"));
    fontSubstitutes.add(FontSubstitute.create("Times New Roman", "Arial"));
    
    // Set default font to be used if a specific font is not found
    loadOptions.setDefaultFont("YOUR_DOCUMENT_DIRECTORY/resources/fonts/Helvetica.ttf");
    
    // Apply the font substitutes to the load options
    loadOptions.setFontSubstitutes(fontSubstitutes);
    
    return loadOptions;
}
```

**說明：**  
- **字型替代** 將不可用的字型（例如 Tahoma）映射為可靠的替代字型（Arial）。  
- **預設字型** 提供最終備援，確保每個文字元素都有字形。  

#### 步驟 2：使用載入選項將簡報轉換為 PDF

現在使用 `Converter` 類別搭配 `PdfConvertOptions` 來執行實際的轉換。

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.convert.PdfConvertOptions;

public void defineConversionProcessWithAdvancedOptions(PresentationLoadOptions loadOptions) {
    // Specify the path for the converted PDF file
    String convertedFile = "YOUR_OUTPUT_DIRECTORY/ConvertedPresentation.pdf";
    
    // Initialize Converter with the presentation file and load options
    Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/Presentation.pptx", () -> loadOptions);
    
    // Set up PDF conversion options (empty for default configuration)
    PdfConvertOptions options = new PdfConvertOptions();
    
    // Perform the conversion from presentation to PDF
    converter.convert(convertedFile, options);
}
```

**說明：**  
- **Converter 初始化** 將來源 `.pptx` 檔案與自訂的 `loadOptions` 連結。  
- **PdfConvertOptions** 可擴充（例如設定影像品質），但預設設定已能滿足大多數情況。  

### 實務使用案例

| 情境 | 為何自訂字型重要 |
|----------|------------------------|
| **企業品牌** | 確保即使在未安裝企業字型的機器上，也能保持品牌一致的字型。 |
| **線上學習教材** | 學生收到的 PDF 與原始投影片外觀完全相同，無論使用何種作業系統。 |
| **法律文件** | 法院常要求 PDF；字型替代可避免文字無法辨識。 |

## 效能考量
- **記憶體管理：** 大型簡報可能佔用大量堆積空間。如遇 `OutOfMemoryError`，請提升 JVM `-Xmx` 參數。  
- **限制替代字型：** 僅映射真正需要的字型；不必要的映射會增加處理負擔。  
- **重複使用載入選項：** 若批次轉換多個檔案，請一次建立 `PresentationLoadOptions` 後重複使用。  

## 常見陷阱與疑難排解
1. **缺少字型檔案：** 確認備援字型檔案（範例中的 `Helvetica.ttf`）存在且路徑正確。  
2. **Maven 版本不正確：** 使用過時的 GroupDocs 版本可能缺少 `FontSubstitute` API。請升級至最新版本。  
3. **檔案路徑問題：** 使用絕對路徑或設定 Maven 資源，以避免 `FileNotFoundException`。  

## 常見問答

**Q：在將簡報轉換為 PDF 時使用自訂字型替代的主要好處是什麼？**  
A：即使目標環境缺少原始字型，也能確保視覺版面保持不變。

**Q："pptx to pdf java" 與簡單的檔案複製有何不同？**  
A：轉換會渲染每張投影片、嵌入字型，並將圖形平面化為 PDF，這是單純複製無法做到的。

**Q：我可以將此轉換整合到 CI/CD 流程中嗎？**  
A：可以——將 Java 程式碼封裝為 Maven 外掛或 Docker 容器，並在建置階段呼叫。

**Q：GroupDocs.Conversion 支援雲端儲存作為輸入嗎？**  
A：當然支援。您可以直接將來自 AWS S3、Azure Blob 或 Google Cloud Storage 的串流傳遞給 `Converter`。

**Q：我的 200 頁簡報轉換速度很慢，有什麼建議嗎？**  
A：增加堆積大小、將字型替代限制在必要的範圍，若 CPU 允許，可考慮平行批次轉換。

## 結論

現在您已擁有完整、可投入生產的解決方案，使用 GroupDocs.Conversion for Java **將簡報轉換為 PDF**，並支援自訂字型處理。只要加入 Maven 相依性、定義字型替代，並呼叫轉換器，即可保證 PDF 在任何裝置上皆與原始投影片完全相同。

**下一步：**  
- 嘗試使用額外的 `PdfConvertOptions`（例如影像壓縮）。  
- 將此邏輯與檔案監看服務結合，以自動化批次轉換。  
- 探索 GroupDocs 的其他轉換功能（例如 DOCX → PDF、HTML → PDF）。

---

**最後更新：** 2025-12-20  
**測試版本：** GroupDocs.Conversion 25.2  
**作者：** GroupDocs