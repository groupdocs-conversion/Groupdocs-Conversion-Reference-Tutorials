---
date: '2026-09-25'
description: GroupDocs.Conversion を使用して eml を pdf に変換し、タイムゾーンオフセットを適用して正しいタイムスタンプを保持する方法を学びます。Java
  開発者向けのステップバイステップガイドです。
keywords:
- convert eml to pdf java
- email to pdf conversion
- timezone offset java
lastmod: '2026-09-25'
og_description: GroupDocs.Conversion を使用して eml を pdf に変換し、タイムゾーンオフセットを適用して正しいタイムスタンプを保持する方法を学びます。開発者向けの詳細な
  Java ガイドです。
og_image_alt: 'Java guide: convert eml to pdf with timezone offset using GroupDocs.Conversion'
og_title: GroupDocs を使用してタイムゾーンオフセット付きで eml を pdf に変換（Java）
schemas:
- author: GroupDocs
  dateModified: '2026-09-25'
  description: Learn how to convert eml to pdf java with GroupDocs.Conversion, applying
    a timezone offset to preserve correct timestamps. Step‑by‑step guide for Java
    developers.
  headline: How to convert eml to pdf java with timezone offset
  type: TechArticle
- description: Learn how to convert eml to pdf java with GroupDocs.Conversion, applying
    a timezone offset to preserve correct timestamps. Step‑by‑step guide for Java
    developers.
  name: How to convert eml to pdf java with timezone offset
  steps:
  - name: '**Libraries & dependencies**'
    text: '**Libraries & dependencies**'
  - name: '**Environment**'
    text: '**Environment**'
  - name: '**Knowledge**'
    text: '**Knowledge**'
  type: HowTo
- questions:
  - answer: It’s a powerful library that enables document conversion across dozens
      of formats, including email to PDF, with built‑in timezone handling.
    question: What is GroupDocs.Conversion for Java?
  - answer: Use `EmailLoadOptions.setTimeZoneOffset(milliseconds)` before initializing
      the `Converter`.
    question: How do I set the timezone offset for emails?
  - answer: Yes, the library supports `.eml`, `.msg`, and other common email file
      types.
    question: Can I convert multiple email formats with this setup?
  - answer: Missing dependencies, incorrect file paths, and providing the offset in
      the wrong unit (seconds vs. milliseconds).
    question: What are common pitfalls during conversion?
  - answer: Visit the [official documentation](https://docs.groupdocs.com/conversion/java/)
      for detailed guides and API references.
    question: Where can I find more resources on GroupDocs.Conversion?
  type: FAQPage
tags:
- convert eml
- GroupDocs.Conversion
- Java email conversion
- timezone offset
- PDF generation
title: タイムゾーンオフセットを使用して eml を pdf に変換する方法（Java）
type: docs
url: /ja/java/email-formats/email-to-pdf-conversion-java-groupdocs/
weight: 1
---

# eml を pdf java に変換する方法（タイムゾーンオフセット付き）

このチュートリアルでは、**convert eml to pdf java** を行い、タイムゾーンの差異に合わせてタイムスタンプを正しく調整する方法を紹介します。GroupDocs.Conversion for Java を使用して、Maven の設定からカスタムオフセットでメールを読み込み、結果の PDF ファイルをストリーミングするまでのエンドツーエンドのワークフローを完全に示します。この手順は、正確なローカル時間を示す信頼性の高いアーカイブ対応 PDF が必要な Java 8+ 開発者向けに書かれています。

## クイック回答

- **変換を処理するライブラリは何ですか？** GroupDocs.Conversion for Java.  
- **タイムゾーンを設定する主なメソッドはどれですか？** `EmailLoadOptions.setTimeZoneOffset`.  
- **ライセンスは必要ですか？** 無料トライアルでテストは可能ですが、本番環境ではフルライセンスが必要です。  
- **多数のメールをバッチ処理できますか？** はい—変換ループをバッチルーチンでラップします。  
- **必要な Java バージョンは何ですか？** JDK 8 以降。  

## convert eml to pdf java とは？

「convert eml to pdf java」というフレーズは、メールファイル（通常は `.eml` または `.msg`）を取得し、Java コードを使用して PDF ドキュメントを生成するプロセスを指します。この変換は、PDF がレイアウトを保持し、普遍的に閲覧可能であるため、アーカイブ、法的コンプライアンス、クロスプラットフォーム共有に不可欠です。

## なぜ GroupDocs.Conversion for Java を使用するのか？

GroupDocs.Conversion は、`.eml`、`.msg`、`.pdf`、`.docx`、画像タイプなど、**70 以上** の入力および出力フォーマットをサポートします。組み込みの `EmailLoadOptions` により、ミリ秒単位でタイムゾーンオフセットを指定でき、PDF のタイムスタンプが意図したローカル時間と一致することが保証されます。ライブラリはストリーミング方式でファイルを処理するため、ドキュメント全体を RAM にロードする場合と比較してメモリ使用量を最大 **80 %** 削減できます。

## 前提条件

開始する前に、以下が揃っていることを確認してください：

1. **ライブラリと依存関係**  
   - GroupDocs.Conversion for Java バージョン **25.2** 以降。  

2. **環境**  
   - JDK 8+ がインストールされ、マシン上で設定されていること。  
   - ビルド自動化ツールとして Maven を使用すること。  

3. **知識**  
   - 基本的な Java プログラミング、特にファイル I/O。  
   - Maven の `pom.xml` 構造に精通していること。  

## GroupDocs.Conversion for Java の設定

### インストール情報

`pom.xml` に GroupDocs リポジトリとコンバージョン依存関係を追加します：

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/conversion/java/</url>
   </repository>
</repositories>
<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-conversion</artifactId>
      <version>25.2</version>
   </dependency>
</dependencies>
```

### ライセンス取得

無料トライアルで開始するか、フル機能テスト用に一時ライセンスをリクエストできます：

- **Free trial** – ライブラリをダウンロードし、基本機能を試すことができます。  
- **Temporary license** – 一時ライセンスを申請するには、[temporary license page](https://purchase.groupdocs.com/temporary-license/) をご利用ください。  
- **Purchase** – 長期利用の場合は、[official site](https://purchase.groupdocs.com/buy) からライセンス購入をご検討ください。  

### 基本的な初期化

以下は、`Converter` インスタンスを作成し、タイムゾーンオフセット付きでメールをロードするために必要な最小限のコードです：

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.load.EmailLoadOptions;

// Initialize GroupDocs.Conversion with necessary load options for email files
EmailLoadOptions loadOptions = new EmailLoadOptions();
loadOptions.setTimeZoneOffset(7200000.0); // Set timezone offset in milliseconds (e.g., 2 hours)
```

## タイムゾーンオフセットの設定方法は？

`EmailLoadOptions` は、変換のためにメールファイルをロードする方法を制御する設定クラスです。変換前にカスタムオフセットでメールをロードします。`setTimeZoneOffset` メソッドはオフセットを **ミリ秒** 単位で受け取り、+2 時間のシフトは `7200000` に相当します。この調整により、生成された PDF の表示タイムスタンプが書き換えられます。オフセットを提供することで、ライブラリは送信・受信時間を再計算し、生成された PDF が受信者のローカルタイムゾーンを反映するようにします。これは、アーカイブされた通信を確認する多国籍チームに特に有用です。

```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
loadOptions.setTimeZoneOffset(7200000.0); // Set to 2 hours ahead (in milliseconds)
```

## Converter オブジェクトの初期化方法は？

`Converter` は、提供されたロードオプションを使用してドキュメント変換を実行するメインクラスです。ソースファイルパスと、事前に定義した `loadOptions` を供給するラムダを渡すことで `Converter` を作成します。これにより、タイムゾーン設定が変換プロセスに結び付けられます。ソースメールを読み込み、`EmailLoadOptions` 設定（タイムゾーンオフセットを含む）を適用し、PDF 生成用の出力ストリームを準備します。ラムダを使用することで、オプションが変換時に評価されるため、設定が異なる複数のファイルを処理する際に便利です。

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.convert.PdfConvertOptions;

String sourceFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.eml"; // Path to the email document.
String outputPattern = "YOUR_OUTPUT_DIRECTORY/ConvertEmailWithTimezoneOffset-%d.pdf";

List<OutputStream> streamPool = new ArrayList<>();
Converter converter = new Converter(sourceFilePath, () -> loadOptions);
PdfConvertOptions options = new PdfConvertOptions();
```

## 変換を実行し、PDF ページをストリーミングする方法は？

`PdfConvertOptions` は、ページサイズ、圧縮、画像品質など、PDF 出力の設定を指定します。`convert` メソッドを呼び出し、`PdfConvertOptions` インスタンスと各ページ用の出力ストリームを提供します。`try‑finally` ブロックにより、すべてのストリームが確実に閉じられ、リソースリークが防止されます。オプションを設定した後、`convert` メソッドはメールの各ページを反復処理し、PDF データを個別の出力ストリームに書き込みます。このアプローチにより、各ページが個別に処理・フラッシュされるため、大容量のメールでも効率的に扱え、メモリ消費を最小限に抑えられます。

```java
try {
    converter.convert((SaveDocumentStreamForFileType) t -> {
        try {
            OutputStream outputStream = Files.newOutputStream(Paths.get(String.format(outputPattern, streamPool.size())));
            streamPool.add(outputStream);
            return outputStream;
        } catch (IOException e) {
            throw new RuntimeException(e);
        }
    }, options);
} finally {
    for (OutputStream outputStream : streamPool) {
        if (outputStream != null) {
            outputStream.close();
        }
    }
}
```

## 実用的な活用例

- **Archiving emails** – 法的または監査目的で正確なタイムスタンプ付きの PDF を保存します。  
- **Cross‑timezone collaboration** – 世界中のチームが変換されたドキュメントで同じローカル時間を見ることができます。  
- **Email reporting** – コンプライアンスのために元の送受信時間を保持した PDF レポートを生成します。

このワークフローは CRM システム、ドキュメント管理プラットフォーム、または自動バッチジョブに組み込んで、ドキュメントパイプラインを効率化できます。

## パフォーマンス上の考慮点

- **Resource management** – （示したように）ストリームを速やかに閉じてメモリを解放します。  
- **Batch processing** – `.eml` ファイルのコレクションをループし、可能な限り単一の `Converter` インスタンスを再利用します。  
- **JVM tuning** – 大規模バッチ向けにヒープサイズ（`-Xmx`）を調整し、`OutOfMemoryError` を回避します。  

## よくある問題と解決策

| 症状 | 考えられる原因 | 対策 |
|------|----------------|------|
| `NullPointerException` at `loadOptions` | ロードオプションが正しく渡されていない | `Converter` 作成時にラムダ `() -> loadOptions` が使用されていることを確認してください。 |
| PDF 出力が空白 | 入力ファイルパスが間違っている、またはファイルが存在しない | `sourceFilePath` が既存の `.eml` ファイルを指していることを確認してください。 |
| タイムゾーンが反映されない | オフセット値が誤っている（例：ミリ秒ではなく秒） | **ミリ秒** 単位でオフセットを提供する（例：+2 h の場合は `7200000`）。 |

## よくある質問

**Q: GroupDocs.Conversion for Java とは何ですか？**  
A: メールから PDF への変換を含む数十のフォーマット間でドキュメント変換を実現する強力なライブラリで、タイムゾーン処理が組み込まれています。

**Q: メールのタイムゾーンオフセットはどう設定しますか？**  
A: `Converter` を初期化する前に `EmailLoadOptions.setTimeZoneOffset(milliseconds)` を使用します。

**Q: この設定で複数のメール形式を変換できますか？**  
A: はい、ライブラリは `.eml`、`.msg`、その他の一般的なメールファイル形式をサポートしています。

**Q: 変換時の一般的な落とし穴は何ですか？**  
A: 依存関係の欠如、ファイルパスの誤り、オフセットを誤った単位（秒 vs ミリ秒）で提供することです。

**Q: GroupDocs.Conversion のリソースはどこで見つけられますか？**  
A: 詳細なガイドと API リファレンスについては、[official documentation](https://docs.groupdocs.com/conversion/java/) をご覧ください。

## 追加リソース

- **Documentation**: 詳細は [GroupDocs Documentation](https://docs.groupdocs.com/conversion/java/) をご覧ください。  
- **API reference**: 詳細な API リファレンスは [API reference](https://reference.groupdocs.com/conversion/java/) で入手できます。  
- **Download GroupDocs.Conversion**: ライブラリの開始は [GroupDocs.Conversion download page](https://releases.groupdocs.com/conversion/java/) から。  
- **Purchase**: 長期利用の場合は、[GroupDocs Purchase Page](https://purchase.groupdocs.com/buy) でライセンスを購入してください。  
- **Free trial & license**: 無料で試すか、[GroupDocs Free Trial](https://releases.groupdocs.com/conversion/java/) と [Temporary License](https://purchase.groupdocs.com/temporary-license/) で一時ライセンスをリクエストしてください。  
- **Support**: サポートが必要な場合は、[GroupDocs Forum](https://forum.groupdocs.com/c/conversion/10) をご利用ください。  

Java アプリケーションで GroupDocs.Conversion の力を活用し、正確でタイムゾーン対応の PDF 変換を今すぐ体験してください！

---

**最終更新:** 2026-09-25  
**テスト環境:** GroupDocs.Conversion 25.2  
**作成者:** GroupDocs

## 関連チュートリアル

- [msg to pdf java – GroupDocs を使用したメール形式の変換](/conversion/java/email-formats/)
- [eml to pdf java – GroupDocs でメールを PDF に変換](/conversion/java/pdf-conversion/convert-emails-to-pdfs-groupdocs-java/)
- [GroupDocs.Conversion Java で複数ファイルタイプを変換 – マスターガイド](/conversion/java/document-operations/groupdocs-conversion-java-master-document-conversion/)