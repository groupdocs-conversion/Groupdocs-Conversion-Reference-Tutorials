---
title: CDR ベクター グラフィックスを PDF に変換
linktitle: CDR ベクター グラフィックスを PDF に変換
second_title: GroupDocs.Conversion .NET API
description: GroupDocs.Conversion for .NET を使用して、CorelDRAW (CDR) ベクター グラフィック ファイルを PDF 形式に簡単に変換します。ドキュメントの変換プロセスを合理化します。
weight: 12
url: /ja/net/file-conversion-to-pdf/convert-cdr-to-pdf/
---
## 導入
GroupDocs.Conversion for .NET は、開発者がさまざまなドキュメント形式を PDF、Word、HTML などにシームレスに変換できる強力なドキュメント変換ライブラリです。このチュートリアルでは、GroupDocs.Conversion for .NET を使用して CorelDRAW (CDR) ベクター グラフィックス ファイルを PDF 形式に変換することに焦点を当てます。このガイドを終えると、.NET アプリケーションでこの変換を簡単に実行するための知識が身につくでしょう。
## 前提条件
変換プロセスに入る前に、次の前提条件が設定されていることを確認してください。
### GroupDocs.Conversion for .NET をインストールする
開始するには、GroupDocs.Conversion for .NET をダウンロードしてインストールする必要があります。ライブラリはからダウンロードできます。[ダウンロードページ](https://releases.groupdocs.com/conversion/net/).
### ライセンスを取得する
グループドキュメント.Conversion for .NET の可能性を最大限に活用するには、有効なライセンスが必要です。からライセンスを取得できます[GroupDocs](https://purchase.groupdocs.com/buy)またはテスト目的で一時ライセンスをリクエストする[ここ](https://purchase.groupdocs.com/temporary-license/).

## 名前空間のインポート
GroupDocs.Conversion 機能を利用するために、.NET プロジェクトに必要な名前空間がインポートされていることを確認してください。その方法は次のとおりです。
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## ステップ 1: 出力フォルダーとファイル名を定義する
まず、変換した PDF ファイルを保存する出力フォルダーと任意のファイル名を指定します。
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "cdr-converted-to.pdf");
```
必ず交換してください`"Your Document Directory"`目的の出力フォルダーへのパスを置き換えます。
## ステップ 2: ソース CDR ファイルをロードする
次に、GroupDocs.Conversion を使用して、PDF に変換するソース CDR ファイルを読み込みます。
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_CDR))
{
    //変換ロジックがここに入ります
}
```
交換する`Constants.SAMPLE_CDR`実際の CDR ファイルへのパスを置き換えます。
## ステップ 3: 変換オプションを指定する
出力形式 (PDF) や追加設定の指定など、変換オプションを定義します。
```csharp
var options = new PdfConvertOptions();
```
要件に応じて変換オプションをカスタマイズできます。
## ステップ 4: 変換を実行する
オプションを指定して変換処理を実行します。
```csharp
converter.Convert(outputFile, options);
```
このコマンドは、CDR ファイルを PDF に変換し、指定されたファイル名で指定された出力フォルダーに保存します。
## ステップ 5: 変換の完了を確認する
最後に、変換プロセスが正常に完了したことを確認するメッセージを表示します。
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```
このメッセージは、変換された PDF ファイルの保存場所を通知します。

## 結論
このチュートリアルでは、GroupDocs.Conversion for .NET を使用して CorelDRAW (CDR) ベクター グラフィック ファイルを PDF 形式に変換する方法を学習しました。概要を示した手順に従うことで、ドキュメント変換機能を .NET アプリケーションにシームレスに統合し、その機能と使いやすさを向上させることができます。
## よくある質問
### GroupDocs.Conversion for .NET は、CorelDRAW ファイルのすべてのバージョンと互換性がありますか?
GroupDocs.Conversion for .NET は、幅広い CorelDRAW バージョンをサポートし、ほとんどの CDR ファイルとの互換性を保証します。
### GroupDocs.Conversion for .NET を使用して複数の CDR ファイルを同時に変換できますか?
はい、GroupDocs.Conversion for .NET を使用して複数の CDR ファイルを PDF またはその他の形式にバッチ変換でき、効率と生産性が向上します。
### GroupDocs.Conversion for .NET では、ドキュメントの変換にインターネット接続が必要ですか?
いいえ、GroupDocs.Conversion for .NET はドキュメント変換をマシン上でローカルに実行するため、変換プロセス中にインターネット接続は必要ありません。
### 特定の要件に応じて変換設定をカスタマイズできますか?
はい。GroupDocs.Conversion for .NET には広範なカスタマイズ オプションが用意されており、ニーズに合わせて変換プロセスを調整できます。
### GroupDocs.Conversion for .NET のテクニカル サポートは利用できますか?
はい、GroupDocs は、GroupDocs.Conversion for .NET を含む自社製品の包括的な技術サポートを提供しています。次の機関に支援を求めることができます。[サポートフォーラム](https://forum.groupdocs.com/c/conversion/11)ご質問や問題がございましたら。