---
title: EPS カプセル化された PostScript ファイルを PDF に変換
linktitle: EPS カプセル化された PostScript ファイルを PDF に変換
second_title: GroupDocs.Conversion .NET API
description: GroupDocs.Conversion for .NET を使用して、EPS ファイルを PDF に簡単に変換します。このチュートリアルでは、シームレスな変換のためのステップバイステップのガイドを提供します。
weight: 17
url: /ja/net/convert-files-to-pdf/convert-eps-to-pdf/
---
## 導入
このチュートリアルでは、GroupDocs.Conversion for .NET を使用して EPS (Encapsulated PostScript) ファイルを PDF に変換する方法を説明します。
## 前提条件
変換を続行する前に、次のものが揃っていることを確認してください。
1.  GroupDocs.Conversion for .NET: GroupDocs.Conversion for .NET がインストールされていることを確認します。からダウンロードできます[ここ](https://releases.groupdocs.com/conversion/net/).
2. ソース EPS ファイル: PDF に変換する EPS ファイルを準備します。

## 名前空間のインポート
変換プロセスを開始する前に、必要な名前空間をインポートします。
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## ステップ 1: 出力フォルダーとファイルを定義する
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "eps-converted-to.pdf");
```
必ず交換してください`"Your Document Directory"`目的の出力フォルダーへのパスを置き換えます。
## ステップ 2: ソース EPS ファイルをロードして PDF に変換する
```csharp
//ソースEPSファイルをロードします
using (var converter = new GroupDocs.Conversion.Converter("Path to Your EPS File"))
{
    var options = new PdfConvertOptions();
    //変換したPDFファイルを保存する
    converter.Convert(outputFile, options);
}
```
交換する`"Path to Your EPS File"`EPS ファイルへの実際のパスを含めます。
## ステップ3：変換完了メッセージの表示
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
この行は、変換された PDF ファイルが保存されるパスとともに成功メッセージを出力します。

## 結論
EPS ファイルを PDF 形式に変換するには、GroupDocs.Conversion for .NET を使用して簡単に実行できます。このチュートリアルで概説されている手順に従うことで、最小限の労力で EPS ファイルを PDF にシームレスに変換できます。
## よくある質問
### GroupDocs.Conversion for .NET は、EPS ファイルのすべてのバージョンと互換性がありますか?
GroupDocs.Conversion for .NET はさまざまなバージョンの EPS ファイルをサポートし、ほとんどの EPS 形式との互換性を保証します。
### EPS から PDF への変換オプションをカスタマイズできますか?
はい、ページの向きの調整や解像度の設定など、要件に応じて変換オプションをカスタマイズできます。
### GroupDocs.Conversion for .NET を商用利用するにはライセンスが必要ですか?
はい、商用利用するにはライセンスを購入する必要があります。からライセンスを取得できます[ここ](https://purchase.groupdocs.com/buy).
### 変換するファイルサイズに制限はありますか?
GroupDocs.Conversion for .NET は、さまざまなサイズのファイルの変換をサポートします。ただし、非常に大きなファイルの場合は追加のリソースが必要になる場合があります。
### 変換中に問題が発生した場合はどこでサポートを受けられますか?
 GroupDocs コミュニティ フォーラムからサポートや支援を求めることができます。[ここ](https://forum.groupdocs.com/c/conversion/11).