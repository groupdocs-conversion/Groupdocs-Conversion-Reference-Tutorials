---
date: '2026-01-23'
description: 学习如何在 Java 中通过使用 GroupDocs.Conversion 实现 Redis 缓存来缓存文档，提升渲染性能并提高效率。
keywords:
- Custom Caching Java
- GroupDocs.Conversion Java
- Redis Cache Implementation
title: 如何在 Java 中使用 Redis 和 GroupDocs 缓存文档
type: docs
url: /zh/java/cache-management/custom-cache-redis-groupdocs-java/
weight: 1
---

# 如何在 Java 中使用 Redis 与 GroupDocs 缓存文档

当您需要高效地 **缓存文档**，尤其是在高并发文档渲染期间，精心设计的缓存可以显著缩短处理时间。在本教程中，我们将逐步讲解一个完整的 **java redis cache tutorial**，将 Redis 与 GroupDocs.Conversion 集成，帮助您 **提升渲染性能**，适用于 PDF、DOCX 等多种格式。

## 快速答案
- **本教程涵盖什么？** 在 Java 中实现基于 Redis 的 GroupDocs.Conversion 缓存。  
- **为什么使用 Redis？** 它提供快速的内存存储、TTL 支持以及易于扩展。  
- **是否需要 GroupDocs 许可证？** 试用或临时许可证可用于测试；生产环境需要正式许可证。  
- **主要步骤是什么？** 设置 Maven 依赖、配置 Jedis、创建缓存助手，并将缓存集成到转换流程中。  
- **支持哪个8+（兼容最新的 GroupDocs（例如生成的 PDF**——减少 CPU **在多个应用实例之间可扩展**，因为 Redis 是中心存储。  
- **对过期策略进行细粒度控制**，以平衡新鲜度和速度。

## 前置条件

- **GroupDocs.Conversion** – 版本 25.2 或更高。  
- **Jedis**（Java 的 Redis 客户端）。  
- 正在运行的 Redis 服务器（开发时本地赖管理的 Maven。  
- 基础的 Java 知识以及对文档转换概念的了解。

## 为 Java 设置 GroupDocs.Conversion

在您的 `pom.xml` 中添加 GroupDocs 仓库和依赖：

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

### 获取许可证
您可以先使用 **Free Trial**，申请 **Temporary License** 进行评估，或购买完整的 **License** 用于生产环境。

在 Java 代码中初始化 GroupDocs.Conversion：

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

## 实施指南

### 使用 Redis 创建自定义缓存

#### 概述
自定义 Redis 缓存保存渲染后的文档字节，以便在重复请求时能够即时获取。

#### 设置 JedisPool
首先，创建连接池以高效管理 Redis 连接：

```java
import redis.clients.jedis.JedisPool;

public class CacheManager {
    private static JedisPool jedisPool = new JedisPool("localhost", 6379);
    
    public static void main(String[] args) {
        // Additional cache setup code here
    }
}
```

#### 存储和检索缓存数据
使用简单的辅助方法将文档存入 Redis 并从 Redis 获取：

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

#### 与 GroupDocs.Conversion 集成
现在将缓存绑定到转换工作流中：

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

### 故障排除技巧
- 验证 Redis 服务器可达（从主机 `ping`）。  
- 确认 `JedisPool` 的主机/端口与您的 Redis 实例匹配。  
- 将缓存调用包装在 try‑catch 块中，以优雅地处理连接问题。  
- 监控 Redis 内存使用情况；生产环境考虑 `maxmemory` 策略。

## 实际应用

1. **高流量门户** – 即时提供频繁请求的 PDF。  
2. **企业文档管理系统 (DMS)** – 当用户反复查看相同合同时，降低转换服务器负载。  
3. **电子商务** – 缓存生成的发票或产品目录。  
4. **学习平台** – 加速讲义和电子书的交付。  
5. **法律服务** – 加快案件文件分发，同时降低存储成本。

## 性能考虑因素

- **调优 Redis** – 根据工作负载调整 `maxmemory`、`eviction-policy` 和超时设置。  
- **跟踪缓存命中/未命中比例** – 使用 Redis `INFO` 统计信息微调键的 TTL。  
- **JVM 堆大小** – 确保堆内存能够容纳转换库及任何进程内缓冲区。

## 常见问题

**问：我可以将此方法用于其他 GroupDocs 输出格式吗？**  
答：当然可以。相同的缓存模式适用于 DOCX、HTML、图像等，只需更改 `ConvertOptions` 类型。

**问：如何选择合适的缓存键？**  
答：将源文件路径、转换选项以及任何版本标识符组合起来。这可确保每种配置的唯一性。

**问：如果文档在缓存后发生更改怎么办？**  
答：手动使缓存失效（例如删除键），或使用较短的 TTL，使陈旧数据快速过期。

**问：Redis 是唯一的缓存选项吗？**  
答：不是，但 Redis 提供低延迟、内置 TTL 和广泛的 Java 客户端支持，使其在此场景中非常受欢迎。

**问：这会增加应用服务器的内存使用吗？**  
答：影响很小。主要工作由 Redis 完成，应用仅通过 Jedis 保持短暂的连接。

## 结论

您现在拥有完整的 **java redis cache tutorial**，展示了如何使用 Redis 和 GroupDocs.Conversion **缓存文档**。通过将渲染输出存入 Redis，您可以 **提升渲染性能**，降低服务器负载，为终端用户提供更流畅的体验。可尝试不同的 TTL 值，监控缓存指标，并根据需要将此模式扩展到其他文档格式。

---

**最后更新：** 2026-01-23  
**测试环境：** GroupDocs.Conversion 25.2, Jedis 4.2  
**作者：** GroupDocs