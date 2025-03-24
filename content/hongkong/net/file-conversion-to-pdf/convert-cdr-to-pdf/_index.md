---
title: 將 CDR 向量圖形轉換為 PDF
linktitle: 將 CDR 向量圖形轉換為 PDF
second_title: GroupDocs.Conversion .NET API
description: 使用 GroupDocs.Conversion for .NET 輕鬆將 CorelDRAW (CDR) 向量圖形檔案轉換為 PDF 格式。簡化您的文件轉換過程。
weight: 12
url: /zh-hant/net/file-conversion-to-pdf/convert-cdr-to-pdf/
---
## 介紹
GroupDocs.Conversion for .NET 是一個功能強大的文件轉換庫，可讓開發人員將各種文件格式無縫轉換為 PDF、Word、HTML 等。在本教程中，我們將重點介紹使用 GroupDocs.Conversion for .NET 將 CorelDRAW (CDR) 向量圖形檔案轉換為 PDF 格式。讀完本指南後，您將掌握在 .NET 應用程式中輕鬆執行此轉換的知識。
## 先決條件
在我們深入了解轉換過程之前，請確保您已設定以下先決條件：
### 安裝適用於 .NET 的 GroupDocs.Conversion
首先，您需要下載並安裝 GroupDocs.Conversion for .NET。您可以從以下位置下載該程式庫[下載頁面](https://releases.groupdocs.com/conversion/net/).
### 獲得許可證
要充分利用 集團文件.Conversion for .NET 的潛力，您需要有效的授權。您可以從以下位置取得許可證[GroupDocs](https://purchase.groupdocs.com/buy)或為測試目的請求臨時許可證[這裡](https://purchase.groupdocs.com/temporary-license/).

## 導入命名空間
確保您已在 .NET 專案中匯入了必要的命名空間以利用 GroupDocs.Conversion 功能。您可以這樣做：
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## 第 1 步：定義輸出資料夾和檔名
首先，指定將儲存轉換後的 PDF 檔案的輸出資料夾以及所需的檔案名稱。
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "cdr-converted-to.pdf");
```
確保更換`"Your Document Directory"`以及所需輸出資料夾的路徑。
## 步驟2：載入來源CDR文件
接下來，使用 GroupDocs.Conversion 載入要轉換為 PDF 的來源 CDR 檔案。
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_CDR))
{
    //轉換邏輯將會放在這裡
}
```
代替`Constants.SAMPLE_CDR`與實際 CDR 檔案的路徑。
## 步驟 3：指定轉換選項
定義轉換選項，例如指定輸出格式 (PDF) 和任何其他設定。
```csharp
var options = new PdfConvertOptions();
```
您可以根據您的要求自訂轉換選項。
## 第 4 步：執行轉換
使用指定選項執行轉換過程。
```csharp
converter.Convert(outputFile, options);
```
此命令會將 CDR 檔案轉換為 PDF，並使用提供的檔案名稱將其儲存到指定的輸出資料夾。
## 第5步：確認轉換完成
最後，顯示一則訊息，確認轉換過程成功完成。
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```
此訊息將告知您轉換後的 PDF 檔案的儲存位置。

## 結論
在本教學中，我們學習如何使用 GroupDocs.Conversion for .NET 將 CorelDRAW (CDR) 向量圖檔轉換為 PDF 格式。透過遵循概述的步驟，您可以將文件轉換功能無縫整合到 .NET 應用程式中，從而增強其功能和可用性。
## 常見問題解答
### GroupDocs.Conversion for .NET 是否與所有版本的 CorelDRAW 檔案相容？
GroupDocs.Conversion for .NET 支援多種 CorelDRAW 版本，確保與大多數 CDR 檔案相容。
### 我可以使用 GroupDocs.Conversion for .NET 同時轉換多個 CDR 檔案嗎？
是的，您可以使用 GroupDocs.Conversion for .NET 將多個 CDR 檔案批次轉換為 PDF 或其他格式，從而提高效率和生產力。
### GroupDocs.Conversion for .NET 是否需要 Internet 連線才能進行文件轉換？
不需要，GroupDocs.Conversion for .NET 在您的電腦上本地執行文件轉換，從而無需在轉換過程中連接 Internet。
### 我可以根據我的具體要求自訂轉換設定嗎？
是的，GroupDocs.Conversion for .NET 提供了廣泛的自訂選項，可讓您自訂轉換過程以滿足您的特定需求。
### GroupDocs.Conversion for .NET 是否提供技術支援？
是的，GroupDocs 為其產品提供全面的技術支持，包括適用於 .NET 的 GroupDocs.Conversion。您可以向以下機構尋求協助[支援論壇](https://forum.groupdocs.com/c/conversion/11)如有任何疑問或問題。