---
title: ODP를 PDF로 변환
linktitle: ODP를 PDF로 변환
second_title: GroupDocs.Conversion .NET API
description: .NET용 GroupDocs.Conversion을 사용하여 ODP를 PDF로 변환하는 방법을 알아보세요. 원활한 문서 변환을 위한 단계별 가이드를 따르세요.
type: docs
weight: 28
url: /ko/net/document-conversion/convert-odp-to-pdf/
---
## 소개
.NET용 GroupDocs.Conversion은 개발자가 .NET 응용 프로그램에서 다양한 문서 형식을 원활하게 변환할 수 있게 해주는 강력한 API입니다. 이 자습서에서는 .NET용 GroupDocs.Conversion을 사용하여 ODP(OpenDocument Presentation) 파일을 PDF 형식으로 변환하는 과정을 안내합니다.
## 전제 조건
시작하기 전에 다음 필수 구성 요소가 있는지 확인하세요.
1.  .NET SDK용 GroupDocs.Conversion: .NET SDK용 GroupDocs.Conversion을 다운로드하여 설치했는지 확인하십시오. 다음에서 다운로드할 수 있습니다.[다운로드 페이지](https://releases.groupdocs.com/conversion/net/).
2. .NET 개발 환경: 컴퓨터에 .NET 개발 환경이 설정되어 있어야 합니다.
3. 원본 ODP 파일: PDF로 변환하려는 ODP 파일을 준비합니다.

## 네임스페이스 가져오기
먼저 필요한 네임스페이스를 C# 코드로 가져옵니다.
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## 1단계: 출력 파일 경로 정의
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "odp-converted-to.pdf");
```
 바꾸다`"Your Document Directory"` 변환된 PDF 파일을 저장할 경로를 입력하세요.
## 2단계: 소스 ODP 파일 로드
```csharp
using (var converter = new GroupDocs.Conversion.Converter("path/to/your/source.odp"))
{
    // 전환 코드가 여기에 표시됩니다.
}
```
 바꾸다`"path/to/your/source.odp"` 소스 ODP 파일의 실제 경로를 사용합니다.
## 3단계: 변환 옵션 설정
```csharp
var options = new PdfConvertOptions();
```
여기에서 요구 사항에 따라 변환 옵션을 사용자 정의할 수 있습니다. 예를 들어 페이지 크기, 여백, 품질 등과 같은 PDF 변환 설정을 지정할 수 있습니다.
## 4단계: 변환 수행
```csharp
converter.Convert(outputFile, options);
```
이 코드 줄은 지정된 옵션을 사용하여 ODP에서 PDF로의 변환 프로세스를 시작합니다.
## 5단계: 성공 메시지 표시
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```
이 줄은 변환된 PDF 파일이 저장되는 출력 폴더와 함께 성공 메시지를 표시합니다.

## 결론
이 자습서에서는 .NET용 GroupDocs.Conversion을 사용하여 ODP 파일을 PDF로 변환하는 방법을 배웠습니다. 제공된 단계를 따르면 문서 변환 기능을 .NET 애플리케이션에 쉽게 통합할 수 있습니다.
## FAQ
### .NET용 GroupDocs.Conversion이 다른 문서 형식을 처리할 수 있습니까?
예, .NET용 GroupDocs.Conversion은 Word, Excel, PowerPoint, PDF 등을 포함한 광범위한 문서 형식을 지원합니다.
### GroupDocs.Conversion for .NET에 대한 무료 평가판이 있습니까?
 예, 무료 평가판을 이용하실 수 있습니다.[웹사이트](https://releases.groupdocs.com/).
### .NET용 GroupDocs.Conversion에 대한 기술 지원을 받으려면 어떻게 해야 합니까?
 기술 지원을 받을 수 있습니다.[지원 포럼](https://forum.groupdocs.com/c/conversion/11).
### 내 요구 사항에 따라 변환 옵션을 사용자 정의할 수 있나요?
예, .NET용 GroupDocs.Conversion은 특정 요구 사항에 맞게 사용자 정의할 수 있는 광범위한 옵션을 제공합니다.
### .NET용 GroupDocs.Conversion 라이센스는 어디서 구입할 수 있나요?
 다음에서 라이센스를 구입할 수 있습니다.[구매 페이지](https://purchase.groupdocs.com/buy).