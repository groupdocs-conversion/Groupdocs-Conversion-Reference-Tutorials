---
"description": "Naučte se, jak převádět prezentace PowerPointu (PPTX) do formátu PDF pomocí nástroje GroupDocs.Conversion pro .NET. Snadný a efektivní proces převodu."
"linktitle": "Převod PPTX do PDF"
"second_title": "GroupDocs.Conversion .NET API"
"title": "Převod PPTX do PDF"
"url": "/cs/net/pdf-conversion/convert-pptx-to-pdf/"
"weight": 29
type: docs
---
# Převod PPTX do PDF

## Zavedení
tomto tutoriálu si projdeme procesem převodu souboru prezentace PowerPoint (PPTX) do formátu PDF (Portable Document Format) pomocí knihovny GroupDocs.Conversion pro .NET. Pro provedení této konverze postupujte podle níže uvedených kroků.
## Předpoklady
Než začneme, ujistěte se, že máte následující předpoklady:
1. Knihovna GroupDocs.Conversion pro .NET: Ujistěte se, že máte nainstalovanou knihovnu GroupDocs.Conversion pro .NET. Můžete si ji stáhnout z [zde](https://releases.groupdocs.com/conversion/net/).
2. Vývojové prostředí: Nastavte vývojové prostředí s potřebnými nástroji, jako je Visual Studio nebo jakékoli jiné .NET IDE.

## Importovat jmenné prostory
Pro přístup k funkcím GroupDocs.Conversion zahrňte do projektu potřebné jmenné prostory.
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Krok 1: Nastavení výstupní složky a názvu souboru
Nejprve definujte výstupní složku, kam bude převedený soubor PDF uložen, a zadejte název výstupního souboru PDF.
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "pptx-converted-to.pdf");
```
## Krok 2: Načtěte zdrojový soubor PPTX
Načtěte zdrojový soubor prezentace PowerPoint (PPTX) pomocí knihovny GroupDocs.Conversion.
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PPTX))
{
    // Logika konverze bude umístěna zde
}
```
## Krok 3: Zadejte možnosti převodu
Definujte možnosti převodu. V tomto případě převádíme do formátu PDF, proto vytvořte instanci `PdfConvertOptions`.
```csharp
var options = new PdfConvertOptions();
```
## Krok 4: Proveďte konverzi
Proveďte proces převodu pomocí `Convert` metodu a předat cestu k výstupnímu souboru spolu s možnostmi převodu.
```csharp
converter.Convert(outputFile, options);
```
## Krok 5: Zkontrolujte výstup
Po úspěšném dokončení převodu se zobrazí zpráva s uvedením dokončení a umístění výstupního souboru.
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```

## Závěr
V tomto tutoriálu jsme se naučili, jak převést soubor prezentace PowerPoint (PPTX) do formátu PDF (Portable Document Format) pomocí knihovny GroupDocs.Conversion pro .NET. Dodržením výše uvedených kroků můžete tuto konverzi snadno provést ve svých aplikacích .NET.
## Často kladené otázky
### Otázka: Je GroupDocs.Conversion kompatibilní se všemi verzemi .NET?
A: Ano, GroupDocs.Conversion podporuje .NET Framework 2.0 a vyšší, včetně .NET Core a .NET Standard.
### Otázka: Mohu převést soubory do jiných formátů než PDF?
A: Ano, GroupDocs.Conversion podporuje širokou škálu formátů dokumentů pro převod, včetně Wordu, Excelu, HTML a dalších.
### Otázka: Nabízí GroupDocs.Conversion nějakou bezplatnou zkušební verzi?
A: Ano, můžete si zdarma vyzkoušet GroupDocs.Conversion z [zde](https://releases.groupdocs.com/).
### Otázka: Jak mohu získat podporu pro GroupDocs.Conversion?
A: Podporu můžete získat na komunitním fóru GroupDocs. [zde](https://forum.groupdocs.com/c/conversion/11).
### Otázka: Je k dispozici dočasná licence pro GroupDocs.Conversion?
A: Ano, dočasnou licenci pro GroupDocs.Conversion můžete získat od [zde](https://purchase.groupdocs.com/temporary-license/).