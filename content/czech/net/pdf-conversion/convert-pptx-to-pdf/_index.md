---
title: Převést PPTX do PDF
linktitle: Převést PPTX do PDF
second_title: GroupDocs.Conversion .NET API
description: Naučte se převádět prezentace PowerPoint (PPTX) do formátu PDF pomocí GroupDocs.Conversion for .NET. Snadný a efektivní proces převodu.
weight: 29
url: /cs/net/pdf-conversion/convert-pptx-to-pdf/
---
## Úvod
tomto tutoriálu projdeme procesem převodu souboru prezentace PowerPoint (PPTX) do formátu PDF (Portable Document Format) pomocí knihovny GroupDocs.Conversion for .NET. Chcete-li dosáhnout této konverze, postupujte podle následujících kroků.
## Předpoklady
Než začneme, ujistěte se, že máte následující předpoklady:
1.  Knihovna GroupDocs.Conversion for .NET: Ujistěte se, že jste nainstalovali knihovnu GroupDocs.Conversion for .NET. Můžete si jej stáhnout z[tady](https://releases.groupdocs.com/conversion/net/).
2. Vývojové prostředí: Nastavte vývojové prostředí s nezbytnými nástroji, jako je Visual Studio nebo jakékoli jiné .NET IDE.

## Import jmenných prostorů
Zahrňte do projektu potřebné obory názvů pro přístup k funkcím GroupDocs.Conversion.
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Krok 1: Nastavte výstupní složku a název souboru
Nejprve definujte výstupní složku, kam bude převedený soubor PDF uložen, a zadejte název výstupního souboru PDF.
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "pptx-converted-to.pdf");
```
## Krok 2: Načtěte zdrojový soubor PPTX
Načtěte zdrojový soubor PowerPoint prezentace (PPTX) pomocí knihovny GroupDocs.Conversion.
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PPTX))
{
    // Zde bude umístěna konverzní logika
}
```
## Krok 3: Zadejte možnosti převodu
Definujte možnosti převodu. V tomto případě převádíme do formátu PDF, takže vytvořte instanci`PdfConvertOptions`.
```csharp
var options = new PdfConvertOptions();
```
## Krok 4: Proveďte konverzi
 Proveďte proces převodu pomocí`Convert` a předat cestu k výstupnímu souboru spolu s možnostmi převodu.
```csharp
converter.Convert(outputFile, options);
```
## Krok 5: Zkontrolujte výstup
Po úspěšném dokončení převodu zobrazte zprávu o dokončení a umístění výstupního souboru.
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```

## Závěr
V tomto tutoriálu jsme se naučili, jak převést soubor prezentace PowerPoint (PPTX) do formátu PDF (Portable Document Format) pomocí knihovny GroupDocs.Conversion pro .NET. Podle výše uvedených kroků můžete tento převod snadno provést ve svých aplikacích .NET.
## FAQ
### Otázka: Je GroupDocs.Conversion kompatibilní se všemi verzemi .NET?
Odpověď: Ano, GroupDocs.Conversion podporuje .NET Framework 2.0 a vyšší, včetně .NET Core a .NET Standard.
### Otázka: Mohu převádět soubory do jiných formátů než PDF?
Odpověď: Ano, GroupDocs.Conversion podporuje širokou škálu formátů dokumentů pro převod, včetně Wordu, Excelu, HTML a dalších.
### Otázka: Nabízí GroupDocs.Conversion nějakou bezplatnou zkušební verzi?
 Odpověď: Ano, máte přístup k bezplatné zkušební verzi GroupDocs.Conversion z[tady](https://releases.groupdocs.com/).
### Otázka: Jak mohu získat podporu pro GroupDocs.Conversion?
 Odpověď: Podporu můžete získat na fóru komunity GroupDocs[tady](https://forum.groupdocs.com/c/conversion/11).
### Otázka: Je k dispozici dočasná licence pro GroupDocs.Conversion?
 Odpověď: Ano, můžete získat dočasnou licenci pro GroupDocs.Conversion od[tady](https://purchase.groupdocs.com/temporary-license/).