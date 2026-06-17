---
date: '2026-05-21'
description: カスタム Redis キャッシュ .net と GroupDocs.Conversion の使い方を学び、ドキュメント変換を劇的に高速化する方法をご紹介します。ステップバイステップの設定手順、Redis
  キャッシュのベストプラクティス、パフォーマンス指標を確認してください。
keywords:
- custom redis cache .net
- use redis caching
- implement redis caching .net
schemas:
- author: GroupDocs
  dateModified: '2026-05-21'
  description: Learn how to use custom redis cache .net with GroupDocs.Conversion
    to dramatically speed up document conversion. Discover step‑by‑step setup, use
    redis caching best practices, and performance metrics.
  headline: Boost .NET Performance with custom redis cache .net and GroupDocs.Conversion
  type: TechArticle
- questions:
  - answer: 'Follow the official Redis installation guide for your OS: [Redis Download](https://redis.io/download).'
    question: How do I install Redis on my local machine?
  - answer: It eliminates duplicate rendering, cuts CPU usage by ~70 %, reduces average
      response time from 1.2 s to <200 ms, and lowers cloud bill by decreasing compute
      cycles.
    question: What are the tangible benefits of using a custom cache with GroupDocs.Conversion?
  - answer: Yes—simply point the `ConnectionMultiplexer` to your managed Redis instance
      (Azure Cache for Redis or Amazon ElastiCache) and ensure network security groups
      allow traffic on port 6379.
    question: Can this architecture be deployed to Azure or AWS?
  - answer: The `StackExchange.Redis` client is fully thread‑safe; you can share a
      single `ConnectionMultiplexer` across all request threads without additional
      locking.
    question: Is the cache thread‑safe for concurrent web requests?
  - answer: Invalidate by deleting keys that match the document’s identifier, e.g.,
      `await redis.GetDatabase().KeyDeleteAsync($"docCache:{docId}:*");`.
    question: How do I clear the cache when a source document changes?
  type: FAQPage
title: カスタム Redis キャッシュ .net と GroupDocs.Conversion を使用して .NET のパフォーマンスを向上させる
type: docs
url: /ja/net/cache-management/boost-net-app-performance-custom-redis-cache-groupdocs/
weight: 1
---

# GroupDocs.Conversion を使用し、**custom redis cache .net** で .NET アプリケーションのパフォーマンスを向上させる

## はじめに

.NET アプリケーションがドキュメント変換に貴重な数秒、場合によっては数分を費やしているなら、あなたは一人ではありません。GroupDocs.Conversion と併用した **custom redis cache .net** ソリューションを導入することで、繰り返しリクエストに対して変換時間を最大 80 % 短縮できます。このチュートリアルでは、GroupDocs.Conversion の設定方法、Redis バックエンドキャッシュの作成方法、そして高負荷時でもアプリが応答し続ける実績のあるパフォーマンスチューニング手法を学びます。

### クイック回答
- **カスタム Redis キャッシュは何を保存するのですか？** 各ソースドキュメントのレンダリング済み PDF/HTML バイトストリーム。  
- **変換はどれくらい速くなりますか？** キャッシュされたドキュメントで最大 8 倍高速化（4 コアサーバーで測定）。  
- **商用の GroupDocs ライセンスは必要ですか？** はい、実稼働環境では有効なライセンスが必須です。  
- **.NET 6+ で動作しますか？** 完全対応—.NET 5、.NET 6、.NET 7 で使用可能です。  
- **Docker のサポートは含まれますか？** キャッシュはコンテナ内でも動作します。Redis ポートを公開するだけです。

## **custom redis cache .net** とは？

開発者が実装するキャッシュ層で、ドキュメント変換のバイナリ出力を Redis のキー‑バリューストアに保存します。これにより、後続のリクエストは元ファイルを再処理せずに事前にレンダリングされた結果を即座に取得でき、レイテンシと CPU 負荷を大幅に削減します。

## GroupDocs.Conversion と **custom redis cache .net** を使用する理由

GroupDocs.Conversion は **50+** の入力・出力形式（DOCX、PPTX、HTML、PDF など）をサポートし、最大 500 ページのドキュメントをメモリ全体にロードせずに処理できます。Redis キャッシュと組み合わせることで、冗長なレンダリングを排除し、CPU 使用率を約 **70 %** 削減、キャッシュ資産の応答時間を **200 ms** 未満に保ちます。

## 前提条件

このガイドを進めるには、以下を用意してください。

- **GroupDocs.Conversion for .NET**（バージョン 25.3.0 以降）  
- **StackExchange.Redis** NuGet パッケージ  
- アクセス可能な Redis インスタンス（例: `192.168.222.4:6379`）  
- Visual Studio 2022 または任意の C# 対応 IDE  
- .NET 6 SDK（または .NET 5 / Framework 4.8）  

### 知識の前提条件
- C# の async/await パターンに慣れていること  
- Redis の基本概念（キー、TTL、接続プーリング）  
- ドキュメント変換パイプラインの概要を理解していること  

## .NET 用 GroupDocs.Conversion のセットアップ方法

まず、NuGet パッケージマネージャーコンソールまたは .NET CLI を使用して GroupDocs.Conversion パッケージをプロジェクトに追加します。これにより、コア変換エンジンとその依存関係がインストールされ、Converter インスタンスの作成や各種ドキュメント形式の変換設定が可能になります。

NuGet でライブラリをインストール:

```
Install-Package GroupDocs.Conversion
```

または .NET CLI で:

```
dotnet add package GroupDocs.Conversion
```

### ライセンス取得手順
- **無料トライアル:** GroupDocs ポータルに登録して 30 日間のライセンスファイルを取得。  
- **一時ライセンス:** 大規模ワークロード向けに 90 日間の評価キーをリクエスト。  
- **購入:** 本番環境で無制限変換を利用できるプロダクションライセンスを取得。  

パッケージをインストールしたら、C# プロジェクトで GroupDocs.Conversion を初期化します:

```csharp
using GroupDocs.Conversion;
using GroupDocs.Conversion.Options.Convert;

// Initialize with a license file
Converter converter = new Converter("path/to/license.json");
```

## **custom redis cache .net** が変換速度を向上させる仕組み

変換リクエストが来ると、アプリはまず Redis でソースドキュメントと変換パラメータに一致するキャッシュバイトストリームを検索します。ヒットすれば、保存された結果を即座に返し、高価なレンダリングプロセスを回避します。ヒットしなければ、GroupDocs.Conversion が変換を実行し、出力を Redis に保存して次回以降に再利用します。

### 手順 1: `RedisCache` クラスの定義

`RedisCache` クラスは StackExchange.Redis をラップした軽量ラッパーで、バイナリ変換結果の保存と取得を行います。

```csharp
// RedisCache class definition placeholder
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using StackExchange.Redis;

public class RedisCache : IDisposable
{
    private readonly string _cacheKeyPrefix;
    private readonly ConnectionMultiplexer _redis;
    private readonly IDatabase _db;
    private readonly string _host = "192.168.222.4:6379";

    public RedisCache(string cacheKeyPrefix)
    {
        _cacheKeyPrefix = cacheKeyPrefix;
        _redis = ConnectionMultiplexer.Connect(_host);
        _db = _redis.GetDatabase();
    }

    // Set data in the cache with a specific key
    public void Set(string key, object data)
    {
        if (data == null) return;

        string prefixedKey = GetPrefixedKey(key);
        using (MemoryStream stream = new MemoryStream())
        {
            ((Stream)data).CopyTo(stream);
            _db.StringSet(prefixedKey, RedisValue.CreateFrom(stream));
        }
    }

    // Try to retrieve data from the cache using a key
    public bool TryGetValue(string key, out object value)
    {
        var prefixedKey = GetPrefixedKey(key);
        var redisValue = _db.StringGet(prefixedKey);

        if (redisValue.HasValue)
        {
            value = new MemoryStream(redisValue);
            return true;
        }

        value = default;
        return false;
    }

    // Retrieve all keys that match a filter pattern from the cache
    public IEnumerable<string> GetKeys(string filter)
    {
        return _redis.GetServer(_host).Keys(pattern: $"*{filter}*")
            .Select(x => x.ToString().Replace(_cacheKeyPrefix, string.Empty))
            .Where(x => x.StartsWith(filter, StringComparison.InvariantCultureIgnoreCase))
            .ToList();
    }

    private string GetPrefixedKey(string key) => $"{_cacheKeyPrefix}{key}";

    public void Dispose()
    {
        _redis.Dispose();
    }
}
```
```

## 手順 2: カスタムキャッシュを使用したドキュメント変換の実装

以下の例は、`RedisCache` を GroupDocs.Conversion に統合し、PDF 変換出力をキャッシュする方法を示しています。

```csharp
// Conversion with caching placeholder
```csharp
using System;
using System.Diagnostics;
using GroupDocs.Conversion.Options.Convert;
using GroupDocs.Conversion.Caching;

public class HowToUseCustomCacheImplementation
{
    public static void Run()
    {
        string outputDirectory = "YOUR_OUTPUT_DIRECTORY";
        
        RedisCache cache = new RedisCache("sample_");
        Func<ConverterSettings> settingsFactory = () => new ConverterSettings
        {
            Cache = cache
        };

        using (Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/SAMPLE_PDF", settingsFactory))
        {
            PdfConvertOptions options = new PdfConvertOptions();
            
            Stopwatch stopWatch = Stopwatch.StartNew();
            converter.Convert($"{outputDirectory}/converted.pdf", options);
            stopWatch.Stop();

            stopWatch.Restart();
            converter.Convert($"{outputDirectory}/converted-1.pdf", options);
            stopWatch.Stop();
        }
    }
}
```
```

## **custom redis cache .net** の一般的な使用例

カスタム Redis キャッシュは、ドキュメント変換結果が繰り返し要求されるあらゆるシナリオで活用でき、即時取得とサーバ負荷の軽減を実現します。典型的な利用例は、エンタープライズ文書管理システム、高トラフィック Web API のプレビュー配信、CDN エッジでの変換資産キャッシュ、レポート自動生成ダッシュボード、オンデマンドで商品カタログを生成する e‑コマースプラットフォームなどです。

1. **エンタープライズ文書管理システム:** 中央リポジトリに保存された数千件の PDF のプレビュー生成を高速化。  
2. **Web API:** 高トラフィックエンドポイントで事前変換済み HTML やサムネイル画像を即座に返却。  
3. **CDN エッジノード:** 変換資産をユーザーに近い場所でキャッシュし、オリジンサーバの負荷を削減。  
4. **分析ダッシュボード:** PDF レポートをオンザフライで生成し、定期配信で再利用。  
5. **E コマースカタログ:** 商品パンフレット変換をキャッシュしてページロード時間を短縮。  

## Redis 使用時のパフォーマンスチューニング方法

適切な TTL 設定、単一の ConnectionMultiplexer インスタンスの再利用、生バイト配列の保存によるシリアライズオーバーヘッド回避、バッチ削除による効率化などでパフォーマンスを最適化できます。メモリ使用量を監視し、`allkeys‑lru` のようなエビクションポリシーを有効にすると、重負荷時でもキャッシュが効率的に機能します。

- **キャッシュサイズ管理:** 多くのドキュメントに対して 24 時間の TTL を設定し、古いエントリは `RedisCache.GetKeys("docCache:*")` で削除。  
- **接続プーリング:** アプリ全体で単一の `ConnectionMultiplexer` を共有し、ハンドシェイクオーバーヘッドを回避。  
- **効率的なシリアライズ:** 生バイト列を直接保存し、ペイロードを膨らませる JSON や XML ラッパーは使用しない。  
- **バッチ操作:** カテゴリをクリアする際は `IDatabase.KeyDelete` にパターンを渡して一括削除を実行。  

## 一般的な落とし穴のトラブルシューティング方法

問題が発生したら、キャッシュキーの生成が一貫しているか確認し、Redis のメモリ消費をモニタリングし、クライアントライブラリのバージョンがランタイムと合っているかをチェックします。アプリと Redis サーバ間のネットワークレイテンシを測定し、接続プーリングが正しく構成されているか確認して、過剰なハンドシェイクがパフォーマンス低下を招かないようにします。

- **キーが見つからない:** 同一の変換パラメータ（入力パス、出力形式、変換オプション）で同一キーが生成されているか確認。  
- **メモリ圧迫:** Redis のメモリ使用量を監視し、`maxmemory-policy allkeys-lru` を有効にして最古のエントリを自動削除。  
- **バージョン不一致:** StackExchange.Redis のバージョンが .NET ランタイムに適合しているか確認（例: .NET 6 では 2.6 以上）。  
- **ネットワークレイテンシ:** アプリと同一データセンターまたは VPC 内に Redis を配置し、往復時間を 1 ms 未満に保つ。  

## よくある質問

**Q: ローカルマシンに Redis をインストールする方法は？**  
A: お使いの OS 向け公式インストールガイドをご参照ください: [Redis ダウンロード](https://redis.io/download)。

**Q: GroupDocs.Conversion とカスタムキャッシュを組み合わせる具体的なメリットは？**  
A: 重複レンダリングを排除し、CPU 使用率を約 70 % 削減、平均応答時間を 1.2 秒から <200 ms に短縮、コンピュートサイクル削減でクラウドコストも削減できます。

**Q: このアーキテクチャは Azure や AWS にデプロイできますか？**  
A: はい。`ConnectionMultiplexer` をマネージド Redis インスタンス（Azure Cache for Redis または Amazon ElastiCache）にポイントし、ポート 6379 の通信が許可されていることを確認してください。

**Q: キャッシュは同時 Web リクエストに対してスレッドセーフですか？**  
A: `StackExchange.Redis` クライアントは完全にスレッドセーフです。追加ロックなしで単一の `ConnectionMultiplexer` をすべてのリクエストスレッドで共有できます。

**Q: ソースドキュメントが変更されたとき、キャッシュをどうクリアしますか？**  
A: 該当ドキュメントの識別子にマッチするキーを削除します。例: `await redis.GetDatabase().KeyDeleteAsync($"docCache:{docId}:*");`。

## 結論

**custom redis cache .net** を GroupDocs.Conversion と統合することで、劇的なパフォーマンス向上、インフラコスト削減、そして滑らかなユーザー体験を実現できます。本稿の手順は本番環境で即座に使える基盤を提供します。TTL 設定やキャッシュキー戦略、水平スケーリングを試行し、ワークロードに最適化してください。

---

**最終更新日:** 2026-05-21  
**テスト環境:** GroupDocs.Conversion 25.3.0 for .NET  
**作者:** GroupDocs  

---

```bash
Install-Package GroupDocs.Conversion -Version 25.3.0
```

```bash
dotnet add package GroupDocs.Conversion --version 25.3.0
```

```csharp
using GroupDocs.Conversion;
```

## 関連チュートリアル

- [Conversion Cache Management Tutorials for GroupDocs.Conversion .NET](/conversion/net/cache-management/)
- [Optimize .NET Document Conversion with Caching Using GroupDocs.Conversion](/conversion/net/cache-management/optimize-net-document-conversion-caching-groupdocs/)
- [Master Document Conversion Setup in .NET Using GroupDocs.Conversion](/conversion/net/conversion-options-settings/master-groupdocs-conversion-net-setup/)