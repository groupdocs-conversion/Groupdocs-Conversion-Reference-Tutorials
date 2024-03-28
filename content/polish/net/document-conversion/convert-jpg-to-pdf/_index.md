---
title: Konwertuj JPG na PDF
linktitle: Konwertuj JPG na PDF
second_title: GroupDocs.Conversion API .NET
description: Konwertuj JPG na PDF bez wysiłku za pomocą GroupDocs.Conversion dla .NET. Postępuj zgodnie z tym samouczkiem krok po kroku, aby bezproblemowo konwertować dokumenty.
type: docs
weight: 14
url: /pl/net/document-conversion/convert-jpg-to-pdf/
---
## Wstęp

Czy chcesz bez wysiłku przekonwertować pliki JPG na format PDF za pomocą GroupDocs.Conversion dla .NET? Ten samouczek przeprowadzi Cię przez proces krok po kroku. GroupDocs.Conversion dla .NET to potężny interfejs API, który umożliwia bezproblemową konwersję różnych formatów dokumentów, w tym obrazów, do formatu PDF. Zanurzmy się!

## Warunki wstępne

Zanim zaczniemy, upewnij się, że masz następujące wymagania wstępne:

1.  GroupDocs.Conversion dla .NET: Upewnij się, że zainstalowałeś GroupDocs.Conversion dla .NET. Można go pobrać z[Tutaj](https://releases.groupdocs.com/conversion/net/).
2. Środowisko programistyczne: Skonfiguruj środowisko programistyczne, takie jak Visual Studio, wraz z .NET Framework lub .NET Core.
3. Przykładowy plik JPG: Przygotuj przykładowy plik JPG, który chcesz przekonwertować na format PDF.

## Importuj przestrzenie nazw

Najpierw zaimportujmy niezbędne przestrzenie nazw:

```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```

Podzielmy teraz proces konwersji na proste kroki:

## Krok 1: Zdefiniuj katalog wyjściowy i nazwę pliku

```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "jpg-converted-to.pdf");
```

Pamiętaj, aby określić katalog, w którym chcesz zapisać przekonwertowany plik PDF i żądaną nazwę pliku wyjściowego.

## Krok 2: Załaduj źródłowy plik JPG i przekonwertuj na format PDF

```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_JPG))
{
    var options = new PdfConvertOptions();
    converter.Convert(outputFile, options);
}
```

 Zainicjuj`Converter` obiekt ścieżką do przykładowego pliku JPG. Następnie skonfiguruj opcje konwersji, na przykład określając opcje konwersji PDF. Na koniec zadzwoń do`Convert` metodę, przekazując ścieżkę pliku wyjściowego i opcje konwersji.

## Krok 3: Wyświetl komunikat o zakończeniu konwersji

```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```

Po zakończeniu konwersji wyświetl komunikat informujący o pomyślnej konwersji i lokalizacji przekonwertowanego pliku PDF.

## Wniosek

Konwertowanie plików JPG na format PDF za pomocą programu GroupDocs.Conversion dla .NET jest proste i wymaga zaledwie kilku linijek kodu. Postępując zgodnie z tym samouczkiem, możesz bezproblemowo zintegrować możliwości konwersji dokumentów z aplikacjami .NET.

## Często zadawane pytania

### P: Czy mogę jednocześnie konwertować wiele plików JPG do formatu PDF?

O: Tak, możesz przekonwertować wiele plików JPG na format PDF, przeglądając każdy plik i wykonując proces konwersji opisany w samouczku.

### P: Czy GroupDocs.Conversion obsługuje inne formaty obrazów oprócz JPG?

O: Tak, GroupDocs.Conversion obsługuje różne formaty obrazów, między innymi PNG, TIFF, BMP i GIF.

### P: Czy mogę dostosować wyjściowy plik PDF za pomocą opcji konwersji?

Odp.: Absolutnie! GroupDocs.Conversion udostępnia szeroką gamę opcji konwersji, pozwalających dostosować wyjściowy plik PDF do własnych wymagań.

### P: Czy dostępna jest wersja próbna programu GroupDocs.Conversion dla platformy .NET?

O: Tak, możesz uzyskać dostęp do bezpłatnej wersji próbnej GroupDocs.Conversion dla .NET z[Tutaj](https://releases.groupdocs.com/).

### P: Gdzie mogę szukać pomocy, jeśli napotkam jakiekolwiek problemy podczas procesu konwersji?

 O: Jeśli napotkasz jakiekolwiek problemy lub masz pytania dotyczące GroupDocs.Conversion dla .NET, nie wahaj się odwiedzić strony[Forum GroupDocs.Conversion](https://forum.groupdocs.com/c/conversion/11) do pomocy.