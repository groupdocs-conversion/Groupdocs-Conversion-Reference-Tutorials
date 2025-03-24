---
title: Převod vektorové grafiky CDR do PDF
linktitle: Převod vektorové grafiky CDR do PDF
second_title: GroupDocs.Conversion .NET API
description: Bez námahy převádějte soubory vektorové grafiky CorelDRAW (CDR) do formátu PDF pomocí GroupDocs.Conversion for .NET. Zefektivněte proces převodu dokumentů.
weight: 12
url: /cs/net/file-conversion-to-pdf/convert-cdr-to-pdf/
---
## Úvod
GroupDocs.Conversion for .NET je výkonná knihovna pro převod dokumentů, která umožňuje vývojářům bezproblémově převádět různé formáty dokumentů do PDF, Wordu, HTML a mnoha dalších. V tomto tutoriálu se zaměříme na převod souborů vektorové grafiky CorelDRAW (CDR) do formátu PDF pomocí GroupDocs.Conversion for .NET. Na konci této příručky budete vybaveni znalostmi, abyste mohli bez námahy provést tento převod ve vašich aplikacích .NET.
## Předpoklady
Než se pustíme do procesu převodu, ujistěte se, že máte nastaveny následující předpoklady:
### Nainstalujte GroupDocs.Conversion for .NET
 Chcete-li začít, musíte si stáhnout a nainstalovat GroupDocs.Conversion for .NET. Knihovnu si můžete stáhnout z[stránka ke stažení](https://releases.groupdocs.com/conversion/net/).
### Získejte licenci
 Chcete-li využít plný potenciál GroupDocs.Conversion for .NET, budete potřebovat platnou licenci. Licenci můžete získat od[GroupDocs](https://purchase.groupdocs.com/buy)nebo požádat o dočasnou licenci pro testovací účely[tady](https://purchase.groupdocs.com/temporary-license/).

## Import jmenných prostorů
Ujistěte se, že jste do svého projektu .NET importovali potřebné jmenné prostory, abyste mohli využívat funkce GroupDocs.Conversion. Můžete to udělat takto:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Krok 1: Definujte výstupní složku a název souboru
Nejprve určete výstupní složku, kam bude převedený soubor PDF uložen, spolu s požadovaným názvem souboru.
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "cdr-converted-to.pdf");
```
Nezapomeňte vyměnit`"Your Document Directory"` s cestou k požadované výstupní složce.
## Krok 2: Načtěte zdrojový soubor CDR
Dále načtěte zdrojový soubor CDR, který chcete převést do PDF, pomocí GroupDocs.Conversion.
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_CDR))
{
    // Zde bude logika konverze
}
```
 Nahradit`Constants.SAMPLE_CDR` s cestou k vašemu skutečnému souboru CDR.
## Krok 3: Zadejte možnosti převodu
Definujte možnosti převodu, jako je zadání výstupního formátu (PDF) a jakákoli další nastavení.
```csharp
var options = new PdfConvertOptions();
```
Možnosti převodu si můžete přizpůsobit podle svých požadavků.
## Krok 4: Proveďte konverzi
Proveďte proces převodu se zadanými možnostmi.
```csharp
converter.Convert(outputFile, options);
```
Tento příkaz převede soubor CDR na PDF a uloží jej do zadané výstupní složky se zadaným názvem souboru.
## Krok 5: Potvrďte dokončení převodu
Nakonec zobrazte zprávu potvrzující úspěšné dokončení procesu převodu.
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```
Tato zpráva vás bude informovat o umístění, kde je uložen převedený soubor PDF.

## Závěr
V tomto kurzu jsme se naučili, jak převést soubory vektorové grafiky CorelDRAW (CDR) do formátu PDF pomocí GroupDocs.Conversion for .NET. Dodržováním nastíněných kroků můžete bez problémů integrovat možnosti převodu dokumentů do vašich aplikací .NET a zlepšit jejich funkčnost a použitelnost.
## FAQ
### Je GroupDocs.Conversion for .NET kompatibilní se všemi verzemi souborů CorelDRAW?
GroupDocs.Conversion for .NET podporuje širokou škálu verzí CorelDRAW, což zajišťuje kompatibilitu s většinou souborů CDR.
### Mohu pomocí GroupDocs.Conversion for .NET převést více souborů CDR současně?
Ano, můžete dávkově převést více souborů CDR do PDF nebo jiných formátů pomocí GroupDocs.Conversion for .NET, což zvyšuje efektivitu a produktivitu.
### Vyžaduje GroupDocs.Conversion for .NET připojení k internetu pro převod dokumentů?
Ne, GroupDocs.Conversion for .NET provádí konverzi dokumentů lokálně na vašem počítači, čímž eliminuje potřebu připojení k internetu během procesu převodu.
### Mohu upravit nastavení převodu podle svých specifických požadavků?
Ano, GroupDocs.Conversion for .NET poskytuje rozsáhlé možnosti přizpůsobení, které vám umožní přizpůsobit proces převodu přesně vašim potřebám.
### Je k dispozici technická podpora pro GroupDocs.Conversion for .NET?
 Ano, GroupDocs nabízí komplexní technickou podporu pro své produkty, včetně GroupDocs.Conversion for .NET. Můžete požádat o pomoc u[Fórum podpory](https://forum.groupdocs.com/c/conversion/11) pro jakékoli dotazy nebo problémy.