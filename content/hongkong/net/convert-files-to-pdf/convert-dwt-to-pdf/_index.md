---
title: 將 DWT CAD 範本檔案轉換為 PDF
linktitle: 將 DWT CAD 範本檔案轉換為 PDF
second_title: GroupDocs.Conversion .NET API
description: 了解如何使用 GroupDocs.Conversion for .NET 將 DWT CAD 範本檔案輕鬆轉換為 PDF 格式。
weight: 11
url: /zh-hant/net/convert-files-to-pdf/convert-dwt-to-pdf/
---

# 將 DWT CAD 範本檔案轉換為 PDF

## 介紹
在本教學中，我們將學習如何使用 GroupDocs.Conversion for .NET 將 DWT CAD 範本檔案轉換為 PDF 格式。 GroupDocs.Conversion for .NET 是一個功能強大的文件轉換庫，可讓您無縫轉換各種文件格式。
## 先決條件
在我們開始之前，請確保您符合以下先決條件：
1.  GroupDocs.Conversion for .NET Library：從以下位置下載並安裝該程式庫：[這裡](https://releases.groupdocs.com/conversion/net/).
2. .NET Framework：確保您的系統上安裝了 .NET Framework。
3. 來源 DWT 檔案：您應該擁有要轉換為 PDF 的 DWT CAD 範本檔案。

## 導入命名空間
首先，讓我們將必要的命名空間匯入到我們的專案中：
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
現在，讓我們將轉換過程分解為多個步驟：
## 第 1 步：設定輸出資料夾和檔名
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "dwt-converted-to.pdf");
```
代替`"Your Document Directory"`以及要儲存轉換後的 PDF 檔案的目錄路徑。
## 步驟 2：載入來源 DWT 檔案並轉換為 PDF
```csharp
//載入來源 DWT 文件
using (var converter = new GroupDocs.Conversion.Converter("Path_to_your_sample_DWT_file.dwt"))
{
    var options = new PdfConvertOptions();
    //儲存轉換後的 PDF 文件
    converter.Convert(outputFile, options);
}
```
代替`"Path_to_your_sample_DWT_file.dwt"`以及來源 DWT 檔案的路徑。
## 步驟 3：顯示轉換狀態
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
此步驟將顯示成功訊息以及儲存轉換後的 PDF 檔案的輸出資料夾。

## 結論
在本教學中，我們學習如何使用 GroupDocs.Conversion for .NET 將 DWT CAD 範本檔案輕鬆轉換為 PDF 格式。透過遵循提供的步驟，您可以將文件轉換功能無縫整合到您的 .NET 應用程式中。
## 常見問題解答
### GroupDocs.Conversion for .NET 是否與所有版本的 .NET Framework 相容？
是的，GroupDocs.Conversion for .NET 與各種版本的 .NET Framework 相容，包括 .NET Core 和 .NET Standard。
### 我可以使用此庫同時轉換多個 DWT 檔案嗎？
是的，您可以使用 GroupDocs.Conversion for .NET 將多個 DWT 檔案批次轉換為 PDF 或其他支援的格式。
### GroupDocs.Conversion for .NET 是否支援 DWT 以外的其他 CAD 檔案格式？
是的，GroupDocs.Conversion for .NET 支援多種 CAD 檔案格式，包括 DWG、DXF、DGN 等。
### 我可以根據我的要求自訂轉換選項嗎？
是的，您可以自訂各種轉換選項，例如頁面大小、方向、品質等，以滿足您的特定需求。
### 在哪裡可以找到有關 GroupDocs.Conversion for .NET 的其他支援或協助？
您可以訪問[GroupDocs.Conversion 論壇](https://forum.groupdocs.com/c/conversion/11)與圖書館相關的任何技術疑問或協助。