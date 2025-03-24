---
title: Převést SVG do PDF
linktitle: Převést SVG do PDF
second_title: GroupDocs.Conversion .NET API
description: Naučte se, jak převést SVG do PDF pomocí GroupDocs.Conversion for .NET bez námahy. Zefektivněte proces správy dokumentů.
weight: 15
url: /cs/net/file-format-conversion-convert-svg-to-pdf/
---

# Převést SVG do PDF

## Úvod
Ve světě programování je převod souborů z jednoho formátu do druhého běžným úkolem. Ať už pracujete s obrázky, dokumenty nebo jinými médii, schopnost bezproblémově převádět mezi formáty je zásadní. V tomto tutoriálu se ponoříme do toho, jak převést soubory SVG (Scalable Vector Graphics) do PDF (Portable Document Format) pomocí GroupDocs.Conversion for .NET.
## Předpoklady
Než se ponoříte do procesu převodu, ujistěte se, že máte nastaveny následující předpoklady:
### 1. Nainstalujte GroupDocs.Conversion for .NET
Ujistěte se, že máte ve vývojovém prostředí nainstalovanou aplikaci GroupDocs.Conversion for .NET. Pokud jste tak ještě neučinili, můžete si jej stáhnout z[webová stránka](https://releases.groupdocs.com/conversion/net/).
### 2. Získejte ukázkový soubor SVG
K převodu do PDF budete potřebovat ukázkový soubor SVG. Pokud žádný nemáte, můžete soubory SVG snadno najít online nebo si je vytvořit pomocí různých nástrojů pro grafický design.
### 3. Základní porozumění C#
Seznamte se se základy programovacího jazyka C#, protože jej budeme používat k psaní konverzního kódu.

## Import jmenných prostorů
Nejprve importujme potřebné jmenné prostory:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Krok 1: Definujte výstupní složku a soubor
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "svg-converted-to.pdf");
```
 Zajistěte výměnu`"Your Document Directory"` s cestou k požadovanému výstupnímu adresáři.
## Krok 2: Načtěte zdrojový soubor SVG
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_SVG))
{
    // Konverzní kód je zde
}
```
 Nahradit`Constants.SAMPLE_SVG` s cestou k vašemu souboru SVG.
## Krok 3: Nastavte možnosti převodu
```csharp
var options = new PdfConvertOptions();
```
Zde nastavujeme možnosti převodu speciálně pro výstup PDF. Tyto možnosti si můžete přizpůsobit podle svých požadavků.
## Krok 4: Proveďte konverzi
```csharp
converter.Convert(outputFile, options);
```
Tento řádek provede proces převodu, vezme zdrojový soubor SVG a převede jej do PDF se zadanými možnostmi.
## Krok 5: Zkontrolujte dokončení konverze
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
Na tomto řádku se zobrazí zpráva potvrzující úspěšné dokončení procesu převodu spolu s adresářem, kde se nachází převedený soubor PDF.

## Závěr
V tomto tutoriálu jsme se naučili, jak převést soubory SVG do PDF pomocí GroupDocs.Conversion for .NET. Pokud se budete řídit podrobným průvodcem a zajistíte, že máte připravené předpoklady, můžete do svých aplikací .NET bez problémů začlenit možnosti převodu formátu souborů.
## FAQ
### Je GroupDocs.Conversion for .NET kompatibilní se všemi frameworky .NET?
Ano, GroupDocs.Conversion for .NET podporuje více rozhraní .NET, včetně .NET Core a .NET Framework.
### Mohu přizpůsobit možnosti převodu pro konkrétní výstupní formáty?
Absolutně! GroupDocs.Conversion for .NET poskytuje rozsáhlé možnosti přizpůsobení pro každý podporovaný výstupní formát.
### Podporuje GroupDocs.Conversion for .NET dávkovou konverzi?
Ano, pomocí GroupDocs.Conversion for .NET můžete převést více souborů současně.
### Je k dispozici zkušební verze pro účely testování?
 Ano, máte přístup k bezplatné zkušební verzi z[tady](https://releases.groupdocs.com/).
### Kde mohu získat technickou podporu pro GroupDocs.Conversion for .NET?
Technickou podporu a pomoc najdete na fóru GroupDocs[tady](https://forum.groupdocs.com/c/conversion/11).