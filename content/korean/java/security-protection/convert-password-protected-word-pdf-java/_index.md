---
"date": "2025-04-28"
"description": "GroupDocs.Conversion for Java를 사용하여 암호로 보호된 Word 문서를 PDF로 변환하는 방법을 알아보세요. 페이지 지정, DPI 조정, 콘텐츠 회전을 완벽하게 익히세요."
"title": "GroupDocs.Conversion을 사용하여 Java에서 암호로 보호된 Word를 PDF로 변환"
"url": "/ko/java/security-protection/convert-password-protected-word-pdf-java/"
"weight": 1
---

# GroupDocs.Conversion을 사용하여 Java에서 암호로 보호된 Word를 PDF로 변환

Java에서 GroupDocs.Conversion 라이브러리를 활용하는 방법에 대한 포괄적인 가이드를 통해 보호된 Word 문서를 PDF 형식으로 손쉽게 변환하세요. 특정 페이지를 지정하고, 사용자 지정 크기를 설정하고, 해상도를 조정하고, 원활한 문서 변환을 위해 성능을 최적화하는 방법을 알아보세요.

## 배울 내용:
- GroupDocs.Conversion for Java를 사용하여 암호로 보호된 Word 파일을 변환합니다.
- PDF 변환을 위해 문서의 정확한 페이지나 섹션을 지정하세요.
- PDF로 변환하기 전에 문서 내용을 회전합니다.
- PDF 변환 중에 사용자 정의 해상도에 맞게 DPI 설정을 조정합니다.
- Java 메모리 관리의 모범 사례를 통해 성능을 향상시키세요.

## 필수 조건
계속 진행하기 전에 다음 전제 조건이 충족되었는지 확인하세요.

### 필수 라이브러리 및 종속성
GroupDocs.Conversion을 사용하려면 필요한 라이브러리를 포함하세요. Maven을 사용하는 경우 저장소와 종속성을 추가하세요. `pom.xml`:

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

### 환경 설정
컴퓨터에 Java Development Kit(JDK)가 설치 및 구성되어 있는지 확인하세요. Java 프로그래밍에 대한 기본적인 이해가 권장됩니다.

### 라이센스 취득
GroupDocs.Conversion은 기능 테스트를 위한 무료 평가판을 제공합니다. 장기간 사용하려면 임시 또는 정식 라이선스를 구매하는 것이 좋습니다. [GroupDocs 구매](https://purchase.groupdocs.com/buy).

## Java용 GroupDocs.Conversion 설정
GroupDocs.Conversion을 시작하려면 프로젝트에서 몇 가지 초기 설정을 수행하세요.

### Maven 설정
이전에 언급한 대로 필요한 Maven 종속성을 포함하여 모든 필수 라이브러리가 다운로드되어 사용 가능한지 확인하세요.

### 기본 초기화
GroupDocs.Conversion을 초기화하려면 인스턴스를 생성해야 합니다. `Converter` 클래스. 기본 설정은 다음과 같습니다.

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.load.WordProcessingLoadOptions;

WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
// 필요한 경우 보호된 문서에 대한 암호를 설정하세요.
loadOptions.setPassword("your_password_here");

Converter converter = new Converter("path_to_your_document.docx", () -> loadOptions);
```

이 스니펫은 문서의 변환을 초기화합니다. `loadOptions` 클래스는 암호 보호 및 기타 설정을 관리하는 데 도움이 됩니다.

## 구현 가이드
Java에서 GroupDocs.Conversion을 사용하여 주요 기능을 구현하는 방법을 살펴보겠습니다.

### 암호로 보호된 문서를 PDF로 변환
**개요:**
암호로 보호된 Word 문서를 원활하게 PDF 파일로 변환하세요.

#### 단계별 구현
##### 비밀번호로 로드 옵션 초기화
보호된 문서에 액세스하기 위한 비밀번호를 설정하세요:

```java
WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
loadOptions.setPassword("12345"); // 실제 비밀번호로 바꿔주세요.
```

##### 변환기 설정 및 변환
초기화 `Converter` 클래스에서 PDF 변환 옵션을 정의하고 변환을 수행합니다.

```java
import com.groupdocs.conversion.options.convert.PdfConvertOptions;

String convertedFile = "YOUR_OUTPUT_DIRECTORY/ConvertedDocument.pdf";
PdfConvertOptions options = new PdfConvertOptions();

Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/SampleProtectedDocx.docx", () -> loadOptions);
converter.convert(convertedFile, options);
```

**설명:**
그만큼 `loadOptions` 객체는 암호로 보호된 문서를 처리하는 데 매우 중요합니다. 암호를 올바르게 설정하면 접근 및 변환이 성공적으로 이루어집니다.

#### 문제 해결 팁
- 비밀번호의 정확성을 다시 한번 확인하세요. 오타는 흔한 문제입니다.
- 파일 경로를 확인하여 방지하세요. `FileNotFoundException`.

### PDF로 변환할 페이지 지정
**개요:**
PDF로 변환할 문서의 특정 페이지를 선택하세요.

#### 단계별 구현
##### 페이지 범위 설정
변환할 페이지를 정의하세요.

```java
PdfConvertOptions options = new PdfConvertOptions();
options.setPageNumber(2); // 2페이지부터 시작하세요.
options.setPagesCount(1); // 한 페이지만 변환하세요.
```

##### 변환 프로세스
지정된 설정을 사용하십시오. `options` 변환을 위해:

```java
String convertedFile = "YOUR_OUTPUT_DIRECTORY/SelectedPagesPdf.pdf";
Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/SampleDocx.docx", () -> loadOptions);
converter.convert(convertedFile, options);
```

**설명:**
그만큼 `setPageNumber()` 그리고 `setPagesCount()` 이 방법을 사용하면 어떤 문서 섹션을 변환할지 정확하게 제어할 수 있습니다.

### PDF 변환에서 페이지 회전
**개요:**
원하는 방향을 얻으려면 변환하는 동안 페이지를 회전하세요.

#### 단계별 구현
##### 회전 옵션 설정
회전 설정 지정:

```java
import com.groupdocs.conversion.options.convert.Rotation;

PdfConvertOptions options = new PdfConvertOptions();
options.setRotate(Rotation.On180); // 페이지를 180도 회전합니다.
```

##### 변환 실행
지정된 회전 옵션으로 초기화하고 변환합니다.

```java
String convertedFile = "YOUR_OUTPUT_DIRECTORY/RotatedPagesPdf.pdf";
Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/SampleDocx.docx", () -> loadOptions);
converter.convert(convertedFile, options);
```

**설명:**
페이지를 회전하면 방향을 수정하거나 특정 레이아웃 요구 사항을 충족하는 데 유용할 수 있습니다.

### PDF 변환을 위한 Dpi 설정
**개요:**
변환된 PDF의 해상도(DPI)를 품질 요구 사항에 맞게 조정하세요.

#### 단계별 구현
##### DPI 설정 구성
원하는 DPI 값을 설정하세요:

```java
PdfConvertOptions options = new PdfConvertOptions();
options.setDpi(300); // 고해상도를 원하시면 DPI를 300으로 설정하세요.
```

##### 사용자 정의 DPI로 변환 수행
다음 설정을 사용하여 변환을 진행하세요.

```java
String convertedFile = "YOUR_OUTPUT_DIRECTORY/HighResolutionPdf.pdf";
Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/SampleDocx.docx", () -> loadOptions);
converter.convert(convertedFile, options);
```

**설명:**
DPI 값이 높을수록 이미지 품질은 향상되지만 파일 크기가 커질 수 있습니다. 필요에 따라 조정하세요.

### PDF 변환을 위한 너비와 높이 설정
**개요:**
변환하는 동안 결과 PDF의 크기를 사용자 정의합니다.

#### 단계별 구현
##### 차원 정의
너비와 높이 매개변수를 설정합니다.

```java
PdfConvertOptions options = new PdfConvertOptions();
options.setWidth(1024); // 너비를 1024픽셀로 설정합니다.
options.setHeight(768); // 높이를 768픽셀로 설정합니다.
```

##### 사용자 정의 크기로 변환
다음 차원을 사용하여 변환을 진행하세요.

```java
String convertedFile = "YOUR_OUTPUT_DIRECTORY/SizedPdf.pdf";
Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/SampleDocx.docx", () -> loadOptions);
converter.convert(convertedFile, options);
```

**설명:**
크기를 사용자 정의하면 출력 PDF를 특정 디스플레이 또는 인쇄 요구 사항에 맞게 조정할 수 있습니다.