---
"description": "了解如何使用 GroupDocs.Conversion for .NET 將 PowerPoint 簡報 (PPTX) 轉換為 PDF 格式。轉換過程簡單又有效率。"
"linktitle": "將PPTX轉換為PDF"
"second_title": "GroupDocs.轉換 .NET API"
"title": "將PPTX轉換為PDF"
"url": "/zh-hant/net/pdf-conversion/convert-pptx-to-pdf/"
"weight": 29
type: docs
---
# 將PPTX轉換為PDF

## 介紹
在本教學中，我們將示範如何使用 .NET 的 GroupDocs.Conversion 庫將 PowerPoint 簡報 (PPTX) 檔案轉換為可移植文件格式 (PDF)。請按照以下步驟完成此轉換。
## 先決條件
在開始之前，請確保您符合以下先決條件：
1. GroupDocs.Conversion for .NET 程式庫：請確保您已安裝 GroupDocs.Conversion for .NET 程式庫。您可以從此處下載 [這裡](https://releases。groupdocs.com/conversion/net/).
2. 開發環境：使用必要的工具（如 Visual Studio 或任何其他 .NET IDE）設定開發環境。

## 導入命名空間
在您的專案中包含必要的命名空間以存取 GroupDocs.Conversion 功能。
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## 步驟 1：設定輸出資料夾和檔案名稱
首先，定義將儲存轉換後的 PDF 檔案的輸出資料夾，並指定輸出 PDF 檔案的名稱。
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "pptx-converted-to.pdf");
```
## 步驟2：載入來源PPTX文件
使用 GroupDocs.Conversion 庫載入來源 PowerPoint 簡報 (PPTX) 檔案。
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PPTX))
{
    // 轉換邏輯將會放在這裡
}
```
## 步驟 3：指定轉換選項
定義轉換選項。在本例中，我們將轉換為 PDF 格式，因此建立一個 `PdfConvertOptions`。
```csharp
var options = new PdfConvertOptions();
```
## 步驟4：執行轉換
使用 `Convert` 方法並傳遞輸出檔案路徑以及轉換選項。
```csharp
converter.Convert(outputFile, options);
```
## 步驟5：檢查輸出
轉換成功完成後，顯示一則訊息，指示完成和輸出檔案的位置。
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```

## 結論
在本教學中，我們學習如何使用 .NET 的 GroupDocs.Conversion 函式庫將 PowerPoint 簡報 (PPTX) 檔案轉換為可移植文件格式 (PDF)。按照上面概述的步驟，您可以輕鬆地在 .NET 應用程式中執行此轉換。
## 常見問題解答
### Q：GroupDocs.Conversion 是否與所有版本的 .NET 相容？
答：是的，GroupDocs.Conversion 支援 .NET Framework 2.0 及更高版本，包括 .NET Core 和 .NET Standard。
### Q：我可以將文件轉換為 PDF 以外的格式嗎？
答：是的，GroupDocs.Conversion 支援多種文件格式轉換，包括 Word、Excel、HTML 等。
### Q：GroupDocs.Conversion 提供免費試用嗎？
答：是的，您可以從以下網址免費試用 GroupDocs.Conversion [這裡](https://releases。groupdocs.com/).
### Q：如何獲得 GroupDocs.Conversion 的支援？
答：您可以從 GroupDocs 社群論壇獲得支持 [這裡](https://forum。groupdocs.com/c/conversion/11).
### Q：GroupDocs.Conversion 有臨時許可證嗎？
答：是的，您可以從以下位置取得 GroupDocs.Conversion 的臨時許可證 [這裡](https://purchase。groupdocs.com/temporary-license/).