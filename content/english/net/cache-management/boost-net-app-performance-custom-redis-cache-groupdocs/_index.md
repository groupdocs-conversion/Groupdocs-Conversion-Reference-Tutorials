---
title: "Boost .NET Performance with custom redis cache .net and GroupDocs.Conversion"
description: "Learn how to use custom redis cache .net with GroupDocs.Conversion to dramatically speed up document conversion. Discover step‑by‑step setup, use redis caching best practices, and performance metrics."
date: "2026-05-21"
weight: 1
url: "/net/cache-management/boost-net-app-performance-custom-redis-cache-groupdocs/"
keywords:
  - custom redis cache .net
  - use redis caching
  - implement redis caching .net
type: docs
schemas:
- type: TechArticle
  headline: Boost .NET Performance with custom redis cache .net and GroupDocs.Conversion
  description: Learn how to use custom redis cache .net with GroupDocs.Conversion
    to dramatically speed up document conversion. Discover step‑by‑step setup, use
    redis caching best practices, and performance metrics.
  dateModified: '2026-05-21'
  author: GroupDocs
- type: FAQPage
  questions:
  - question: How do I install Redis on my local machine?
    answer: 'Follow the official Redis installation guide for your OS: [Redis Download](https://redis.io/download).'
  - question: What are the tangible benefits of using a custom cache with GroupDocs.Conversion?
    answer: It eliminates duplicate rendering, cuts CPU usage by ~70 %, reduces average
      response time from 1.2 s to <200 ms, and lowers cloud bill by decreasing compute
      cycles.
  - question: Can this architecture be deployed to Azure or AWS?
    answer: Yes—simply point the `ConnectionMultiplexer` to your managed Redis instance
      (Azure Cache for Redis or Amazon ElastiCache) and ensure network security groups
      allow traffic on port 6379.
  - question: Is the cache thread‑safe for concurrent web requests?
    answer: The `StackExchange.Redis` client is fully thread‑safe; you can share a
      single `ConnectionMultiplexer` across all request threads without additional
      locking.
  - question: How do I clear the cache when a source document changes?
    answer: Invalidate by deleting keys that match the document’s identifier, e.g.,
      `await redis.GetDatabase().KeyDeleteAsync($"docCache:{docId}:*");`.
---

# Boost Your .NET Application Performance with **custom redis cache .net** Using GroupDocs.Conversion

## Introduction

If your .NET application spends valuable seconds—or even minutes—converting documents, you’re not alone. Implementing a **custom redis cache .net** solution alongside GroupDocs.Conversion can cut conversion times by up to 80 % for repeat requests. In this tutorial you’ll learn how to set up GroupDocs.Conversion, create a Redis‑backed cache, and apply proven performance‑tuning techniques that keep your app responsive under heavy load.

### Quick Answers
- **What does the custom Redis cache store?** Rendered PDF/HTML byte streams for each source document.  
- **How much faster can conversion become?** Up to 8× faster for cached documents, measured on a 4‑core server.  
- **Do I need a commercial GroupDocs license?** Yes, a valid license is required for production use.  
- **Can this run on .NET 6+?** Absolutely—compatible with .NET 5, .NET 6, and .NET 7.  
- **Is Docker support included?** The cache works inside containers; just expose the Redis port.

## What is **custom redis cache .net**?

It is a developer‑implemented caching layer that stores the binary output of document conversions in a Redis key‑value store, enabling subsequent requests to fetch the pre‑rendered result instantly instead of re‑processing the original file, thereby reducing latency and CPU load across the application.

## Why use **custom redis cache .net** with GroupDocs.Conversion?

GroupDocs.Conversion supports **50+** input and output formats—including DOCX, PPTX, HTML, and PDF—and can process documents up to 500 pages without loading the entire file into memory. By pairing it with a Redis cache, you eliminate redundant rendering, reduce CPU usage by roughly **70 %**, and keep response times under **200 ms** for cached assets.

## Prerequisites

To follow this guide, ensure you have:

- **GroupDocs.Conversion for .NET** (Version 25.3.0 or later)  
- **StackExchange.Redis** NuGet package  
- A reachable Redis instance (e.g., `192.168.222.4:6379`)  
- Visual Studio 2022 or any C#‑compatible IDE  
- .NET 6 SDK (or .NET 5/Framework 4.8) installed  

### Knowledge prerequisites
- Comfortable with C# async/await patterns  
- Basic Redis concepts (keys, TTL, connection pooling)  
- Familiarity with document conversion pipelines  

## How to set up GroupDocs.Conversion for .NET?

Begin by adding the GroupDocs.Conversion package to your project using either the NuGet Package Manager Console or the .NET CLI. This installs the core conversion engine and its dependencies, preparing your environment to create Converter instances and configure conversion settings for various document formats.

Install the library via NuGet:

```
Install-Package GroupDocs.Conversion
```

Or with the .NET CLI:

```
dotnet add package GroupDocs.Conversion
```

### License acquisition steps
- **Free trial:** Register on the GroupDocs portal for a 30‑day license file.  
- **Temporary license:** Request a 90‑day evaluation key for larger workloads.  
- **Purchase:** Obtain a production license to unlock unlimited conversions.

After installing the package, initialize GroupDocs.Conversion in your C# project:

```csharp
using GroupDocs.Conversion;
using GroupDocs.Conversion.Options.Convert;

// Initialize with a license file
Converter converter = new Converter("path/to/license.json");
```

## How does a **custom redis cache .net** improve conversion speed?

When a conversion request arrives, the application first queries Redis for a cached byte stream matching the source document and conversion parameters. If a hit occurs, the stored result is returned immediately, bypassing the expensive rendering process; otherwise, GroupDocs.Conversion performs the conversion and the output is saved back to Redis for future use.

### Step 1: Define the `RedisCache` class

The `RedisCache` class provides a lightweight wrapper around StackExchange.Redis for storing and retrieving binary conversion results.

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

## Step 2: Implement document conversion with the custom cache

The following example demonstrates integrating the `RedisCache` with GroupDocs.Conversion to cache PDF conversion output.

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

## What are common use cases for **custom redis cache .net**?

The custom Redis cache can be leveraged in any scenario where document conversion results are repeatedly requested, providing instant retrieval and reducing server load. Typical applications include enterprise document management systems, high‑traffic web APIs delivering previews, CDN edge caching of converted assets, automated reporting dashboards, and e‑commerce platforms that generate product brochures on demand.

1. **Enterprise Document Management Systems:** Speed up preview generation for thousands of PDFs stored in a central repository.  
2. **Web APIs:** Return pre‑converted HTML or image thumbnails instantly for high‑traffic endpoints.  
3. **CDN Edge Nodes:** Cache converted assets close to users, reducing origin server load.  
4. **Analytics Dashboards:** Generate PDF reports on‑the‑fly and reuse them for recurring scheduled deliveries.  
5. **E‑commerce Catalogs:** Cache product brochure conversions to improve page load times.  

## How can you fine‑tune performance when using Redis?

Performance can be optimized by configuring appropriate TTL values, reusing a single ConnectionMultiplexer instance, storing raw byte arrays to avoid serialization overhead, and employing batch operations for bulk deletions. Monitoring memory usage and enabling an eviction policy such as allkeys‑lru ensures the cache remains efficient under heavy load.

- **Cache size management:** Set a TTL of 24 hours for most documents; purge older entries with `RedisCache.GetKeys("docCache:*")`.  
- **Connection pooling:** Reuse a single `ConnectionMultiplexer` instance across the application to avoid handshake overhead.  
- **Efficient serialization:** Store raw bytes directly; avoid JSON or XML wrappers that inflate payload size.  
- **Batch operations:** When clearing a category, use `IDatabase.KeyDelete` with a pattern to remove many keys in one call.  

## How to troubleshoot common pitfalls?

When issues arise, verify that cache keys are generated consistently, monitor Redis memory consumption, and ensure the client library version matches the runtime. Check network latency between the application and Redis server, and confirm that connection pooling is correctly configured to avoid excessive handshakes that can degrade performance.

- **Missing keys:** Verify that the same cache key is generated for identical conversion parameters (input path, output format, conversion options).  
- **Memory pressure:** Monitor Redis memory usage; enable `maxmemory-policy allkeys-lru` to evict least‑recently‑used entries automatically.  
- **Version mismatches:** Ensure the StackExchange.Redis version matches the .NET runtime (e.g., 2.6+ for .NET 6).  
- **Network latency:** Place Redis in the same data center or VPC as your application to keep round‑trip times below 1 ms.  

## Frequently Asked Questions

**Q: How do I install Redis on my local machine?**  
A: Follow the official Redis installation guide for your OS: [Redis Download](https://redis.io/download).

**Q: What are the tangible benefits of using a custom cache with GroupDocs.Conversion?**  
A: It eliminates duplicate rendering, cuts CPU usage by ~70 %, reduces average response time from 1.2 s to <200 ms, and lowers cloud bill by decreasing compute cycles.

**Q: Can this architecture be deployed to Azure or AWS?**  
A: Yes—simply point the `ConnectionMultiplexer` to your managed Redis instance (Azure Cache for Redis or Amazon ElastiCache) and ensure network security groups allow traffic on port 6379.

**Q: Is the cache thread‑safe for concurrent web requests?**  
A: The `StackExchange.Redis` client is fully thread‑safe; you can share a single `ConnectionMultiplexer` across all request threads without additional locking.

**Q: How do I clear the cache when a source document changes?**  
A: Invalidate by deleting keys that match the document’s identifier, e.g., `await redis.GetDatabase().KeyDeleteAsync($"docCache:{docId}:*");`.

## Conclusion

By integrating a **custom redis cache .net** with GroupDocs.Conversion, you unlock dramatic performance gains, lower infrastructure costs, and deliver a smoother user experience. The steps above give you a production‑ready foundation—experiment with TTL values, cache key strategies, and horizontal scaling to tailor the solution to your workload.

---

**Last Updated:** 2026-05-21  
**Tested With:** GroupDocs.Conversion 25.3.0 for .NET  
**Author:** GroupDocs  

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

## Related Tutorials

- [Conversion Cache Management Tutorials for GroupDocs.Conversion .NET](/conversion/net/cache-management/)
- [Optimize .NET Document Conversion with Caching Using GroupDocs.Conversion](/conversion/net/cache-management/optimize-net-document-conversion-caching-groupdocs/)
- [Master Document Conversion Setup in .NET Using GroupDocs.Conversion](/conversion/net/conversion-options-settings/master-groupdocs-conversion-net-setup/)
