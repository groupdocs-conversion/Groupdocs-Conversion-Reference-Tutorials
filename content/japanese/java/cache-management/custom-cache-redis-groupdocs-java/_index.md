---
date: '2026-10-21'
description: シンプルなJavaプロジェクトで、cache key Javaの作成方法とRedisをGroupDocs.Conversionと統合して、レンダリング性能を向上させ、変換時間を短縮し、TTLを設定する方法を学びます。
images:
- /java/cache-management/custom-cache-redis-groupdocs-java/og-image.png
keywords:
- create cache key java
- java redis caching
- groupdocs conversion cache
- redis ttl java
lastmod: '2026-10-21'
og_description: このステップバイステップガイドでは、cache key Javaの作成方法とRedisをGroupDocs.Conversionと統合してdocument
  bytesをキャッシュし、レンダリング性能を向上させ、変換時間を短縮する方法を示します。TTLを設定し、速度向上を測定します。
og_image_alt: 'Developer guide: create cache key Java using Redis and GroupDocs'
og_title: Javaでキャッシュキーを作成 – RedisとGroupDocsでドキュメントをキャッシュ
schemas:
- author: GroupDocs
  dateModified: '2026-10-21'
  description: Learn how to create cache key Java and integrate Redis with GroupDocs.Conversion
    to boost rendering performance, reduce conversion time, and configure TTLs.
  headline: Create cache key Java – cache docs with Redis and GroupDocs
  type: TechArticle
- description: Learn how to create cache key Java and integrate Redis with GroupDocs.Conversion
    to boost rendering performance, reduce conversion time, and configure TTLs.
  name: Create cache key Java – cache docs with Redis and GroupDocs
  steps:
  - name: '**High‑traffic portals** – Serve frequently requested PDFs (catalogs, whitepapers)
      instantly.'
    text: '**High‑traffic portals** – Serve frequently requested PDFs (catalogs, whitepapers)
      instantly.'
  - name: '**Enterprise DMS** – Reduce load when users repeatedly view the same contracts
      or policy documents.'
    text: '**Enterprise DMS** – Reduce load when users repeatedly view the same contracts
      or policy documents.'
  - name: '**E‑commerce** – Cache generated invoices or product catalogs to speed
      up checkout.'
    text: '**E‑commerce** – Cache generated invoices or product catalogs to speed
      up checkout.'
  - name: '**Learning platforms** – Deliver lecture notes and e‑books without re‑rendering
      on every student request.'
    text: '**Learning platforms** – Deliver lecture notes and e‑books without re‑rendering
      on every student request.'
  - name: '**Legal services** – Accelerate distribution of case files while keeping
      storage costs low.'
    text: '**Legal services** – Accelerate distribution of case files while keeping
      storage costs low.'
  type: HowTo
- questions:
  - answer: Absolutely. The same caching pattern works for DOCX, HTML, images, and
      more – just change the `ConvertOptions` type.
    question: Can I use this approach with other GroupDocs output formats?
  - answer: Combine the source file path, conversion options, and any version identifiers.
      This guarantees uniqueness per configuration.
    question: How do I choose a good cache key?
  - answer: Invalidate the cache manually (e.g., delete the key) or use a shorter
      TTL so stale data expires quickly.
    question: What if a document changes after it’s cached?
  - answer: No, but Redis offers low latency, built‑in TTL, and wide Java client support,
      making it a popular choice for this scenario.
    question: Is Redis the only option for caching?
  - answer: Minimal. The heavy lifting is done by Redis; the app only holds short‑lived
      connections via Jedis.
    question: Does this increase memory usage on the application server?
  type: FAQPage
tags:
- create cache key java
- java redis cache
- groupdocs conversion
- document rendering
title: Javaでキャッシュキーを作成 – RedisでJavaのドキュメントをキャッシュ
type: docs
url: /ja/java/cache-management/custom-cache-redis-groupdocs-java/
weight: 1
---

# Javaでキャッシュキーを作成 – RedisでJavaのドキュメントをキャッシュ

モダンなウェブアプリケーションでは、同じ変換済みドキュメントを繰り返し提供することは CPU サイクルの無駄遣いとなり、応答時間を伸ばす原因となります。**Javaでキャッシュキーを作成**することで、変換結果を一度保存し、以降のリクエストで瞬時に取得できるようになります。このチュートリアルでは、Redis を GroupDocs.Conversion のワークフローに組み込み、信頼性の高いキャッシュキーを生成し、TTL を設定し、期待できるパフォーマンス向上を測定する方法を示します。

## クイック回答
- **このチュートリアルでカバーする内容は？** Redis と GroupDocs.Conversion を統合した完全な Java Redis キャッシュチュートリアルです。  
- **Redis を使用する理由は？** ミリ秒未満のレイテンシを提供し、TTL の有効期限をサポートし、複数のアプリインスタンスにまたがって水平スケーリングできます。  
- **GroupDocs のライセンスは必要ですか？** テストにはトライアルまたは一時ライセンスで問題ありませんが、本番環境ではフルライセンスが必要です。  
- **主な手順は何ですか？** Maven 依存関係を追加し、`JedisPool` を設定し、キャッシュヘルパーメソッドを作成し、キャッシュを変換パイプラインに組み込みます。  
- **サポートされている Java バージョンは？** Java 8 以上（最新の GroupDocs.Conversion リリースと互換性あり）。

## Redis を使用したドキュメントのキャッシュとは？
Redis を使用したドキュメントのキャッシュとは、変換のバイナリ出力（例: PDF バイト配列）を Redis に永続化し、同一の将来のリクエストがキャッシュされたバイトを取得できるようにすることです。これにより、冗長な CPU 作業が排除され、ネットワーク帯域が削減され、エンドユーザー体験がスムーズになります。

## なぜ Java で Redis キャッシュを実装するのか？
ドキュメントを一度読み込み、結果を保存し、再リクエスト時に瞬時に提供することで、頻繁にアクセスされるファイルの変換時間を最大 **90 %** 短縮し、CPU 使用率を削減してインフラコストを低減し、クラスタ環境のすべてのアプリケーションノードで **単一の真実の情報源** を提供できます。Redis は単一ノードで 1 秒あたり 200 k 超の操作を処理でき、ミリ秒未満の検索を保証します。

## 前提条件
- **GroupDocs.Conversion** – バージョン 25.2 以上（**120+** の入力・出力フォーマットをサポート）。  
- **Jedis**（Java 用公式 Redis クライアント）。  
- 稼働中の Redis インスタンス（ローカル開発ではデフォルトの `localhost:6379` を使用可能）。  
- 依存関係管理のための Maven。  
- Java の例外処理と I/O ストリームに関する基本的な知識。

## Java 用 GroupDocs.Conversion の設定

`GroupDocs.Conversion` は、レイアウト保持、フォント埋め込み、画像抽出を自動的に処理しながら、ドキュメントを幅広いフォーマットに変換・レンダリングする Java ライブラリです。

Add the GroupDocs repository and dependency to your `pom.xml`:

```xml
<repositories>
    <repository>
        <id>groupdocs-maven</id>
        <url>https://repo.groupdocs.com/maven</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-conversion</artifactId>
        <version>25.2.0</version>
    </dependency>
    <dependency>
        <groupId>redis.clients</groupId>
        <artifactId>jedis</artifactId>
        <version>4.2.3</version>
    </dependency>
</dependencies>
```

### ライセンス取得
**Free Trial** で開始し、評価用に **Temporary License** をリクエストするか、本番利用のためにフル **License** を購入できます。

Initialize GroupDocs.Conversion in your Java code:

```java
import com.groupdocs.conversion.*;

ConversionConfig config = new ConversionConfig();
config.setLicensePath("path/to/license/file.lic");
ConversionApi conversionApi = new ConversionApi(config);
```

## 実装ガイド

### Redis を使用したカスタムキャッシュの作成

#### 概要
カスタム Redis キャッシュは、レンダリングされたドキュメントバイトを保持し、再リクエスト時に瞬時に取得できるようにします。

#### JedisPool の設定
`JedisPool` は、再利用可能な Redis 接続のスレッドセーフプールで、ソケットオーバーヘッドを最小化し、スループットを向上させます。

```java
import redis.clients.jedis.JedisPool;
import redis.clients.jedis.JedisPoolConfig;

JedisPoolConfig poolConfig = new JedisPoolConfig();
poolConfig.setMaxTotal(20);               // maximum active connections
poolConfig.setMaxIdle(10);                // maximum idle connections
poolConfig.setMinIdle(2);                 // minimum idle connections
JedisPool jedisPool = new JedisPool(poolConfig, "localhost", 6379);
```

#### キャッシュデータの保存と取得
以下のヘルパーメソッドは、バイト配列を安全に保存できる Base64 文字列にシリアライズし、再びバイト配列に復元します。

```java
import java.util.Base64;
import redis.clients.jedis.Jedis;

public class RedisCacheHelper {

    private final JedisPool pool;
    private final int ttlSeconds; // time‑to‑live for cached entries

    public RedisCacheHelper(JedisPool pool, int ttlSeconds) {
        this.pool = pool;
        this.ttlSeconds = ttlSeconds;
    }

    public void put(String key, byte[] data) {
        try (Jedis jedis = pool.getResource()) {
            String encoded = Base64.getEncoder().encodeToString(data);
            jedis.setex(key, ttlSeconds, encoded); // configure redis ttl
        }
    }

    public byte[] get(String key) {
        try (Jedis jedis = pool.getResource()) {
            String encoded = jedis.get(key);
            return encoded != null ? Base64.getDecoder().decode(encoded) : null;
        }
    }
}
```

#### GroupDocs.Conversion との統合
これでキャッシュを変換ワークフローに組み込みます。メソッドはまずキャッシュを確認し、ヒットしなければ変換を実行し、結果を保存してバイトを返します。

```java
import com.groupdocs.conversion.options.convertoptions.PdfConvertOptions;

public class DocumentService {

    private final ConversionApi conversionApi;
    private final RedisCacheHelper cacheHelper;

    public DocumentService(ConversionApi conversionApi, RedisCacheHelper cacheHelper) {
        this.conversionApi = conversionApi;
        this.cacheHelper = cacheHelper;
    }

    public byte[] convertToPdf(String sourcePath, PdfConvertOptions options) throws Exception {
        // Build a deterministic cache key
        String cacheKey = "pdf:" + sourcePath + ":" + options.hashCode();

        // Attempt to fetch from Redis
        byte[] cached = cacheHelper.get(cacheKey);
        if (cached != null) {
            // Cache hit – return stored bytes
            return cached;
        }

        // Cache miss – perform conversion
        byte[] result = conversionApi.convert(sourcePath, options).toByteArray();

        // Store result for future calls
        cacheHelper.put(cacheKey, result);
        return result;
    }
}
```

## Redis キャッシュ用の Java キャッシュキーの作成方法は？
ソースファイルパス、選択した `ConvertOptions` の値、任意のバージョンタグを連結し、SHA‑256 でハッシュすることで決定的なキーを生成します。このキーは各変換設定を一意に識別し、同一リクエストはキャッシュにヒットし、異なるオプションは別エントリとして生成されます。

`ConversionApi` クラスは GroupDocs.Conversion の中心コンポーネントで、ドキュメント変換を実行します。キャッシュキーを作成し Redis で検索し、キーが存在しない場合にのみ `ConversionApi.convert` を呼び出すことで、変換時間とサーバー負荷を大幅に削減できます。

## Java で Redis キャッシュを実装する方法は？
`ConversionApi` は GroupDocs.Conversion の主要クラスで、ドキュメント変換操作を実行します。ソースドキュメントをロードし、決定的なキャッシュキーを生成し、Redis で検索し、キーが存在しない場合にのみ `ConversionApi` を呼び出します。このパターンにより、各ユニークな変換は一度だけ実行され、設定された TTL の間キャッシュから提供されます。

## トラブルシューティングのヒント
- Redis サーバーに接続できることを確認します（`redis-cli ping` が `PONG` を返すはずです）。  
- `JedisPool` のホストとポートが Redis デプロイと一致していることを確認してください。  
- キャッシュ呼び出しを try‑catch ブロックでラップし、接続障害が発生しても変換フローが中断しないようにします。  
- Redis のメモリを監視（`INFO memory`）し、`maxmemory` ポリシー（例: `volatile-lru`）を設定して古いエントリを適切に削除します。  
- JVM で `OutOfMemoryError` が発生した場合は、ヒープサイズを増やすか `-XX:+UseCompressedOops` を有効にしてください。

## 実用的な適用例

1. **高トラフィックポータル** – 頻繁にリクエストされる PDF（カタログ、ホワイトペーパー）を瞬時に提供。  
2. **エンタープライズ DMS** – ユーザーが同じ契約書やポリシードキュメントを繰り返し閲覧する際の負荷を軽減。  
3. **Eコマース** – 生成された請求書や商品カタログをキャッシュし、チェックアウトを高速化。  
4. **学習プラットフォーム** – 講義ノートや電子書籍を、学生ごとのリクエストごとに再レンダリングせずに提供。  
5. **法務サービス** – ケースファイルの配布を高速化し、ストレージコストを低減。

## パフォーマンス上の考慮点

- **Redis のチューニング** – `maxmemory` を調整し、`allkeys-lru` などのエビクションポリシーを選択し、トラフィックパターンに応じて適切な `timeout` 値を設定します。  
- **キャッシュヒット/ミス率の追跡** – `INFO stats` または Redis の `keyspace_hits` / `keyspace_misses` カウンタを使用して TTL を微調整します。  
- **JVM ヒープサイズ** – ヒープが GroupDocs のバッファを収容できるようにします。目安として、同時変換ペイロード 100 MB あたり 1 GB のヒープが推奨されます。  
- **バッチ変換** – 多数のファイルを変換する際は、スレッドごとに単一の `Jedis` インスタンスを再利用してソケットの負荷を最小化します。

## よくある質問

**Q: このアプローチを他の GroupDocs 出力フォーマットでも使用できますか？**  
A: もちろんです。同じキャッシュパターンは DOCX、HTML、画像などにも適用でき、`ConvertOptions` の型を変更するだけです。

**Q: 良いキャッシュキーの選び方は？**  
A: ソースファイルパス、変換オプション、バージョン識別子を組み合わせます。これにより構成ごとの一意性が保証されます。

**Q: キャッシュ後にドキュメントが変更された場合は？**  
A: キーを手動で削除する（例: キーを削除）か、短い TTL を設定して古いデータがすぐに期限切れになるようにします。

**Q: キャッシュに Redis だけが唯一の選択肢ですか？**  
A: いいえ、他のオプションもありますが、Redis は低レイテンシ、組み込み TTL、豊富な Java クライアントサポートを提供するため、このシナリオで人気があります。

**Q: これによりアプリケーションサーバーのメモリ使用量は増えますか？**  
A: 最小限です。重い処理は Redis が担当し、アプリは Jedis 経由の短命接続だけを保持します。

## 結論
これで、Redis と GroupDocs.Conversion を使用してドキュメントをキャッシュする完全な **java redis caching** チュートリアルが完成しました。レンダリング結果を Redis に永続化することで、**レンダリング性能が向上**し、**変換時間が短縮**され、エンドユーザーによりスムーズな体験を提供できます。さまざまな TTL 値を試し、キャッシュ指標を監視し、アプリケーションの成長に合わせて他のドキュメント形式にもパターンを拡張してください。

---

**最終更新日:** 2026-10-21  
**テスト環境:** GroupDocs.Conversion 25.2, Jedis 4.2.3  
**作者:** GroupDocs

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

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.convert.PdfConvertOptions;

public class DocumentConversion {
    public static void main(String[] args) {
        // Initialize the Converter with a document path
        Converter converter = new Converter("input.docx");
        
        // Set up conversion options for PDF
        PdfConvertOptions options = new PdfConvertOptions();
        converter.convert("output.pdf", options);
    }
}
```

```java
import redis.clients.jedis.JedisPool;

public class CacheManager {
    private static JedisPool jedisPool = new JedisPool("localhost", 6379);
    
    public static void main(String[] args) {
        // Additional cache setup code here
    }
}
```

```java
import redis.clients.jedis.Jedis;

public class CacheManager {

    public static void storeDocument(String key, String documentContent) {
        try (Jedis jedis = jedisPool.getResource()) {
            // Set the content in Redis cache with an expiration time of one hour
            jedis.setex(key, 3600, documentContent);
        }
    }

    public static String retrieveDocument(String key) {
        try (Jedis jedis = jedisPool.getResource()) {
            return jedis.get(key); // Retrieve cached content if available
        }
    }
}
```

```java
public class DocumentConversion {

    public static void convertWithCache(String inputPath, String outputPath) {
        Converter converter = new Converter(inputPath);
        PdfConvertOptions options = new PdfConvertOptions();

        // Generate a cache key based on the document path and conversion settings
        String cacheKey = "doc:" + inputPath;

        // Check if the converted document is already cached
        String cachedDocument = CacheManager.retrieveDocument(cacheKey);

        if (cachedDocument != null) {
            System.out.println("Using cached version of the document.");
            // Save cached content to output file
            Files.write(Paths.get(outputPath), cachedDocument.getBytes());
        } else {
            // Perform conversion and cache the result
            converter.convert(output -> {
                String documentContent = new String(output.toByteArray());
                CacheManager.storeDocument(cacheKey, documentContent);
                Files.write(Paths.get(outputPath), output.toByteArray());
            }, options);
        }
    }

    public static void main(String[] args) {
        convertWithCache("input.docx", "output.pdf");
    }
}
```

## 関連チュートリアル

- [カスタムキャッシュ Java の実装 – GroupDocs Conversion キャッシュ](/conversion/java/cache-management/)
- [Java と GroupDocs.Conversion で Redis キャッシュを使用する方法](/conversion/java/cache-management/redis-cache-java-groupdocs-conversion-guide/)
- [Java と GroupDocs.Conversion でファイルをキャッシュする方法 – 効率的なドキュメント変換のための包括的ガイド](/conversion/java/cache-management/implement-java-file-caching-groupdocs-conversion-guide/)
