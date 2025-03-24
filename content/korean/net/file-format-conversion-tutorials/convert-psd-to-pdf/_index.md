---
title: PSD를 PDF로 변환
linktitle: PSD를 PDF로 변환
second_title: GroupDocs.Conversion .NET API
description: .NET용 GroupDocs.Conversion을 사용하여 PSD 파일을 PDF로 손쉽게 변환하는 방법을 알아보세요. 단계별 가이드를 따르세요.
weight: 10
url: /ko/net/file-format-conversion-convert-psd-to-pdf/
---

# PSD를 PDF로 변환

## 소개
이 튜토리얼에서는 .NET용 GroupDocs.Conversion 라이브러리를 사용하여 PSD(Photoshop 문서) 파일을 PDF 형식으로 변환하는 과정을 안내합니다. 이러한 단계별 지침을 따르면 PSD 파일을 PDF로 쉽게 원활하게 변환할 수 있습니다.
## 전제 조건
시작하기 전에 다음 필수 구성 요소가 설정되어 있는지 확인하세요.
1.  GroupDocs.Conversion 라이브러리 설치: .NET용 GroupDocs.Conversion 라이브러리를 설치했는지 확인하십시오. 다음에서 다운로드할 수 있습니다.[웹사이트](https://releases.groupdocs.com/conversion/net/).
2. PSD 파일에 대한 액세스: PDF로 변환하려는 PSD 파일에 액세스할 수 있습니다.

## 네임스페이스 가져오기
변환 프로세스를 시작하기 전에 필요한 네임스페이스를 가져옵니다.
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## 1단계: 출력 폴더 및 파일 정의
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "psd-converted-to.pdf");
```
 이 단계에서는 변환된 PDF 파일을 저장할 출력 폴더를 지정합니다. 교체했는지 확인하세요.`"Your Document Directory"` 실제 디렉토리 경로와 함께.
## 2단계: 소스 PSD 파일 로드
```csharp
using (var converter = new GroupDocs.Conversion.Converter("Path_to_your_PSD_file.psd"))
{
    var options = new PdfConvertOptions();
    // 변환된 PDF 파일 저장
    converter.Convert(outputFile, options);
}
```
 여기서는`Converter` PSD 파일 경로가 있는 개체입니다. 바꾸다`"Path_to_your_PSD_file.psd"` PSD 파일의 실제 경로를 사용하세요. 그런 다음`PdfConvertOptions` 변환 설정을 지정합니다. 마지막으로`Convert` PSD 파일을 PDF로 변환하고 지정된 출력 파일에 저장하는 방법입니다.
## 3단계: 변환 완료 확인
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```
이 단계에서는 변환 프로세스가 성공적으로 완료되었음을 확인하는 메시지를 콘솔에 인쇄하고 변환된 PDF 파일이 저장되는 위치를 나타냅니다.

## 결론
이 튜토리얼에서는 .NET용 GroupDocs.Conversion 라이브러리를 사용하여 PSD 파일을 PDF 형식으로 변환하는 방법을 보여주었습니다. 제공된 단계를 따르면 PSD 파일을 PDF로 손쉽게 변환하여 문서를 더 쉽게 공유하고 볼 수 있습니다.
## FAQ

### GroupDocs.Conversion을 사용하여 여러 PSD 파일을 한 번에 변환할 수 있습니까?
예, GroupDocs.Conversion을 사용하면 여러 PSD 파일을 PDF 또는 기타 형식으로 일괄 변환할 수 있습니다.

### GroupDocs.Conversion은 PDF 외에 다른 출력 형식을 지원합니까?
예, GroupDocs.Conversion은 DOCX, XLSX, PPTX, JPEG, PNG 등을 포함한 광범위한 출력 형식을 지원합니다.

### GroupDocs.Conversion은 다른 버전의 .NET과 호환됩니까?
예, GroupDocs.Conversion은 .NET Core 및 .NET Framework를 포함한 다양한 버전의 .NET과 호환됩니다.

### 출력을 더 효과적으로 제어하기 위해 변환 옵션을 사용자 정의할 수 있습니까?
예, GroupDocs.Conversion은 페이지 크기, 방향, 품질 등과 같은 사용자 정의를 위한 광범위한 옵션을 제공합니다.

### 구매하기 전에 테스트할 수 있는 평가판이 있나요?
예, 다음에서 GroupDocs.Conversion의 무료 평가판을 받을 수 있습니다.[웹사이트](https://releases.groupdocs.com/conversion/net/) 구매하기 전에 기능을 테스트하십시오.