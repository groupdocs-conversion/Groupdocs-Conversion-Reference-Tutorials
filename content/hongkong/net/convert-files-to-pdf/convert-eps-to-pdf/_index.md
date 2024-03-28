---
title: 將 EPS 封裝的 PostScript 檔案轉換為 PDF
linktitle: 將 EPS 封裝的 PostScript 檔案轉換為 PDF
second_title: GroupDocs.Conversion .NET API
description: 使用 GroupDocs.Conversion for .NET 輕鬆將 EPS 檔案轉換為 PDF。本教程提供了無縫轉換的逐步指南。
type: docs
weight: 17
url: /zh-hant/net/convert-files-to-pdf/convert-eps-to-pdf/
---
## 介紹
在本教學中，我們將示範如何使用 GroupDocs.Conversion for .NET 將 EPS（封裝 PostScript）檔案轉換為 PDF。
## 先決條件
在繼續轉換之前，請確保您具備以下條件：
1.  GroupDocs.Conversion for .NET：請確保您已安裝 GroupDocs.Conversion for .NET。您可以從以下位置下載：[這裡](https://releases.groupdocs.com/conversion/net/).
2. 來源 EPS 檔案：準備要轉換為 PDF 的 EPS 檔案。

## 導入命名空間
在開始轉換過程之前，先導入必要的命名空間：
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## 第 1 步：定義輸出資料夾和文件
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "eps-converted-to.pdf");
```
確保更換`"Your Document Directory"`以及所需輸出資料夾的路徑。
## 步驟 2： 載入來源 EPS 檔案並轉換為 PDF
```csharp
//載入來源 EPS 文件
using (var converter = new GroupDocs.Conversion.Converter("Path to Your EPS File"))
{
    var options = new PdfConvertOptions();
    //儲存轉換後的 PDF 文件
    converter.Convert(outputFile, options);
}
```
代替`"Path to Your EPS File"`與 EPS 檔案的實際路徑。
## 步驟 3：顯示轉換完成訊息
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
此行將輸出一條成功訊息以及儲存轉換後的 PDF 檔案的路徑。

## 結論
使用 GroupDocs.Conversion for .NET 可以輕鬆將 EPS 檔案轉換為 PDF 格式。透過遵循本教學中概述的步驟，您可以輕鬆地將 EPS 檔案無縫轉換為 PDF。
## 常見問題解答
### GroupDocs.Conversion for .NET 是否與所有版本的 EPS 檔案相容？
GroupDocs.Conversion for .NET 支援各種版本的 EPS 文件，確保與大多數 EPS 格式相容。
### 我可以自訂 EPS 到 PDF 轉換的轉換選項嗎？
是的，您可以根據您的要求自訂轉換選項，例如調整頁面方向、設定解析度等。
### GroupDocs.Conversion for .NET 是否需要商業用途授權？
是的，您需要購買商業用途的許可證。您可以從以下位置取得許可證[這裡](https://purchase.groupdocs.com/buy).
### 轉換的檔案大小有限制嗎？
GroupDocs.Conversion for .NET 支援各種大小的檔案的轉換。但是，非常大的文件可能需要額外的資源。
### 如果在轉換過程中遇到任何問題，我可以在哪裡獲得支援？
您可以從 GroupDocs 社群論壇尋求支援和協助[這裡](https://forum.groupdocs.com/c/conversion/11).