---
title: Převést obrázky DNG do PDF
linktitle: Převést obrázky DNG do PDF
second_title: GroupDocs.Conversion .NET API
description: Naučte se, jak bez námahy převést obrázky DNG do PDF pomocí GroupDocs.Conversion for .NET. Postupujte podle našeho podrobného průvodce pro bezproblémovou konverzi.
weight: 21
url: /cs/net/file-conversion-to-pdf/convert-dng-to-pdf/
---
## Úvod
V tomto tutoriálu vás provedeme procesem převodu obrázků DNG do PDF pomocí GroupDocs.Conversion for .NET. DNG (Digital Negative) je formát souboru používaný pro digitální fotografii. Převedením obrázků DNG do PDF je můžete snadno sdílet nebo ukládat v univerzálněji přijímaném formátu.
## Předpoklady
Než začnete, ujistěte se, že máte následující:
1.  GroupDocs.Conversion for .NET: Stáhněte si a nainstalujte knihovnu GroupDocs.Conversion pro .NET z[tady](https://releases.groupdocs.com/conversion/net/).
2. Zdrojový soubor DNG: Potřebujete soubor obrázku DNG, který chcete převést do formátu PDF.
3. Vývojové prostředí: Ujistěte se, že máte nastavené vývojové prostředí .NET.

## Import jmenných prostorů
Nejprve musíte do projektu importovat potřebné jmenné prostory. Pomocí direktiv přidejte do souboru kódu následující:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Krok 1: Načtěte zdrojový soubor DNG
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "dng-converted-to.pdf");
// Načtěte zdrojový soubor DNG
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_DNG))
{
    // Pokračujte v procesu převodu
}
```
 V tomto kroku definujete výstupní složku, kam se uloží převedený soubor PDF. Zajistěte výměnu`"Your Document Directory"` s cestou k požadovanému adresáři. Poté zadejte název a cestu výstupního souboru PDF.
## Krok 2: Převeďte DNG do PDF
```csharp
var options = new PdfConvertOptions();
// Uložit převedený soubor PDF
converter.Convert(outputFile, options);
```
 Zde vytvoříte instanci`PdfConvertOptions` pro nastavení jakýchkoli specifických voleb pro převod PDF, je-li to nutné. Poté zavoláte`Convert` metoda`converter`objekt, předání cesty k výstupnímu souboru a možností převodu.
## Krok 3: Zvládněte dokončení převodu
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
Po dokončení procesu převodu se zobrazí zpráva o úspěchu spolu s adresářem, kde se nachází převedený soubor PDF.

## Závěr
Závěrem lze říci, že převod obrázků DNG do PDF lze snadno provést pomocí GroupDocs.Conversion for .NET. Pomocí jednoduchých kroků popsaných v tomto tutoriálu můžete efektivně převést své soubory DNG do formátu PDF, aby byly přístupnější a sdílené.
## FAQ
### Je GroupDocs.Conversion for .NET kompatibilní se všemi verzemi .NET?
Ano, GroupDocs.Conversion for .NET je kompatibilní s .NET Framework 4.6.1 a vyšším, stejně jako .NET Core 2.0 a vyšším.
### Mohu převést více souborů DNG do PDF současně?
Ano, můžete převést více souborů DNG do PDF tím, že projdete každý soubor a pro každý z nich provedete proces převodu.
### Existují nějaká omezení velikosti souborů DNG, které lze převést?
GroupDocs.Conversion for .NET nemá žádná konkrétní omezení velikosti souborů DNG, které lze převést. Výkon se však může lišit v závislosti na velikosti a složitosti vstupních souborů.
### Mohu přizpůsobit možnosti převodu pro výstup PDF?
 Ano, můžete upravit různé možnosti, jako je velikost stránky, orientace, komprese a další pomocí`PdfConvertOptions`třídy poskytované GroupDocs.Conversion for .NET.
### Je k dispozici technická podpora pro GroupDocs.Conversion for .NET?
 Ano, technická podpora je k dispozici prostřednictvím fóra GroupDocs[tady](https://forum.groupdocs.com/c/conversion/11), kde můžete klást otázky a získat pomoc od odborníků.