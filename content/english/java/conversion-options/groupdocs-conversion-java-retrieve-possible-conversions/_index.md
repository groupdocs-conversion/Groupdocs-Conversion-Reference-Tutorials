---
date: '2026-07-29'
description: Discover how to list formats and retrieve all possible conversions using
  GroupDocs.Conversion for Java, ideal for cloud storage file conversion workflows.
images:
- /java/conversion-options/groupdocs-conversion-java-retrieve-possible-conversions/og-image.png
keywords:
- how to list formats
- cloud storage file conversion
- GroupDocs.Conversion Java
lastmod: '2026-07-29'
og_description: Learn how to list formats and retrieve all possible conversions using
  GroupDocs.Conversion for Java. Ideal for cloud storage file conversion pipelines.
og_image_alt: 'Guide: List formats and get conversion matrix with GroupDocs.Conversion
  Java'
og_title: How to List Formats with GroupDocs.Conversion for Java
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
title: How to List Formats with GroupDocs.Conversion for Java
type: docs
url: /java/conversion-options/groupdocs-conversion-java-retrieve-possible-conversions/
weight: 1
---

# How to List Formats and Retrieve All Possible Conversions with GroupDocs.Conversion for Java

In many document‑processing projects the first step is to know **how to list formats** that the conversion engine supports. This tutorial shows you, step by step, how to query GroupDocs.Conversion for Java, retrieve every source‑to‑target pair, and apply that knowledge in cloud storage file conversion pipelines. By the end you’ll have a reusable method that returns the full conversion matrix, plus practical tips for performance and error handling.

## Quick Answers
- **What does “list formats” mean?** It returns every source‑to‑target conversion pair the library can handle.  
- **Do I need a license?** A free trial works for testing; a paid license is required for production.  
- **Can this help cloud storage file conversion?** Yes—knowing supported formats lets you automate conversions in cloud storage pipelines.  
- **Which Java version is required?** JDK 8 or later.  
- **Is the feature thread‑safe?** The `Converter` instance can be reused across threads, but dispose resources after use.

## What is “how to list formats” in GroupDocs.Conversion?
The **list formats** operation returns a collection that describes every source format together with the target formats it can be transformed into. This matrix is generated from the library’s internal conversion rules and is essential for building dynamic workflows that adapt to the actual capabilities of GroupDocs.Conversion at runtime.

## Why Use GroupDocs.Conversion for Java?
GroupDocs.Conversion for Java supports **200+ input formats** and **200+ output formats**, covering everything from DOCX and PPTX to PDF/A and image types. It runs completely on the server, so no Microsoft Office or Adobe products are required. The API is thread‑safe, can process multi‑hundred‑page documents without loading the entire file into memory, and integrates seamlessly with cloud storage services such as AWS S3, Azure Blob, and Google Cloud Storage.

## Prerequisites
- **Java Development Kit (JDK):** Version 8 or newer.  
- **Maven:** Properly configured in your IDE (IntelliJ IDEA, Eclipse, NetBeans, etc.).  
- **GroupDocs.Conversion for Java:** Added as a Maven dependency (see below).  

## Setting Up GroupDocs.Conversion for Java

Add the GroupDocs repository and dependency to your `pom.xml`:

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

### License Acquisition
Start with a free trial to explore the API. For production workloads, purchase a license or request a temporary evaluation license.

### Basic Initialization and Setup

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

## How to List Formats Using GroupDocs.Conversion for Java
`Converter` is the core class that performs conversions and provides format information. `getAllPossibleConversions()` returns a list of all supported source‑to‑target conversion pairs. `ConversionInfo` represents a single conversion mapping between a source and a target format.  

Load the `Converter` engine, call `getAllPossibleConversions()`, and you’ll receive a list of `ConversionInfo` objects that describe every permissible source‑to‑target pair. This single call is all you need to build a dropdown of export options, validate incoming files, or design batch‑migration scripts.

### Initialize and Retrieve Conversions

The `Converter` class is the core engine that provides conversion capabilities and exposes the `getAllPossibleConversions()` method.  

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.contracts.PossibleConversions;

public class GetAllPossibleConversionsFeature {
    public static void run() {
        // Initialize the Converter object
        Converter converter = new Converter();
```

### Iterate Over Possible Conversions

```java
// Retrieve all possible conversions supported by the library
for (PossibleConversions conversions : converter.getAllPossibleConversions()) {
    // Print source format description
    System.out.print(String.format("Source format: %s \n", conversions.getSource().getDescription()));
```

### Determine Conversion Types

```java
// Iterate through each target conversion available for the source format
for (TargetConversion conversion : conversions.getAll()) {
    // Determine if it's a primary or secondary conversion and print details
    System.out.print(String.format("\t...can be converted to %s format as %s conversion.\n",
            conversion.getFormat(),
            conversion.isPrimary() ? "primary" : "secondary"));
}
```

### Complete Function

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

## Cloud Storage File Conversion Use Cases
Knowing the full conversion matrix is especially valuable when building **cloud storage file conversion** services:

1. **Dynamic Format Detection:** When a file lands in cloud storage, you can instantly query whether the desired target format is supported.  
2. **Batch Migration:** Move large document libraries to a unified format (e.g., PDF/A) by iterating over supported source types.  
3. **User‑Driven Export:** Offer end‑users a dropdown of only the formats their current document can be exported to, reducing errors and improving UX.

## Performance Considerations
- **Resource Management:** Dispose of the `Converter` instance or use try‑with‑resources if you create many short‑lived converters.  
- **Batch Processing:** Group multiple files into a single job to reduce overhead.  
- **Caching:** Cache the result of `getAllPossibleConversions()` if you query it frequently; the conversion matrix rarely changes at runtime.  

## Common Issues and Solutions
| Symptom | Likely Cause | Fix |
|---------|--------------|-----|
| No output appears | `Converter` not initialized correctly | Ensure the library JAR is on the classpath and the license is loaded. |
| `TargetConversion` list is empty | Using an outdated library version | Upgrade to the latest GroupDocs.Conversion release. |
| Memory spikes on large documents | Not disposing of converter resources | Call `converter.close()` or use try‑with‑resources. |

## Frequently Asked Questions

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

**Last Updated:** 2026-07-29  
**Tested With:** GroupDocs.Conversion 25.2 for Java  
**Author:** GroupDocs

## Related Tutorials

- [Convert Word to PDF and Other File Formats with GroupDocs.Conversion for Java](/conversion/java/)
- [Word to PDF Java – Hide Tracked Changes & Conversion Options](/conversion/java/conversion-options/)
- [How to Track Conversion Progress in Java with GroupDocs - A Complete Guide](/conversion/java/conversion-events-logging/java-groupdocs-conversion-progress-listener/)