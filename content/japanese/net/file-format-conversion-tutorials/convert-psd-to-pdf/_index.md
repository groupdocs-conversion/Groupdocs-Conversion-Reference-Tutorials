---
title: PSDをPDFに変換
linktitle: PSDをPDFに変換
second_title: GroupDocs.Conversion .NET API
description: GroupDocs.Conversion for .NET を使用して PSD ファイルを PDF に簡単に変換する方法を学びます。ステップバイステップのガイドに従ってください。
weight: 10
url: /ja/net/file-format-conversion-convert-psd-to-pdf/
---

# PSDをPDFに変換

## 導入
このチュートリアルでは、.NET 用の GroupDocs.Conversion ライブラリを使用して PSD (Photoshop ドキュメント) ファイルを PDF 形式に変換するプロセスを説明します。これらの段階的な手順に従うことで、PSD ファイルを簡単にシームレスに PDF に変換できるようになります。
## 前提条件
始める前に、次の前提条件が設定されていることを確認してください。
1.  GroupDocs.Conversion ライブラリのインストール: .NET 用の GroupDocs.Conversion ライブラリがインストールされていることを確認してください。からダウンロードできます。[Webサイト](https://releases.groupdocs.com/conversion/net/).
2. PSD ファイルへのアクセス: PDF に変換する PSD ファイルにアクセスできます。

## 名前空間のインポート
変換プロセスに入る前に、必要な名前空間をインポートします。
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## ステップ 1: 出力フォルダーとファイルを定義する
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "psd-converted-to.pdf");
```
このステップでは、変換された PDF ファイルを保存する出力フォルダーを指定します。必ず交換してください`"Your Document Directory"`実際のディレクトリパスを使用します。
## ステップ 2: ソース PSD ファイルをロードする
```csharp
using (var converter = new GroupDocs.Conversion.Converter("Path_to_your_PSD_file.psd"))
{
    var options = new PdfConvertOptions();
    //変換したPDFファイルを保存する
    converter.Convert(outputFile, options);
}
```
ここで初期化します`Converter`オブジェクトを PSD ファイルへのパスに置き換えます。交換する`"Path_to_your_PSD_file.psd"`PSD ファイルへの実際のパスを含めます。次に、のインスタンスを作成します`PdfConvertOptions`をクリックして変換設定を指定します。最後に、`Convert` PSD ファイルを PDF に変換し、指定した出力ファイルに保存するメソッドです。
## ステップ 3: 変換の完了を確認する
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```
このステップでは、変換プロセスが正常に完了したことを確認するメッセージをコンソールに出力し、変換された PDF ファイルの保存場所を示すだけです。

## 結論
このチュートリアルでは、.NET 用の GroupDocs.Conversion ライブラリを使用して PSD ファイルを PDF 形式に変換する方法を説明しました。指定された手順に従うことで、PSD ファイルを PDF に簡単に変換でき、ドキュメントの共有と表示が容易になります。
## よくある質問

### GroupDocs.Conversion を使用して複数の PSD ファイルを一度に変換できますか?
はい、GroupDocs.Conversion を使用して、複数の PSD ファイルを PDF またはその他の形式にバッチ変換できます。

### GroupDocs.Conversion は PDF 以外の他の出力形式をサポートしていますか?
はい、GroupDocs.Conversion は、DOCX、XLSX、PPTX、JPEG、PNG などを含む幅広い出力形式をサポートしています。

### GroupDocs.Conversion は、.NET のさまざまなバージョンと互換性がありますか?
はい、GroupDocs.Conversion は、.NET Core や .NET Framework を含む .NET のさまざまなバージョンと互換性があります。

### 出力をより詳細に制御するために変換オプションをカスタマイズできますか?
はい。GroupDocs.Conversion には、ページ サイズ、方向、品質などの指定など、カスタマイズのための広範なオプションが用意されています。

### 購入前にテストできる試用版はありますか?
はい、GroupDocs.Conversion の無料試用版を次のサイトから入手できます。[Webサイト](https://releases.groupdocs.com/conversion/net/)購入する前に機能をテストしてください。