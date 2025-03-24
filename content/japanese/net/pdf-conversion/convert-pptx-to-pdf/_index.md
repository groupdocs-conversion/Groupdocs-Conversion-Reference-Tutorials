---
title: PPTXをPDFに変換
linktitle: PPTXをPDFに変換
second_title: GroupDocs.Conversion .NET API
description: GroupDocs.Conversion for .NET を使用して PowerPoint プレゼンテーション (PPTX) を PDF 形式に変換する方法を学びます。簡単かつ効率的な変換プロセス。
weight: 29
url: /ja/net/pdf-conversion/convert-pptx-to-pdf/
---

# PPTXをPDFに変換

## 導入
このチュートリアルでは、.NET 用の GroupDocs.Conversion ライブラリを使用して、PowerPoint プレゼンテーション (PPTX) ファイルを Portable Document Format (PDF) に変換するプロセスを説明します。この変換を行うには、次の手順に従ってください。
## 前提条件
始める前に、次の前提条件を満たしていることを確認してください。
1.  GroupDocs.Conversion for .NET ライブラリ: GroupDocs.Conversion for .NET ライブラリがインストールされていることを確認してください。からダウンロードできます[ここ](https://releases.groupdocs.com/conversion/net/).
2. 開発環境: Visual Studio やその他の .NET IDE などの必要なツールを使用して開発環境をセットアップします。

## 名前空間のインポート
GroupDocs.Conversion 機能にアクセスするために必要な名前空間をプロジェクトに含めます。
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## ステップ 1: 出力フォルダーとファイル名を設定する
まず、変換した PDF ファイルを保存する出力フォルダーを定義し、出力 PDF ファイルの名前を指定します。
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "pptx-converted-to.pdf");
```
## ステップ 2: ソース PPTX ファイルをロードする
GroupDocs.Conversion ライブラリを使用して、ソース PowerPoint プレゼンテーション (PPTX) ファイルを読み込みます。
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PPTX))
{
    //変換ロジックはここに配置されます
}
```
## ステップ 3: 変換オプションを指定する
変換オプションを定義します。今回はPDF形式に変換するので、`PdfConvertOptions`.
```csharp
var options = new PdfConvertOptions();
```
## ステップ 4: 変換を実行する
を使用して変換処理を実行します。`Convert`メソッドを使用して、変換オプションとともに出力ファイルのパスを渡します。
```csharp
converter.Convert(outputFile, options);
```
## ステップ 5: 出力を確認する
変換が正常に完了すると、完了と出力ファイルの場所を示すメッセージが表示されます。
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```

## 結論
このチュートリアルでは、.NET 用の GroupDocs.Conversion ライブラリを使用して、PowerPoint プレゼンテーション (PPTX) ファイルを Portable Document Format (PDF) に変換する方法を学習しました。上記の手順に従うことで、.NET アプリケーションでこの変換を簡単に実行できます。
## よくある質問
### Q: GroupDocs.Conversion は .NET のすべてのバージョンと互換性がありますか?
A: はい、GroupDocs.Conversion は、.NET Core や .NET Standard を含む .NET Framework 2.0 以降をサポートしています。
### Q: ファイルを PDF 以外の形式に変換できますか?
A: はい、GroupDocs.Conversion は、Word、Excel、HTML などを含む幅広いドキュメント形式の変換をサポートしています。
### Q: GroupDocs.Conversion には無料トライアルが提供されていますか?
 A: はい、次から GroupDocs.Conversion の無料トライアルにアクセスできます。[ここ](https://releases.groupdocs.com/).
### Q: GroupDocs.Conversion のサポートを受けるにはどうすればよいですか?
 A: GroupDocs コミュニティ フォーラムからサポートを受けることができます。[ここ](https://forum.groupdocs.com/c/conversion/11).
### Q: GroupDocs.Conversion に使用できる一時ライセンスはありますか?
 A: はい、GroupDocs.Conversion の一時ライセンスは次のサイトから取得できます。[ここ](https://purchase.groupdocs.com/temporary-license/).