---
title: DNG 이미지를 PDF로 변환
linktitle: DNG 이미지를 PDF로 변환
second_title: GroupDocs.Conversion .NET API
description: .NET용 GroupDocs.Conversion을 사용하여 DNG 이미지를 PDF로 손쉽게 변환하는 방법을 알아보세요. 원활한 변환을 위해 단계별 가이드를 따르세요.
weight: 21
url: /ko/net/file-conversion-to-pdf/convert-dng-to-pdf/
---
## 소개
이 자습서에서는 .NET용 GroupDocs.Conversion을 사용하여 DNG 이미지를 PDF로 변환하는 과정을 안내합니다. DNG(Digital Negative)는 디지털 사진에 사용되는 파일 형식입니다. DNG 이미지를 PDF로 변환하면 보다 보편적으로 허용되는 형식으로 쉽게 공유하거나 저장할 수 있습니다.
## 전제 조건
시작하기 전에 다음 사항이 있는지 확인하세요.
1.  .NET용 GroupDocs.Conversion: 다음 위치에서 .NET용 GroupDocs.Conversion 라이브러리를 다운로드하고 설치합니다.[여기](https://releases.groupdocs.com/conversion/net/).
2. 원본 DNG 파일: PDF로 변환하려는 DNG 이미지 파일이 필요합니다.
3. 개발 환경: .NET 개발 환경이 설정되어 있는지 확인하세요.

## 네임스페이스 가져오기
먼저, 필요한 네임스페이스를 프로젝트로 가져와야 합니다. 코드 파일에 다음 using 지시문을 추가합니다.
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## 1단계: 소스 DNG 파일 로드
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "dng-converted-to.pdf");
// 소스 DNG 파일 로드
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_DNG))
{
    // 변환 프로세스를 계속 진행하세요.
}
```
 이 단계에서는 변환된 PDF 파일이 저장될 출력 폴더를 정의합니다. 반드시 교체하세요`"Your Document Directory"` 원하는 디렉토리의 경로로. 그런 다음 출력 PDF 파일의 이름과 경로를 지정합니다.
## 2단계: DNG를 PDF로 변환
```csharp
var options = new PdfConvertOptions();
// 변환된 PDF 파일 저장
converter.Convert(outputFile, options);
```
 여기서는 인스턴스를 생성합니다.`PdfConvertOptions` 필요한 경우 PDF 변환에 대한 특정 옵션을 설정합니다. 그런 다음`Convert` 의 방법`converter`객체, 출력 파일 경로 및 변환 옵션을 전달합니다.
## 3단계: 변환 완료 처리
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
변환 프로세스가 완료되면 변환된 PDF 파일이 있는 디렉터리와 함께 성공 메시지가 표시됩니다.

## 결론
결론적으로 DNG 이미지를 PDF로 변환하는 작업은 .NET용 GroupDocs.Conversion을 사용하여 쉽게 수행할 수 있습니다. 이 튜토리얼에 설명된 간단한 단계를 따르면 DNG 파일을 PDF 형식으로 효율적으로 변환하여 더 쉽게 액세스하고 공유할 수 있습니다.
## FAQ
### .NET용 GroupDocs.Conversion은 모든 버전의 .NET과 호환됩니까?
예, .NET용 GroupDocs.Conversion은 .NET Framework 4.6.1 이상은 물론 .NET Core 2.0 이상과도 호환됩니다.
### 여러 DNG 파일을 동시에 PDF로 변환할 수 있습니까?
예, 각 파일을 반복하고 각 파일에 대해 변환 프로세스를 수행하여 여러 DNG 파일을 PDF로 변환할 수 있습니다.
### 변환할 수 있는 DNG 파일의 크기에 제한이 있나요?
.NET용 GroupDocs.Conversion에는 변환할 수 있는 DNG 파일 크기에 대한 특별한 제한이 없습니다. 그러나 성능은 입력 파일의 크기와 복잡성에 따라 달라질 수 있습니다.
### PDF 출력에 대한 변환 옵션을 사용자 정의할 수 있습니까?
 예. 페이지 크기, 방향, 압축 등과 같은 다양한 옵션을 사용자 정의할 수 있습니다.`PdfConvertOptions`.NET용 GroupDocs.Conversion에서 제공하는 클래스입니다.
### .NET용 GroupDocs.Conversion에 대한 기술 지원이 제공됩니까?
 예, GroupDocs 포럼을 통해 기술 지원을 받을 수 있습니다.[여기](https://forum.groupdocs.com/c/conversion/11)에서 질문하고 전문가에게 도움을 받을 수 있습니다.