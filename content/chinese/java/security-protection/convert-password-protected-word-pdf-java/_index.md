---
"date": "2025-04-28"
"description": "学习如何使用 GroupDocs.Conversion for Java 将受密码保护的 Word 文档转换为 PDF。掌握如何指定页面、调整 DPI 以及旋转内容。"
"title": "使用 GroupDocs.Conversion 在 Java 中将受密码保护的 Word 转换为 PDF"
"url": "/zh/java/security-protection/convert-password-protected-word-pdf-java/"
"weight": 1
type: docs
---
# 使用 GroupDocs.Conversion 在 Java 中将受密码保护的 Word 转换为 PDF

这份全面的指南将指导您如何使用 Java 中的 GroupDocs.Conversion 库，轻松将受保护的 Word 文档转换为 PDF 格式。了解如何指定特定页面、设置自定义尺寸、调整分辨率以及优化性能，以实现无缝文档转换。

## 您将学到什么：
- 使用 GroupDocs.Conversion for Java 转换受密码保护的 Word 文件。
- 指定文档的确切页面或部分以进行 PDF 转换。
- 在转换为 PDF 之前旋转文档内容。
- 在 PDF 转换期间调整自定义分辨率的 DPI 设置。
- 利用 Java 内存管理的最佳实践来提高性能。

## 先决条件
在继续操作之前，请确保您已满足以下先决条件：

### 所需的库和依赖项
要使用 GroupDocs.Conversion，请添加必要的库。如果使用 Maven，请将存储库和依赖项添加到您的 `pom.xml`：

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

### 环境设置
确保您的计算机上已安装并配置 Java 开发工具包 (JDK)。建议您对 Java 编程有基本的了解。

### 许可证获取
GroupDocs.Conversion 提供免费试用版，方便您测试各项功能。如需长期使用，请考虑从以下平台获取临时或完整许可证： [GroupDocs 购买](https://purchase。groupdocs.com/buy).

## 为 Java 设置 GroupDocs.Conversion
要开始使用 GroupDocs.Conversion，请在项目中执行一些初始设置。

### Maven 设置
包含前面提到的必要的 Maven 依赖项，以确保下载所有必需的库并可供使用。

### 基本初始化
通过创建以下实例来初始化 GroupDocs.Conversion `Converter` 类。这是一个基本设置：

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.load.WordProcessingLoadOptions;

WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
// 如果需要，请为受保护的文档设置密码：
loadOptions.setPassword("your_password_here");

Converter converter = new Converter("path_to_your_document.docx", () -> loadOptions);
```

此代码片段初始化文档的转换。 `loadOptions` 类有助于管理密码保护和其他设置。

## 实施指南
让我们探索如何使用 Java 中的 GroupDocs.Conversion 实现关键功能。

### 将受密码保护的文档转换为 PDF
**概述：**
将受密码保护的 Word 文档无缝转换为 PDF 文件。

#### 逐步实施
##### 使用密码初始化加载选项
设置访问受保护文档的密码：

```java
WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
loadOptions.setPassword("12345"); // 替换为您的实际密码。
```

##### 设置转换器并转换
初始化 `Converter` 类，定义PDF转换选项，并执行转换：

```java
import com.groupdocs.conversion.options.convert.PdfConvertOptions;

String convertedFile = "YOUR_OUTPUT_DIRECTORY/ConvertedDocument.pdf";
PdfConvertOptions options = new PdfConvertOptions();

Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/SampleProtectedDocx.docx", () -> loadOptions);
converter.convert(convertedFile, options);
```

**解释：**
这 `loadOptions` 对象对于处理受密码保护的文档至关重要。正确设置密码可确保成功访问和转换。

#### 故障排除提示
- 仔细检查密码的准确性；拼写错误是常见问题。
- 验证文件路径以防止 `FileNotFoundException`。

### 指定要转换的 PDF 页面
**概述：**
选择文档的特定页面进行 PDF 转换。

#### 逐步实施
##### 设置页面范围
定义要转换的页面：

```java
PdfConvertOptions options = new PdfConvertOptions();
options.setPageNumber(2); // 从第 2 页开始。
options.setPagesCount(1); // 仅转换一页。
```

##### 转换过程
使用指定的设置 `options` 转换：

```java
String convertedFile = "YOUR_OUTPUT_DIRECTORY/SelectedPagesPdf.pdf";
Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/SampleDocx.docx", () -> loadOptions);
converter.convert(convertedFile, options);
```

**解释：**
这 `setPageNumber()` 和 `setPagesCount()` 方法可以精确控制要转换的文档部分。

### PDF转换中旋转页面
**概述：**
在转换过程中旋转页面以实现所需的方向。

#### 逐步实施
##### 设置旋转选项
指定旋转设置：

```java
import com.groupdocs.conversion.options.convert.Rotation;

PdfConvertOptions options = new PdfConvertOptions();
options.setRotate(Rotation.On180); // 将页面旋转 180 度。
```

##### 执行转换
使用指定的旋转选项进行初始化和转换：

```java
String convertedFile = "YOUR_OUTPUT_DIRECTORY/RotatedPagesPdf.pdf";
Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/SampleDocx.docx", () -> loadOptions);
converter.convert(convertedFile, options);
```

**解释：**
旋转页面对于纠正方向或满足特定的布局要求很有用。

### 设置 PDF 转换的 Dpi
**概述：**
调整转换后的 PDF 的分辨率 (DPI) 以满足质量需求。

#### 逐步实施
##### 配置 DPI 设置
设置所需的 DPI 值：

```java
PdfConvertOptions options = new PdfConvertOptions();
options.setDpi(300); // 将 DPI 设置为 300 以获得高分辨率。
```

##### 使用自定义 DPI 执行转换
使用以下设置继续转换：

```java
String convertedFile = "YOUR_OUTPUT_DIRECTORY/HighResolutionPdf.pdf";
Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/SampleDocx.docx", () -> loadOptions);
converter.convert(convertedFile, options);
```

**解释：**
较高的 DPI 值可提升图像质量，但可能会增加文件大小。请根据您的需求进行调整。

### 设置 PDF 转换的宽度和高度
**概述：**
在转换过程中自定义生成的 PDF 的尺寸。

#### 逐步实施
##### 定义维度
设置宽度和高度参数：

```java
PdfConvertOptions options = new PdfConvertOptions();
options.setWidth(1024); // 将宽度设置为 1024 像素。
options.setHeight(768); // 将高度设置为 768 像素。
```

##### 使用自定义尺寸进行转换
使用以下尺寸继续进行转换：

```java
String convertedFile = "YOUR_OUTPUT_DIRECTORY/SizedPdf.pdf";
Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/SampleDocx.docx", () -> loadOptions);
converter.convert(convertedFile, options);
```

**解释：**
自定义尺寸有助于根据特定的显示或打印要求定制输出 PDF。