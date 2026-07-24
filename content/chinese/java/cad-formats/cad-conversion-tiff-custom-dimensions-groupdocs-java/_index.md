---
date: '2026-07-24'
description: Java 图像转换变得简单：了解如何使用 GroupDocs Conversion Java 将 CAD 文件转换为具有自定义尺寸的 TIFF。面向开发者的分步指南。
keywords:
- java image conversion
- custom width height
- set image dimensions java
lastmod: '2026-07-24'
og_description: Java 图像转换变得简单。使用 GroupDocs Conversion Java 将 CAD 文件转换为高质量的 TIFF 图像，并可自定义宽度和高度。请参阅我们的详细指南。
og_image_alt: 'Guide: Convert CAD to TIFF with custom dimensions using GroupDocs Conversion
  Java'
og_title: Java 图像转换：CAD 转换为自定义尺寸的 TIFF
schemas:
- author: GroupDocs
  dateModified: '2026-07-24'
  description: 'Java image conversion made easy: learn how to convert CAD files to
    TIFF with custom dimensions using GroupDocs Conversion Java. Step‑by‑step guide
    for developers.'
  headline: 'Java Image Conversion: CAD to TIFF with Custom Dimensions'
  type: TechArticle
- questions:
  - answer: GroupDocs Conversion Java, a robust Java image conversion library.
    question: What library should I use for Java image conversion?
  - answer: Use `CadLoadOptions` and specify `setWidth()` and `setHeight()`.
    question: How do I set custom dimensions for a CAD file?
  - answer: Yes—load the CAD, set dimensions, then convert with `ImageConvertOptions`.
    question: Can I convert DWG to TIFF in one step?
  - answer: A free trial works for evaluation; a full license unlocks all features.
    question: Do I need a license?
  - answer: Any Java 8+ runtime is supported.
    question: What Java version is required?
  type: FAQPage
tags:
- convert CAD
- GroupDocs Conversion
- Java image conversion
- TIFF
- CAD processing
title: Java 图像转换：CAD 转换为自定义尺寸的 TIFF
type: docs
url: /zh/java/cad-formats/cad-conversion-tiff-custom-dimensions-groupdocs-java/
weight: 1
---

# Java 图像转换：CAD 到 TIFF（自定义尺寸）

如果您需要将 CAD 图纸转换为高分辨率的 TIFF 图像，同时控制精确的像素宽度和高度，**java image conversion** 是关键。使用 GroupDocs Conversion Java，您可以将任何受支持的 CAD 格式（DWG、DGN、DXF 等）光栅化为 TIFF 文件，完美适用于报告、Web 门户或打印布局。本指南将逐步演示从项目设置到最终转换的每一步，帮助您将此过程集成到任何基于 Java 的工作流中。

## 快速答案
- **应该使用哪个库进行 Java 图像转换？** GroupDocs Conversion Java，是一个强大的 Java 图像转换库。  
- **如何为 CAD 文件设置自定义尺寸？** 使用 `CadLoadOptions` 并指定 `setWidth()` 和 `setHeight()`。  
- **我可以一步将 DWG 转换为 TIFF 吗？** 是的——加载 CAD，设置尺寸，然后使用 `ImageConvertOptions` 进行转换。  
- **我需要许可证吗？** 免费试用可用于评估；完整许可证可解锁所有功能。  
- **需要哪个 Java 版本？** 支持任何 Java 8+ 运行时。

## 什么是 GroupDocs Conversion Java？
`GroupDocs Conversion Java` 库是一个 **java image conversion** 解决方案，支持超过 110 种输入和输出格式，包括所有主要的 CAD 和光栅图像类型。  
`Converter` 类是启动文件转换操作的核心组件。  
它提供服务器端渲染、缩放和特定格式的选项，使开发者无需安装第三方查看器即可转换文件。

## 为什么要将 CAD 转换为带自定义尺寸的 TIFF？
设置明确的宽度和高度可确保生成的 TIFF 完全符合下游系统的布局约束。通过在光栅化之前定义像素尺寸，您可以避免下游缩放产生的伪影，保持线宽一致性，并确保图像能够无缝集成到 PDF、网页或印刷材料中，无需额外处理。这种方法还简化了自动化流水线，因为每张图像都必须符合预定义的尺寸规范。  

- **保留视觉保真度：** 在 1920 × 1080 px（或您选择的任何尺寸）进行光栅化，可保持线条和填充的清晰度。  
- **确保一致的布局：** 图像可以干净地嵌入 PDF、HTML 页面或打印模板，无需额外的重新调整大小。  
- **提升兼容性：** TIFF 在 Windows、macOS、Linux 以及大多数设计工具中被普遍接受，减少了格式转换的麻烦。  

## 前置条件
在开始之前，请确保您拥有：

1. **GroupDocs Conversion Java** 版本 25.2 或更高（建议使用最新发布）。  
2. Java IDE，例如 IntelliJ IDEA 或 Eclipse。  
3. 已安装 Maven 用于依赖管理。  
4. 基本的 Java 编程知识并熟悉 Maven 的 `pom.xml`。  

## 设置 GroupDocs Conversion Java

将 GroupDocs Maven 依赖添加到您的 `pom.xml` 中：

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-conversion</artifactId>
    <version>25.2</version>
</dependency>
```

**许可证获取：** 您可以获取免费试用、请求临时许可证以获得完整功能，或购买永久许可证以完全解锁 GroupDocs Conversion 功能。

一旦您的 Java 项目正确链接了这些依赖，即可开始转换 CAD 文件！

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

## 如何使用自定义尺寸将 CAD 转换为 TIFF？

将 CAD 文件转换为具有精确尺寸的 TIFF 需要加载源图纸、配置渲染选项并调用转换 API。通过遵循线性顺序——设置宽度和高度、选择 TIFF 作为输出格式并执行转换——您可以确保生成的图像符合下游应用的精确尺寸要求，同时保留原始图纸的细节和质量。

1. **导入所需的类**（请参见下面的逐步说明）。  
2. **创建 `CadLoadOptions` 实例** 并将 `width` 和 `height` 设置为目标尺寸。  
3. **实例化 `ImageConvertOptions`**，指定 `ImageFileType.Tiff`。  
4. **调用 `Converter` 对象的 `convert` 方法**，传入源路径、加载选项和转换选项。  

### 加载具有自定义尺寸的 CAD 文档（如何设置尺寸）

`CadLoadOptions` 类告诉 GroupDocs 在转换前如何光栅化图纸。

`CadLoadOptions` 是用于定义 CAD 文件渲染参数（如宽度、高度和 DPI）的配置对象。

#### 步骤 1：导入必要的库
```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.filetypes.ImageFileType;
import com.groupdocs.conversion.options.convert.ImageConvertOptions;
import com.groupdocs.conversion.options.load.CadLoadOptions;
```

#### 步骤 2：使用自定义尺寸设置加载选项
```java
String sourceDocumentPath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DWG_WITH_LAYOUTS_AND_LAYERS";
CadLoadOptions loadOptions = new CadLoadOptions();
loadOptions.setWidth(1920); // Specify the desired width in pixels
loadOptions.setHeight(1080); // Specify the desired height in pixels
Converter converter = new Converter(sourceDocumentPath, () -> loadOptions);
```
*说明：* 通过配置 `CadLoadOptions`，您告诉 **GroupDocs Conversion Java** 在任何进一步处理之前，以 1920 × 1080 像素光栅化 CAD 图纸。

### 将 CAD 转换为 TIFF 图像（Convert CAD to TIFF）

`ImageConvertOptions` 指示库使用您指定的设置生成 TIFF 文件。

`ImageConvertOptions` 封装了所有图像特定的转换参数，包括输出格式、分辨率和压缩级别。

#### 步骤 3：配置转换选项
```java
String convertedFilePath = "YOUR_OUTPUT_DIRECTORY/ConvertCadAndSpecifyWidthAndHeight.tiff";
ImageConvertOptions options = new ImageConvertOptions();
options.setFormat(ImageFileType.Tiff); // Set the conversion target to TIFF format
```

#### 步骤 4：执行转换
```java
converter.convert(convertedFilePath, options);
```
*说明：* 设置 `ImageFileType.Tiff` 可指示 **GroupDocs Conversion Java** 输出符合您先前定义的宽度和高度的高质量 TIFF 文件。

## 故障排除技巧与常见陷阱
- **文件路径问题：** 验证源路径和目标路径是否正确，并确保应用程序具有读/写权限。  
- **不支持的格式：** 确保 CAD 文件是受支持的格式之一（DWG、DGN、DXF 等）。  
- **内存限制：** 大型图纸可能需要增加 JVM 堆大小（`-Xmx2g` 或更高）。  
- **质量问题：** 如果默认 DPI 未达到您的质量标准，请调整 `ImageConvertOptions` 的分辨率设置。  

## 实际应用
1. **建筑可视化：** 将平面图导出为 TIFF，以用于高分辨率演示。  
2. **工程文档：** 生成标准化图像，以便嵌入技术手册。  
3. **自动化报告：** 通过 CI 流水线将 CAD 派生的 TIFF 嵌入 PDF 或 HTML 报告中。  

## 性能考虑因素
- **优化内存使用：** 转换完成后释放 `Converter` 实例（如适用，调用 `converter.close()`）。  
- **批处理：** 遍历 CAD 文件列表并复用单个 `Converter` 配置，以减少开销。  
- **保持更新：** 定期升级到最新的 GroupDocs Conversion Java 版本，以获得性能提升和错误修复。  

## 常见问题

**Q:** GroupDocs Conversion 支持哪些文件格式？  
**A:** 它支持超过 110 种格式，包括 DWG、DGN、DXF 等 CAD 文件，以及常见的图像、文档和归档类型。

**Q:** 我可以一次转换多个 CAD 文件吗？  
**A:** 可以——实现一个简单的循环，为每个文件创建新的 `Converter`，或使用相同实例并提供不同的源路径。

**Q:** 在转换过程中如何处理大文件？  
**A:** 增加 JVM 堆大小，将文件分成更小的批次处理，或使用库提供的流式选项。

**Q:** 如果输出图像质量不满意怎么办？  
**A:** 调整 `ImageConvertOptions` 中的 DPI 或缩放设置以提升分辨率。

**Q:** 如果遇到问题，是否有支持？  
**A:** GroupDocs 提供丰富的文档、社区论坛，以及对授权客户的直接支持。

## 资源
- [GroupDocs 文档](https://docs.groupdocs.com/conversion/java/)
- [API 参考](https://reference.groupdocs.com/conversion/java/)
- [下载最新版本](https://releases.groupdocs.com/conversion/java/)
- [购买许可证](https://purchase.groupdocs.com/buy)
- [免费试用访问](https://releases.groupdocs.com/conversion/java/)
- [临时许可证请求](https://purchase.groupdocs.com/temporary-license/)
- [支持论坛](https://forum.groupdocs.com/c/conversion/10)

---

**最后更新：** 2026-07-24  
**测试环境：** GroupDocs Conversion Java 25.2  
**作者：** GroupDocs  

---

## 相关教程

- [convert cad pdf java – GroupDocs.Conversion Java CAD 格式转换教程](/conversion/java/cad-formats/)
- [convert pdf to jpg java 使用 GroupDocs.Conversion – 指南](/conversion/java/document-operations/convert-pdf-to-jpg-groupdocs-java/)
- [如何为 GroupDocs.Conversion Java 设置许可证 - 步骤指南](/conversion/java/getting-started/groupdocs-conversion-java-license-setup-file-path/)