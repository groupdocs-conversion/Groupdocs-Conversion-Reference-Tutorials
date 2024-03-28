---
title: 將 PSD 轉換為 PDF
linktitle: 將 PSD 轉換為 PDF
second_title: GroupDocs.Conversion .NET API
description: 了解如何使用 GroupDocs.Conversion for .NET 將 PSD 檔案輕鬆轉換為 PDF。請遵循我們的逐步指南。
type: docs
weight: 10
url: /zh-hant/net/file-format-conversion-tutorials/convert-psd-to-pdf/
---
## 介紹
在本教學中，我們將引導您完成使用 .NET 的 GroupDocs.Conversion 函式庫將 PSD（Photoshop 文件）檔案轉換為 PDF 格式的流程。透過遵循這些逐步說明，您將能夠輕鬆地將 PSD 檔案無縫轉換為 PDF。
## 先決條件
在開始之前，請確保您已設定以下先決條件：
1. 安裝 GroupDocs.Conversion 程式庫：確保您已安裝適用於 .NET 的 GroupDocs.Conversion 程式庫。您可以從[網站](https://releases.groupdocs.com/conversion/net/).
2. 存取 PSD 檔案：可以存取要轉換為 PDF 的 PSD 檔案。

## 導入命名空間
在深入轉換過程之前，先導入必要的命名空間：
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## 第 1 步：定義輸出資料夾和文件
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "psd-converted-to.pdf");
```
在此步驟中，指定要儲存轉換後的 PDF 檔案的輸出資料夾。確保更換`"Your Document Directory"`與實際的目錄路徑。
## 第 2 步：載入來源 PSD 文件
```csharp
using (var converter = new GroupDocs.Conversion.Converter("Path_to_your_PSD_file.psd"))
{
    var options = new PdfConvertOptions();
    //儲存轉換後的 PDF 文件
    converter.Convert(outputFile, options);
}
```
在這裡，您將初始化`Converter`物件與 PSD 檔案的路徑。代替`"Path_to_your_PSD_file.psd"`與 PSD 檔案的實際路徑。然後，建立一個實例`PdfConvertOptions`指定轉換設定。最後，致電`Convert`方法將 PSD 檔案轉換為 PDF 並將其儲存到指定的輸出檔案。
## 第 3 步：檢查轉換完成情況
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```
此步驟只是向控制台列印一則訊息，確認轉換過程已成功完成，並指示轉換後的 PDF 檔案的儲存位置。

## 結論
在本教學中，我們示範如何使用 .NET 的 GroupDocs.Conversion 函式庫將 PSD 檔案轉換為 PDF 格式。透過按照提供的步驟操作，您可以輕鬆地將 PSD 檔案轉換為 PDF，從而更輕鬆地共用和檢視文件。
## 常見問題解答

### 我可以使用 GroupDocs.Conversion 一次轉換多個 PSD 檔案嗎？
是的，您可以使用 GroupDocs.Conversion 將多個 PSD 檔案批次轉換為 PDF 或其他格式。

### GroupDocs.Conversion 是否支援 PDF 以外的其他輸出格式？
是的，GroupDocs.Conversion 支援多種輸出格式，包括 DOCX、XLSX、PPTX、JPEG、PNG 等。

### GroupDocs.Conversion 是否與不同版本的 .NET 相容？
是的，GroupDocs.Conversion 與各種版本的 .NET 相容，包括 .NET Core 和 .NET Framework。

### 我可以自訂轉換選項以更好地控制輸出嗎？
是的，GroupDocs.Conversion 提供了廣泛的自訂選項，例如指定頁面大小、方向、品質等。

### 購買前是否有試用版可供測試？
是的，您可以從 GroupDocs.Conversion 取得免費試用版[網站](https://releases.groupdocs.com/conversion/net/)在購買之前測試其功能。