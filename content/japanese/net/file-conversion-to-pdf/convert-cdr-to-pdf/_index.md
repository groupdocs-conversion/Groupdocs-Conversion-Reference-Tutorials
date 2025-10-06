---
"description": "GroupDocs.Conversion for .NET を使えば、CorelDRAW (CDR) ベクターグラフィックファイルを PDF 形式に簡単に変換できます。ドキュメント変換プロセスを効率化できます。"
"linktitle": "CDRベクターグラフィックをPDFに変換する"
"second_title": "GroupDocs.Conversion .NET API"
"title": "CDRベクターグラフィックをPDFに変換する"
"url": "/ja/net/file-conversion-to-pdf/convert-cdr-to-pdf/"
"weight": 12
type: docs
---
# CDRベクターグラフィックをPDFに変換する

## 導入
GroupDocs.Conversion for .NETは、開発者が様々な形式のドキュメントをPDF、Word、HTMLなど、様々な形式にシームレスに変換できる強力なドキュメント変換ライブラリです。このチュートリアルでは、GroupDocs.Conversion for .NETを使用して、CorelDRAW（CDR）ベクターグラフィックファイルをPDF形式に変換する方法に焦点を当てます。このガイドを読み終える頃には、.NETアプリケーションでこの変換を簡単に実行するための知識が身に付くでしょう。
## 前提条件
変換プロセスに進む前に、次の前提条件が設定されていることを確認してください。
### GroupDocs.Conversion for .NET をインストールする
始めるには、GroupDocs.Conversion for .NETをダウンロードしてインストールする必要があります。ライブラリは以下からダウンロードできます。 [ダウンロードページ](https://releases。groupdocs.com/conversion/net/).
### ライセンスを取得する
GroupDocs.Conversion for .NETの機能をフルに活用するには、有効なライセンスが必要です。ライセンスは以下から取得できます。 [グループドキュメント](https://purchase.groupdocs.com/buy) またはテスト目的で一時ライセンスを申請する [ここ](https://purchase。groupdocs.com/temporary-license/).

## 名前空間のインポート
GroupDocs.Conversion 機能を利用するには、.NET プロジェクトに必要な名前空間がインポートされていることを確認してください。手順は以下のとおりです。
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## ステップ1: 出力フォルダとファイル名を定義する
まず、変換された PDF ファイルを保存する出力フォルダーと、希望のファイル名を指定します。
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "cdr-converted-to.pdf");
```
必ず交換してください `"Your Document Directory"` 希望する出力フォルダーへのパスを入力します。
## ステップ2: ソースCDRファイルをロードする
次に、GroupDocs.Conversion を使用して PDF に変換するソース CDR ファイルを読み込みます。
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_CDR))
{
    // 変換ロジックはここに記述します
}
```
交換する `Constants.SAMPLE_CDR` 実際の CDR ファイルへのパスを入力します。
## ステップ3: 変換オプションを指定する
出力形式 (PDF) や追加設定の指定など、変換オプションを定義します。
```csharp
var options = new PdfConvertOptions();
```
要件に応じて変換オプションをカスタマイズできます。
## ステップ4: 変換を実行する
指定されたオプションで変換プロセスを実行します。
```csharp
converter.Convert(outputFile, options);
```
このコマンドは、CDR ファイルを PDF に変換し、指定されたファイル名で指定された出力フォルダーに保存します。
## ステップ5: 変換完了を確認する
最後に、変換プロセスが正常に完了したことを確認するメッセージを表示します。
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```
このメッセージは、変換された PDF ファイルが保存される場所を通知します。

## 結論
このチュートリアルでは、GroupDocs.Conversion for .NET を使用して、CorelDRAW (CDR) ベクターグラフィックファイルを PDF 形式に変換する方法を学習しました。概要に示された手順に従うことで、ドキュメント変換機能を .NET アプリケーションにシームレスに統合し、機能性と使いやすさを向上させることができます。
## よくある質問
### GroupDocs.Conversion for .NET は、CorelDRAW ファイルのすべてのバージョンと互換性がありますか?
GroupDocs.Conversion for .NET は、幅広い CorelDRAW バージョンをサポートし、ほとんどの CDR ファイルとの互換性を保証します。
### GroupDocs.Conversion for .NET を使用して複数の CDR ファイルを同時に変換できますか?
はい、GroupDocs.Conversion for .NET を使用して複数の CDR ファイルを PDF またはその他の形式に一括変換できるため、効率と生産性が向上します。
### GroupDocs.Conversion for .NET では、ドキュメント変換にインターネット接続が必要ですか?
いいえ、GroupDocs.Conversion for .NET はドキュメント変換をマシン上でローカルに実行するので、変換プロセス中にインターネット接続は必要ありません。
### 特定の要件に応じて変換設定をカスタマイズできますか?
はい、GroupDocs.Conversion for .NET には広範なカスタマイズ オプションが用意されており、ニーズに合わせて変換プロセスをカスタマイズできます。
### GroupDocs.Conversion for .NET のテクニカル サポートは受けられますか?
はい、GroupDocsはGroupDocs.Conversion for .NETを含む製品について包括的なテクニカルサポートを提供しています。 [サポートフォーラム](https://forum.groupdocs.com/c/conversion/11) ご質問や問題がございましたら、