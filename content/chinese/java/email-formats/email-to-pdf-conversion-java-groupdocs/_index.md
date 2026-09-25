---
date: '2026-09-25'
description: 了解如何使用 GroupDocs.Conversion 将 eml 转换为 pdf（java），并应用时区偏移以保留正确的时间戳。面向 Java
  开发者的分步指南。
keywords:
- convert eml to pdf java
- email to pdf conversion
- timezone offset java
lastmod: '2026-09-25'
og_description: 了解如何使用 GroupDocs.Conversion 将 eml 转换为 pdf（java），并应用时区偏移以保留正确的时间戳。面向开发者的详细
  Java 指南。
og_image_alt: 'Java guide: convert eml to pdf with timezone offset using GroupDocs.Conversion'
og_title: 使用 GroupDocs 将 eml 转换为 pdf（java）并使用时区偏移
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
title: 如何在 Java 中将 eml 转换为 pdf 并使用时区偏移
type: docs
url: /zh/java/email-formats/email-to-pdf-conversion-java-groupdocs/
weight: 1
---

# 如何在 Java 中将 eml 转换为 pdf 并处理时区偏移

在本教程中，您将学习如何 **convert eml to pdf java**，并正确调整时间戳以适应任何时区差异。使用 GroupDocs.Conversion for Java，您将看到完整的端到端工作流——从 Maven 配置、加载带自定义偏移的邮件，到流式输出生成的 PDF 文件。此步骤面向 Java 8+ 开发者，帮助他们生成可靠、适合归档的 PDF，并显示正确的本地时间。

## 快速答案
- **使用哪个库进行转换？** GroupDocs.Conversion for Java。  
- **哪个主要方法设置时区？** `EmailLoadOptions.setTimeZoneOffset`。  
- **需要许可证吗？** 免费试用可用于测试；生产环境需要完整许可证。  
- **可以批量处理多个邮件吗？** 可以——将转换循环包装在批处理例程中。  
- **需要哪个 Java 版本？** JDK 8 或更高版本。  

## 什么是 convert eml to pdf java？
“convert eml to pdf java” 描述了使用 Java 代码将电子邮件文件（通常为 `.eml` 或 `.msg`）生成 PDF 文档的过程。此转换对于归档、法律合规以及跨平台共享至关重要，因为 PDF 能保留布局并且可在任何设备上查看。

## 为什么使用 GroupDocs.Conversion for Java？
GroupDocs.Conversion 支持 **70+** 种输入和输出格式，包括 `.eml`、`.msg`、`.pdf`、`.docx` 和各种图像类型。其内置的 `EmailLoadOptions` 允许您以毫秒为单位指定时区偏移，确保 PDF 时间戳匹配预期的本地时间。库以流式方式处理文件，与将整个文档加载到内存相比，可将内存使用量降低 **80 %**。

## 前置条件
在开始之前，请确保您具备以下条件：

1. **库和依赖**  
   - GroupDocs.Conversion for Java 版本 **25.2** 或更高。  

2. **环境**  
   - 已安装并配置 JDK 8+。  
   - 使用 Maven 作为构建自动化工具。  

3. **知识**  
   - 基础的 Java 编程，尤其是文件 I/O。  
   - 熟悉 Maven 的 `pom.xml` 结构。

## 设置 GroupDocs.Conversion for Java

### 安装信息
在 `pom.xml` 中添加 GroupDocs 仓库和转换依赖：

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
您可以使用免费试用或申请临时许可证以测试全部功能：

- **免费试用** – 下载库并探索基本功能。  
- **临时许可证** – 申请临时许可证 [temporary license page](https://purchase.groupdocs.com/temporary-license/)。  
- **购买** – 长期使用请在 [official site](https://purchase.groupdocs.com/buy) 购买许可证。

### 基本初始化
以下代码展示了创建 `Converter` 实例并使用时区偏移加载邮件的最小示例：

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.load.EmailLoadOptions;

// Initialize GroupDocs.Conversion with necessary load options for email files
EmailLoadOptions loadOptions = new EmailLoadOptions();
loadOptions.setTimeZoneOffset(7200000.0); // Set timezone offset in milliseconds (e.g., 2 hours)
```

## 如何设置时区偏移？
`EmailLoadOptions` 是用于控制邮件文件加载方式的配置类。请在转换前使用自定义偏移加载邮件。`setTimeZoneOffset` 方法接受 **毫秒** 为单位的偏移值，例如 +2 小时对应 `7200000`。此调整会重新写入生成的 PDF 中显示的时间戳。通过提供偏移，库会重新计算显示的发送和接收时间，确保生成的 PDF 反映收件人的本地时区。这对跨国团队审阅归档通信尤为有用。

```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
loadOptions.setTimeZoneOffset(7200000.0); // Set to 2 hours ahead (in milliseconds)
```

## 如何初始化 Converter 对象？
`Converter` 是使用提供的加载选项执行文档转换的核心类。通过传入源文件路径和返回先前定义的 `loadOptions` 的 lambda 来创建 `Converter`。这将时区设置绑定到转换过程。它读取源邮件，应用包括时区偏移在内的 `EmailLoadOptions` 设置，并为 PDF 生成准备输出流。使用 lambda 可确保在转换时评估选项，对于处理多个文件且设置各不相同时非常有帮助。

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.convert.PdfConvertOptions;

String sourceFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.eml"; // Path to the email document.
String outputPattern = "YOUR_OUTPUT_DIRECTORY/ConvertEmailWithTimezoneOffset-%d.pdf";

List<OutputStream> streamPool = new ArrayList<>();
Converter converter = new Converter(sourceFilePath, () -> loadOptions);
PdfConvertOptions options = new PdfConvertOptions();
```

## 如何执行转换并流式输出 PDF 页面？
`PdfConvertOptions` 指定 PDF 输出的设置，如页面大小、压缩和图像质量。调用 `convert` 方法，提供 `PdfConvertOptions` 实例以及每页的输出流。`try‑finally` 块确保所有流都被关闭，防止资源泄漏。配置完选项后，`convert` 方法遍历邮件的每一页，将 PDF 数据写入各自的输出流。此方式能够高效处理大邮件，因为每页单独处理并刷新，最大限度降低内存消耗。

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

## 实际应用场景
- **邮件归档** – 将带准确时间戳的 PDF 存储用于法律或审计目的。  
- **跨时区协作** – 全球团队在转换后的文档中看到相同的本地时间。  
- **邮件报告** – 生成保留原始发送/接收时间的 PDF 报告，以满足合规要求。

您可以将此工作流嵌入 CRM 系统、文档管理平台或自动化批处理作业，以简化文档流水线。

## 性能考量
- **资源管理** – 如示例所示及时关闭流以释放内存。  
- **批量处理** – 循环遍历 `.eml` 文件集合，尽可能复用单个 `Converter` 实例。  
- **JVM 调优** – 为大批量任务调整堆大小（`-Xmx`），避免 `OutOfMemoryError`。

## 常见问题及解决方案

| 症状 | 可能原因 | 解决方案 |
|------|----------|----------|
| `NullPointerException` at `loadOptions` | 未正确传递加载选项 | 确保在创建 `Converter` 时使用 lambda `() -> loadOptions`。 |
| PDF 输出为空 | 输入文件路径不正确或文件缺失 | 确认 `sourceFilePath` 指向存在的 `.eml` 文件。 |
| 时区未反映 | 偏移值错误（例如使用秒而不是毫秒） | 提供 **毫秒** 为单位的偏移值（例如 +2 h 为 `7200000`）。 |

## 常见问答
**Q: 什么是 GroupDocs.Conversion for Java？**  
A: 它是一个强大的库，支持数十种格式的文档转换，包括邮件转 PDF，并内置时区处理功能。

**Q: 如何为邮件设置时区偏移？**  
A: 在初始化 `Converter` 前，使用 `EmailLoadOptions.setTimeZoneOffset(milliseconds)`。

**Q: 该设置能转换多种邮件格式吗？**  
A: 能，库支持 `.eml`、`.msg` 以及其他常见邮件文件类型。

**Q: 转换过程中常见的陷阱有哪些？**  
A: 依赖缺失、文件路径错误以及以错误单位（秒而非毫秒）提供偏移。

**Q: 哪里可以找到更多关于 GroupDocs.Conversion 的资源？**  
A: 访问 [official documentation](https://docs.groupdocs.com/conversion/java/) 获取详细指南和 API 参考。

## 其他资源
- **文档**：进一步了解请访问 [GroupDocs Documentation](https://docs.groupdocs.com/conversion/java/)  
- **API 参考**：详细的 API 参考请见 [API reference](https://reference.groupdocs.com/conversion/java/)  
- **下载 GroupDocs.Conversion**：从 [GroupDocs.Conversion download page](https://releases.groupdocs.com/conversion/java/) 开始使用  
- **购买**：长期使用请在 [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy) 购买许可证  
- **免费试用与许可证**：免费试用或申请临时许可证请访问 [GroupDocs Free Trial](https://releases.groupdocs.com/conversion/java/) 和 [Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **支持**：如需帮助，请访问 [GroupDocs Forum](https://forum.groupdocs.com/c/conversion/10)

拥抱 GroupDocs.Conversion 的强大功能，让您的 Java 应用实现准确、时区感知的 PDF 转换吧！

---

**最后更新：** 2026-09-25  
**测试环境：** GroupDocs.Conversion 25.2  
**作者：** GroupDocs

## 相关教程

- [msg to pdf java – Email Formats Conversion with GroupDocs](/conversion/java/email-formats/)
- [eml to pdf java – Convert Email to PDF with GroupDocs](/conversion/java/pdf-conversion/convert-emails-to-pdfs-groupdocs-java/)
- [Convert Multiple File Types with GroupDocs.Conversion Java – Master Guide](/conversion/java/document-operations/groupdocs-conversion-java-master-document-conversion/)