---
date: '2026-07-19'
description: 发现一步步的 java redis 缓存教程，该教程将 Redis 与 GroupDocs.Conversion 集成，以提升渲染性能、缩短转换时间并简化缓存管理。
keywords:
- java redis caching
- boost rendering performance
- configure redis ttl
- reduce conversion time
- cache documents java
lastmod: '2026-07-19'
og_description: 学习使用 GroupDocs.Conversion 的 java redis 缓存。本教程展示了如何提升渲染性能、缩短转换时间，并在简单的
  Java 项目中配置 Redis TTL。
og_image_alt: 'Guide: java redis caching with GroupDocs and Redis'
og_title: java redis 缓存 – 在 Java 中使用 Redis 缓存文档
schemas:
- author: GroupDocs
  dateModified: '2026-07-19'
  description: Discover a step‑by‑step java redis caching tutorial that integrates
    Redis with GroupDocs.Conversion to boost rendering performance, reduce conversion
    time, and simplify cache management.
  headline: 'java redis caching: Cache Docs in Java with Redis'
  type: TechArticle
- description: Discover a step‑by‑step java redis caching tutorial that integrates
    Redis with GroupDocs.Conversion to boost rendering performance, reduce conversion
    time, and simplify cache management.
  name: 'java redis caching: Cache Docs in Java with Redis'
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
- java redis cache
- GroupDocs.Conversion
- document rendering
- performance optimization
title: java redis 缓存：在 Java 中使用 Redis 缓存文档
type: docs
url: /zh/java/cache-management/custom-cache-redis-groupdocs-java/
weight: 1
---

# java redis 缓存：在 Java 中使用 Redis 缓存文档

在现代 Web 应用程序中，重复提供相同的已转换文档会浪费 CPU 周期并延长响应时间。**java redis caching** 通过将转换输出存储在快速的内存数据存储中来解决此问题，从而使后续请求即时响应。在本教程中，您将学习如何将 Redis 集成到 GroupDocs.Conversion 工作流中，配置 TTL，并衡量预期的性能提升。

## 快速答案
- **本教程涵盖什么？** 一个完整的 java redis 缓存教程，将 Redis 与 GroupDocs.Conversion 集成。  
- **为什么使用 Redis？** 它提供亚毫秒级延迟，支持 TTL 过期，并能够在多个应用实例之间横向扩展。  
- **我需要 GroupDocs 许可证吗？** 试用或临时许可证用于测试是可以的；生产部署需要正式许可证。  
- **主要步骤是什么？** 添加 Maven 依赖，配置 `JedisPool`，构建缓存帮助方法，并将缓存接入转换流水线。  
- **支持哪个 Java 版本？** Java 8+（兼容最新的 GroupDocs.Conversion 版本）。

## 使用 Redis 缓存文档是什么？
使用 Redis 缓存文档是指将转换的二进制输出（例如 PDF 字节数组）持久化到 Redis 中，以便相同的后续请求能够检索缓存的字节，而不是重新运行转换引擎。这消除了冗余的 CPU 工作，降低了网络带宽消耗，并提供更流畅的终端用户体验。

## 为什么在 Java 中实现 Redis 缓存？
将文档加载一次，存储结果，并在重复访问时即时提供。基于 Redis 的缓存可以为经常访问的文件 **将转换时间缩短高达 90 %**，通过降低 CPU 使用率 **降低基础设施成本**，并在集群环境中为所有应用节点 **提供单一真实来源**。

## 前提条件
- **GroupDocs.Conversion** – 版本 25.2 或更高（支持 **120+** 输入和输出格式）。  
- **Jedis**（Java 官方 Redis 客户端）。  
- 运行中的 Redis 实例（本地开发可使用默认的 `localhost:6379`）。  
- 用于依赖管理的 Maven。  
- 熟悉 Java 异常处理和 I/O 流的基本知识。

## 为 Java 设置 GroupDocs.Conversion

`GroupDocs.Conversion` 是一个 Java 库，可将文档转换并渲染为多种格式，自动处理布局保留、字体嵌入和图像提取。

将 GroupDocs 仓库和依赖添加到您的 `pom.xml` 中：

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

### 许可证获取
您可以先使用 **免费试用**，申请 **临时许可证** 进行评估，或购买完整的 **许可证** 用于生产环境。

在 Java 代码中初始化 GroupDocs.Conversion：

```java
import com.groupdocs.conversion.*;

ConversionConfig config = new ConversionConfig();
config.setLicensePath("path/to/license/file.lic");
ConversionApi conversionApi = new ConversionApi(config);
```

## 实施指南

### 使用 Redis 创建自定义缓存

#### 概述
自定义 Redis 缓存保存渲染后的文档字节，允许在重复请求时即时检索。

#### 设置 JedisPool
`JedisPool` 是一个线程安全的可复用 Redis 连接池，可最小化套接字开销并提升吞吐量。

```java
import redis.clients.jedis.JedisPool;
import redis.clients.jedis.JedisPoolConfig;

JedisPoolConfig poolConfig = new JedisPoolConfig();
poolConfig.setMaxTotal(20);               // maximum active connections
poolConfig.setMaxIdle(10);                // maximum idle connections
poolConfig.setMinIdle(2);                 // minimum idle connections
JedisPool jedisPool = new JedisPool(poolConfig, "localhost", 6379);
```

#### 存储和检索缓存数据
下面的帮助方法将字节数组序列化为 Base64 字符串以安全存储，并将其检索回字节数组。

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

#### 与 GroupDocs.Conversion 集成
现在将缓存接入转换工作流。该方法首先检查缓存；如果未命中，则执行转换，存储结果并返回字节。

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

## 如何实现 java redis 缓存？
`ConversionApi` 是 GroupDocs.Conversion 中执行文档转换操作的主要类。

加载源文档，生成确定性的缓存键，在 Redis 中查找该键，仅在键不存在时调用 `ConversionApi`。此模式确保每个唯一的转换只执行一次，然后在配置的 TTL 期间从缓存中提供。

## 故障排除技巧
- 验证 Redis 服务器可达（`redis-cli ping` 应返回 `PONG`）。  
- 确保 `JedisPool` 的主机和端口与您的 Redis 部署匹配。  
- 在 try‑catch 块中包装缓存调用，以处理连接中断而不破坏转换流程。  
- 监控 Redis 内存（`INFO memory`），并设置 `maxmemory` 策略（例如 `volatile-lru`）以优雅地驱逐旧条目。  
- 如果在 JVM 上遇到 `OutOfMemoryError`，请增大堆大小或启用 `-XX:+UseCompressedOops`。

## 实际应用

1. **高流量门户** – 即时提供经常请求的 PDF（目录、白皮书）。  
2. **企业文档管理系统（DMS）** – 当用户重复查看相同合同或政策文件时降低负载。  
3. **电子商务** – 缓存生成的发票或产品目录，以加快结账速度。  
4. **学习平台** – 在每个学生请求时无需重新渲染即可提供讲义和电子书。  
5. **法律服务** – 加速案件文件的分发，同时保持低存储成本。

## 性能考虑因素

- **调优 Redis** – 调整 `maxmemory`，选择如 `allkeys-lru` 的驱逐策略，并根据流量模式设置合适的 `timeout` 值。  
- **跟踪缓存命中/未命中比例** – 使用 `INFO stats` 或 Redis 的 `keyspace_hits` / `keyspace_misses` 计数器来微调 TTL。  
- **JVM 堆大小** – 确保堆能够容纳 GroupDocs 缓冲区；经验法则是每 100 MB 并发转换负载分配 1 GB 堆。  
- **批量转换** – 在转换大量文件时，每个线程复用单个 `Jedis` 实例，以最小化套接字切换。

## 常见问题

**Q: 我可以将此方法用于其他 GroupDocs 输出格式吗？**  
A: 当然可以。相同的缓存模式适用于 DOCX、HTML、图像等，只需更改 `ConvertOptions` 类型。

**Q: 我该如何选择合适的缓存键？**  
A: 将源文件路径、转换选项和任何版本标识符组合起来。这可确保每个配置的唯一性。

**Q: 如果文档在缓存后发生更改怎么办？**  
A: 手动使缓存失效（例如删除键）或使用更短的 TTL，以便陈旧数据快速过期。

**Q: Redis 是唯一的缓存选项吗？**  
A: 不是，但 Redis 提供低延迟、内置 TTL 和广泛的 Java 客户端支持，使其成为此场景的热门选择。

**Q: 这会增加应用服务器的内存使用吗？**  
A: 很少。繁重的工作由 Redis 完成；应用仅通过 Jedis 保持短暂的连接。

## 结论
您现在拥有完整的 **java redis 缓存** 教程，展示了如何使用 Redis 和 GroupDocs.Conversion 缓存文档。通过在 Redis 中持久化渲染输出，您将 **提升渲染性能**、**缩短转换时间**，并为终端用户提供更流畅的体验。尝试不同的 TTL 值，监控缓存指标，并随着应用的增长将此模式扩展到其他文档格式。

---

**最后更新：** 2026-07-19  
**测试环境：** GroupDocs.Conversion 25.2, Jedis 4.2.3  
**作者：** GroupDocs

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

## 相关教程

- [实现自定义缓存 Java – GroupDocs Conversion 缓存](/conversion/java/cache-management/)
- [如何在 Java 中使用 Redis 缓存与 GroupDocs.Conversion](/conversion/java/cache-management/redis-cache-java-groupdocs-conversion-guide/)
- [如何在 Java 中缓存文件与 GroupDocs.Conversion – 高效文档转换的全面指南](/conversion/java/cache-management/implement-java-file-caching-groupdocs-conversion-guide/)