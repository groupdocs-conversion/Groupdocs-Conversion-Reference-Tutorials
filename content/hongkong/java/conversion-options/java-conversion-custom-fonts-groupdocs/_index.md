---
date: '2026-01-28'
description: 學習如何使用 GroupDocs.Conversion for Java 將簡報轉換為 PDF，並進行自訂字型取代。保留字型，確保文件外觀一致。
keywords:
- Java document conversion
- custom fonts in Java
- GroupDocs.Conversion for Java
title: 如何使用 GroupDocs.Conversion for Java 將簡報轉換為帶自訂字型的 PDF
type: docs
url: /zh-hant/java/conversion-options/java-conversion-custom-fonts-groupdocs/
weight: 1
---

# 如何使用 GroupDocs.Conversion for Java 以自訂字型將簡報轉換為 PDF

在現代商業工作流程中，您常常需要 **convert presentation to pdf** 同時保留原始的外觀與感受。無論是分享客戶簡報、歸檔培訓資料，或是自動化報告產生，缺少字型都會破壞視覺品質。本教學將向您展示如何在 Java pptx 轉 pdf 的過程中使用 **GroupDocs.Conversion for Java** 完整保留字型。

## 快速解答
- **What is the primary benefit of custom font substitution?** 它保證 PDF 的外觀與來源簡報完全相同，即使目標機器未安裝原始字型。  
- **Which library handles the conversion?** `GroupDocs.Conversion` for Java.  
- **Do I need a license?** 免費試用可用於開發；商業授權則需於正式環境使用。  
- **Can I use this in a Maven project?** 可以 – 只需在下面加入儲存庫與相依性。  
- **Is the process thread‑safe?** `Converter` 實例輕量；您可以為每個轉換執行緒建立一個實例。

## 什麼是 **convert presentation to pdf**？
此詞語僅描述將 PowerPoint (.pptx) 檔案轉換為 PDF 文件的動作。轉換為 PDF 可讓檔案在任何平台上皆可檢視、列印，且更易於保存，同時保留版面配置、影像與文字。

## 為什麼使用 **custom font substitution**？
- **Brand consistency:** 確保企業字型即使在未安裝該字型的機器上也能正確顯示。  
- **Cross‑platform reliability:** PDF 在 Windows、macOS、Linux 以及行動裝置上皆呈現相同。  
- **Reduced support tickets:** 不再出現「我的 PDF 因字型缺失而顯示異常」的問題。  

## 前置條件
1. **Java Development Kit (JDK)** – 版本 8 或以上。  
2. **Maven** – 用於相依性管理。  
3. **IDE** – IntelliJ IDEA、Eclipse 或任何相容 Java 的編輯器。  
4. **Basic Java knowledge** – 您應熟悉類別與方法的使用。  

## 設定 GroupDocs.Conversion for Java
將 GroupDocs.Conversion 函式庫整合至您的 Maven 專案。以下 XML 片段會加入官方儲存庫與所需的相依性。

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
- **Free Trial:** 從 GroupDocs 官方網站下載試用版。  
- **Temporary License:** 申請臨時金鑰以延長測試時間。  
- **Purchase:** 滿意後升級為正式授權。  

Maven 解析完相依性後，即可開始編寫轉換邏輯。

## 實作指南

### 步驟 1：定義含字型替換的 Presentation Load Options
以下方法會建立 `PresentationLoadOptions` 物件，並告訴 GroupDocs 如何取代缺少的字型。這是 **how to preserve fonts** 在轉換過程中的核心。

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

**Explanation**  
- **Font Substitution:** 將 “Tahoma” 與 “Times New Roman” 映射至 “Arial”。  
- **Default Font:** 若無匹配的映射，提供備用字型 (`Helvetica.ttf`)。  

### 步驟 2：使用進階選項將簡報文件轉換為 PDF
現在我們使用步驟 1 的載入選項，實際執行 **convert presentation to pdf** 操作。

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

**Explanation**  
- **Converter Initialization:** 傳入 PPTX 路徑以及自訂的 `loadOptions`。  
- **PDF Conversion Options:** 如有需要，可進一步調整設定（例如影像品質）。  

## 實務應用
1. **Business Presentations:** 與外部合作夥伴分享 PDF 時，保持企業品牌一致性。  
2. **Educational Materials:** 將講義簡報轉為 PDF，供離線學習且不必擔心字型缺失。  
3. **Legal Documents:** 保留證據投影片的精確版面，以供法院提交。  

## 效能考量
- **Memory Management:** 為大型簡報分配足夠的堆積空間（`-Xmx2g` 為不錯的起始值）。  
- **Limit Font Substitutions:** 僅映射實際需要的字型；過多映射會降低處理速度。  
- **Garbage Collection:** 若發現記憶體激增，於大量批次轉換後呼叫 `System.gc()`。  

## 常見問題與解決方案

| Issue | Solution |
|-------|----------|
| **Missing default font file** | 確認 `setDefaultFont` 中的路徑指向有效的 `.ttf` 檔案且該檔案可讀取。 |
| **Conversion hangs on large PPTX** | 增加 JVM 堆積大小，並考慮分批轉換投影片。 |
| **Font not substituted as expected** | 確保來源字型名稱與 `FontSubstitute.create` 中使用的名稱完全相符（區分大小寫）。 |
| **Output PDF is blank** | 確認來源 PPTX 未損毀，且 `Converter` 指向正確的檔案路徑。 |

## 常見問答

**Q: What is the primary benefit of using custom font substitutions in conversions?**  
A: 自訂字型替換可確保 PDF 保持預期的外觀，即使目標系統上沒有原始字型。

**Q: How can I handle unsupported fonts during conversion?**  
A: 使用 `FontSubstitute` 功能將不支援的字型映射至替代字型，確保文件美觀一致。

**Q: Can I use GroupDocs.Conversion with cloud storage solutions?**  
A: 可以，GroupDocs 提供整合，可直接從 AWS S3、Azure Blob Storage 等雲端儲存平台進行轉換。

**Q: What should I do if my conversion process is slow?**  
A: 優化系統資源、限制字型替換映射，並增加 JVM 堆積大小以提升效能。

**Q: Is this tutorial part of a larger **document conversion tutorial java** series?**  
A: 當然——本指南聚焦於自訂字型，系列亦涵蓋使用 GroupDocs.Conversion for Java 的影像擷取、加浮水印與批次處理等內容。

## 結論
您現在擁有一套完整、可投入生產環境的 **convert presentation to pdf** 解決方案，能在使用 **GroupDocs.Conversion for Java** 時保留字型。透過定義含字型替換的載入選項並運用強大的 `Converter` API，即可確保在任何平台上皆能維持視覺一致性。

**Next Steps**  
- 嘗試其他 `PdfConvertOptions`（例如設定 PDF/A 相容性）。  
- 將轉換邏輯整合至 REST 服務，以提供即時 PDF 產生。  
- 探索其他 GroupDocs 模組，如 `GroupDocs.Annotation`，以在產生的 PDF 中加入註解。

---

**最後更新：** 2026-01-28  
**測試環境：** GroupDocs.Conversion 25.2 for Java  
**作者：** GroupDocs