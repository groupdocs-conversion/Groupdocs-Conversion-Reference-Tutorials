---
"description": "使用 GroupDocs.Conversion for .NET 輕鬆將 JPG 轉換為 PDF。按照本逐步教程，即可實現無縫文件轉換。"
"linktitle": "將 JPG 轉換為 PDF"
"second_title": "GroupDocs.轉換 .NET API"
"title": "將 JPG 轉換為 PDF"
"url": "/zh-hant/net/document-conversion/convert-jpg-to-pdf/"
"weight": 14
---

# 將 JPG 轉換為 PDF

## 介紹

您是否想使用 GroupDocs.Conversion for .NET 輕鬆將 JPG 檔案轉換為 PDF？本教學將逐步引導您完成整個過程。 GroupDocs.Conversion for .NET 是一款功能強大的 API，可讓您輕鬆將各種文件格式（包括影像）無縫轉換為 PDF。讓我們開始吧！

## 先決條件

在開始之前，請確保您符合以下先決條件：

1. GroupDocs.Conversion for .NET：請確保您已安裝 GroupDocs.Conversion for .NET。您可以從以下網址下載： [這裡](https://releases。groupdocs.com/conversion/net/).
2. 開發環境：設定開發環境，例如 Visual Studio，以及 .NET Framework 或 .NET Core。
3. 範例 JPG 檔案：準備要轉換為 PDF 的範例 JPG 檔案。

## 導入命名空間

首先，讓我們導入必要的命名空間：

```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```

現在，讓我們將轉換過程分解為簡單的步驟：

## 步驟 1：定義輸出目錄和檔名

```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "jpg-converted-to.pdf");
```

確保指定要儲存轉換後的 PDF 檔案的目錄和所需的輸出檔案名稱。

## 步驟2：載入來源JPG檔案並轉換為PDF

```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_JPG))
{
    var options = new PdfConvertOptions();
    converter.Convert(outputFile, options);
}
```

初始化 `Converter` 對象，其中包含範例 JPG 檔案的路徑。然後，配置轉換選項，例如指定 PDF 轉換選項。最後，調用 `Convert` 方法，傳遞輸出檔案路徑和轉換選項。

## 步驟3：顯示轉換完成訊息

```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```

轉換完成後，顯示轉換成功的訊息以及轉換後的PDF檔案的位置。

## 結論

使用 GroupDocs.Conversion for .NET 將 JPG 檔案轉換為 PDF 非常簡單，只需幾行程式碼即可。按照本教學課程，您可以將文件轉換功能無縫整合到您的 .NET 應用程式中。

## 常見問題解答

### Q：我可以同時將多個 JPG 檔案轉換為 PDF 嗎？

答：是的，您可以透過遍歷每個檔案並執行教程中描述的轉換過程將多個 JPG 檔案轉換為 PDF。

### Q：GroupDocs.Conversion 除了 JPG 之外還支援其他影像格式嗎？

答：是的，GroupDocs.Conversion 支援各種影像格式，例如 PNG、TIFF、BMP 和 GIF 等。

### Q：我可以使用轉換選項自訂輸出 PDF 檔案嗎？

答：當然！ GroupDocs.Conversion 提供了多種轉換選項，可讓您根據需求自訂輸出 PDF。

### Q：GroupDocs.Conversion for .NET 有試用版嗎？

答：是的，您可以從以下網址取得 GroupDocs.Conversion for .NET 的免費試用版 [這裡](https://releases。groupdocs.com/).

### Q：如果我在轉換過程中遇到任何問題，我可以在哪裡尋求協助？

答：如果您遇到任何問題或對 GroupDocs.Conversion for .NET 有任何疑問，請隨時訪問 [GroupDocs.Conversion 論壇](https://forum.groupdocs.com/c/conversion/11) 尋求幫助。