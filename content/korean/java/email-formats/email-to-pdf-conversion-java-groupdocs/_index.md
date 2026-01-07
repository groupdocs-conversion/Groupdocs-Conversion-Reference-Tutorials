---
date: '2025-12-26'
description: GroupDocs.Conversion for Java를 사용하여 이메일을 PDF로 변환하고 시간대 오프셋을 관리하는 방법을
  배워보세요. 보관 및 시간대 간 협업에 이상적입니다.
keywords:
- Email to PDF Conversion
- Timezone Offset in Java
- GroupDocs.Conversion for Java
title: Java와 GroupDocs.Conversion을 사용하여 이메일을 PDF로 변환하고 시간대 오프셋 적용하는 방법
type: docs
url: /ko/java/email-formats/email-to-pdf-conversion-java-groupdocs/
weight: 1
---

# Java에서 GroupDocs.Conversion을 사용하여 타임존 오프셋으로 이메일을 PDF로 변환하는 방법

이메일 문서를 PDF로 변환하는 것은 어려울 수 있으며, 특히 정확한 타임존 정보를 유지하는 것이 중요합니다. 이 튜토리얼에서는 GroupDocs.Conversion for Java를 사용하여 사용자 정의 타임존 오프셋으로 **이메일을 PDF로 변환하는 방법**을 배웁니다. 규정 준수를 위해 이메일을 보관하거나 전 세계 팀과 공유하든, 이 가이드는 프로젝트 설정부터 최종 변환까지 모든 단계를 안내하여 신뢰할 수 있는 솔루션을 빠르게 구현할 수 있도록 도와줍니다.

## 빠른 답변
- **변환을 처리하는 라이브러리는 무엇인가요?** GroupDocs.Conversion for Java.  
- **타임존을 설정하는 주요 메서드는 무엇인가요?** `EmailLoadOptions.setTimeZoneOffset`.  
- **라이선스가 필요합니까?** 테스트용으로는 무료 체험판으로 충분하며, 프로덕션에서는 정식 라이선스가 필요합니다.  
- **여러 이메일을 배치 처리할 수 있나요?** 예—변환 루프를 배치 루틴으로 감싸면 됩니다.  
- **필요한 Java 버전은 무엇인가요?** JDK 8 이상.

## “이메일을 PDF로 변환”이란 무엇이며 왜 타임존이 중요한가요?

이메일(`.eml`, `.msg` 등)을 PDF로 변환하면 원본 타임스탬프가 그대로 복사됩니다. 이메일이 다른 타임존에서 전송된 경우, 해당 타임스탬프는 다른 지역의 독자에게 오해를 일으킬 수 있습니다. **타임존 오프셋**을 적용하면 PDF가 올바른 현지 시간을 반영하도록 하여 커뮤니케이션의 맥락을 보존합니다.

## 왜 Java용 GroupDocs.Conversion을 사용하나요?

- **광범위한 포맷 지원** – `.eml`, `.msg` 및 기타 많은 이메일 형식을 처리합니다.  
- **내장 타임존 처리** – `EmailLoadOptions`를 사용하면 밀리초 단위로 오프셋을 설정할 수 있습니다.  
- **고성능** – 스트림 기반 변환으로 메모리 사용량을 줄입니다.  
- **엔터프라이즈 수준 라이선스** – 유연한 체험 및 구매 옵션을 제공합니다.

## 사전 요구 사항

1. **라이브러리 및 종속성**  
   - GroupDocs.Conversion for Java 버전 25.2 이상.  

2. **환경 설정**  
   - Java Development Kit (JDK 8+)가 설치되어 있어야 합니다.  
   - Maven을 빌드 도구로 사용합니다.  

3. **지식**  
   - 기본 Java 프로그래밍 및 파일 I/O.  
   - Maven 종속성 관리에 대한 이해.

## Java용 GroupDocs.Conversion 설정

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

전체 기능 테스트를 위해 무료 체험판으로 시작하거나 임시 라이선스를 요청할 수 있습니다:

- **Free Trial** – 라이브러리를 다운로드하고 기본 기능을 살펴봅니다.  
- **Temporary License** – 임시 라이선스를 신청하려면 [here](https://purchase.groupdocs.com/temporary-license/)를 클릭합니다.  
- **Purchase** – 장기 사용을 위해 [official site](https://purchase.groupdocs.com/buy)에서 라이선스를 구매하는 것을 고려하십시오.

### 기본 초기화

다음은 `Converter` 인스턴스를 생성하고 타임존 오프셋을 적용하여 이메일을 로드하는 최소 코드입니다:

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.load.EmailLoadOptions;

// Initialize GroupDocs.Conversion with necessary load options for email files
EmailLoadOptions loadOptions = new EmailLoadOptions();
loadOptions.setTimeZoneOffset(7200000.0); // Set timezone offset in milliseconds (e.g., 2 hours)
```

## 구현 가이드

### 이메일 문서 로드 옵션

타임존 오프셋을 설정하면 PDF가 올바른 현지 시간을 반영합니다.

#### 단계 1 – 타임존 오프셋 설정

```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
loadOptions.setTimeZoneOffset(7200000.0); // Set to 2 hours ahead (in milliseconds)
```

*설명*: `setTimeZoneOffset`은 지정된 밀리초 수만큼 문서의 타임스탬프를 조정합니다.

### 변환 설정 및 실행

#### 단계 2 – Converter 객체 초기화

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.convert.PdfConvertOptions;

String sourceFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.eml"; // Path to the email document.
String outputPattern = "YOUR_OUTPUT_DIRECTORY/ConvertEmailWithTimezoneOffset-%d.pdf";

List<OutputStream> streamPool = new ArrayList<>();
Converter converter = new Converter(sourceFilePath, () -> loadOptions);
PdfConvertOptions options = new PdfConvertOptions();
```

*설명*: `Converter`는 소스 파일 경로와 이전에 정의한 `loadOptions`를 제공하는 람다와 함께 생성됩니다. 이렇게 하면 타임존 설정이 변환 프로세스와 연결됩니다.

#### 단계 3 – 변환 실행

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

*설명*: `convert` 메서드는 각 PDF 페이지를 고유한 파일 이름으로 스트리밍합니다. `try‑finally` 블록은 모든 스트림을 닫아 자원 누수를 방지합니다.

## 실용적인 적용 사례

- **Archiving Emails** – 법적 또는 감사 목적을 위해 정확한 타임스탬프가 포함된 PDF를 저장합니다.  
- **Cross‑Timezone Collaboration** – 전 세계 팀이 변환된 문서에서 동일한 현지 시간을 확인합니다.  
- **Email Reporting** – 원본 송수신 시간을 보존하는 PDF 보고서를 생성합니다.

이 워크플로우를 CRM 시스템, 문서 관리 플랫폼 또는 자동화된 배치 작업과 통합하여 문서 파이프라인을 효율화할 수 있습니다.

## 성능 고려 사항

- **Resource Management** – (위와 같이) 스트림을 즉시 닫아 메모리를 해제합니다.  
- **Batch Processing** – `.eml` 파일 컬렉션을 순회하고 가능한 경우 단일 `Converter` 인스턴스를 재사용합니다.  
- **JVM Tuning** – 대량 배치 시 `OutOfMemoryError`를 방지하기 위해 힙 크기(`-Xmx`)를 조정합니다.

## 일반적인 문제 및 해결책

| 증상 | 가능한 원인 | 해결 방법 |
|------|------------|----------|
| `NullPointerException` at `loadOptions` | 로드 옵션이 올바르게 전달되지 않음 | `Converter`를 생성할 때 람다 `() -> loadOptions`가 사용되었는지 확인합니다. |
| PDF 출력이 비어 있음 | 입력 파일 경로가 잘못되었거나 파일이 없음 | `sourceFilePath`가 존재하는 `.eml` 파일을 가리키는지 확인합니다. |
| 타임존이 반영되지 않음 | 오프셋 값이 잘못됨(예: 밀리초가 아닌 초) | **밀리초** 단위로 오프셋을 제공하세요(예: +2 h는 `7200000`). |

## 자주 묻는 질문

**Q: GroupDocs.Conversion for Java란 무엇인가요?**  
A: 이메일을 PDF로 변환을 포함해 수십 가지 포맷 간 문서 변환을 가능하게 하는 강력한 라이브러리입니다.

**Q: 이메일에 대한 타임존 오프셋을 어떻게 설정하나요?**  
A: `Converter`를 초기화하기 전에 `EmailLoadOptions.setTimeZoneOffset(milliseconds)`를 사용합니다.

**Q: 이 설정으로 여러 이메일 포맷을 변환할 수 있나요?**  
A: 예, 라이브러리는 `.eml`, `.msg` 및 기타 일반적인 이메일 파일 형식을 지원합니다.

**Q: 변환 중 흔히 발생하는 실수는 무엇인가요?**  
A: 종속성 누락, 잘못된 파일 경로, 오프셋을 잘못된 단위(초 대신 밀리초)로 제공하는 경우입니다.

**Q: GroupDocs.Conversion에 대한 추가 자료는 어디에서 찾을 수 있나요?**  
A: 자세한 가이드와 API 레퍼런스는 [official documentation](https://docs.groupdocs.com/conversion/java/)을 방문하십시오.

## 리소스

- **Documentation**: 자세히 보려면 [GroupDocs Documentation](https://docs.groupdocs.com/conversion/java/)을 확인하십시오.  
- **API Reference**: 상세 API 레퍼런스는 [here](https://reference.groupdocs.com/conversion/java/)에서 확인할 수 있습니다.  
- **Download GroupDocs.Conversion**: 라이브러리를 시작하려면 [here](https://releases.groupdocs.com/conversion/java/)에서 다운로드하십시오.  
- **Purchase**: 장기 사용을 위해 [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy)에서 라이선스를 구매하십시오.  
- **Free Trial & License**: 무료 체험을 해보거나 임시 라이선스를 요청하려면 [GroupDocs Free Trial](https://releases.groupdocs.com/conversion/java/) 및 [Temporary License](https://purchase.groupdocs.com/temporary-license/)를 방문하십시오.  
- **Support**: 지원이 필요하면 [GroupDocs Forum](https://forum.groupdocs.com/c/conversion/10)을 방문하십시오.

Java 애플리케이션에서 GroupDocs.Conversion의 강력함을 활용하고 정확한 타임존 인식 PDF 변환을 오늘부터 누리세요!

---

**Last Updated:** 2025-12-26  
**Tested With:** GroupDocs.Conversion 25.2  
**Author:** GroupDocs