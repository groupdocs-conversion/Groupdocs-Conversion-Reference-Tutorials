---
title: DNG 画像を PDF に変換
linktitle: DNG 画像を PDF に変換
second_title: GroupDocs.Conversion .NET API
description: GroupDocs.Conversion for .NET を使用して DNG 画像を PDF に簡単に変換する方法を学びます。シームレスな変換については、ステップバイステップのガイドに従ってください。
weight: 21
url: /ja/net/file-conversion-to-pdf/convert-dng-to-pdf/
---

# DNG 画像を PDF に変換

## 導入
このチュートリアルでは、GroupDocs.Conversion for .NET を使用して DNG 画像を PDF に変換するプロセスを説明します。 DNG (Digital Negative) は、デジタル写真に使用されるファイル形式です。 DNG 画像を PDF に変換すると、より広く受け入れられている形式で簡単に共有したり保存したりできます。
## 前提条件
始める前に、以下のものがあることを確認してください。
1.  GroupDocs.Conversion for .NET: .NET 用の GroupDocs.Conversion ライブラリをダウンロードしてインストールします。[ここ](https://releases.groupdocs.com/conversion/net/).
2. ソース DNG ファイル: PDF に変換する DNG 画像ファイルが必要です。
3. 開発環境: .NET 開発環境がセットアップされていることを確認します。

## 名前空間のインポート
まず、必要な名前空間をプロジェクトにインポートする必要があります。次の using ディレクティブをコード ファイルに追加します。
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## ステップ 1: ソース DNG ファイルをロードする
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "dng-converted-to.pdf");
//ソース DNG ファイルをロードします
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_DNG))
{
    //変換プロセスを続行します
}
```
このステップでは、変換された PDF ファイルが保存される出力フォルダーを定義します。必ず交換してください`"Your Document Directory"`目的のディレクトリへのパスを置き換えます。次に、出力 PDF ファイルの名前とパスを指定します。
## ステップ 2: DNG を PDF に変換する
```csharp
var options = new PdfConvertOptions();
//変換したPDFファイルを保存する
converter.Convert(outputFile, options);
```
ここでは、次のインスタンスを作成します。`PdfConvertOptions`必要に応じて、PDF 変換の特定のオプションを設定します。次に、`Convert`の方法`converter`オブジェクトを渡し、出力ファイルのパスと変換オプションを渡します。
## ステップ 3: 変換の完了を処理する
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
変換プロセスが完了すると、成功メッセージと変換された PDF ファイルが置かれているディレクトリが表示されます。

## 結論
結論として、GroupDocs.Conversion for .NET を使用すると、DNG イメージを PDF に簡単に変換できます。このチュートリアルで説明する簡単な手順に従うことで、DNG ファイルを PDF 形式に効率的に変換し、よりアクセスしやすく、共有しやすくすることができます。
## よくある質問
### GroupDocs.Conversion for .NET は、.NET のすべてのバージョンと互換性がありますか?
はい。GroupDocs.Conversion for .NET は、.NET Framework 4.6.1 以降および .NET Core 2.0 以降と互換性があります。
### 複数の DNG ファイルを同時に PDF に変換できますか?
はい、各ファイルを繰り返し処理し、それぞれの変換プロセスを実行することで、複数の DNG ファイルを PDF に変換できます。
### 変換できる DNG ファイルのサイズに制限はありますか?
GroupDocs.Conversion for .NET には、変換できる DNG ファイルのサイズに特別な制限はありません。ただし、パフォーマンスは入力ファイルのサイズと複雑さによって異なる場合があります。
### PDF 出力の変換オプションをカスタマイズできますか?
はい、ページ サイズ、方向、圧縮などのさまざまなオプションをカスタマイズできます。`PdfConvertOptions`GroupDocs.Conversion for .NET によって提供されるクラス。
### GroupDocs.Conversion for .NET のテクニカル サポートは利用できますか?
はい、GroupDocs フォーラムを通じてテクニカル サポートを利用できます。[ここ](https://forum.groupdocs.com/c/conversion/11)で質問したり、専門家からサポートを受けることができます。