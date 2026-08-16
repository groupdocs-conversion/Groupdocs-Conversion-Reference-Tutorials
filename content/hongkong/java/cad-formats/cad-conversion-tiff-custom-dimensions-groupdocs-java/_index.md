---
date: '2026-07-24'
description: 簡化 Java 圖像轉換：學習如何使用 GroupDocs Conversion Java 將 CAD 檔案轉換為具自訂尺寸的 TIFF。開發人員一步一步的指南。
keywords:
- java image conversion
- custom width height
- set image dimensions java
lastmod: '2026-07-24'
og_description: 簡化 Java 圖像轉換。使用 GroupDocs Conversion Java 將 CAD 檔案轉換為高品質的 TIFF 圖像，並可自訂寬度與高度。請參考我們的詳細指南。
og_image_alt: 'Guide: Convert CAD to TIFF with custom dimensions using GroupDocs Conversion
  Java'
og_title: Java 圖像轉換：將 CAD 轉為 TIFF（自訂尺寸）
schemas:
- author: GroupDocs
  dateModified: '2026-07-24'
  description: 'Java image conversion made easy: learn how to convert CAD files to
    TIFF with custom dimensions using GroupDocs Conversion Java. Step‑by‑step guide
    for developers.'
  headline: 'Java Image Conversion: CAD to TIFF with Custom Dimensions'
  type: TechArticle
- questions:
  - answer: GroupDocs Conversion Java, a robust Java image conversion library.
    question: What library should I use for Java image conversion?
  - answer: Use `CadLoadOptions` and specify `setWidth()` and `setHeight()`.
    question: How do I set custom dimensions for a CAD file?
  - answer: Yes—load the CAD, set dimensions, then convert with `ImageConvertOptions`.
    question: Can I convert DWG to TIFF in one step?
  - answer: A free trial works for evaluation; a full license unlocks all features.
    question: Do I need a license?
  - answer: Any Java 8+ runtime is supported.
    question: What Java version is required?
  type: FAQPage
tags:
- convert CAD
- GroupDocs Conversion
- Java image conversion
- TIFF
- CAD processing
title: Java 圖像轉換：將 CAD 轉為 TIFF（自訂尺寸）
type: docs
url: /zh-hant/java/cad-formats/cad-conversion-tiff-custom-dimensions-groupdocs-java/
weight: 1
---

# Java 圖像轉換：CAD 轉 TIFF（自訂尺寸）

如果您需要將 CAD 圖紙轉換為高解析度的 TIFF 圖像，同時控制精確的像素寬度和高度，**java image conversion** 是關鍵。使用 GroupDocs Conversion Java，您可以將任何支援的 CAD 格式（DWG、DGN、DXF 等）光柵化為符合報告、網上入口網站或列印版面的 TIFF 檔案。本指南將逐步說明從專案設定到最終轉換的每個步驟，讓您能將此流程整合到任何基於 Java 的工作流程中。

## 快速解答
- **應該使用哪個 Java 圖像轉換庫？** GroupDocs Conversion Java，是一個強大的 Java 圖像轉換庫。  
- **如何為 CAD 檔案設定自訂尺寸？** 使用 `CadLoadOptions` 並指定 `setWidth()` 和 `setHeight()`。  
- **我可以一步完成 DWG 轉 TIFF 嗎？** 可以 — 先載入 CAD，設定尺寸，然後使用 `ImageConvertOptions` 進行轉換。  
- **我需要授權嗎？** 免費試用可用於評估；完整授權可解鎖所有功能。  
- **需要哪個 Java 版本？** 支援任何 Java 8 以上的執行環境。

## 什麼是 GroupDocs Conversion Java？
`GroupDocs Conversion Java` 函式庫是一個 **java image conversion** 解決方案，支援超過 110 種輸入與輸出格式，包括所有主要的 CAD 與點陣圖類型。  
`Converter` 類別是啟動檔案轉換作業的核心元件。  
它提供伺服器端的渲染、縮放與特定格式選項，讓開發者無需安裝第三方檢視器即可轉換檔案。

## 為什麼要將 CAD 轉換為自訂尺寸的 TIFF？
設定明確的寬度與高度可確保產生的 TIFF 完全符合下游系統的版面限制。於光柵化前先定義像素尺寸，可避免下游縮放產生的瑕疵，保持線寬一致性，並確保圖像能無縫整合至 PDF、網頁或列印材料中，無需額外處理。此方法亦簡化了自動化流水線，讓每張圖像都符合預先定義的尺寸規格。  

- **保留視覺保真度：** 在 1920 × 1080 px（或您選擇的任何尺寸）進行光柵化，可保持線條與陰影的清晰度。  
- **確保版面一致性：** 圖像可乾淨地嵌入 PDF、HTML 頁面或列印範本，無需額外調整大小。  
- **提升相容性：** TIFF 在 Windows、macOS、Linux 以及大多數設計工具中皆被廣泛接受，減少格式轉換的困擾。  

## 前置條件
在開始之前，請確保您已具備以下條件：

1. **GroupDocs Conversion Java** 版本 25.2 或更新（建議使用最新版本）。  
2. 如 IntelliJ IDEA 或 Eclipse 等 Java IDE。  
3. 已安裝 Maven 用於相依管理。  
4. 基本的 Java 程式設計知識，並熟悉 Maven 的 `pom.xml`。  

## 設定 GroupDocs Conversion Java

將 GroupDocs Maven 相依加入您的 `pom.xml`：

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-conversion</artifactId>
    <version>25.2</version>
</dependency>
```

**授權取得：** 您可以取得免費試用、申請臨時授權以獲得完整功能，或購買永久授權以完整解鎖 GroupDocs Conversion 功能。

一旦您的 Java 專案正確連結這些相依，即可開始轉換 CAD 檔案！

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

## 如何將 CAD 轉換為自訂尺寸的 TIFF？

將 CAD 檔案轉換為具有精確尺寸的 TIFF 需要載入來源圖紙、設定渲染選項，並呼叫轉換 API。依照線性流程——設定寬度與高度、選擇 TIFF 為輸出格式，然後執行轉換——即可確保產生的圖像符合下游應用的精確尺寸需求，同時保留原始圖紙的細節與品質。  

1. **匯入所需類別**（請參考以下逐步說明）。  
2. **建立 `CadLoadOptions` 實例**，並將 `width` 與 `height` 設為目標尺寸。  
3. **實例化 `ImageConvertOptions`**，指定 `ImageFileType.Tiff`。  
4. **呼叫 `Converter` 物件的 `convert` 方法**，傳入來源路徑、載入選項與轉換選項。  

### 載入具自訂尺寸的 CAD 文件（如何設定尺寸）

`CadLoadOptions` 類別告訴 GroupDocs 在轉換前如何光柵化圖紙。  
`CadLoadOptions` 是用於定義 CAD 檔案渲染參數（如寬度、高度與 DPI）的設定物件。  

#### 步驟 1：匯入必要的函式庫
```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.filetypes.ImageFileType;
import com.groupdocs.conversion.options.convert.ImageConvertOptions;
import com.groupdocs.conversion.options.load.CadLoadOptions;
```

#### 步驟 2：設定具自訂尺寸的載入選項
```java
String sourceDocumentPath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DWG_WITH_LAYOUTS_AND_LAYERS";
CadLoadOptions loadOptions = new CadLoadOptions();
loadOptions.setWidth(1920); // Specify the desired width in pixels
loadOptions.setHeight(1080); // Specify the desired height in pixels
Converter converter = new Converter(sourceDocumentPath, () -> loadOptions);
```
*說明：* 透過設定 `CadLoadOptions`，您告訴 **GroupDocs Conversion Java** 在任何後續處理之前，以 1920 × 1080 像素光柵化 CAD 圖紙。

### 將 CAD 轉換為 TIFF 圖像（Convert CAD to TIFF）

`ImageConvertOptions` 指示函式庫產生符合您設定的 TIFF 檔案。  
`ImageConvertOptions` 包含所有影像相關的轉換參數，包括輸出格式、解析度與壓縮等級。  

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
*說明：* 設定 `ImageFileType.Tiff` 可指示 **GroupDocs Conversion Java** 輸出符合先前定義寬度與高度的高品質 TIFF 檔案。  

## 疑難排解技巧與常見陷阱
- **檔案路徑問題：** 確認來源與目的路徑正確，且應用程式具備讀寫權限。  
- **不支援的格式：** 確認 CAD 檔案屬於支援的格式（DWG、DGN、DXF 等）。  
- **記憶體限制：** 大型圖紙可能需要增加 JVM 堆積大小（例如 `-Xmx2g` 或更高）。  
- **品質問題：** 若預設 DPI 未達到品質標準，請調整 `ImageConvertOptions` 的解析度設定。  

## 實務應用
1. **建築可視化：** 將平面圖匯出為 TIFF，用於高解析度的簡報。  
2. **工程文件化：** 產生標準化圖像，以納入技術手冊。  
3. **自動化報告：** 透過 CI 流程將 CAD 產生的 TIFF 嵌入 PDF 或 HTML 報告中。  

## 效能考量
- **最佳化記憶體使用：** 轉換完成後釋放 `Converter` 實例（如適用，呼叫 `converter.close()`）。  
- **批次處理：** 迭代 CAD 檔案清單，重複使用單一 `Converter` 設定以降低開銷。  
- **保持更新：** 定期升級至最新的 GroupDocs Conversion Java 版本，以獲得效能提升與錯誤修正。  

## 常見問答

**Q:** GroupDocs Conversion 支援哪些檔案格式？  
**A:** 它支援超過 110 種格式，包括 DWG、DGN、DXF 等 CAD 檔案，以及常見的影像、文件與壓縮檔類型。  

**Q:** 我可以一次轉換多個 CAD 檔案嗎？  
**A:** 可以 — 實作簡單的迴圈，為每個檔案建立新的 `Converter`，或使用相同的實例搭配不同的來源路徑。  

**Q:** 在轉換過程中如何處理大型檔案？  
**A:** 增加 JVM 堆積大小、將檔案分成較小批次處理，或使用函式庫提供的串流選項。  

**Q:** 若輸出圖像品質不理想該怎麼辦？  
**A:** 調整 `ImageConvertOptions` 中的 DPI 或縮放設定，以提升解析度。  

**Q:** 若遇到問題是否有支援？  
**A:** GroupDocs 提供完整的文件、社群論壇，並為授權客戶提供直接支援。  

## 資源
- [GroupDocs 文件說明](https://docs.groupdocs.com/conversion/java/)
- [API 參考文件](https://reference.groupdocs.com/conversion/java/)
- [下載最新版本](https://releases.groupdocs.com/conversion/java/)
- [購買授權](https://purchase.groupdocs.com/buy)
- [免費試用入口](https://releases.groupdocs.com/conversion/java/)
- [臨時授權申請](https://purchase.groupdocs.com/temporary-license/)
- [支援論壇](https://forum.groupdocs.com/c/conversion/10)

---

**最後更新：** 2026-07-24  
**測試環境：** GroupDocs Conversion Java 25.2  
**作者：** GroupDocs  

---

## 相關教學

- [convert cad pdf java – CAD 格式轉換教學（適用於 GroupDocs.Conversion Java）](/conversion/java/cad-formats/)
- [使用 GroupDocs.Conversion 將 PDF 轉為 JPG（Java） – 指南](/conversion/java/document-operations/convert-pdf-to-jpg-groupdocs-java/)
- [如何為 GroupDocs.Conversion Java 設定授權 - 步驟指南](/conversion/java/getting-started/groupdocs-conversion-java-license-setup-file-path/)