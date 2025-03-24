---
title: Konwertuj PPTX na PDF
linktitle: Konwertuj PPTX na PDF
second_title: GroupDocs.Conversion API .NET
description: Dowiedz się, jak konwertować prezentacje programu PowerPoint (PPTX) do formatu PDF przy użyciu programu GroupDocs.Conversion dla .NET. Łatwy i wydajny proces konwersji.
weight: 29
url: /pl/net/pdf-conversion/convert-pptx-to-pdf/
---
## Wstęp
tym samouczku omówimy proces konwertowania pliku prezentacji programu PowerPoint (PPTX) na format dokumentu przenośnego (PDF) przy użyciu biblioteki GroupDocs.Conversion dla platformy .NET. Aby osiągnąć tę konwersję, wykonaj poniższe czynności.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz następujące wymagania wstępne:
1.  Biblioteka GroupDocs.Conversion dla .NET: Upewnij się, że zainstalowana została biblioteka GroupDocs.Conversion dla .NET. Można go pobrać z[Tutaj](https://releases.groupdocs.com/conversion/net/).
2. Środowisko programistyczne: Skonfiguruj środowisko programistyczne z niezbędnymi narzędziami, takimi jak Visual Studio lub dowolne inne środowisko .NET IDE.

## Importuj przestrzenie nazw
Uwzględnij w projekcie niezbędne przestrzenie nazw, aby uzyskać dostęp do funkcjonalności GroupDocs.Conversion.
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Krok 1: Ustaw folder wyjściowy i nazwę pliku
Najpierw zdefiniuj folder wyjściowy, w którym zostanie zapisany przekonwertowany plik PDF, i podaj nazwę wyjściowego pliku PDF.
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "pptx-converted-to.pdf");
```
## Krok 2: Załaduj źródłowy plik PPTX
Załaduj źródłowy plik prezentacji programu PowerPoint (PPTX), korzystając z biblioteki GroupDocs.Conversion.
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PPTX))
{
    // Tutaj zostanie umieszczona logika konwersji
}
```
## Krok 3: Określ opcje konwersji
Zdefiniuj opcje konwersji. W tym przypadku konwertujemy do formatu PDF, więc utwórz instancję`PdfConvertOptions`.
```csharp
var options = new PdfConvertOptions();
```
## Krok 4: Wykonaj konwersję
 Wykonaj proces konwersji za pomocą`Convert` metodę i przekaż ścieżkę pliku wyjściowego wraz z opcjami konwersji.
```csharp
converter.Convert(outputFile, options);
```
## Krok 5: Sprawdź dane wyjściowe
Po pomyślnym zakończeniu konwersji wyświetl komunikat informujący o zakończeniu i lokalizacji pliku wyjściowego.
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```

## Wniosek
W tym samouczku dowiedzieliśmy się, jak przekonwertować plik prezentacji programu PowerPoint (PPTX) na format dokumentu przenośnego (PDF) przy użyciu biblioteki GroupDocs.Conversion dla platformy .NET. Wykonując kroki opisane powyżej, możesz łatwo przeprowadzić tę konwersję w aplikacjach .NET.
## Często zadawane pytania
### P: Czy GroupDocs.Conversion jest kompatybilny ze wszystkimi wersjami .NET?
O: Tak, GroupDocs.Conversion obsługuje .NET Framework 2.0 i nowsze wersje, w tym .NET Core i .NET Standard.
### P: Czy mogę konwertować pliki do formatów innych niż PDF?
O: Tak, GroupDocs.Conversion obsługuje szeroką gamę formatów dokumentów do konwersji, w tym Word, Excel, HTML i inne.
### P: Czy GroupDocs.Conversion oferuje bezpłatną wersję próbną?
 O: Tak, możesz uzyskać dostęp do bezpłatnej wersji próbnej GroupDocs.Conversion z[Tutaj](https://releases.groupdocs.com/).
### P: Jak mogę uzyskać pomoc dotyczącą GroupDocs.Conversion?
 Odpowiedź: Możesz uzyskać pomoc na forum społeczności GroupDocs[Tutaj](https://forum.groupdocs.com/c/conversion/11).
### P: Czy dostępna jest tymczasowa licencja na GroupDocs.Conversion?
 O: Tak, tymczasową licencję na GroupDocs.Conversion można uzyskać od[Tutaj](https://purchase.groupdocs.com/temporary-license/).