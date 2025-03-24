---
title: 將 SVG 轉換為 PDF
linktitle: 將 SVG 轉換為 PDF
second_title: GroupDocs.Conversion .NET API
description: 了解如何使用 GroupDocs.Conversion for .NET 輕鬆將 SVG 轉換為 PDF。簡化您的文件管理流程。
weight: 15
url: /zh-hant/net/file-format-conversion-convert-svg-to-pdf/
---

# 將 SVG 轉換為 PDF

## 介紹
在程式設計領域，將檔案從一種格式轉換為另一種格式是一項常見任務。無論您要處理圖像、文件還是其他媒體，能夠在格式之間無縫轉換都至關重要。在本教學中，我們將深入研究如何使用 GroupDocs.Conversion for .NET 將 SVG（可縮放向量圖）檔案轉換為 PDF（可攜式文件格式）。
## 先決條件
在深入轉換過程之前，請確保您已設定以下先決條件：
### 1. 安裝 .NET 的 GroupDocs.Conversion
確保您的開發環境中安裝了 GroupDocs.Conversion for .NET。如果您還沒有下載，您可以從[網站](https://releases.groupdocs.com/conversion/net/).
### 2. 取得範例 SVG 文件
您需要一個範例 SVG 檔案才能轉換為 PDF。如果您沒有 SVG 文件，您可以輕鬆地在線上找到 SVG 文件或使用各種圖形設計工具建立一個。
### 3.C#的基本理解
熟悉 C# 程式語言基礎知識，因為我們將使用它來編寫轉換程式碼。

## 導入命名空間
首先，讓我們導入必要的名稱空間：
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## 第 1 步：定義輸出資料夾和文件
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "svg-converted-to.pdf");
```
確保更換`"Your Document Directory"`以及所需輸出目錄的路徑。
## 第 2 步：載入來源 SVG 文件
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_SVG))
{
    //轉換程式碼放在這裡
}
```
代替`Constants.SAMPLE_SVG`以及 SVG 檔案的路徑。
## 第 3 步：設定轉換選項
```csharp
var options = new PdfConvertOptions();
```
在這裡，我們專門為 PDF 輸出設定轉換選項。您可以根據您的要求自訂這些選項。
## 第 4 步：執行轉換
```csharp
converter.Convert(outputFile, options);
```
此行執行轉換過程，取得來源 SVG 檔案並使用指定選項將其轉換為 PDF。
## 第 5 步：檢查轉換完成狀況
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
此行輸出一則訊息，確認轉換過程成功完成，以及轉換後的 PDF 檔案所在的目錄。

## 結論
在本教學中，我們學習如何使用 GroupDocs.Conversion for .NET 將 SVG 檔案轉換為 PDF。透過遵循逐步指南並確保滿足先決條件，您可以將檔案格式轉換功能無縫合併到您的 .NET 應用程式中。
## 常見問題解答
### GroupDocs.Conversion for .NET 是否與所有 .NET 框架相容？
是的，GroupDocs.Conversion for .NET 支援多個 .NET 框架，包括 .NET Core 和 .NET Framework。
### 我可以自訂特定輸出格式的轉換選項嗎？
絕對地！ GroupDocs.Conversion for .NET 為每個支援的輸出格式提供了廣泛的自訂選項。
### GroupDocs.Conversion for .NET 支援批次轉換嗎？
是的，您可以使用 GroupDocs.Conversion for .NET 同時轉換多個檔案。
### 是否有可用於測試目的的試用版？
是的，您可以存取免費試用版[這裡](https://releases.groupdocs.com/).
### 在哪裡可以獲得 GroupDocs.Conversion for .NET 的技術支援？
您可以在 GroupDocs 論壇上找到技術支援和協助[這裡](https://forum.groupdocs.com/c/conversion/11).