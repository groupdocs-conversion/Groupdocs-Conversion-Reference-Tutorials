---
title: PNG를 PDF로 변환
linktitle: PNG를 PDF로 변환
second_title: GroupDocs.Conversion .NET API
description: .NET용 GroupDocs.Conversion을 사용하여 PNG 이미지를 PDF 문서로 손쉽게 변환하세요. 원활한 파일 형식 변환을 위한 간단한 단계입니다.
type: docs
weight: 20
url: /ko/net/pdf-conversion/convert-png-to-pdf/
---
## 소개
오늘날의 디지털 시대에는 다양한 응용 프로그램에서 파일 형식을 효율적으로 변환하는 것이 중요합니다. 문서 관리, 보관, 공유 등 어떤 용도로든 파일을 한 형식에서 다른 형식으로 원활하게 변환할 수 있다는 것은 매우 중요합니다. 이 자습서에서는 .NET용 GroupDocs.Conversion을 사용하여 PNG 이미지를 PDF 문서로 변환하는 방법을 살펴보겠습니다. GroupDocs.Conversion은 개발자에게 다양한 형식 간에 파일을 쉽게 변환하는 데 필요한 도구를 제공하는 강력한 문서 변환 API입니다.
## 전제 조건
변환 프로세스를 시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
1.  .NET SDK용 GroupDocs.Conversion: 다음에서 SDK를 다운로드하고 설치합니다.[다운로드 페이지](https://releases.groupdocs.com/conversion/net/). 개발 환경에서 SDK를 설정하려면 제공된 설치 지침을 따르세요.
2. 개발 환경: 컴퓨터에 .NET 개발 환경을 설정합니다. 이는 Visual Studio 또는 .NET 개발을 지원하는 다른 IDE일 수 있습니다.
3. 소스 PNG 파일: PDF로 변환하려는 PNG 이미지 파일을 준비합니다. .NET 애플리케이션에 액세스할 수 있는 디렉터리에 파일이 저장되어 있는지 확인하세요.

## 네임스페이스 가져오기
변환 프로세스를 시작하려면 필요한 네임스페이스를 .NET 애플리케이션으로 가져와야 합니다. 이러한 네임스페이스는 파일 변환에 필요한 기능에 대한 액세스를 제공합니다.
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```

## 1단계: 출력 폴더 및 파일 이름 정의
먼저, 변환된 PDF 파일이 저장될 출력 폴더를 지정하고 출력 파일의 이름을 정의합니다.
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "png-converted-to.pdf");
```
 바꾸다`"Your Document Directory"` 변환된 PDF 파일을 저장하려는 디렉토리 경로를 사용하세요.
## 2단계: 소스 PNG 파일 로드
다음으로 GroupDocs.Conversion을 사용하여 PDF로 변환하려는 소스 PNG 파일을 로드합니다.
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PNG))
{
    // 전환 코드가 여기에 표시됩니다.
}
```
 바꾸다`Constants.SAMPLE_PNG` PNG 파일의 경로를 사용하세요.
## 3단계: 변환 옵션 구성
요구 사항에 따라 변환 옵션을 구성하십시오. 이 경우 PNG를 PDF로 변환하기 위해 PdfConvertOptions를 사용합니다.
```csharp
var options = new PdfConvertOptions();
```
필요에 따라 페이지 방향, 여백, 품질 등과 같은 변환 옵션을 사용자 정의할 수 있습니다.
## 4단계: 변환 수행
 이제 다음을 호출하여 변환 프로세스를 시작합니다.`Convert` Converter 개체의 메서드를 사용하고 변환 옵션과 함께 출력 파일 경로를 전달합니다.
```csharp
converter.Convert(outputFile, options);
```
그러면 PNG 이미지가 PDF 문서로 변환되어 지정된 출력 파일 경로에 저장됩니다.
## 5단계: 변환 완료 메시지 표시
마지막으로 사용자에게 변환 프로세스가 성공적으로 완료되었음을 알리고 출력 PDF 파일의 경로를 제공합니다.
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```
이 메시지는 사용자가 변환된 PDF 파일을 찾을 수 있는 위치를 알 수 있도록 합니다.

## 결론
결론적으로, .NET용 GroupDocs.Conversion은 PNG 이미지를 PDF 문서로 원활하게 변환할 수 있는 간단하면서도 강력한 솔루션을 제공합니다. 이 튜토리얼에 설명된 단계를 따르면 PNG 파일을 PDF 형식으로 효율적으로 변환하여 문서 관리 및 공유에 대한 가능성의 세계를 열 수 있습니다.
## FAQ
### GroupDocs.Conversion은 PNG 및 PDF 이외의 다른 파일 형식과 호환됩니까?
 예, GroupDocs.Conversion은 DOCX, XLSX, PPTX, JPG, TIFF 등을 포함하여 광범위한 변환 파일 형식을 지원합니다. 다음을 참조하세요.[선적 서류 비치](https://reference.groupdocs.com/conversion/net/) 지원되는 형식의 전체 목록을 보려면
### 특정 요구 사항에 따라 변환 설정을 사용자 정의할 수 있습니까?
전적으로! GroupDocs.Conversion은 광범위한 사용자 정의 옵션을 제공하므로 정확한 요구 사항에 맞게 변환 프로세스를 맞춤화할 수 있습니다. 페이지 크기, 방향, 품질 등과 같은 매개변수를 조정할 수 있습니다.
### GroupDocs.Conversion은 대규모 문서 변환 작업에 적합합니까?
예, GroupDocs.Conversion은 대규모 문서 변환 작업을 효율적으로 처리하도록 설계되었습니다. 강력한 아키텍처는 많은 수의 파일을 처리할 때에도 최적의 성능과 안정성을 보장합니다.
### GroupDocs.Conversion은 개발자에게 지원을 제공합니까?
 예, GroupDocs는 전담 서비스를 통해 개발자에게 포괄적인 지원을 제공합니다.[법정](https://forum.groupdocs.com/c/conversion/11) 질문을 하고, 지침을 구하고, 동료 개발자와 상호 작용할 수 있는 곳입니다.
### 구매하기 전에 GroupDocs.Conversion을 사용해 볼 수 있나요?
 전적으로! 다음을 방문하여 GroupDocs.Conversion의 무료 평가판을 이용할 수 있습니다.[웹사이트](https://releases.groupdocs.com/) 평가판을 다운로드합니다. 이를 통해 결정을 내리기 전에 해당 기능을 탐색할 수 있습니다.