---
date: '2026-07-29'
description: GroupDocs.Conversion for Java를 사용하여 형식을 나열하고 가능한 모든 변환을 검색하는 방법을 알아보세요.
  클라우드 스토리지 파일 변환 워크플로에 적합합니다.
keywords:
- how to list formats
- cloud storage file conversion
- GroupDocs.Conversion Java
lastmod: '2026-07-29'
og_description: GroupDocs.Conversion for Java를 사용하여 형식을 나열하고 가능한 모든 변환을 검색하는 방법을 배워보세요.
  클라우드 스토리지 파일 변환 파이프라인에 적합합니다.
og_image_alt: 'Guide: List formats and get conversion matrix with GroupDocs.Conversion
  Java'
og_title: GroupDocs.Conversion for Java를 사용하여 형식 나열하는 방법
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
title: GroupDocs.Conversion for Java를 사용하여 형식 나열하는 방법
type: docs
url: /ko/java/conversion-options/groupdocs-conversion-java-retrieve-possible-conversions/
weight: 1
---

# GroupDocs.Conversion for Java를 사용하여 형식 목록을 가져오고 모든 가능한 변환을 검색하는 방법

많은 문서 처리 프로젝트에서 첫 번째 단계는 변환 엔진이 지원하는 **형식 목록을 어떻게 가져오는지** 아는 것입니다. 이 튜토리얼에서는 GroupDocs.Conversion for Java를 단계별로 쿼리하고, 모든 소스‑대‑타깃 쌍을 검색한 뒤, 클라우드 스토리지 파일 변환 파이프라인에 적용하는 방법을 보여줍니다. 마지막에는 전체 변환 매트릭스를 반환하는 재사용 가능한 메서드와 성능 및 오류 처리에 대한 실용적인 팁을 제공받게 됩니다.

## 빠른 답변
- **“list formats”는 무엇을 의미합니까?** 라이브러리가 처리할 수 있는 모든 소스‑대‑타깃 변환 쌍을 반환합니다.  
- **라이선스가 필요합니까?** 무료 체험은 테스트에 사용할 수 있으며, 프로덕션에는 유료 라이선스가 필요합니다.  
- **클라우드 스토리지 파일 변환에 도움이 될 수 있나요?** 예—지원되는 형식을 알면 클라우드 스토리지 파이프라인에서 변환을 자동화할 수 있습니다.  
- **필요한 Java 버전은?** JDK 8 이상.  
- **이 기능은 스레드 안전합니까?** `Converter` 인스턴스를 여러 스레드에서 재사용할 수 있지만, 사용 후 리소스를 해제해야 합니다.

## GroupDocs.Conversion에서 “list formats”란 무엇인가요?
**list formats** 작업은 변환 가능한 모든 소스 형식과 해당 형식을 변환할 수 있는 대상 형식을 설명하는 컬렉션을 반환합니다. 이 매트릭스는 라이브러리 내부 변환 규칙에서 생성되며, 런타임에 GroupDocs.Conversion의 실제 기능에 맞게 동적 워크플로를 구축하는 데 필수적입니다.

## 왜 GroupDocs.Conversion for Java를 사용해야 할까요?
GroupDocs.Conversion for Java는 **200개 이상의 입력 형식**과 **200개 이상의 출력 형식**을 지원하며, DOCX와 PPTX부터 PDF/A 및 이미지 유형까지 모두 포괄합니다. 서버에서 완전히 실행되므로 Microsoft Office나 Adobe 제품이 필요하지 않습니다. API는 스레드 안전하며, 전체 파일을 메모리에 로드하지 않고 수백 페이지 문서를 처리할 수 있고, AWS S3, Azure Blob, Google Cloud Storage와 같은 클라우드 스토리지 서비스와 원활하게 통합됩니다.

## Prerequisites
- **Java Development Kit (JDK):** 버전 8 이상.  
- **Maven:** IDE(IntelliJ IDEA, Eclipse, NetBeans 등)에서 올바르게 구성되어 있어야 합니다.  
- **GroupDocs.Conversion for Java:** Maven 의존성으로 추가 (아래 참고).

## GroupDocs.Conversion for Java 설정하기

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

### 라이선스 획득
API를 탐색하려면 무료 체험으로 시작하십시오. 프로덕션 작업에는 라이선스를 구매하거나 임시 평가 라이선스를 요청하십시오.

### 기본 초기화 및 설정

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

## GroupDocs.Conversion for Java를 사용하여 형식 목록을 가져오는 방법
`Converter`는 변환을 수행하고 형식 정보를 제공하는 핵심 클래스입니다. `getAllPossibleConversions()`는 지원되는 모든 소스‑대‑타깃 변환 쌍의 목록을 반환합니다. `ConversionInfo`는 소스와 대상 형식 사이의 단일 변환 매핑을 나타냅니다.

`Converter` 엔진을 로드하고 `getAllPossibleConversions()`를 호출하면, 허용되는 모든 소스‑대‑타깃 쌍을 설명하는 `ConversionInfo` 객체 목록을 받게 됩니다. 이 단일 호출만으로 내보내기 옵션 드롭다운을 구축하거나, 들어오는 파일을 검증하거나, 배치 마이그레이션 스크립트를 설계할 수 있습니다.

### 초기화 및 변환 검색

The `Converter` class is the core engine that provides conversion capabilities and exposes the `getAllPossibleConversions()` method.  

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.contracts.PossibleConversions;

public class GetAllPossibleConversionsFeature {
    public static void run() {
        // Initialize the Converter object
        Converter converter = new Converter();
```

### 가능한 변환 반복하기

```java
// Retrieve all possible conversions supported by the library
for (PossibleConversions conversions : converter.getAllPossibleConversions()) {
    // Print source format description
    System.out.print(String.format("Source format: %s \n", conversions.getSource().getDescription()));
```

### 변환 유형 결정하기

```java
// Iterate through each target conversion available for the source format
for (TargetConversion conversion : conversions.getAll()) {
    // Determine if it's a primary or secondary conversion and print details
    System.out.print(String.format("\t...can be converted to %s format as %s conversion.\n",
            conversion.getFormat(),
            conversion.isPrimary() ? "primary" : "secondary"));
}
```

### 완전한 함수

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

## 클라우드 스토리지 파일 변환 사용 사례
전체 변환 매트릭스를 아는 것은 **클라우드 스토리지 파일 변환** 서비스를 구축할 때 특히 가치가 있습니다:

1. **동적 형식 감지:** 파일이 클라우드 스토리지에 도착하면 원하는 대상 형식이 지원되는지 즉시 조회할 수 있습니다.  
2. **배치 마이그레이션:** 지원되는 소스 유형을 반복하여 대규모 문서 라이브러리를 통합 형식(예: PDF/A)으로 이동합니다.  
3. **사용자 주도 내보내기:** 현재 문서가 내보낼 수 있는 형식만을 드롭다운으로 제공하여 오류를 줄이고 사용자 경험을 향상시킵니다.

## 성능 고려 사항
- **리소스 관리:** 많은 단기 `Converter` 인스턴스를 생성하는 경우 `Converter` 인스턴스를 해제하거나 try‑with‑resources를 사용하십시오.  
- **배치 처리:** 오버헤드를 줄이기 위해 여러 파일을 하나의 작업으로 그룹화하십시오.  
- **캐싱:** 자주 조회한다면 `getAllPossibleConversions()` 결과를 캐시하십시오; 변환 매트릭스는 런타임에 거의 변경되지 않습니다.

## 일반적인 문제와 해결책
| 증상 | 가능한 원인 | 해결 방법 |
|---------|--------------|-----|
| 출력이 나타나지 않음 | `Converter`가 올바르게 초기화되지 않음 | 라이브러리 JAR가 클래스패스에 있고 라이선스가 로드되었는지 확인하십시오. |
| `TargetConversion` 목록이 비어 있음 | 구버전 라이브러리 사용 | 최신 GroupDocs.Conversion 릴리스로 업그레이드하십시오. |
| 대형 문서에서 메모리 급증 | 컨버터 리소스를 해제하지 않음 | `converter.close()`를 호출하거나 try‑with‑resources를 사용하십시오. |

## 자주 묻는 질문

**Q: GroupDocs.Conversion for Java란 무엇인가요?**  
A: 서버‑사이드 라이브러리로 200개 이상의 입력 및 200개 이상의 출력 형식을 지원하며, 외부 소프트웨어 없이 빠르고 라이선스‑무료로 문서를 변환할 수 있습니다.

**Q: GroupDocs.Conversion을 어떻게 시작하나요?**  
A: Maven 프로젝트를 설정하고, 앞서 보여준 의존성을 추가한 뒤, 라이선스 파일을 로드하고 초기화 섹션에示된 대로 `Converter` 클래스를 인스턴스화하십시오.

**Q: GroupDocs.Conversion으로 사용자 정의 파일 형식을 변환할 수 있나요?**  
A: 예—API의 확장 지점을 통해 사용자 정의 컨버터를 등록하거나 서드파티 핸들러를 플러그인하여 독점 형식을 처리할 수 있습니다.

**Q: 변환 구현 시 흔히 겪는 함정은 무엇인가요?**  
A: `Converter`를 닫지 않거나 오래된 JAR 버전을 사용하거나 대용량 PDF의 메모리 사용을 간과하는 경우가 있습니다. 위의 리소스‑관리 팁을 따르세요.

**Q: 추가 도움을 어디서 받을 수 있나요?**  
A: 공식 [documentation](https://docs.groupdocs.com/conversion/java/)을 방문하거나 GroupDocs 커뮤니티 포럼에 질문하십시오.

**Last Updated:** 2026-07-29  
**Tested With:** GroupDocs.Conversion 25.2 for Java  
**Author:** GroupDocs

## 관련 튜토리얼

- [Convert Word to PDF and Other File Formats with GroupDocs.Conversion for Java](/conversion/java/)
- [Word to PDF Java – Hide Tracked Changes & Conversion Options](/conversion/java/conversion-options/)
- [How to Track Conversion Progress in Java with GroupDocs - A Complete Guide](/conversion/java/conversion-events-logging/java-groupdocs-conversion-progress-listener/)