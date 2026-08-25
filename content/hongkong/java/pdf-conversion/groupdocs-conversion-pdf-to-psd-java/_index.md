---
date: '2026-02-10'
description: 了解如何在 Java 中使用 GroupDocs.Conversion 將 pdf 轉換為 psd。逐步指南涵蓋 Maven 設定、授權啟用，以及將第一頁
  PDF 轉換為 PSD 圖像。
keywords:
- convert pdf to psd
- how to convert pdf
- pdf to photoshop psd
lastmod: '2026-08-25'
og_description: 在 Java 中使用 GroupDocs.Conversion 將 pdf 轉換為 psd。請依照本教學設定 Maven、配置轉換選項，並產生高保真度的
  PSD 檔案。
og_image_alt: Guide showing Java code converting a PDF page to a Photoshop PSD file
og_title: 使用 GroupDocs.Conversion for Java 將 pdf 轉換為 psd
schemas:
- author: GroupDocs
  dateModified: '2026-02-10'
  description: Learn how to convert pdf to psd in Java with GroupDocs.Conversion.
    Step‑by‑step guide covers Maven setup, license activation, and converting the
    first PDF page to a PSD image.
  headline: Convert pdf to psd using GroupDocs.Conversion for Java
  type: TechArticle
- description: Learn how to convert pdf to psd in Java with GroupDocs.Conversion.
    Step‑by‑step guide covers Maven setup, license activation, and converting the
    first PDF page to a PSD image.
  name: Convert pdf to psd using GroupDocs.Conversion for Java
  steps:
  - name: define file paths
    text: Specify the source PDF location and the destination folder for the PSD file.
  - name: configure image conversion options
    text: '`ImageConvertOptions` controls the target format and page range. Setting
      `setFormat(ImageFileType.Psd)` tells GroupDocs to output a Photoshop PSD, while
      `setPagesCount(1)` limits the conversion to the first page.'
  - name: perform the conversion
    text: '`Converter` is the core class that performs document conversions. Initialize
      the `Converter` with the source PDF, then invoke `convert` using the configured
      options and a `FileOutputStream` to write the PSD file.'
  type: HowTo
- questions:
  - answer: Increase `setPagesCount` to the total number of pages and iterate over
      page indexes, updating the output filename for each iteration.
    question: How do I convert multiple pages of a PDF into separate PSD files?
  - answer: Yes – manually add the downloaded JAR to your project’s classpath.
    question: Can I use GroupDocs.Conversion in non‑Maven projects?
  - answer: Confirm that the source document is compatible with the target format
      and consult the API reference for any format‑specific limitations.
    question: What happens if a conversion fails due to an unsupported format?
  - answer: A trial version is available, but a temporary or full license is recommended
      for production environments.
    question: Is GroupDocs.Conversion free to use?
  - answer: Visit the [API Reference](https://reference.groupdocs.com/conversion/java/)
      and the official [Documentation](https://docs.groupdocs.com/conversion/java/).
      For additional guidance, see the [GroupDocs API Reference](https://reference.groupdocs.com/conversion/java/)
      and the [GroupDocs Conversion Documentation](https://docs.groupdocs.com/conversion/java/).
    question: Where can I find more information about conversion options?
  type: FAQPage
tags:
- convert pdf
- GroupDocs.Conversion
- Java document processing
- PSD conversion
title: 使用 GroupDocs.Conversion for Java 將 pdf 轉換為 psd
type: docs
url: /zh-hant/java/pdf-conversion/groupdocs-conversion-pdf-to-psd-java/
weight: 1
---

# 使用 GroupDocs.Conversion for Java 將 pdf 轉換為 psd

在本教學中，您將學習如何在 Java 應用程式中使用 GroupDocs.Conversion **將 pdf 轉換為 psd**。無論您是需要 PDF 的第一頁用於 Photoshop 設計工作流程、想批次處理多個 PDF，或只是想在現有流程中加入 PSD 匯出，下列步驟將從 Maven 依賴設定到完整的轉換程式碼逐步說明。

## 快速答案
- **GroupDocs 能否僅將 PDF 的第一頁轉換為 PSD？** 是 – 在 `ImageConvertOptions` 中將 `pagesCount` 設為 1。  
- **我需要 Maven 的 GroupDocs 依賴嗎？** 建議的做法是加入 GroupDocs Maven repository 及相應的依賴。  
- **需要哪個 Java 版本？** JDK 8 或更高版本。  
- **在生產環境中需要授權嗎？** 試用版可用於測試；正式使用完整功能需永久或臨時授權。  
- **我可以在非 Maven 專案中執行嗎？** 可以 – 從 GroupDocs 官方網站下載 JAR 並加入 classpath。

## 什麼是「將 pdf 轉換為 psd」？
`convert pdf to psd` 指的是將 PDF 頁面的視覺內容提取出來，並儲存為 Photoshop 原生的分層 PSD 格式。這讓設計師能直接在 Photoshop 中開啟檔案，保留圖層、向量形狀與影像品質，從而在不必重新製作的情況下編輯圖形。

## 為何使用 GroupDocs.Conversion 將 PDF 轉換為 PSD？
GroupDocs.Conversion 提供高保真度的轉換，保留向量資料、字型與影像品質，將 PDF 頁面轉換為 PSD 檔案時不會遺失細節。它支援超過 50 種輸入與輸出格式，能在不將整份文件載入記憶體的情況下處理大型多頁 PDF，並提供簡易的 API 呼叫，讓您能針對單一頁面或批次處理多個檔案。

## 先決條件
- 已安裝 Java Development Kit (JDK) 8 以上。  
- IDE，例如 IntelliJ IDEA、Eclipse 或 NetBeans。  
- 具備 Java 與 Maven 的基本知識。  

### 所需函式庫與相依性
將 GroupDocs Maven repository 與相依性加入您的 `pom.xml`，如下所示：

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

您可以在 [GroupDocs website](https://releases.groupdocs.com/conversion/java/) 上找到 Maven repository 及最新版本資訊。若未使用 Maven，請從 GroupDocs 官方網站下載 JAR，並加入專案的建置路徑。

### 授權取得步驟
- **Free trial:** 免費試用：在未取得授權的情況下測試基本功能。  
- **Temporary license:** 臨時授權：取得臨時授權以在開發期間完整使用。  
- **Purchase:** 購買：在生產環境中，從 GroupDocs 購買頁面購買授權。

可從 [GroupDocs Temporary License](https://purchase.groupdocs.com/temporary-license/) 頁面取得臨時授權，或透過 [GroupDocs Purchase](https://purchase.groupdocs.com/buy) 頁面購買完整授權。

## 如何使用 GroupDocs.Conversion 將 pdf 轉換為 psd
載入來源 PDF，設定轉換選項，並寫入 PSD 輸出——全部只需三個簡單步驟。

### 直接答案
建立 `Converter` 以處理 PDF，將 `ImageConvertOptions` 設為 PSD 且 `pagesCount = 1`，然後在寫入 `FileOutputStream` 時呼叫 `convert`。此流程可在一般 300 dpi 文件下於一秒內完成第一頁的 PDF 轉 PSD。

### 步驟 1：定義檔案路徑
指定來源 PDF 的位置以及 PSD 檔案的目標資料夾。

```java
String sourceFilePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_PDF"; // Replace with your PDF path
String outputFolder = "YOUR_OUTPUT_DIRECTORY"; // Destination folder for the PSD file
```

### 步驟 2：設定影像轉換選項
`ImageConvertOptions` 控制目標格式與頁面範圍。設定 `setFormat(ImageFileType.Psd)` 告訴 GroupDocs 輸出 Photoshop PSD，而 `setPagesCount(1)` 則限制僅轉換第一頁。

```java
import com.groupdocs.conversion.options.convert.ImageConvertOptions;
import com.groupdocs.conversion.filetypes.ImageFileType;

ImageConvertOptions options = new ImageConvertOptions();
options.setFormat(ImageFileType.Psd); // Set format to PSD
options.setPagesCount(1); // Convert only the first page
```

### 步驟 3：執行轉換
`Converter` 是執行文件轉換的核心類別。以來源 PDF 初始化 `Converter`，然後使用已設定的選項與 `FileOutputStream` 呼叫 `convert`，將 PSD 檔寫出。

```java
import com.groupdocs.conversion.Converter;
import java.io.FileOutputStream;

String outputFileTemplate = String.format("%s/converted-page-%d.psd", outputFolder, 1);

try (FileOutputStream getPageStream = new FileOutputStream(outputFileTemplate)) {
    Converter converter = new Converter(sourceFilePath); // Initialize with the source PDF
    converter.convert(() -> getPageStream, options); // Convert and save to PSD
} catch (IOException e) {
    System.out.println(e.getMessage());
}
```

## 常見陷阱與故障排除
- **缺少相依性：** 確認 Maven 能正確解析 GroupDocs 套件且無錯誤。  
- **檔案路徑不正確：** 再次確認來源與輸出路徑；相對路徑常導致 `FileNotFoundException`。  
- **轉換失敗：** 確保 PDF 未受密碼保護或損壞後再執行轉換。

## 實務應用
1. **Graphic design workflows:** 圖形設計工作流程：提取 PDF 封面頁並直接在 Photoshop 中編輯。  
2. **Automated report generation:** 自動化報告產生：將 PDF 報告轉換為可編輯的 PSD，以便進行品牌調整。  
3. **Content management systems:** 內容管理系統：使用者上傳 PDF 時自動產生 PSD 預覽。  

## 效能建議
- **記憶體管理：** 使用 try‑with‑resources 及時關閉串流，如程式碼所示。  
- **批次處理：** 重複使用單一 `Converter` 實例，並在大型文件上迭代頁碼。  
- **硬體資源：** 處理高解析度 PDF 時分配足夠的堆積空間（例如 `-Xmx2g`），以避免 `OutOfMemoryError`。

## 常見問題

**問：如何將 PDF 的多個頁面轉換為個別的 PSD 檔案？**  
答：將 `setPagesCount` 設為總頁數，並遍歷頁索引，在每次迭代時更新輸出檔名。

**問：我可以在非 Maven 專案中使用 GroupDocs.Conversion 嗎？**  
答：可以 – 手動將下載的 JAR 加入專案的 classpath。

**問：如果因為不支援的格式導致轉換失敗，會發生什麼情況？**  
答：確認來源文件與目標格式相容，並參考 API 說明文件了解任何特定格式的限制。

**問：GroupDocs.Conversion 可以免費使用嗎？**  
答：提供試用版，但建議在生產環境中使用臨時或完整授權。

**問：在哪裡可以找到有關轉換選項的更多資訊？**  
答：請造訪 [API Reference](https://reference.groupdocs.com/conversion/java/) 與官方 [Documentation](https://docs.groupdocs.com/conversion/java/)。另可參考 [GroupDocs API Reference](https://reference.groupdocs.com/conversion/java/) 以及 [GroupDocs Conversion Documentation](https://docs.groupdocs.com/conversion/java/)。

---

**最後更新：** 2026-08-25  
**測試環境：** GroupDocs.Conversion 25.2 for Java  
**作者：** GroupDocs

## 相關教學

- [如何設定 GroupDocs 授權（Java） – 步驟指南](/conversion/java/getting-started/groupdocs-conversion-java-license-setup-file-path/)
- [如何使用 GroupDocs.Conversion for Java 轉換 PDF 指定頁面](/conversion/java/pdf-conversion/convert-specific-pages-pdf-groupdocs-java/)
- [PDF 轉 Word（Java）：使用 GroupDocs 轉換 PDF 為 Word 的完整指南](/conversion/java/pdf-conversion/java-pdf-to-word-groupdocs-conversion/)