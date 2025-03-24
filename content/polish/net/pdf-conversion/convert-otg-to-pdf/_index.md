---
title: Konwertuj OTG na PDF
linktitle: Konwertuj OTG na PDF
second_title: GroupDocs.Conversion API .NET
description: Dowiedz się, jak konwertować pliki OTG do formatu PDF za pomocą GroupDocs.Conversion dla .NET. Prosta, wydajna i bezproblemowa integracja Twoich projektów.
weight: 13
url: /pl/net/pdf-conversion/convert-otg-to-pdf/
---

# Konwertuj OTG na PDF

## Wstęp
Konwersja plików OTG (OpenDocument Graphics) do formatu PDF może być kluczowym zadaniem, szczególnie w przypadku systemów zarządzania dokumentami lub udostępniania plików na różnych platformach. W tym samouczku przeprowadzimy Cię przez proces konwersji plików OTG do formatu PDF przy użyciu biblioteki GroupDocs.Conversion dla .NET. Zanurzmy się!
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz następujące wymagania wstępne:
1. GroupDocs.Conversion dla .NET: Upewnij się, że zainstalowałeś bibliotekę GroupDocs.Conversion dla .NET. Można go pobrać z[Tutaj](https://releases.groupdocs.com/conversion/net/).
2. Plik OTG: Przygotuj plik OTG, który chcesz przekonwertować na format PDF, w swoim katalogu dokumentów.

## Importuj przestrzenie nazw
Najpierw musisz zaimportować niezbędne przestrzenie nazw do swojego projektu .NET. 
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Krok 1: Ustaw katalog wyjściowy i nazwę pliku
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "otg-converted-to.pdf");
```
 Na tym etapie definiujesz katalog wyjściowy, w którym zostanie zapisany przekonwertowany plik PDF. Zastępować`"Your Document Directory"` ze ścieżką do żądanego katalogu wyjściowego.
## Krok 2: Załaduj źródłowy plik OTG i przekonwertuj go na format PDF
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_OTG))
{
    var options = new PdfConvertOptions();
    // Zapisz przekonwertowany plik PDF
    converter.Convert(outputFile, options);
}
```
 Tutaj tworzymy instancję nowego`Converter` obiekt z biblioteki GroupDocs.Conversion, przekazując ścieżkę źródłowego pliku OTG. Następnie tworzymy`PdfConvertOptions` aby określić opcje konwersji. Na koniec nazywamy`Convert` metoda konwersji pliku OTG do formatu PDF.
## Krok 3: Sprawdź zakończenie konwersji
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
Ten krok powiadamia użytkownika, że proces konwersji zakończył się pomyślnie i podaje ścieżkę, w której zapisywany jest przekonwertowany plik PDF.

## Wniosek
Konwersja plików OTG do formatu PDF jest prosta dzięki bibliotece GroupDocs.Conversion dla .NET. Wykonując kroki opisane w tym samouczku, możesz bezproblemowo zintegrować tę funkcjonalność z aplikacjami .NET, zwiększając interoperacyjność i dostępność dokumentów.
## Często zadawane pytania
### Czy GroupDocs.Conversion może konwertować inne formaty plików oprócz OTG na PDF?
Tak, GroupDocs.Conversion obsługuje szeroką gamę formatów plików do konwersji, w tym DOCX, XLSX, PPTX, HTML i inne.
### Czy GroupDocs.Conversion nadaje się do użytku komercyjnego?
Absolutnie! GroupDocs.Conversion oferuje licencje komercyjne dla firm i organizacji, które chcą wykorzystać jego zaawansowane możliwości konwersji dokumentów.
### Czy GroupDocs.Conversion zapewnia pomoc techniczną?
Tak, GroupDocs oferuje dedykowaną pomoc techniczną, która pomaga użytkownikom w razie jakichkolwiek pytań lub problemów, jakie mogą napotkać podczas wdrażania.
### Czy mogę wypróbować GroupDocs.Conversion przed zakupem licencji?
Tak, możesz skorzystać z bezpłatnej wersji próbnej GroupDocs.Conversion, aby poznać jego funkcje i zgodność ze swoimi wymaganiami.
### Jak mogę uzyskać tymczasową licencję na GroupDocs.Conversion?
Możesz uzyskać tymczasową licencję od GroupDocs do celów ewaluacyjnych lub projektów krótkoterminowych, odwiedzając stronę tymczasową[licencja](https://purchase.groupdocs.com/temporary-license/).