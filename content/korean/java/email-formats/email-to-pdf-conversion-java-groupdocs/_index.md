---
date: '2026-09-25'
description: GroupDocs.Conversion을 사용하여 eml을 pdf java로 변환하고, 정확한 타임스탬프를 유지하기 위해 timezone
  offset을 적용하는 방법을 배웁니다. Java 개발자를 위한 단계별 가이드.
keywords:
- convert eml to pdf java
- email to pdf conversion
- timezone offset java
lastmod: '2026-09-25'
og_description: GroupDocs.Conversion을 사용하여 eml을 pdf java로 변환하고, 정확한 타임스탬프를 유지하기 위해
  timezone offset을 적용하는 방법을 배웁니다. 개발자를 위한 상세 Java 가이드.
og_image_alt: 'Java guide: convert eml to pdf with timezone offset using GroupDocs.Conversion'
og_title: GroupDocs를 사용하여 timezone offset과 함께 eml을 pdf java로 변환
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
title: 시간대 오프셋을 적용하여 eml을 pdf java로 변환하는 방법
type: docs
url: /ko/java/email-formats/email-to-pdf-conversion-java-groupdocs/
weight: 1
---

# 시간대 오프셋을 포함한 eml을 pdf java로 변환하는 방법

이 튜토리얼에서는 **convert eml to pdf java**를 수행하면서 시간대 차이에 따라 타임스탬프를 올바르게 조정하는 방법을 알아봅니다. GroupDocs.Conversion for Java를 사용하여 Maven 설정부터 사용자 지정 오프셋으로 이메일을 로드하고 결과 PDF 파일을 스트리밍하는 전체 워크플로우를 확인할 수 있습니다. 이 단계는 올바른 현지 시간을 표시하는 신뢰할 수 있는 아카이브용 PDF가 필요한 Java 8+ 개발자를 위해 작성되었습니다.

## 빠른 답변
- **변환을 처리하는 라이브러리는 무엇인가요?** GroupDocs.Conversion for Java.  
- **시간대를 설정하는 주요 메서드는 무엇인가요?** `EmailLoadOptions.setTimeZoneOffset`.  
- **라이선스가 필요합니까?** A free trial works for testing; a full license is required for production.  
- **여러 이메일을 배치 처리할 수 있나요?** Yes—wrap the conversion loop in a batch routine.  
- **필요한 Java 버전은 무엇인가요?** JDK 8 or later.  

## convert eml to pdf java가 무엇인가요?
“convert eml to pdf java”라는 문구는 이메일 파일(보통 `.eml` 또는 `.msg`)을 가져와 Java 코드를 사용해 PDF 문서를 생성하는 과정을 설명합니다. 이 변환은 레이아웃을 보존하고 모든 플랫폼에서 볼 수 있기 때문에 아카이빙, 법적 준수 및 크로스 플랫폼 공유에 필수적입니다.

## 왜 GroupDocs.Conversion for Java를 사용하나요?
GroupDocs.Conversion은 `.eml`, `.msg`, `.pdf`, `.docx` 및 이미지 형식을 포함한 **70개 이상의** 입력 및 출력 형식을 지원합니다. 내장된 `EmailLoadOptions`를 사용하면 밀리초 단위로 시간대 오프셋을 지정할 수 있어 PDF 타임스탬프가 원하는 현지 시간과 일치하도록 보장합니다. 이 라이브러리는 파일을 스트리밍 방식으로 처리하여 전체 문서를 RAM에 로드하는 경우에 비해 메모리 사용량을 **80 %**까지 줄입니다.

## 전제 조건
1. **라이브러리 및 종속성**  
   - GroupDocs.Conversion for Java version **25.2** or later.  

2. **환경**  
   - JDK 8+이 설치되고 머신에 구성되어 있음.  
   - 빌드 자동화 도구로 Maven 사용.  

3. **지식**  
   - 기본 Java 프로그래밍, 특히 파일 I/O.  
   - Maven의 `pom.xml` 구조에 대한 이해.  

## GroupDocs.Conversion for Java 설정

### 설치 정보
`pom.xml`에 GroupDocs 저장소와 변환 종속성을 추가합니다:

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
무료 체험 또는 전체 기능 테스트를 위한 임시 라이선스를 요청할 수 있습니다:
- **무료 체험** – 라이브러리를 다운로드하고 기본 기능을 살펴보세요.  
- **임시 라이선스** – 임시 라이선스를 신청하세요 [임시 라이선스 페이지](https://purchase.groupdocs.com/temporary-license/).  
- **구매** – 장기 사용을 위해 [공식 사이트](https://purchase.groupdocs.com/buy)에서 라이선스를 구매하는 것을 고려하세요.

### 기본 초기화
다음은 `Converter` 인스턴스를 생성하고 시간대 오프셋을 사용해 이메일을 로드하는 데 필요한 최소 코드입니다:

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.load.EmailLoadOptions;

// Initialize GroupDocs.Conversion with necessary load options for email files
EmailLoadOptions loadOptions = new EmailLoadOptions();
loadOptions.setTimeZoneOffset(7200000.0); // Set timezone offset in milliseconds (e.g., 2 hours)
```

## 시간대 오프셋을 설정하는 방법?
`EmailLoadOptions`는 변환을 위해 이메일 파일을 로드하는 방식을 제어하는 구성 클래스입니다. 변환 전에 사용자 지정 오프셋으로 이메일을 로드하십시오. `setTimeZoneOffset` 메서드는 **밀리초** 단위의 오프셋을 받으며, +2시간 이동은 `7200000`과 같습니다. 이 조정은 생성된 PDF에 표시되는 타임스탬프를 재작성합니다. 오프셋을 제공함으로써 라이브러리는 표시된 송수신 시간을 재계산하여 생성된 PDF가 수신자의 현지 시간대를 반영하도록 합니다. 이는 아카이브된 커뮤니케이션을 검토하는 다국적 팀에 특히 유용합니다.

```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
loadOptions.setTimeZoneOffset(7200000.0); // Set to 2 hours ahead (in milliseconds)
```

## Converter 객체를 초기화하는 방법?
`Converter`는 제공된 로드 옵션을 사용하여 문서 변환을 수행하는 주요 클래스입니다. 소스 파일 경로와 이전에 정의한 `loadOptions`를 제공하는 람다를 전달하여 `Converter`를 생성합니다. 이렇게 하면 시간대 설정이 변환 프로세스와 연결됩니다. 소스 이메일을 읽고 `EmailLoadOptions` 설정(시간대 오프셋 포함)을 적용한 뒤 PDF 생성을 위한 출력 스트림을 준비합니다. 람다를 사용하면 옵션이 변환 시점에 평가되므로 다양한 설정을 가진 여러 파일을 처리할 때 유용합니다.

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.convert.PdfConvertOptions;

String sourceFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.eml"; // Path to the email document.
String outputPattern = "YOUR_OUTPUT_DIRECTORY/ConvertEmailWithTimezoneOffset-%d.pdf";

List<OutputStream> streamPool = new ArrayList<>();
Converter converter = new Converter(sourceFilePath, () -> loadOptions);
PdfConvertOptions options = new PdfConvertOptions();
```

## 변환을 실행하고 PDF 페이지를 스트리밍하는 방법?
`PdfConvertOptions`는 페이지 크기, 압축 및 이미지 품질과 같은 PDF 출력 설정을 지정합니다. `PdfConvertOptions` 인스턴스와 각 페이지에 대한 출력 스트림을 제공하여 `convert` 메서드를 호출합니다. `try‑finally` 블록은 모든 스트림이 닫히도록 보장하여 리소스 누수를 방지합니다. 옵션을 구성한 후 `convert` 메서드는 이메일의 각 페이지를 순회하며 PDF 데이터를 별도의 출력 스트림에 씁니다. 이 접근 방식은 각 페이지를 개별적으로 처리하고 플러시하므로 메모리 사용량을 최소화하면서 대용량 이메일을 효율적으로 처리할 수 있게 합니다.

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

## 실용적인 적용 사례
- **이메일 아카이빙** – 법적 또는 감사 목적을 위해 정확한 타임스탬프가 포함된 PDF를 저장합니다.  
- **시간대 간 협업** – 전 세계 팀이 변환된 문서에서 동일한 현지 시간을 확인합니다.  
- **이메일 보고** – 원본 송수신 시간을 보존하는 PDF 보고서를 생성하여 규정 준수를 지원합니다.

이 워크플로우를 CRM 시스템, 문서 관리 플랫폼 또는 자동화된 배치 작업에 삽입하여 문서 파이프라인을 간소화할 수 있습니다.

## 성능 고려 사항
- **리소스 관리** – (보여진 대로) 스트림을 즉시 닫아 메모리를 해제합니다.  
- **배치 처리** – `.eml` 파일 컬렉션을 순회하고 가능하면 단일 `Converter` 인스턴스를 재사용합니다.  
- **JVM 튜닝** – 대규모 배치에 대해 힙 크기(`-Xmx`)를 조정하여 `OutOfMemoryError`를 방지합니다.  

## 일반적인 문제 및 해결책
| 증상 | 가능한 원인 | 해결 방법 |
|---------|--------------|-----|
| `NullPointerException` at `loadOptions` | 로드 옵션이 올바르게 전달되지 않음 | `Converter`를 생성할 때 람다 `() -> loadOptions`가 사용되는지 확인하십시오. |
| PDF 출력이 비어 있음 | 입력 파일 경로가 잘못되었거나 파일이 없음 | `sourceFilePath`가 기존 `.eml` 파일을 가리키는지 확인하십시오. |
| 시간대가 반영되지 않음 | 오프셋 값이 잘못됨(예: 밀리초 대신 초) | **밀리초** 단위로 오프셋을 제공하십시오(예: +2 h는 `7200000`). |

## 자주 묻는 질문
**Q: GroupDocs.Conversion for Java가 무엇인가요?**  
A: 이메일을 PDF로 변환하는 것을 포함해 수십 가지 형식 간 문서 변환을 가능하게 하는 강력한 라이브러리이며, 내장된 시간대 처리를 제공합니다.

**Q: 이메일의 시간대 오프셋을 어떻게 설정하나요?**  
A: `Converter`를 초기화하기 전에 `EmailLoadOptions.setTimeZoneOffset(milliseconds)`를 사용합니다.

**Q: 이 설정으로 여러 이메일 형식을 변환할 수 있나요?**  
A: 예, 라이브러리는 `.eml`, `.msg` 및 기타 일반적인 이메일 파일 형식을 지원합니다.

**Q: 변환 중 흔히 발생하는 함정은 무엇인가요?**  
A: 종속성 누락, 잘못된 파일 경로, 오프셋을 잘못된 단위(초 대신 밀리초)로 제공하는 경우입니다.

**Q: GroupDocs.Conversion에 대한 추가 자료는 어디서 찾을 수 있나요?**  
A: 자세한 가이드와 API 레퍼런스는 [공식 문서](https://docs.groupdocs.com/conversion/java/)를 방문하십시오.

## 추가 자료
- **문서**: 자세히 살펴보려면 [GroupDocs Documentation](https://docs.groupdocs.com/conversion/java/)을 방문하십시오.  
- **API 레퍼런스**: 자세한 API 레퍼런스는 [API reference](https://reference.groupdocs.com/conversion/java/)에서 확인할 수 있습니다.  
- **GroupDocs.Conversion 다운로드**: 라이브러리를 시작하려면 [GroupDocs.Conversion download page](https://releases.groupdocs.com/conversion/java/)를 이용하십시오.  
- **구매**: 장기 사용을 위해 [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy)에서 라이선스를 구매하십시오.  
- **무료 체험 및 라이선스**: 무료로 사용해 보거나 [GroupDocs Free Trial](https://releases.groupdocs.com/conversion/java/) 및 [Temporary License](https://purchase.groupdocs.com/temporary-license/)에서 임시 라이선스를 요청하십시오.  
- **지원**: 도움이 필요하면 [GroupDocs Forum](https://forum.groupdocs.com/c/conversion/10)을 방문하십시오.  

Java 애플리케이션에서 GroupDocs.Conversion의 강력함을 활용하고 정확하고 시간대 인식이 가능한 PDF 변환을 오늘부터 누리세요!

---

**마지막 업데이트:** 2026-09-25  
**테스트 환경:** GroupDocs.Conversion 25.2  
**작성자:** GroupDocs

## 관련 튜토리얼
- [msg to pdf java – GroupDocs를 사용한 이메일 형식 변환](/conversion/java/email-formats/)
- [eml to pdf java – GroupDocs로 이메일을 PDF로 변환](/conversion/java/pdf-conversion/convert-emails-to-pdfs-groupdocs-java/)
- [GroupDocs.Conversion Java로 다중 파일 형식 변환 – 마스터 가이드](/conversion/java/document-operations/groupdocs-conversion-java-master-document-conversion/)