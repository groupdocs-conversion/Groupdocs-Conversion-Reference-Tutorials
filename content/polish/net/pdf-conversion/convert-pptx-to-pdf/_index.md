---
"description": "Dowiedz się, jak konwertować prezentacje PowerPoint (PPTX) do formatu PDF za pomocą GroupDocs.Conversion dla .NET. Łatwy i wydajny proces konwersji."
"linktitle": "Konwertuj PPTX do PDF"
"second_title": "GroupDocs.Conversion .NET API"
"title": "Konwertuj PPTX do PDF"
"url": "/pl/net/pdf-conversion/convert-pptx-to-pdf/"
"weight": 29
---

# Konwertuj PPTX do PDF

## Wstęp
tym samouczku przeprowadzimy Cię przez proces konwersji pliku prezentacji PowerPoint (PPTX) do formatu Portable Document Format (PDF) przy użyciu biblioteki GroupDocs.Conversion dla .NET. Wykonaj poniższe kroki, aby dokonać tej konwersji.
## Wymagania wstępne
Zanim zaczniemy, upewnij się, że spełniasz następujące wymagania wstępne:
1. Biblioteka GroupDocs.Conversion for .NET: Upewnij się, że zainstalowałeś bibliotekę GroupDocs.Conversion for .NET. Możesz ją pobrać z [Tutaj](https://releases.groupdocs.com/conversion/net/).
2. Środowisko programistyczne: Skonfiguruj środowisko programistyczne przy użyciu niezbędnych narzędzi, takich jak Visual Studio lub inne środowisko IDE .NET.

## Importuj przestrzenie nazw
Aby uzyskać dostęp do funkcjonalności GroupDocs.Conversion, uwzględnij w swoim projekcie niezbędne przestrzenie nazw.
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Krok 1: Ustaw folder wyjściowy i nazwę pliku
Najpierw zdefiniuj folder wyjściowy, w którym zostanie zapisany przekonwertowany plik PDF, i podaj nazwę pliku wyjściowego PDF.
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "pptx-converted-to.pdf");
```
## Krok 2: Załaduj plik źródłowy PPTX
Załaduj plik źródłowy prezentacji PowerPoint (PPTX) przy użyciu biblioteki GroupDocs.Conversion.
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PPTX))
{
    // Logika konwersji zostanie umieszczona tutaj
}
```
## Krok 3: Określ opcje konwersji
Zdefiniuj opcje konwersji. W tym przypadku konwertujemy do formatu PDF, więc utwórz wystąpienie `PdfConvertOptions`.
```csharp
var options = new PdfConvertOptions();
```
## Krok 4: Wykonaj konwersję
Wykonaj proces konwersji za pomocą `Convert` i przekazujemy ścieżkę do pliku wyjściowego wraz z opcjami konwersji.
```csharp
converter.Convert(outputFile, options);
```
## Krok 5: Sprawdź wynik
Po pomyślnym zakończeniu konwersji zostanie wyświetlony komunikat informujący o jej zakończeniu i lokalizacji pliku wyjściowego.
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```

## Wniosek
W tym samouczku nauczyliśmy się, jak przekonwertować plik prezentacji PowerPoint (PPTX) na Portable Document Format (PDF) przy użyciu biblioteki GroupDocs.Conversion dla .NET. Postępując zgodnie z powyższymi krokami, możesz łatwo wykonać tę konwersję w swoich aplikacjach .NET.
## Najczęściej zadawane pytania
### P: Czy GroupDocs.Conversion jest kompatybilny ze wszystkimi wersjami .NET?
O: Tak, GroupDocs.Conversion obsługuje środowisko .NET Framework 2.0 i nowsze, w tym .NET Core i .NET Standard.
### P: Czy mogę konwertować pliki do formatów innych niż PDF?
O: Tak, GroupDocs.Conversion obsługuje szeroką gamę formatów dokumentów na potrzeby konwersji, w tym Word, Excel, HTML i inne.
### P: Czy GroupDocs.Conversion oferuje bezpłatny okres próbny?
O: Tak, możesz uzyskać dostęp do bezpłatnej wersji próbnej GroupDocs.Conversion z [Tutaj](https://releases.groupdocs.com/).
### P: W jaki sposób mogę uzyskać pomoc techniczną dotyczącą GroupDocs.Conversion?
A: Możesz uzyskać pomoc na forum społeczności GroupDocs [Tutaj](https://forum.groupdocs.com/c/conversion/11).
### P: Czy jest dostępna tymczasowa licencja na GroupDocs.Conversion?
O: Tak, możesz uzyskać tymczasową licencję na GroupDocs.Conversion z [Tutaj](https://purchase.groupdocs.com/temporary-license/).