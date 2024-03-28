---
title: PST를 PDF로 변환
linktitle: PST를 PDF로 변환
second_title: GroupDocs.Conversion .NET API
description: .NET용 GroupDocs.Conversion을 사용하여 PST 파일을 PDF로 손쉽게 변환하세요. 원활한 문서 관리로 생산성을 높이세요.
type: docs
weight: 12
url: /ko/net/file-format-conversion-tutorials/convert-pst-to-pdf/
---
## 소개
문서 관리 영역에서는 파일을 한 형식에서 다른 형식으로 원활하게 변환하는 기능이 가장 중요합니다. 이메일, 스프레드시트, 프리젠테이션 등 무엇을 처리하든 신뢰할 수 있는 변환 도구를 사용하면 작업 흐름을 간소화하고 생산성을 높일 수 있습니다. 이 튜토리얼에서는 GroupDocs.Conversion for .NET을 사용하여 PST(Personal Storage Table) 파일을 PDF 형식으로 변환하는 방법을 살펴보겠습니다.
## 전제 조건
PST를 PDF로 변환하는 과정을 시작하기 전에 필요한 모든 것이 있는지 확인하십시오.
### 1. .NET용 GroupDocs.Conversion 설치
 먼저 개발 환경에 .NET용 GroupDocs.Conversion이 설치되어 있는지 확인하세요. 제공된 파일에서 필요한 파일을 다운로드할 수 있습니다.[다운로드 링크](https://releases.groupdocs.com/conversion/net/).
### 2. 소스 PST 파일 얻기
변환을 수행하려면 샘플 PST 파일이 필요합니다. 아직 없는 경우 이메일 클라이언트에서 얻거나 테스트 목적으로 샘플 PST 파일을 만들 수 있습니다.
### 3. 개발 환경 설정
.NET 프로그래밍에 적합한 개발 환경이 설정되어 있는지 확인하세요. 여기에는 Visual Studio 또는 호환되는 IDE가 시스템에 설치되어 있는 것이 포함됩니다.

## 네임스페이스 가져오기
이제 변환 프로세스를 시작하는 데 필요한 네임스페이스를 가져와 보겠습니다.

```csharp
using System;
using System.IO;
using GroupDocs.Conversion.FileTypes;
using GroupDocs.Conversion.Options.Convert;
using GroupDocs.Conversion.Options.Load;
```

System.IO 네임스페이스는 파일 읽기 및 쓰기와 같은 입출력 작업을 처리하는 데 필수적입니다.

이제 전제 조건을 다루고 필요한 네임스페이스를 가져왔으므로 PST를 PDF로 변환하는 단계별 프로세스를 살펴보겠습니다.
## 1단계: 출력 폴더 및 파일 이름 정의
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "pst-converted-{0}-to.pdf");
```
변환된 PDF 파일이 저장될 출력 폴더를 파일 이름 패턴과 함께 지정합니다. "{0}" 자리 표시자는 고유한 파일 이름을 생성하는 카운터로 대체됩니다.
## 2단계: 원본 PST 파일 로드
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PST, fileType => fileType == EmailFileType.Pst
                                                                                                    ? new PersonalStorageLoadOptions()
                                                                                                    : null))
```
소스 PST 파일의 경로를 사용하여 GroupDocs.Conversion.Converter 개체를 초기화합니다. PST 파일에 대한 적절한 로드 옵션을 제공해야 합니다.
## 3단계: 변환 옵션 구성
```csharp
var options = new PdfConvertOptions();
```
필요한 경우 PDF 변환에 대한 추가 설정을 지정하려면 PdfConvertOptions 인스턴스를 만듭니다.
## 4단계: 변환 수행
```csharp
var counter = 1;
converter.Convert(
    (FileType fileType) => new FileStream(string.Format(outputFile, counter++), FileMode.Create),
    options
);
```
변환된 각 PDF 파일에 대해 FileStream을 생성하는 대리자 함수를 전달하여 변환기 개체의 Convert 메서드를 호출합니다. 카운터는 고유한 파일 이름을 보장합니다.
## 5단계: 변환 완료 확인
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```
변환 프로세스가 성공적으로 완료되었음을 확인하는 메시지를 표시하고 변환된 PDF 파일의 위치를 나타냅니다.

## 결론
이 자습서에서는 .NET용 GroupDocs.Conversion을 사용하여 PST 파일을 PDF 형식으로 변환하는 방법을 살펴보았습니다. 단계별 가이드를 따르고 이 라이브러리의 기능을 활용하면 문서 변환 작업을 쉽고 정확하게 효율적으로 관리할 수 있습니다.
## FAQ
### .NET용 GroupDocs.Conversion은 모든 버전의 .NET과 호환됩니까?
예, .NET용 GroupDocs.Conversion은 다양한 버전의 .NET과 호환되므로 개발자에게 광범위한 지원을 보장합니다.
### 내 요구 사항에 따라 변환 옵션을 사용자 정의할 수 있나요?
전적으로! .NET용 GroupDocs.Conversion은 광범위한 사용자 정의 옵션을 제공하므로 특정 요구 사항에 맞게 변환 프로세스를 맞춤화할 수 있습니다.
### .NET용 GroupDocs.Conversion은 일괄 변환을 지원합니까?
예, GroupDocs.Conversion for .NET을 사용하면 여러 파일을 동시에 변환하여 효율성과 생산성을 높일 수 있습니다.
### GroupDocs.Conversion for .NET에 사용할 수 있는 평가판이 있습니까?
예, .NET용 GroupDocs.Conversion의 무료 평가판을 사용하여 구매 결정을 내리기 전에 기능을 탐색해 볼 수 있습니다.
### .NET용 GroupDocs.Conversion에 대한 도움은 어디서 구할 수 있나요?
 .NET용 GroupDocs.Conversion과 관련된 질문, 지원 또는 지원이 필요한 경우 다음 위치에서 제공되는 전용 지원 포럼을 방문하세요.[GroupDocs 지원](https://forum.groupdocs.com/c/conversion/11).