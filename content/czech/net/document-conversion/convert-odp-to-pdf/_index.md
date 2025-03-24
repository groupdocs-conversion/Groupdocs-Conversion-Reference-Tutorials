---
title: Převést ODP do PDF
linktitle: Převést ODP do PDF
second_title: GroupDocs.Conversion .NET API
description: Naučte se, jak převést ODP do PDF pomocí GroupDocs.Conversion for .NET. Postupujte podle našeho podrobného průvodce pro bezproblémový převod dokumentů.
weight: 28
url: /cs/net/document-conversion/convert-odp-to-pdf/
---
## Úvod
GroupDocs.Conversion for .NET je výkonné API, které umožňuje vývojářům bezproblémově převádět různé formáty dokumentů v jejich aplikacích .NET. V tomto tutoriálu vás provedeme procesem převodu souboru ODP (OpenDocument Presentation) do formátu PDF pomocí GroupDocs.Conversion for .NET.
## Předpoklady
Než začneme, ujistěte se, že máte následující předpoklady:
1.  GroupDocs.Conversion for .NET SDK: Ujistěte se, že jste si stáhli a nainstalovali GroupDocs.Conversion for .NET SDK. Můžete si jej stáhnout z[stránka ke stažení](https://releases.groupdocs.com/conversion/net/).
2. Vývojové prostředí .NET: Na svém počítači byste měli mít nastavené vývojové prostředí .NET.
3. Zdrojový soubor ODP: Připravte soubor ODP, který chcete převést do PDF.

## Import jmenných prostorů
Nejprve importujte potřebné jmenné prostory do kódu C#:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Krok 1: Definujte cestu k výstupnímu souboru
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "odp-converted-to.pdf");
```
 Nahradit`"Your Document Directory"` s cestou, kam chcete uložit převedený soubor PDF.
## Krok 2: Načtěte zdrojový soubor ODP
```csharp
using (var converter = new GroupDocs.Conversion.Converter("path/to/your/source.odp"))
{
    // Konverzní kód půjde sem
}
```
 Nahradit`"path/to/your/source.odp"` se skutečnou cestou ke zdrojovému souboru ODP.
## Krok 3: Nastavte možnosti převodu
```csharp
var options = new PdfConvertOptions();
```
Zde si můžete přizpůsobit možnosti převodu podle svých požadavků. Můžete například nastavit nastavení převodu PDF, jako je velikost stránky, okraje, kvalita atd.
## Krok 4: Proveďte konverzi
```csharp
converter.Convert(outputFile, options);
```
Tento řádek kódu zahájí proces převodu z ODP do PDF pomocí zadaných možností.
## Krok 5: Zobrazte zprávu o úspěchu
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```
Na tomto řádku se zobrazí zpráva o úspěchu spolu s výstupní složkou, kam je převedený soubor PDF uložen.

## Závěr
V tomto tutoriálu jsme se naučili, jak převést soubor ODP do PDF pomocí GroupDocs.Conversion for .NET. Podle uvedených kroků můžete snadno integrovat možnosti převodu dokumentů do aplikací .NET.
## FAQ
### Dokáže GroupDocs.Conversion for .NET zpracovat jiné formáty dokumentů?
Ano, GroupDocs.Conversion for .NET podporuje širokou škálu formátů dokumentů včetně Wordu, Excelu, PowerPointu, PDF a dalších.
### Je k dispozici bezplatná zkušební verze pro GroupDocs.Conversion for .NET?
 Ano, můžete využít bezplatnou zkušební verzi z[webová stránka](https://releases.groupdocs.com/).
### Jak mohu získat technickou podporu pro GroupDocs.Conversion for .NET?
 Technickou podporu můžete získat od[Fórum podpory](https://forum.groupdocs.com/c/conversion/11).
### Mohu upravit možnosti převodu podle svých požadavků?
Ano, GroupDocs.Conversion for .NET poskytuje rozsáhlé možnosti přizpůsobení vašim specifickým potřebám.
### Kde si mohu zakoupit licenci pro GroupDocs.Conversion for .NET?
 Licenci si můžete zakoupit od[nákupní stránku](https://purchase.groupdocs.com/buy).