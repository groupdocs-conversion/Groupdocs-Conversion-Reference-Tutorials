---
date: '2025-12-17'
description: 學習如何使用 GroupDocs.Conversion Java 將 DWG 轉換為 TIFF，設定自訂尺寸，並在此一步一步的指南中優化效能。
keywords:
- CAD Conversion
- TIFF Image
- Custom Dimensions
- GroupDocs.Conversion Java
title: 使用 GroupDocs.Conversion Java 指南將 dwg 轉換為 tiff
type: docs
url: /zh-hant/java/cad-formats/cad-conversion-tiff-custom-dimensions-groupdocs-java/
weight: 1
---

# 使用 GroupDocs.Conversion Java 轉換 dwg 為 tiff

將 **dwg** 檔案轉換為 **tiff** 格式是建築師、工程師以及需要與沒有 CAD 軟體的利害關係人分享高解析度圖紙的任何人的常見需求。在本指南中，我們將示範如何使用 **GroupDocs.Conversion Java** **轉換 dwg 為 tiff**，並套用自訂尺寸，使輸出符合您的精確顯示或列印需求。

## 快速解答
- **什麼函式庫負責轉換？** GroupDocs.Conversion for Java  
- **我可以設定寬度和高度嗎？** 是 – 使用 `CadLoadOptions` 來指定自訂尺寸。  
- **使用哪種輸出格式？** TIFF (`ImageFileType.Tiff`).  
- **需要授權嗎？** 需要試用版或正式授權才能在生產環境使用。  
- **支援哪個 Java 版本？** Java 8+ 搭配 Maven 進行相依管理。  

## 介紹

將 CAD 檔案轉換為高品質 TIFF 圖像可能具有挑戰性，尤其是當您需要為應用程式量身訂做特定尺寸時。使用 **GroupDocs.Conversion for Java**，此過程變得無縫且高效。無論是建築設計或工程藍圖，將這些文件轉換為具精確尺寸的 TIFF 格式都是非常有價值的。

在本教學中，我們將一步一步指導您載入 CAD 檔案、設定自訂尺寸，並使用 **GroupDocs.Conversion Java** 轉換為高品質 TIFF 圖像。閱讀完本文後，您將能如專業人士般處理 CAD 轉換任務！

**您將學會**
- 設定 **GroupDocs.Conversion Java**
- 載入具指定尺寸的 CAD 文件
- 將 CAD 檔案轉換為 TIFF 格式
- 最佳化效能與排除常見問題

## 「convert dwg to tiff」是什麼？為何重要？

「convert dwg to tiff」這個詞語描述了將 DWG（AutoCAD）圖紙轉換為 TIFF 點陣圖的工作流程。TIFF 被出版工具、GIS 平台與文件管理系統廣泛支援，當沒有向量式 CAD 工具時，這是分享、列印或保存的理想格式。

## 為何在此任務中使用 GroupDocs.Conversion Java？

- **Zero‑install**：純 Java 函式庫，無需外部原生相依性。  
- **Custom dimensions**：在轉換前輕鬆定義寬度/高度。  
- **High fidelity**：保留線條粗細、圖層與版面細節。  
- **Enterprise‑ready**：具可擴充性、執行緒安全，且有授權可用於生產環境。  

## 前置條件

在開始之前，請確保您已具備：  
1. **必備函式庫**：GroupDocs.Conversion for Java 版本 25.2 或更新版本。  
2. **環境設定**：  
   - 可正常運作的 Java 開發環境（IntelliJ IDEA、Eclipse 等）。  
   - 已安裝 Maven 以管理相依性。  
3. **知識前提**：基本的 Java 程式設計與 Maven 使用經驗。  

## 設定 GroupDocs.Conversion Java

首先，透過在 `pom.xml` 檔案中加入以下內容，設定 Maven 以包含必要的 GroupDocs 函式庫：

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

**授權取得**：您可以取得免費試用版、申請臨時授權以獲得完整功能，或購買永久授權以完整解鎖 GroupDocs.Conversion 功能。

當您的 Java 專案正確連結這些相依性後，即可開始轉換 CAD 檔案！

## 實作指南

### 如何使用自訂尺寸將 dwg 轉換為 tiff

#### 步驟 1：匯入必要的函式庫
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
**說明**：我們設定 `CadLoadOptions` 以定義輸出尺寸，確保在載入 CAD 文件時符合這些指定的測量值。

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
**說明**：透過指定 `ImageFileType.Tiff`，您指示 GroupDocs.Conversion 輸出 TIFF 圖像。此程序利用這些設定產生最佳化的檔案。

### 疑難排解技巧
- **檔案路徑問題**：確保來源文件路徑正確且可存取。  
- **輸出格式錯誤**：再次檢查格式規格，以避免不支援的轉換。  
- **記憶體配置**：對於記憶體密集的檔案，增加 Java 堆積大小 (`-Xmx`) 或分批處理頁面。  

## 實務應用
1. **建築視覺化** – 將 DWG 圖紙轉換為 TIFF，以供高解析度的客戶簡報使用。  
2. **工程文件** – 使用精確尺寸的技術藍圖，顯示於大型螢幕或列印於繪圖機。  
3. **自動化報告產生** – 將轉換後的 TIFF 圖像嵌入後端服務產生的 PDF 或 HTML 報告中。  

## 效能考量
- **最佳化記憶體使用**：為大型圖紙調整 Java 堆積大小。  
- **資源管理**：轉換完成後關閉 `Converter` 實例，以釋放原生資源。  
- **保持更新**：定期升級至最新的 GroupDocs.Conversion 版本，以獲得效能提升與錯誤修正。  

## 結論

透過本指南，您已學會如何使用 **GroupDocs.Conversion Java** 以自訂尺寸 **轉換 dwg 為 tiff**。此功能透過提供量身訂製的高品質圖像輸出，順利整合至後續流程，提升工作流效率。

下一步：探索其他轉換選項（PDF、PNG、SVG）、批次處理多個 DWG 檔案，或將轉換邏輯嵌入 REST API，以提供即時文件服務。

## 常見問答
1. **GroupDocs.Conversion 支援哪些檔案格式？**  
   - 它支援多種格式，包括 DWG、DGN 等 CAD 檔案。  

2. **我可以一次轉換多個 CAD 檔案嗎？**  
   - 可以，透過迴圈批次轉換相當有效率。  

3. **在轉換過程中如何處理大型檔案？**  
   - 可分段處理或優化系統記憶體設定以改善處理。  

4. **如果輸出圖像品質不滿意該怎麼辦？**  
   - 在 `ImageConvertOptions` 中調整解析度設定以提升品質。  

5. **遇到問題時是否有支援？**  
   - 有，GroupDocs 提供論壇與文件以協助排除故障。  

## 資源
- [GroupDocs 文件說明](https://docs.groupdocs.com/conversion/java/)  
- [API 參考文件](https://reference.groupdocs.com/conversion/java/)  
- [下載最新版本](https://releases.groupdocs.com/conversion/java/)  
- [購買授權](https://purchase.groupdocs.com/buy)  
- [免費試用入口](https://releases.groupdocs.com/conversion/java/)  
- [申請臨時授權](https://purchase.groupdocs.com/temporary-license/)  
- [支援論壇](https://forum.groupdocs.com/c/conversion/10)  

---
**最後更新：** 2025-12-17  
**測試環境：** GroupDocs.Conversion Java 25.2  
**作者：** GroupDocs