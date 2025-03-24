---
title: CDR 벡터 그래픽을 PDF로 변환
linktitle: CDR 벡터 그래픽을 PDF로 변환
second_title: GroupDocs.Conversion .NET API
description: .NET용 GroupDocs.Conversion을 사용하여 CorelDRAW(CDR) 벡터 그래픽 파일을 PDF 형식으로 쉽게 변환할 수 있습니다. 문서 변환 프로세스를 간소화하세요.
weight: 12
url: /ko/net/file-conversion-to-pdf/convert-cdr-to-pdf/
---
## 소개
.NET용 GroupDocs.Conversion은 개발자가 다양한 문서 형식을 PDF, Word, HTML 등으로 원활하게 변환할 수 있는 강력한 문서 변환 라이브러리입니다. 이 튜토리얼에서는 GroupDocs.Conversion for .NET을 사용하여 CorelDRAW(CDR) 벡터 그래픽 파일을 PDF 형식으로 변환하는 방법을 중점적으로 설명합니다. 이 가이드를 마치면 .NET 애플리케이션에서 이러한 변환을 손쉽게 수행할 수 있는 지식을 갖추게 될 것입니다.
## 전제 조건
변환 프로세스를 시작하기 전에 다음 전제 조건이 설정되어 있는지 확인하십시오.
### .NET용 GroupDocs.Conversion 설치
 시작하려면 .NET용 GroupDocs.Conversion을 다운로드하여 설치해야 합니다. 라이브러리는 다음에서 다운로드할 수 있습니다.[다운로드 페이지](https://releases.groupdocs.com/conversion/net/).
### 라이센스 취득
 .NET용 그룹 문서.Conversion의 잠재력을 최대한 활용하려면 유효한 라이센스가 필요합니다. 에서 라이센스를 얻을 수 있습니다.[GroupDocs](https://purchase.groupdocs.com/buy)또는 테스트 목적으로 임시 라이선스를 요청하세요.[여기](https://purchase.groupdocs.com/temporary-license/).

## 네임스페이스 가져오기
GroupDocs.Conversion 기능을 활용하려면 .NET 프로젝트에 필요한 네임스페이스를 가져왔는지 확인하세요. 방법은 다음과 같습니다.
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## 1단계: 출력 폴더 및 파일 이름 정의
먼저 변환된 PDF 파일이 저장될 출력 폴더와 원하는 파일 이름을 지정합니다.
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "cdr-converted-to.pdf");
```
꼭 교체하세요`"Your Document Directory"` 원하는 출력 폴더의 경로를 사용하세요.
## 2단계: 소스 CDR 파일 로드
다음으로 GroupDocs.Conversion을 사용하여 PDF로 변환하려는 소스 CDR 파일을 로드합니다.
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_CDR))
{
    // 변환 로직이 여기에 위치합니다.
}
```
 바꾸다`Constants.SAMPLE_CDR` 실제 CDR 파일의 경로와 함께.
## 3단계: 변환 옵션 지정
출력 형식(PDF) 및 추가 설정 지정과 같은 변환 옵션을 정의합니다.
```csharp
var options = new PdfConvertOptions();
```
요구 사항에 따라 변환 옵션을 사용자 정의할 수 있습니다.
## 4단계: 변환 수행
지정된 옵션을 사용하여 변환 프로세스를 실행합니다.
```csharp
converter.Convert(outputFile, options);
```
이 명령은 CDR 파일을 PDF로 변환하고 제공된 파일 이름으로 지정된 출력 폴더에 저장합니다.
## 5단계: 변환 완료 확인
마지막으로 변환 프로세스가 성공적으로 완료되었음을 확인하는 메시지를 표시합니다.
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```
이 메시지는 변환된 PDF 파일이 저장되는 위치를 알려줍니다.

## 결론
이 자습서에서는 .NET용 GroupDocs.Conversion을 사용하여 CorelDRAW(CDR) 벡터 그래픽 파일을 PDF 형식으로 변환하는 방법을 배웠습니다. 설명된 단계를 따르면 문서 변환 기능을 .NET 애플리케이션에 원활하게 통합하여 기능과 유용성을 향상시킬 수 있습니다.
## FAQ
### .NET용 GroupDocs.Conversion은 모든 버전의 CorelDRAW 파일과 호환됩니까?
.NET용 GroupDocs.Conversion은 광범위한 CorelDRAW 버전을 지원하여 대부분의 CDR 파일과의 호환성을 보장합니다.
### .NET용 GroupDocs.Conversion을 사용하여 여러 CDR 파일을 동시에 변환할 수 있습니까?
예, GroupDocs.Conversion for .NET을 사용하면 여러 CDR 파일을 PDF 또는 기타 형식으로 일괄 변환하여 효율성과 생산성을 높일 수 있습니다.
### .NET용 GroupDocs.Conversion에서는 문서 변환을 위해 인터넷 연결이 필요합니까?
아니요, .NET용 GroupDocs.Conversion은 컴퓨터에서 로컬로 문서 변환을 수행하므로 변환 프로세스 중에 인터넷에 연결할 필요가 없습니다.
### 특정 요구 사항에 따라 변환 설정을 사용자 정의할 수 있습니까?
예, .NET용 GroupDocs.Conversion은 광범위한 사용자 정의 옵션을 제공하므로 정확한 요구 사항에 맞게 변환 프로세스를 맞춤화할 수 있습니다.
### .NET용 GroupDocs.Conversion에 대한 기술 지원이 제공됩니까?
 예, GroupDocs는 .NET용 GroupDocs.Conversion을 포함하여 해당 제품에 대한 포괄적인 기술 지원을 제공합니다. 귀하는 다음 기관으로부터 도움을 요청할 수 있습니다.[지원 포럼](https://forum.groupdocs.com/c/conversion/11) 문의 사항이나 문제가 있으면.