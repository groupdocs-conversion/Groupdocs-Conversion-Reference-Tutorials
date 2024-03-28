---
title: OTG를 PDF로 변환
linktitle: OTG를 PDF로 변환
second_title: GroupDocs.Conversion .NET API
description: .NET용 GroupDocs.Conversion을 사용하여 OTG 파일을 PDF로 변환하는 방법을 알아보세요. 귀하의 프로젝트를 위한 간단하고 효율적이며 원활한 통합입니다.
type: docs
weight: 13
url: /ko/net/pdf-conversion/convert-otg-to-pdf/
---
## 소개
OTG(OpenDocument Graphics) 파일을 PDF 형식으로 변환하는 것은 특히 문서 관리 시스템을 다루거나 다양한 플랫폼에서 파일을 공유할 때 중요한 작업이 될 수 있습니다. 이 자습서에서는 .NET용 GroupDocs.Conversion 라이브러리를 사용하여 OTG 파일을 PDF로 변환하는 과정을 안내합니다. 뛰어들어보자!
## 전제 조건
시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
1. .NET용 GroupDocs.Conversion: .NET용 GroupDocs.Conversion 라이브러리를 설치했는지 확인하십시오. 다음에서 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/conversion/net/).
2. OTG 파일: PDF로 변환하려는 OTG 파일을 문서 디렉터리에 준비하세요.

## 네임스페이스 가져오기
먼저 필요한 네임스페이스를 .NET 프로젝트로 가져와야 합니다. 
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## 1단계: 출력 디렉터리 및 파일 이름 설정
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "otg-converted-to.pdf");
```
 이 단계에서는 변환된 PDF 파일이 저장될 출력 디렉터리를 정의합니다. 바꾸다`"Your Document Directory"` 원하는 출력 디렉터리의 경로를 사용하세요.
## 2단계: 소스 OTG 파일 로드 및 PDF로 변환
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_OTG))
{
    var options = new PdfConvertOptions();
    // 변환된 PDF 파일 저장
    converter.Convert(outputFile, options);
}
```
 여기서는 새로운 인스턴스를 생성합니다.`Converter` GroupDocs.Conversion 라이브러리의 개체를 가져와 소스 OTG 파일의 경로를 전달합니다. 그런 다음 우리는`PdfConvertOptions` 변환 옵션을 지정합니다. 마지막으로 우리는`Convert` OTG 파일을 PDF 형식으로 변환하는 방법.
## 3단계: 변환 완료 확인
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
이 단계에서는 변환 프로세스가 성공적으로 완료되었음을 사용자에게 알리고 변환된 PDF 파일이 저장되는 경로를 제공합니다.

## 결론
.NET용 GroupDocs.Conversion 라이브러리를 사용하면 OTG 파일을 PDF 형식으로 간단하게 변환할 수 있습니다. 이 자습서에 설명된 단계를 따르면 이 기능을 .NET 애플리케이션에 원활하게 통합하여 문서 상호 운용성과 접근성을 향상시킬 수 있습니다.
## FAQ
### GroupDocs.Conversion은 OTG 이외의 다른 파일 형식을 PDF로 변환할 수 있습니까?
예, GroupDocs.Conversion은 DOCX, XLSX, PPTX, HTML 등을 포함하여 광범위한 변환 파일 형식을 지원합니다.
### GroupDocs.Conversion은 상업적 용도로 적합합니까?
전적으로! GroupDocs.Conversion은 강력한 문서 변환 기능을 활용하려는 기업 및 조직에 상용 라이센스를 제공합니다.
### GroupDocs.Conversion은 기술 지원을 제공합니까?
예, GroupDocs는 구현 중에 발생할 수 있는 모든 쿼리나 문제에 대해 사용자를 지원하기 위해 전담 기술 지원을 제공합니다.
### 라이센스를 구매하기 전에 GroupDocs.Conversion을 사용해 볼 수 있습니까?
예, GroupDocs.Conversion의 무료 평가판을 사용하여 해당 기능과 요구 사항과의 호환성을 살펴볼 수 있습니다.
### GroupDocs.Conversion에 대한 임시 라이센스를 얻으려면 어떻게 해야 합니까?
임시 라이센스를 방문하여 평가 목적이나 단기 프로젝트를 위해 GroupDocs에서 임시 라이센스를 얻을 수 있습니다.[특허](https://purchase.groupdocs.com/temporary-license/).