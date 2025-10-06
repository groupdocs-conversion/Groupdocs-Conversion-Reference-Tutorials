---
"date": "2025-05-03"
"description": "學習如何使用 GroupDocs.Conversion for .NET 將 IGES (IGS) 檔案轉換為文字格式。本指南包含程式碼範例和實際應用，內容全面。"
"title": "使用 GroupDocs.Conversion for .NET 將 IGS 檔案轉換為 TXT — 逐步指南"
"url": "/zh-hant/net/cad-technical-drawing-formats/convert-igs-to-txt-groupdocs-conversion-dotnet/"
"weight": 1
type: docs
---
# 使用 GroupDocs.Conversion for .NET 將 IGS 檔案轉換為 TXT：逐步指南

## 介紹
還在為將 IGES (IGS) 檔案轉換為更容易存取的文字格式而苦惱嗎？透過 GroupDocs.Conversion for .NET 的強大功能，您可以將複雜的 CAD 圖紙無縫地轉換為簡單的文字檔案。本教學將指導您如何使用這個強大的庫高效地處理文件轉換。

在本教程中，我們將介紹：
- 使用 GroupDocs.Conversion 載入 IGS 文件
- 將 IGS 檔案轉換為 TXT 格式
- 設定環境和必要的依賴項

讓我們逐步指導您從安裝到實施。

## 先決條件
在開始之前，請確保您的開發環境符合以下要求：
- **所需庫**：需要.NET Core 或 .NET Framework。
- **依賴項**：安裝 GroupDocs.Conversion for .NET 版本 25.3.0。
- **知識前提**：對 C# 和檔案 I/O 操作有基本的了解。

## 為 .NET 設定 GroupDocs.Conversion
### 安裝
若要將 GroupDocs.Conversion 整合到您的專案中，請按照以下步驟操作：

**NuGet 套件管理器控制台**
```plaintext
Install-Package GroupDocs.Conversion -Version 25.3.0
```

**\.NET CLI**
```bash
dotnet add package GroupDocs.Conversion --version 25.3.0
```

### 許可證獲取
您可以先免費試用，也可以獲得臨時許可證以進行更廣泛的測試：
- **免費試用**：下載並評估該庫以查看它是否滿足您的需求。
- **臨時執照**：透過申請臨時執照 [群組文檔](https://purchase。groupdocs.com/temporary-license/).
- **購買**：如果您準備好了，請購買完整許可證以解鎖所有功能。

### 基本初始化
以下是如何在 C# 專案中初始化和設定 GroupDocs.Conversion：

```csharp
using System;
using GroupDocs.Conversion;

class Program
{
    static void Main(string[] args)
    {
        // 使用 IGS 檔案的路徑進行初始化
        using (var converter = new Converter("sample.igs"))
        {
            Console.WriteLine("Converter initialized successfully.");
        }
    }
}
```
此程式碼片段示範如何載入 IGS 文件，為進一步的轉換操作奠定基礎。

## 實施指南
我們將把實施過程分解為易於管理的部分：
### 載入IGS文件
**概述**
載入 IGS 檔案是任何轉換前的第一步。此操作將初始化 `Converter` 物件與您的來源檔案。

```csharp
using System;
using System.IO;
using GroupDocs.Conversion;

string igFilePath = Path.Combine("YOUR_DOCUMENT_DIRECTORY\