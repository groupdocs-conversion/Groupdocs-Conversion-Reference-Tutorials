---
"date": "2025-04-28"
"description": "GroupDocs.Conversion for Javaを使用して、パスワードで保護されたWord文書をPDFに変換する方法を学びます。ページの指定、DPIの調整、コンテンツの回転をマスターしましょう。"
"title": "GroupDocs.Conversion を使用して Java でパスワード保護された Word を PDF に変換する"
"url": "/ja/java/security-protection/convert-password-protected-word-pdf-java/"
"weight": 1
type: docs
---
# GroupDocs.Conversion を使用して Java でパスワード保護された Word を PDF に変換する

JavaでGroupDocs.Conversionライブラリを活用するための包括的なガイドで、保護されたWord文書を簡単にPDF形式に変換できます。特定のページを指定したり、カスタムサイズを設定したり、解像度を調整したり、パフォーマンスを最適化してシームレスなドキュメント変換を実現する方法を学びましょう。

## 学習内容:
- GroupDocs.Conversion for Java を使用して、パスワードで保護された Word ファイルを変換します。
- PDF 変換するドキュメントの正確なページまたはセクションを指定します。
- PDF に変換する前にドキュメントの内容を回転します。
- PDF 変換中にカスタム解像度の DPI 設定を調整します。
- Java メモリ管理のベスト プラクティスを使用してパフォーマンスを向上させます。

## 前提条件
続行する前に、次の前提条件が満たされていることを確認してください。

### 必要なライブラリと依存関係
GroupDocs.Conversionを使用するには、必要なライブラリをインクルードしてください。Mavenを使用する場合は、リポジトリと依存関係を `pom.xml`：

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

### 環境設定
お使いのマシンにJava開発キット（JDK）がインストールされ、設定されていることを確認してください。Javaプログラミングの基礎知識があることが推奨されます。

### ライセンス取得
GroupDocs.Conversionは、機能のテスト用に無料トライアル版を提供しています。長期間ご利用いただくには、一時ライセンスまたはフルライセンスのご購入をご検討ください。 [GroupDocs購入](https://purchase。groupdocs.com/buy).

## Java 用の GroupDocs.Conversion の設定
GroupDocs.Conversion を開始するには、プロジェクトでいくつかの初期設定を実行します。

### Mavenのセットアップ
必要なライブラリがすべてダウンロードされ、使用可能であることを確認するために、前述の必要な Maven 依存関係を含めます。

### 基本的な初期化
GroupDocs.Conversionのインスタンスを作成して初期化します。 `Converter` クラス。基本的な設定は次のとおりです。

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.load.WordProcessingLoadOptions;

WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
// 必要に応じて、保護されたドキュメントにパスワードを設定します。
loadOptions.setPassword("your_password_here");

Converter converter = new Converter("path_to_your_document.docx", () -> loadOptions);
```

このスニペットはドキュメントの変換を初期化します。 `loadOptions` クラスは、パスワード保護やその他の設定の管理に役立ちます。

## 実装ガイド
Java で GroupDocs.Conversion を使用して主要な機能を実装する方法を見てみましょう。

### パスワードで保護された文書をPDFに変換する
**概要：**
パスワードで保護された Word 文書をシームレスに PDF ファイルに変換します。

#### ステップバイステップの実装
##### パスワードを使用してロードオプションを初期化する
保護されたドキュメントにアクセスするためのパスワードを設定します。

```java
WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
loadOptions.setPassword("12345"); // 実際のパスワードに置き換えてください。
```

##### コンバーターの設定と変換
初期化する `Converter` クラスを作成し、PDF 変換オプションを定義して変換を実行します。

```java
import com.groupdocs.conversion.options.convert.PdfConvertOptions;

String convertedFile = "YOUR_OUTPUT_DIRECTORY/ConvertedDocument.pdf";
PdfConvertOptions options = new PdfConvertOptions();

Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/SampleProtectedDocx.docx", () -> loadOptions);
converter.convert(convertedFile, options);
```

**説明：**
その `loadOptions` オブジェクトはパスワードで保護されたドキュメントを扱う上で非常に重要です。パスワードを正しく設定することで、アクセスと変換が確実に行えます。

#### トラブルシューティングのヒント
- パスワードの正確さを再確認してください。入力ミスはよくある問題です。
- ファイルパスを確認して防止する `FileNotFoundException`。

### PDFに変換するページを指定する
**概要：**
PDF 変換するドキュメントの特定のページを選択します。

#### ステップバイステップの実装
##### ページ範囲の設定
変換するページを定義します。

```java
PdfConvertOptions options = new PdfConvertOptions();
options.setPageNumber(2); // 2ページ目から始めてください。
options.setPagesCount(1); // 1 ページのみ変換します。
```

##### 変換プロセス
指定されたセットアップを使用する `options` 変換用:

```java
String convertedFile = "YOUR_OUTPUT_DIRECTORY/SelectedPagesPdf.pdf";
Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/SampleDocx.docx", () -> loadOptions);
converter.convert(convertedFile, options);
```

**説明：**
その `setPageNumber()` そして `setPagesCount()` メソッドを使用すると、どのドキュメントセクションを変換するかを正確に制御できます。

### PDF変換でページを回転する
**概要：**
変換中にページを回転して、希望の方向を実現します。

#### ステップバイステップの実装
##### 回転オプションの設定
回転設定を指定します:

```java
import com.groupdocs.conversion.options.convert.Rotation;

PdfConvertOptions options = new PdfConvertOptions();
options.setRotate(Rotation.On180); // ページを180度回転します。
```

##### 変換を実行
指定された回転オプションで初期化して変換します。

```java
String convertedFile = "YOUR_OUTPUT_DIRECTORY/RotatedPagesPdf.pdf";
Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/SampleDocx.docx", () -> loadOptions);
converter.convert(convertedFile, options);
```

**説明：**
ページを回転すると、向きを修正したり、特定のレイアウト要件を満たしたりするのに役立ちます。

### PDF変換のDpiを設定する
**概要：**
品質のニーズに合わせて、変換した PDF の解像度 (DPI) を調整します。

#### ステップバイステップの実装
##### DPI設定を構成する
希望する DPI 値を設定します。

```java
PdfConvertOptions options = new PdfConvertOptions();
options.setDpi(300); // 高解像度にするには、DPI を 300 に設定します。
```

##### カスタムDPIで変換を実行する
次の設定を使用して変換を続行します。

```java
String convertedFile = "YOUR_OUTPUT_DIRECTORY/HighResolutionPdf.pdf";
Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/SampleDocx.docx", () -> loadOptions);
converter.convert(convertedFile, options);
```

**説明：**
DPI値を高くすると画質は向上しますが、ファイルサイズが大きくなる可能性があります。必要に応じて調整してください。

### PDF変換の幅と高さを設定する
**概要：**
変換中に生成される PDF のサイズをカスタマイズします。

#### ステップバイステップの実装
##### ディメンションを定義する
幅と高さのパラメータを設定します。

```java
PdfConvertOptions options = new PdfConvertOptions();
options.setWidth(1024); // 幅を1024ピクセルに設定します。
options.setHeight(768); // 高さを768ピクセルに設定します。
```

##### カスタムサイズで変換
次のディメンションを使用して変換を続行します。

```java
String convertedFile = "YOUR_OUTPUT_DIRECTORY/SizedPdf.pdf";
Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/SampleDocx.docx", () -> loadOptions);
converter.convert(convertedFile, options);
```

**説明：**
寸法をカスタマイズすると、出力 PDF を特定の表示または印刷要件に合わせて調整できます。