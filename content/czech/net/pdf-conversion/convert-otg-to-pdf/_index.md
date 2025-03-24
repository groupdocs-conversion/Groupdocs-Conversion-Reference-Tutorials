---
title: Převést OTG do PDF
linktitle: Převést OTG do PDF
second_title: GroupDocs.Conversion .NET API
description: Naučte se převádět soubory OTG do PDF pomocí GroupDocs.Conversion for .NET. Jednoduchá, efektivní a bezproblémová integrace pro vaše projekty.
weight: 13
url: /cs/net/pdf-conversion/convert-otg-to-pdf/
---

# Převést OTG do PDF

## Úvod
Převod souborů OTG (OpenDocument Graphics) do formátu PDF může být zásadním úkolem, zejména při práci se systémy správy dokumentů nebo sdílení souborů na různých platformách. V tomto tutoriálu vás provedeme procesem převodu souborů OTG do PDF pomocí knihovny GroupDocs.Conversion pro .NET. Pojďme se ponořit!
## Předpoklady
Než začneme, ujistěte se, že máte následující předpoklady:
1. GroupDocs.Conversion for .NET: Ujistěte se, že jste nainstalovali knihovnu GroupDocs.Conversion pro .NET. Můžete si jej stáhnout z[tady](https://releases.groupdocs.com/conversion/net/).
2. Soubor OTG: Připravte si soubor OTG, který chcete převést do PDF, v adresáři dokumentů.

## Import jmenných prostorů
Nejprve musíte do svého projektu .NET importovat potřebné jmenné prostory. 
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Krok 1: Nastavte výstupní adresář a název souboru
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "otg-converted-to.pdf");
```
 V tomto kroku definujete výstupní adresář, kam bude převedený soubor PDF uložen. Nahradit`"Your Document Directory"` s cestou k požadovanému výstupnímu adresáři.
## Krok 2: Načtěte zdrojový soubor OTG a převeďte jej do PDF
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_OTG))
{
    var options = new PdfConvertOptions();
    // Uložit převedený soubor PDF
    converter.Convert(outputFile, options);
}
```
 Zde vytvoříme nový`Converter` objekt z knihovny GroupDocs.Conversion, předá cestu ke zdrojovému souboru OTG. Poté tvoříme`PdfConvertOptions` specifikovat možnosti převodu. Nakonec zavoláme`Convert` způsob převodu souboru OTG do formátu PDF.
## Krok 3: Zkontrolujte dokončení konverze
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
Tento krok upozorní uživatele, že proces převodu je úspěšně dokončen, a poskytne cestu, kam je převedený soubor PDF uložen.

## Závěr
Převod souborů OTG do formátu PDF je jednoduchý s knihovnou GroupDocs.Conversion pro .NET. Podle kroků uvedených v tomto kurzu můžete tuto funkci hladce integrovat do svých aplikací .NET a zlepšit tak interoperabilitu a dostupnost dokumentů.
## FAQ
### Může GroupDocs.Conversion převést jiné formáty souborů kromě OTG do PDF?
Ano, GroupDocs.Conversion podporuje širokou škálu formátů souborů pro převod, včetně DOCX, XLSX, PPTX, HTML a dalších.
### Je GroupDocs.Conversion vhodný pro komerční použití?
Absolutně! GroupDocs.Conversion nabízí komerční licence pro podniky a organizace, které chtějí využít jeho výkonné možnosti konverze dokumentů.
### Poskytuje GroupDocs.Conversion technickou podporu?
Ano, GroupDocs nabízí vyhrazenou technickou podporu, která uživatelům pomůže s jakýmikoli dotazy nebo problémy, se kterými se mohou během implementace setkat.
### Mohu vyzkoušet GroupDocs.Conversion před zakoupením licence?
Ano, můžete využít bezplatnou zkušební verzi GroupDocs.Conversion a prozkoumat její funkce a kompatibilitu s vašimi požadavky.
### Jak mohu získat dočasnou licenci pro GroupDocs.Conversion?
Dočasnou licenci od GroupDocs pro účely hodnocení nebo krátkodobé projekty můžete získat návštěvou dočasné licence[licence](https://purchase.groupdocs.com/temporary-license/).