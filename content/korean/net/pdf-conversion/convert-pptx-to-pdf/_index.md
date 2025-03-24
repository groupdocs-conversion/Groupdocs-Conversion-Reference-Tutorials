---
title: PPTX를 PDF로 변환
linktitle: PPTX를 PDF로 변환
second_title: GroupDocs.Conversion .NET API
description: .NET용 GroupDocs.Conversion을 사용하여 PowerPoint 프레젠테이션(PPTX)을 PDF 형식으로 변환하는 방법을 알아보세요. 쉽고 효율적인 변환 프로세스.
weight: 29
url: /ko/net/pdf-conversion/convert-pptx-to-pdf/
---

# PPTX를 PDF로 변환

## 소개
이 자습서에서는 .NET용 GroupDocs.Conversion 라이브러리를 사용하여 PowerPoint 프레젠테이션(PPTX) 파일을 PDF(Portable Document Format)로 변환하는 과정을 안내합니다. 이 변환을 수행하려면 아래 단계를 따르십시오.
## 전제 조건
시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
1.  .NET 라이브러리용 GroupDocs.Conversion: .NET 라이브러리용 GroupDocs.Conversion을 설치했는지 확인하십시오. 다음에서 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/conversion/net/).
2. 개발 환경: Visual Studio 또는 기타 .NET IDE와 같은 필수 도구를 사용하여 개발 환경을 설정합니다.

## 네임스페이스 가져오기
GroupDocs.Conversion 기능에 액세스하려면 프로젝트에 필요한 네임스페이스를 포함하세요.
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## 1단계: 출력 폴더 및 파일 이름 설정
먼저, 변환된 PDF 파일이 저장될 출력 폴더를 정의하고 출력 PDF 파일의 이름을 지정합니다.
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "pptx-converted-to.pdf");
```
## 2단계: 소스 PPTX 파일 로드
GroupDocs.Conversion 라이브러리를 사용하여 소스 PowerPoint 프레젠테이션(PPTX) 파일을 로드합니다.
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PPTX))
{
    // 변환 논리가 여기에 배치됩니다.
}
```
## 3단계: 변환 옵션 지정
변환 옵션을 정의합니다. 이 경우에는 PDF 형식으로 변환하므로`PdfConvertOptions`.
```csharp
var options = new PdfConvertOptions();
```
## 4단계: 변환 수행
 다음을 사용하여 변환 프로세스를 실행합니다.`Convert` 메서드를 사용하고 변환 옵션과 함께 출력 파일 경로를 전달합니다.
```csharp
converter.Convert(outputFile, options);
```
## 5단계: 출력 확인
변환이 성공적으로 완료되면 완료 및 출력 파일의 위치를 나타내는 메시지가 표시됩니다.
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```

## 결론
이 자습서에서는 .NET용 GroupDocs.Conversion 라이브러리를 사용하여 PowerPoint 프레젠테이션(PPTX) 파일을 PDF(Portable Document Format)로 변환하는 방법을 배웠습니다. 위에 설명된 단계를 따르면 .NET 애플리케이션에서 이 변환을 쉽게 수행할 수 있습니다.
## FAQ
### Q: GroupDocs.Conversion은 모든 버전의 .NET과 호환됩니까?
A: 예, GroupDocs.Conversion은 .NET Core 및 .NET Standard를 포함하여 .NET Framework 2.0 이상을 지원합니다.
### Q: 파일을 PDF가 아닌 다른 형식으로 변환할 수 있나요?
A: 예, GroupDocs.Conversion은 Word, Excel, HTML 등을 포함하여 광범위한 변환 문서 형식을 지원합니다.
### Q: GroupDocs.Conversion은 무료 평가판을 제공합니까?
 A: 예, 다음에서 GroupDocs.Conversion의 무료 평가판에 액세스할 수 있습니다.[여기](https://releases.groupdocs.com/).
### Q: GroupDocs.Conversion에 대한 지원을 받으려면 어떻게 해야 합니까?
 A: GroupDocs 커뮤니티 포럼에서 지원을 받을 수 있습니다.[여기](https://forum.groupdocs.com/c/conversion/11).
### Q: GroupDocs.Conversion에 사용할 수 있는 임시 라이센스가 있습니까?
 A: 예, 다음에서 GroupDocs.Conversion에 대한 임시 라이센스를 얻을 수 있습니다.[여기](https://purchase.groupdocs.com/temporary-license/).