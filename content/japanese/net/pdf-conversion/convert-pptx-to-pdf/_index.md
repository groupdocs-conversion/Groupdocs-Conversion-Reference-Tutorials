---
"description": "GroupDocs.Conversion for .NETを使用して、PowerPointプレゼンテーション（PPTX）をPDF形式に変換する方法を学びましょう。簡単で効率的な変換プロセスです。"
"linktitle": "PPTXをPDFに変換する"
"second_title": "GroupDocs.Conversion .NET API"
"title": "PPTXをPDFに変換する"
"url": "/ja/net/pdf-conversion/convert-pptx-to-pdf/"
"weight": 29
---

# PPTXをPDFに変換する

## 導入
このチュートリアルでは、.NET用のGroupDocs.Conversionライブラリを使用して、PowerPointプレゼンテーション（PPTX）ファイルをPortable Document Format（PDF）に変換する手順を説明します。変換を実行するには、以下の手順に従ってください。
## 前提条件
始める前に、次の前提条件が満たされていることを確認してください。
1. GroupDocs.Conversion for .NETライブラリ: GroupDocs.Conversion for .NETライブラリがインストールされていることを確認してください。ダウンロードはこちらから行えます。 [ここ](https://releases。groupdocs.com/conversion/net/).
2. 開発環境: Visual Studio やその他の .NET IDE などの必要なツールを使用して開発環境をセットアップします。

## 名前空間のインポート
GroupDocs.Conversion 機能にアクセスするには、プロジェクトに必要な名前空間を含めます。
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## ステップ1：出力フォルダとファイル名を設定する
まず、変換された PDF ファイルを保存する出力フォルダーを定義し、出力 PDF ファイルの名前を指定します。
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "pptx-converted-to.pdf");
```
## ステップ2: ソースPPTXファイルを読み込む
GroupDocs.Conversion ライブラリを使用して、ソースの PowerPoint プレゼンテーション (PPTX) ファイルを読み込みます。
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PPTX))
{
    // 変換ロジックはここに配置されます
}
```
## ステップ3: 変換オプションを指定する
変換オプションを定義します。今回はPDF形式に変換するので、 `PdfConvertOptions`。
```csharp
var options = new PdfConvertOptions();
```
## ステップ4: 変換を実行する
変換プロセスを実行するには、 `Convert` メソッドを使用し、変換オプションとともに出力ファイル パスを渡します。
```csharp
converter.Convert(outputFile, options);
```
## ステップ5: 出力を確認する
変換が正常に完了すると、完了と出力ファイルの場所を示すメッセージが表示されます。
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```

## 結論
このチュートリアルでは、.NET用のGroupDocs.Conversionライブラリを使用して、PowerPointプレゼンテーション（PPTX）ファイルをPortable Document Format（PDF）に変換する方法を学習しました。上記の手順に従えば、.NETアプリケーションで簡単にこの変換を実行できます。
## よくある質問
### Q: GroupDocs.Conversion は、すべてのバージョンの .NET と互換性がありますか?
A: はい、GroupDocs.Conversion は、.NET Core および .NET Standard を含む .NET Framework 2.0 以上をサポートしています。
### Q: ファイルを PDF 以外の形式に変換できますか?
A: はい、GroupDocs.Conversion は、Word、Excel、HTML など、幅広いドキュメント形式の変換をサポートしています。
### Q: GroupDocs.Conversion には無料トライアルはありますか?
A: はい、GroupDocs.Conversionの無料トライアルは以下からご利用いただけます。 [ここ](https://releases。groupdocs.com/).
### Q: GroupDocs.Conversion のサポートを受けるにはどうすればよいですか?
A: GroupDocsコミュニティフォーラムからサポートを受けることができます [ここ](https://forum。groupdocs.com/c/conversion/11).
### Q: GroupDocs.Conversion に利用できる一時ライセンスはありますか?
A: はい、GroupDocs.Conversionの一時ライセンスは以下から取得できます。 [ここ](https://purchase。groupdocs.com/temporary-license/).