---
title: JPG를 PDF로 변환
linktitle: JPG를 PDF로 변환
second_title: GroupDocs.Conversion .NET API
description: .NET용 GroupDocs.Conversion을 사용하여 JPG를 PDF로 손쉽게 변환하세요. 원활한 문서 변환을 위해 이 단계별 튜토리얼을 따르세요.
weight: 14
url: /ko/net/document-conversion/convert-jpg-to-pdf/
---
## 소개

.NET용 GroupDocs.Conversion을 사용하여 JPG 파일을 PDF로 쉽게 변환하고 싶으십니까? 이 튜토리얼에서는 프로세스를 단계별로 안내합니다. GroupDocs.Conversion for .NET은 이미지를 포함한 다양한 문서 형식을 PDF로 쉽게 원활하게 변환할 수 있는 강력한 API입니다. 뛰어들어보자!

## 전제 조건

시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.

1.  .NET용 GroupDocs.Conversion: .NET용 GroupDocs.Conversion을 설치했는지 확인하십시오. 다음에서 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/conversion/net/).
2. 개발 환경: .NET Framework 또는 .NET Core와 함께 Visual Studio와 같은 개발 환경을 설정합니다.
3. 샘플 JPG 파일: PDF로 변환하려는 샘플 JPG 파일을 준비합니다.

## 네임스페이스 가져오기

먼저 필요한 네임스페이스를 가져오겠습니다.

```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```

이제 변환 프로세스를 간단한 단계로 나누어 보겠습니다.

## 1단계: 출력 디렉터리 및 파일 이름 정의

```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "jpg-converted-to.pdf");
```

변환된 PDF 파일을 저장할 디렉토리와 원하는 출력 파일 이름을 지정하십시오.

## 2단계: 원본 JPG 파일을 로드하고 PDF로 변환

```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_JPG))
{
    var options = new PdfConvertOptions();
    converter.Convert(outputFile, options);
}
```

 초기화`Converter` 샘플 JPG 파일의 경로가 있는 개체입니다. 그런 다음 PDF 변환 옵션 지정과 같은 변환 옵션을 구성합니다. 마지막으로`Convert` 메서드를 사용하여 출력 파일 경로와 변환 옵션을 전달합니다.

## 3단계: 변환 완료 메시지 표시

```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```

변환이 완료되면 성공적인 변환과 변환된 PDF 파일의 위치를 나타내는 메시지가 표시됩니다.

## 결론

.NET용 GroupDocs.Conversion을 사용하여 JPG 파일을 PDF로 변환하는 작업은 단 몇 줄의 코드만으로 간단합니다. 이 튜토리얼을 따르면 문서 변환 기능을 .NET 애플리케이션에 원활하게 통합할 수 있습니다.

## FAQ

### Q: 여러 JPG 파일을 동시에 PDF로 변환할 수 있나요?

A: 예, 각 파일을 반복하고 튜토리얼에 설명된 변환 프로세스를 수행하여 여러 JPG 파일을 PDF로 변환할 수 있습니다.

### Q: GroupDocs.Conversion은 JPG 외에 다른 이미지 형식을 지원합니까?

A: 예, GroupDocs.Conversion은 PNG, TIFF, BMP, GIF 등 다양한 이미지 형식을 지원합니다.

### Q: 변환 옵션을 사용하여 출력 PDF 파일을 사용자 정의할 수 있습니까?

답: 물론이죠! GroupDocs.Conversion은 요구 사항에 따라 출력 PDF를 사용자 정의할 수 있는 광범위한 변환 옵션을 제공합니다.

### Q: GroupDocs.Conversion for .NET에 사용할 수 있는 평가판이 있습니까?

A: 예. 다음 위치에서 .NET용 GroupDocs.Conversion 무료 평가판에 액세스할 수 있습니다.[여기](https://releases.groupdocs.com/).

### Q: 변환 과정에서 문제가 발생하면 어디서 도움을 받을 수 있나요?

 A: GroupDocs.Conversion for .NET과 관련하여 문제가 발생하거나 질문이 있는 경우 언제든지 다음을 방문하십시오.[GroupDocs.Conversion 포럼](https://forum.groupdocs.com/c/conversion/11) 도움을 위해.