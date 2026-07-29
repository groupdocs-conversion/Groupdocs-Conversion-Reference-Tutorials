---
date: '2026-07-29'
description: 了解如何使用 GroupDocs.Conversion for Java 列出格式并获取所有可能的转换，适用于云存储文件转换工作流。
keywords:
- how to list formats
- cloud storage file conversion
- GroupDocs.Conversion Java
lastmod: '2026-07-29'
og_description: 学习如何使用 GroupDocs.Conversion for Java 列出格式并获取所有可能的转换。适用于云存储文件转换管道。
og_image_alt: 'Guide: List formats and get conversion matrix with GroupDocs.Conversion
  Java'
og_title: 如何使用 GroupDocs.Conversion for Java 列出格式
schemas:
- author: GroupDocs
  dateModified: '2026-07-29'
  description: Discover how to list formats and retrieve all possible conversions
    using GroupDocs.Conversion for Java, ideal for cloud storage file conversion workflows.
  headline: How to List Formats with GroupDocs.Conversion for Java
  type: TechArticle
- description: Discover how to list formats and retrieve all possible conversions
    using GroupDocs.Conversion for Java, ideal for cloud storage file conversion workflows.
  name: How to List Formats with GroupDocs.Conversion for Java
  steps:
  - name: '**Dynamic Format Detection:** When a file lands in cloud storage, you can
      instantly query whether the desired target format is supported.'
    text: '**Dynamic Format Detection:** When a file lands in cloud storage, you can
      instantly query whether the desired target format is supported.'
  - name: '**Batch Migration:** Move large document libraries to a unified format
      (e.g., PDF/A) by iterating over supported source types.'
    text: '**Batch Migration:** Move large document libraries to a unified format
      (e.g., PDF/A) by iterating over supported source types.'
  - name: '**User‑Driven Export:** Offer end‑users a dropdown of only the formats
      their current document can be exported to, reducing errors and improving UX.'
    text: '**User‑Driven Export:** Offer end‑users a dropdown of only the formats
      their current document can be exported to, reducing errors and improving UX.'
  type: HowTo
- questions:
  - answer: It is a server‑side library that supports 200+ input and 200+ output formats,
      enabling fast, license‑free document conversion without external software.
    question: What is GroupDocs.Conversion for Java?
  - answer: Set up your Maven project, add the dependency shown earlier, load a license
      file, and instantiate the `Converter` class as demonstrated in the initialization
      section.
    question: How do I start with GroupDocs.Conversion?
  - answer: Yes—through the API’s extensibility points you can register custom converters
      or plug‑in third‑party handlers for proprietary formats.
    question: Can I convert custom file types using GroupDocs.Conversion?
  - answer: Forgetting to close the `Converter`, using an old JAR version, or overlooking
      memory usage for very large PDFs. Follow the resource‑management tips above.
    question: What are common pitfalls when implementing conversions?
  - answer: Visit the official [documentation](https://docs.groupdocs.com/conversion/java/)
      or ask questions in the GroupDocs community forum.
    question: Where can I get more help?
  type: FAQPage
tags:
- convert formats
- GroupDocs.Conversion
- Java document conversion
- cloud storage conversion
title: 如何使用 GroupDocs.Conversion for Java 列出格式
type: docs
url: /zh/java/conversion-options/groupdocs-conversion-java-retrieve-possible-conversions/
weight: 1
---

# 如何列出格式并检索所有可能的转换，使用 GroupDocs.Conversion for Java

在许多文档处理项目中，第一步是了解 **如何列出格式**，即转换引擎支持的格式。本教程将一步步演示如何查询 GroupDocs.Conversion for Java，检索每个源到目标的配对，并在云存储文件转换流水线中应用这些知识。完成后，你将拥有一个可复用的方法，返回完整的转换矩阵，并提供性能与错误处理的实用技巧。

## 快速答案
- **“list formats” 是什么意思？** 它返回库能够处理的每个源到目标的转换对。  
- **我需要许可证吗？** 免费试用可用于测试；生产环境需要付费许可证。  
- **这能帮助云存储文件转换吗？** 是的——了解支持的格式可以让你在云存储流水线中自动化转换。  
- **需要哪个 Java 版本？** JDK 8 或更高。  
- **该功能是线程安全的吗？** `Converter` 实例可以跨线程复用，但使用后需释放资源。

## 在 GroupDocs.Conversion 中，“如何列出格式” 是什么？
**list formats** 操作返回一个集合，描述每种源格式及其可以转换成的目标格式。该矩阵由库内部的转换规则生成，对于构建能够在运行时适配 GroupDocs.Conversion 实际能力的动态工作流至关重要。

## 为什么使用 GroupDocs.Conversion for Java？
GroupDocs.Conversion for Java 支持 **200+ 输入格式** 和 **200+ 输出格式**，涵盖从 DOCX、PPTX 到 PDF/A 以及各种图像类型。它完全在服务器上运行，无需 Microsoft Office 或 Adobe 产品。API 是线程安全的，能够在不将整个文件加载到内存的情况下处理数百页的文档，并可无缝集成 AWS S3、Azure Blob、Google Cloud Storage 等云存储服务。

## 前提条件
- **Java Development Kit (JDK)：** 版本 8 或更新。  
- **Maven：** 在你的 IDE（IntelliJ IDEA、Eclipse、NetBeans 等）中正确配置。  
- **GroupDocs.Conversion for Java：** 以 Maven 依赖方式添加（见下文）。

## 设置 GroupDocs.Conversion for Java

将 GroupDocs 仓库和依赖添加到你的 `pom.xml`：

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

### 许可证获取
先使用免费试用来探索 API。对于生产工作负载，请购买许可证或申请临时评估许可证。

### 基本初始化和设置

```java
import com.groupdocs.conversion.Converter;

public class ConversionSetup {
    public static void main(String[] args) {
        // Initialize the Converter object
        Converter converter = new Converter();
        
        System.out.println("GroupDocs.Conversion for Java has been initialized successfully.");
    }
}
```

## 使用 GroupDocs.Conversion for Java 列出格式
`Converter` 是执行转换并提供格式信息的核心类。`getAllPossibleConversions()` 返回所有支持的源到目标转换对的列表。`ConversionInfo` 表示源格式与目标格式之间的单个转换映射。  

加载 `Converter` 引擎，调用 `getAllPossibleConversions()`，即可获得描述每个允许的源‑到‑目标配对的 `ConversionInfo` 对象列表。此单一调用即可用于构建导出选项下拉列表、验证上传文件或设计批量迁移脚本。

### 初始化并检索转换

`Converter` 类是提供转换能力的核心引擎，并公开 `getAllPossibleConversions()` 方法。  

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.contracts.PossibleConversions;

public class GetAllPossibleConversionsFeature {
    public static void run() {
        // Initialize the Converter object
        Converter converter = new Converter();
```

### 遍历可能的转换

```java
// Retrieve all possible conversions supported by the library
for (PossibleConversions conversions : converter.getAllPossibleConversions()) {
    // Print source format description
    System.out.print(String.format("Source format: %s \n", conversions.getSource().getDescription()));
```

### 确定转换类型

```java
// Iterate through each target conversion available for the source format
for (TargetConversion conversion : conversions.getAll()) {
    // Determine if it's a primary or secondary conversion and print details
    System.out.print(String.format("\t...can be converted to %s format as %s conversion.\n",
            conversion.getFormat(),
            conversion.isPrimary() ? "primary" : "secondary"));
}
```

### 完整函数

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.contracts.PossibleConversions;
import com.groupdocs.conversion.contracts.TargetConversion;

public class GetAllPossibleConversionsFeature {
    public static void run() {
        // Initialize the Converter object
        Converter converter = new Converter();

        // Retrieve all possible conversions supported by the library
        for (PossibleConversions conversions : converter.getAllPossibleConversions()) {
            // Print source format description
            System.out.print(String.format("Source format: %s \n", conversions.getSource().getDescription()));

            // Iterate through each target conversion available for the source format
            for (TargetConversion conversion : conversions.getAll()) {
                // Determine if it's a primary or secondary conversion and print details
                System.out.print(String.format("\t...can be converted to %s format as %s conversion.\n",
                        conversion.getFormat(),
                        conversion.isPrimary() ? "primary" : "secondary"));
            }
        }
    }
}
```

## 云存储文件转换使用案例
了解完整的转换矩阵在构建 **云存储文件转换** 服务时尤为有价值：

1. **动态格式检测：** 当文件落入云存储时，你可以立即查询所需的目标格式是否受支持。  
2. **批量迁移：** 通过遍历受支持的源类型，将大型文档库迁移为统一格式（例如 PDF/A）。  
3. **用户驱动导出：** 为最终用户提供仅包含其当前文档可导出的格式的下拉列表，减少错误并提升用户体验。

## 性能考虑
- **资源管理：** 释放 `Converter` 实例或在创建大量短生命周期转换器时使用 try‑with‑resources。  
- **批量处理：** 将多个文件合并为单个作业以降低开销。  
- **缓存：** 若频繁查询 `getAllPossibleConversions()`，请缓存其结果；转换矩阵在运行时很少变化。

## 常见问题及解决方案
| 症状 | 可能原因 | 解决方案 |
|---------|--------------|-----|
| 没有输出 | `Converter` 未正确初始化 | 确保库 JAR 在类路径上且已加载许可证。 |
| `TargetConversion` 列为空 | 使用了过时的库版本 | 升级到最新的 GroupDocs.Conversion 版本。 |
| 大文档内存激增 | 未释放转换器资源 | 调用 `converter.close()` 或使用 try‑with‑resources。 |

## 常见问题

**Q: What is GroupDocs.Conversion for Java?**  
A: It is a server‑side library that supports 200+ input and 200+ output formats, enabling fast, license‑free document conversion without external software.

**Q: How do I start with GroupDocs.Conversion?**  
A: Set up your Maven project, add the dependency shown earlier, load a license file, and instantiate the `Converter` class as demonstrated in the initialization section.

**Q: Can I convert custom file types using GroupDocs.Conversion?**  
A: Yes—through the API’s extensibility points you can register custom converters or plug‑in third‑party handlers for proprietary formats.

**Q: What are common pitfalls when implementing conversions?**  
A: Forgetting to close the `Converter`, using an old JAR version, or overlooking memory usage for very large PDFs. Follow the resource‑management tips above.

**Q: Where can I get more help?**  
A: Visit the official [documentation](https://docs.groupdocs.com/conversion/java/) or ask questions in the GroupDocs community forum.

---

**最后更新：** 2026-07-29  
**测试环境：** GroupDocs.Conversion 25.2 for Java  
**作者：** GroupDocs

## 相关教程

- [使用 GroupDocs.Conversion for Java 将 Word 转换为 PDF 及其他文件格式](/conversion/java/)
- [Word 转 PDF Java – 隐藏修订痕迹和转换选项](/conversion/java/conversion-options/)
- [如何在 Java 中使用 GroupDocs 跟踪转换进度 - 完整指南](/conversion/java/conversion-events-logging/java-groupdocs-conversion-progress-listener/)