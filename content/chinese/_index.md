---
additionalTitle: Complete Document Conversion API Solutions
date: 2026-08-19
description: 学习文档转换教程，了解如何将 PDF、Word、Excel、PowerPoint 等 50 多种格式进行转换，并提供一步一步的指南。使用
  GroupDocs.Conversion 高效地将 PDF 转换为 Word 等。
is_root: true
keywords:
- document conversion tutorial
- convert PDF to Word
- GroupDocs.Conversion
lastmod: 2026-08-19
linktitle: GroupDocs.Conversion 教程
og_description: 文档转换教程指导您使用 GroupDocs.Conversion 将 PDF、Word、Excel 等 50 多种格式进行转换。了解如何高效地将
  PDF 转换为 Word。
og_image_alt: 'Guide: Convert documents with GroupDocs.Conversion library'
og_title: 使用 GroupDocs.Conversion 的文档转换教程
schemas:
- author: GroupDocs
  dateModified: '2026-08-19'
  description: Learn the document conversion tutorial for converting PDF, Word, Excel,
    PowerPoint and 50+ formats with step‑by‑step guides. Efficiently convert PDF to
    Word and more using GroupDocs.Conversion.
  headline: Document conversion tutorial with GroupDocs.Conversion
  type: TechArticle
- questions:
  - answer: Yes, the library runs in any .NET or Java runtime, including Docker containers
      and Kubernetes pods, without requiring external services.
    question: Can I use GroupDocs.Conversion in a cloud‑native microservice?
  - answer: You can supply the password via `LoadOptions` (or the equivalent Java
      option) when creating the `Converter`, and the library will decrypt the file
      for conversion.
    question: How does the library handle password‑protected PDFs?
  - answer: Use the asynchronous API (or parallel streams in Java) to process files
      concurrently, and enable caching to reuse loaded fonts and resources for better
      performance.
    question: What is the recommended way to convert a large batch of files?
  - answer: Yes, OCR can be enabled through the `OcrOptions` class, allowing conversion
      of scanned PDFs or images into searchable, selectable text.
    question: Does GroupDocs.Conversion support OCR for scanned images?
  - answer: .NET Framework 4.5+, .NET Core 3.1+, .NET 5, .NET 6, and later versions
      are fully supported.
    question: Which .NET versions are officially supported?
  type: FAQPage
tags:
- document conversion
- GroupDocs
- .NET conversion
- Java conversion
- file format conversion
title: 使用 GroupDocs.Conversion 的文档转换教程
type: docs
url: /zh/
weight: 11
---

# 使用 GroupDocs.Conversion 的文档转换教程

在本 **文档转换教程** 中，您将了解如何使用 GroupDocs.Conversion 将 PDF、Word 文件、Excel 电子表格、PowerPoint 幻灯片以及超过 50 种其他格式直接从 .NET 或 Java 应用程序中进行转换。该库离线工作，无需外部服务，并提供高保真结果，使其非常适合企业级工作流。

## 快速答案
- **支持哪些格式？** 超过 50 种输入和输出格式，包括 PDF、DOCX、XLSX、PPTX、CAD 和图像类型。  
- **可以在没有互联网的情况下进行转换吗？** 可以，GroupDocs.Conversion 完全在本地运行。  
- **文件大小有上限吗？** 支持最高 2 GB 的文件，同时内存使用保持在 200 MB 以下。  
- **生产环境需要许可证吗？** 生产使用需要商业许可证；提供免费试用供评估。  
- **支持哪些平台？** 完全支持 .NET（Framework、Core、.NET 5/6）和 Java。

## 什么是 GroupDocs.Conversion？
GroupDocs.Conversion 是一个跨平台库，使开发者能够在 50 多种格式之间转换文档，而无需依赖外部服务。它提供了一个简洁的 API，用于加载源文件、选择转换选项并将结果保存为所需格式。

## 为什么选择 GroupDocs.Conversion？
GroupDocs.Conversion 提供广泛的格式支持、高保真输出以及性能优化的处理，适用于大规模企业项目。它在本地运行，无需第三方依赖，确保安全性和合规性。

- **广泛的格式覆盖：** 支持 50+ 种输入和输出格式，能够处理最高 2 GB 的文件，内存使用低于 200 MB。  
- **高保真转换：** 保留布局、字体、图像和嵌入对象，视觉准确度高达 99 %。  
- **性能优化：** 在普通服务器级虚拟机上，批量转换 1 000 页耗时不到 30 秒。  
- **零依赖部署：** 无需 Microsoft Office、Adobe Acrobat 或其他第三方软件。

## 如何在 .NET 中开始使用 GroupDocs.Conversion？
`Converter` 是执行文档转换的主要类。向项目添加 NuGet 包 `GroupDocs.Conversion`，使用文件路径或流实例化 `Converter` 类，选择目标格式，然后调用 `Save`。此三步流程可在几秒钟内完成从源文件到转换后文件的转换。

## 如何在 Java 中开始使用 GroupDocs.Conversion？
`Converter` 是 Java 中用于转换文档的核心类。在 `pom.xml` 中加入 Maven 构件 `com.groupdocs:groupdocs-conversion`，创建 `Converter` 实例，设置所需的 `LoadOptions`，并使用目标格式调用 `convert`。Java API 与 .NET 体验相同，确保跨平台的开发者体验一致。

{{% alert color="primary" %}}
在您的 .NET 应用程序中无缝转换任何文档格式，使用 GroupDocs.Conversion。我们全面的 .NET 库为开发者提供强大的工具，以精确且快速地在 50 多种格式之间转换文件。从将文档转换为 PDF 到在各种格式之间转换，我们的分步教程将指导您完成实现、定制和优化。立即开始将强大的文档转换功能集成到您的 C# 应用程序中。
{{% /alert %}}

### 必备教程

- [入门与许可](./net/getting-started-licensing/)
- [从本地来源加载](./net/loading-from-local-sources/)
- [从远程来源加载](./net/loading-from-remote-sources/)
- [从云存储加载](./net/loading-from-cloud-storage/)
- [处理安全文档](./net/working-with-secure-documents/)
- [文档输出与保存](./net/document-output-saving/)
- [页面管理与内容操作](./net/page-management-content-manipulation/)
- [转换选项与设置](./net/conversion-options-settings/)

### 特定格式转换

- [PDF 转换](./net/pdf-conversion/)
- [Word 处理转换](./net/word-processing-conversion/)
- [电子表格转换](./net/spreadsheet-conversion/)
- [演示文稿转换](./net/presentation-conversion/)
- [图像转换](./net/image-conversion/)
- [电子邮件格式与功能](./net/email-formats-features/)
- [CAD 与技术绘图格式](./net/cad-technical-drawing-formats/)
- [Web 与标记格式](./net/web-markup-formats/)

### 高级功能

- [CSV 与结构化数据处理](./net/csv-structured-data-processing/)
- [XML 与 JSON 处理](./net/xml-json-processing/)
- [压缩与归档处理](./net/compression-archive-handling/)
- [存储文件与 PST 处理](./net/storage-files-pst-processing/)
- [字体处理与替换](./net/font-handling-substitution/)
- [缓存管理](./net/cache-management/)
- [转换事件与日志记录](./net/conversion-events-logging/)
- [转换实用工具与信息](./net/conversion-utilities-information/)
- [文本与标记转换](./net/text-markup-conversion/)

{{% alert color="primary" %}}
在您的 Java 应用程序中实现强大的文档转换功能，使用 GroupDocs.Conversion。我们的 Java API 使开发者能够以卓越的精度和灵活性在众多文档格式之间进行转换。非常适合企业应用，我们的库帮助您在保持格式完整性的同时转换 PDF、Office 文档、图像及其他多种格式。请遵循我们的分步 Java 教程，为您的应用程序增添专业的文档转换功能。
{{% /alert %}}

### 核心功能

- [入门](./java/getting-started/)
- [文档操作](./java/document-operations/)
- [转换选项](./java/conversion-options/)

### 特定格式指南

- [PDF 转换](./java/pdf-conversion/)
- [Word 处理格式](./java/word-processing-formats/)
- [电子表格格式](./java/spreadsheet-formats/)
- [演示文稿格式](./java/presentation-formats/)
- [电子邮件格式](./java/email-formats/)
- [CAD 格式](./java/cad-formats/)
- [Web 与标记格式](./java/web-markup-formats/)

### 高级配置

- [转换事件与日志记录](./java/conversion-events-logging/)
- [缓存管理](./java/cache-management/)
- [安全与保护](./java/security-protection/)
- [水印与注释](./java/watermarks-annotations/)

## 常见问题

**Q: 我可以在云原生微服务中使用 GroupDocs.Conversion 吗？**  
A: 可以，库可以在任何 .NET 或 Java 运行时中运行，包括 Docker 容器和 Kubernetes pod，无需外部服务。

**Q: 库如何处理受密码保护的 PDF？**  
A: 在创建 `Converter` 时，您可以通过 `LoadOptions`（或相应的 Java 选项）提供密码，库会解密文件后进行转换。

**Q: 推荐的批量文件转换方式是什么？**  
A: 使用异步 API（或 Java 中的并行流）并发处理文件，并启用缓存以重用已加载的字体和资源，从而提升性能。

**Q: GroupDocs.Conversion 是否支持对扫描图像进行 OCR？**  
A: 支持，可通过 `OcrOptions` 类启用 OCR，将扫描的 PDF 或图像转换为可搜索、可选择的文本。

**Q: 官方支持哪些 .NET 版本？**  
A: 完全支持 .NET Framework 4.5+、.NET Core 3.1+、.NET 5、.NET 6 以及更高版本。

---

**最后更新：** 2026-08-19  
**测试环境：** GroupDocs.Conversion 23.11 for .NET & Java  
**作者：** GroupDocs

[API 参考](https://reference.groupdocs.com/)  
[免费试用](https://releases.groupdocs.com/)  
[联系支持团队](https://forum.groupdocs.com/)