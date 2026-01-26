---
date: '2026-01-26'
description: 了解如何使用 GroupDocs Conversion Java（領先的 Java 圖像轉換庫）將 CAD 檔案轉換為自訂尺寸的 TIFF。逐步指南。
keywords:
- CAD Conversion
- TIFF Image
- Custom Dimensions
- GroupDocs.Conversion Java
title: 使用 GroupDocs Conversion Java 將 CAD 轉換為 TIFF（自訂尺寸）：完整指南
type: docs
url: /zh-hant/java/cad-formats/cad-conversion-tiff-custom-dimensions-groupdocs-java/
weight: 1
---

# 使用可能相為應用程式量身訂做特定尺寸時。透過 **groupdocs conversion java**，此流程變得順暢且高效。無論是建築設計還是工程藍圖，將這些文件以精確的寬度與高度轉為 TIFF 格式都是非常有價值的。

## 快速解答
- **應該使用哪個 Java 圖像轉換函式庫？** GroupDocs Conversion Java，一個強大的 java 圖像轉換函式庫。  
- **如何為 CAD 檔案設定自訂尺寸？** 使用 `CadLoadOptions` 並指定 `setWidth()` 與 `setHeight()`。  
- **可以一步完成 DWG 轉 TIFF 嗎？** 可以——先載入 CAD、設定尺寸，然後使用 `ImageConvertOptions` ** 免費試用可供評估；完整授權則解鎖全部功能。  
的輸出尺寸控制完成。

## 為什的向量資訊。  
- **版面一致：** 指定寬度與高度可確保圖像完美嵌入報告、入口網站或列印版面。  
- **跨平台相容性：** TIFF 檔案在各作業系統與設計工具中皆得到廣泛支援。  

## 前置條件
在開始之前，請確保您已具備：

1. **GroupDocs Conversion Java** 版本 25.2 或更新（建議使用最新版本）。  
2. 如 IntelliJ IDEA 或 Eclipse 等 Java IDE。  
3. 已安裝 Maven 以管理相依性。  
4. 基本的 Java 程式設計知識，並熟悉 Maven 的 `pom.xml`。  

## 設定 GroupDocs Conversion Java

首先，於 `pom.xml` 中加入必要的 GroupDocs 函式庫，以讓 Maven 下載相依性：

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

**取得授權：** 您可以取得免費試用、申請臨時授權以獲得完整功能，或購買永久授權以完整解鎖 GroupDocs Conversion 的所有功能。

只要您的 Java 專案正確連結上述相依性，即可開始轉換 CAD 檔案！

## 步驟說明

### 載入具自訂尺寸的 CAD 文件（如何設定尺寸）

**概述：** 本步驟說明在 *如何轉換 CAD* 時，如何指定精確的寬度與高度。

#### 步驟 1：匯入必要的程式庫
```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.filetypes.ImageFileType;
import com.groupdocs.conversion.options.convert.ImageConvertOptions;
import com.groupdocs.conversion.options.load.CadLoadOptions;
```

#### 步驟 2：使用自訂尺寸設定載入選項
```java
String sourceDocumentPath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DWG_WITH_LAYOUTS_AND_LAYERS";
CadLoadOptions loadOptions = new CadLoadOptions();
loadOptions.setWidth(1920); // Specify the desired width in pixels
loadOptions.setHeight(1080); // Specify the desired height in pixels
Converter converter = new Converter(sourceDocumentPath, () -> loadOptions);
```
*說明：* 透過設定 `CadLoadOptions`，您告訴 **groupdocs conversion java** 在進一步處理前，先以 1920 × 1080 像素光柵化 CAD 繪圖。

### 將 CAD 轉為 TIFF 圖像（Convert CAD to TIFF）

**概述：** 在以自訂尺寸載入 CAD 檔案後，即可直接轉換為 TIFF 圖像。

#### 步驟 3：設定轉換選項
```java
String convertedFilePath = "YOUR_OUTPUT_DIRECTORY/ConvertCadAndSpecifyWidthAndHeight.tiff";
ImageConvertOptions options = new ImageConvertOptions();
options.setFormat(ImageFileType.Tiff); // Set the conversion target to TIFF format
```

#### 步驟 4：執行轉換
```java
converter.convert(convertedFilePath, options);
```
*說明：* 設定 `ImageFileType.Tiff` 會指示 **groupdocs conversion java** 輸出符合先前定義寬度與高度的高品質 TIFF 檔案。

## 疑難排解與常見問題
- **檔案路徑問題：** 確認來源與目的路徑正確，且應用程式具備讀寫權限。  
- **不支援的格式：** 確認 CAD 檔案為支援的格式（DWG、DGN、DXF 等）。  
- **記憶體限制：** 大型圖紙可能需要提升 JVM 堆積大小（`-Xmx2g` 或更高）。  
- **品質疑慮：** 若預設 DPI 無法滿足需求，可調整 `ImageConvertOptions` 的解析度設定。  

## 實務應用
1. **建築視覺化：** 將平面圖匯出為 TIFF，以供高解析度簡報使用。  
2. **工程文件化：** 產生標準化圖像，納入技術手冊。  
3. **自動化報告：** 於 CI 流程中將 CAD 產生的 TIFF 嵌入 PDF 或 HTML 報告。  

## 效能考量
- **最佳化記憶體使用：** 轉換完成後釋放 `Converter` 實例（如適用，呼叫 `converter.close()`）。  
- **批次處理：** 迭代處理多個 CAD 檔案時，可重複使用單一 `Converter` 設定以減少開銷。  
- **保持更新：** 定期升級至最新的 GroupDocs Conversion Java 版本，以獲得效能提升與錯誤修正。  

## 結論
透過本指南，您已學會使用 **groupdocs conversion java** 以自訂尺寸將 **CAD** 檔案轉換為 TIFF。此功能可簡化需要精確圖像尺寸的工作流程，無論是簡報、文件或自動化管線皆適用。

**後續步驟：** 探索 PDF、PNG、SVG 等其他轉換選項，並將轉換邏輯整合至現有的 Java 服務，以實現端對端自動化。

## 常見問答

**Q:** GroupDocs Conversion 支援哪些檔案格式？  
**A:** 支援超過 100 種格式，包含 DWG、DGN、DXF 等 CAD 檔案，以及常見的圖像、文件與壓縮檔類型。

**Q:** 能一次轉換多個 CAD 檔案嗎？  
**A:** 可以——實作簡單迴圈為每個檔案建立新的 `Converter`，或使用相同實例搭配不同來源路徑。

**Q:** 如何處理大型檔案的轉換？  
**A:** 增加 JVM 堆積大小、分批處理檔案，或使用函式庫提供的串流選項。

**Q:** 若輸出圖像品質不理想該怎麼辦？  
**A:** 調整 `ImageConvertOptions` 中的 DPI 或縮放設定，以提升解析度。

**Q:** 若遇到問題，是否有支援服務？  
**A:** GroupDocs 提供完整文件、社群論壇，並為授權客戶提供直接支援。

## 資源
- [GroupDocs 文件](https://docs.groupdocs.com/conversion/java/)
- [API 參考文件](https://reference.groupdocs.com/conversion/java/)
- [下載最新版本](https://releases.groupdocs.com/conversion/java/)
- [購買授權](https://purchase.groupdocs.com/buy)
- [免費試用入口](https://releases.groupdocs.com/conversion/java/)
- [臨時授權申請](https://purchase.groupdocs.com/temporary-license/)
- [支援論壇](https://forum.groupdocs.com/c/conversion/10)

---

**最後更新：** 2026-01-26  
**測試環境：** GroupDocs Conversion Java 25.2  
**作者：** GroupDocs  

---