---
title: BMP 이미지를 PDF로 변환
linktitle: BMP 이미지를 PDF로 변환
second_title: GroupDocs.Conversion .NET API
description: .NET용 GroupDocs.Conversion을 사용하여 BMP 이미지를 PDF로 원활하게 변환하세요. 최적의 출력을 위한 맞춤형 옵션.
weight: 11
url: /ko/net/file-conversion-to-pdf/convert-bmp-to-pdf/
---
## 소개
.NET용 GroupDocs.Conversion은 BMP 이미지를 PDF 형식으로 원활하게 변환하기 위한 강력한 솔루션을 제공합니다. 이 튜토리얼에서는 프로세스를 단계별로 안내합니다.
### 전제 조건
시작하기 전에 다음 사항이 있는지 확인하세요.
1.  .NET용 GroupDocs.Conversion: 라이브러리를 다운로드하여 설치합니다.[다운로드 링크](https://releases.groupdocs.com/conversion/net/).
2. 소스 BMP 파일: 변환하려는 BMP 이미지 파일을 준비합니다.

## 네임스페이스 가져오기
먼저 필요한 클래스와 메서드에 액세스하려면 필요한 네임스페이스를 가져옵니다.
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## 1단계: 출력 폴더 및 파일 이름 설정
변환된 PDF 파일의 출력 폴더 경로와 이름을 정의합니다.
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "bmp-converted-to.pdf");
```
## 2단계: 소스 BMP 파일 로드
 다음을 사용하여 소스 BMP 파일을 로드합니다.`Converter` 수업:
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_BMP))
{
    // 변환 논리가 여기에 표시됩니다.
}
```
## 3단계: 변환 옵션 구성
 변환 옵션을 지정합니다. 이 경우에는 다음을 사용합니다.`PdfConvertOptions` PDF 형식으로 변환하려면:
```csharp
var options = new PdfConvertOptions();
```
## 4단계: BMP를 PDF로 변환
변환을 수행하고 변환된 PDF 파일을 저장합니다.
```csharp
converter.Convert(outputFile, options);
```
## 5단계: 변환 확인
변환이 성공했는지 확인하고 출력 폴더 경로를 표시합니다.
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
축하해요! .NET용 GroupDocs.Conversion을 사용하여 BMP 이미지를 PDF로 성공적으로 변환했습니다.

## 결론
결론적으로, .NET용 GroupDocs.Conversion은 BMP 이미지를 PDF 형식으로 변환하기 위한 간단하면서도 강력한 솔루션을 제공합니다. 이 자습서에 설명된 단계를 따르면 이 기능을 .NET 애플리케이션에 원활하게 통합할 수 있습니다.
## FAQ
### .NET용 GroupDocs.Conversion은 모든 BMP 이미지 형식과 호환됩니까?
.NET용 GroupDocs.Conversion은 광범위한 BMP 이미지 형식을 지원하여 대부분의 BMP 파일과의 호환성을 보장합니다.
### 출력 PDF를 더 효과적으로 제어하기 위해 변환 옵션을 사용자 정의할 수 있습니까?
예, DPI, 페이지 크기, 방향 등과 같은 다양한 변환 옵션을 사용자 정의하여 요구 사항에 따라 출력 PDF를 맞춤화할 수 있습니다.
### .NET용 GroupDocs.Conversion에는 추가 종속성이 필요합니까?
아니요, .NET용 GroupDocs.Conversion은 기본 변환 작업에 대한 추가 종속성이 필요하지 않은 독립 실행형 라이브러리입니다.
### 구매하기 전에 테스트할 수 있는 평가판이 있나요?
 예, 다음에서 무료 평가판을 다운로드할 수 있습니다.[릴리스 페이지](https://releases.groupdocs.com/) 구매하기 전에 라이브러리의 기능을 평가합니다.
### 문제가 발생하면 어디서 지원을 받을 수 있나요?
 당신은 방문 할 수 있습니다[GroupDocs.Conversion 포럼](https://forum.groupdocs.com/c/conversion/11) 커뮤니티의 도움을 받거나 맞춤 지원을 받으려면 지원팀에 직접 문의하세요.