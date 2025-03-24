---
title: OTGをPDFに変換
linktitle: OTGをPDFに変換
second_title: GroupDocs.Conversion .NET API
description: GroupDocs.Conversion for .NET を使用して OTG ファイルを PDF に変換する方法を学びます。プロジェクトのシンプル、効率的、シームレスな統合。
weight: 13
url: /ja/net/pdf-conversion/convert-otg-to-pdf/
---

# OTGをPDFに変換

## 導入
OTG (OpenDocument Graphics) ファイルを PDF 形式に変換することは、特にドキュメント管理システムを扱う場合や、異なるプラットフォーム間でファイルを共有する場合に重要なタスクとなることがあります。このチュートリアルでは、.NET 用の GroupDocs.Conversion ライブラリを使用して OTG ファイルを PDF に変換するプロセスを説明します。飛び込んでみましょう！
## 前提条件
始める前に、次の前提条件を満たしていることを確認してください。
1. GroupDocs.Conversion for .NET: .NET 用の GroupDocs.Conversion ライブラリがインストールされていることを確認してください。からダウンロードできます[ここ](https://releases.groupdocs.com/conversion/net/).
2. OTG ファイル: PDF に変換する OTG ファイルをドキュメント ディレクトリに用意します。

## 名前空間のインポート
まず、必要な名前空間を .NET プロジェクトにインポートする必要があります。 
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## ステップ 1: 出力ディレクトリとファイル名を設定する
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "otg-converted-to.pdf");
```
このステップでは、変換された PDF ファイルが保存される出力ディレクトリを定義します。交換する`"Your Document Directory"`目的の出力ディレクトリへのパスを置き換えます。
## ステップ 2: ソース OTG ファイルをロードして PDF に変換する
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_OTG))
{
    var options = new PdfConvertOptions();
    //変換したPDFファイルを保存する
    converter.Convert(outputFile, options);
}
```
ここで、新しいインスタンスを作成します。`Converter`GroupDocs.Conversion ライブラリのオブジェクトを取得し、ソース OTG ファイルのパスを渡します。次に、作成します`PdfConvertOptions`変換オプションを指定します。最後に、`Convert` OTGファイルをPDF形式に変換する方法。
## ステップ 3: 変換の完了を確認する
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
このステップでは、変換プロセスが正常に完了したことをユーザーに通知し、変換された PDF ファイルが保存されるパスを提供します。

## 結論
.NET 用の GroupDocs.Conversion ライブラリを使用すると、OTG ファイルを PDF 形式に変換することが簡単になります。このチュートリアルで概説されている手順に従うことで、この機能を .NET アプリケーションにシームレスに統合し、ドキュメントの相互運用性とアクセシビリティを強化できます。
## よくある質問
### GroupDocs.Conversion は OTG 以外の他のファイル形式を PDF に変換できますか?
はい、GroupDocs.Conversion は、DOCX、XLSX、PPTX、HTML などを含む幅広いファイル形式の変換をサポートしています。
### GroupDocs.Conversion は商用利用に適していますか?
絶対に！ GroupDocs.Conversion は、強力なドキュメント変換機能を活用したい企業や組織に商用ライセンスを提供します。
### GroupDocs.Conversion は技術サポートを提供しますか?
はい。GroupDocs は、実装中に発生する可能性のある質問や問題についてユーザーを支援する専用のテクニカル サポートを提供しています。
### ライセンスを購入する前に GroupDocs.Conversion を試すことはできますか?
はい、GroupDocs.Conversion の無料トライアルを利用して、その機能と要件との互換性を調べることができます。
### GroupDocs.Conversion の一時ライセンスを取得するにはどうすればよいですか?
評価目的または短期プロジェクトの場合は、一時ライセンスを GroupDocs から取得できます。[ライセンス](https://purchase.groupdocs.com/temporary-license/).