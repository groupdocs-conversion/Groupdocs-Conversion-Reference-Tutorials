---
title: Převést PSD do PDF
linktitle: Převést PSD do PDF
second_title: GroupDocs.Conversion .NET API
description: Naučte se, jak bez námahy převést soubory PSD do PDF pomocí GroupDocs.Conversion for .NET. Postupujte podle našeho podrobného průvodce.
weight: 10
url: /cs/net/file-format-conversion-convert-psd-to-pdf/
---
## Úvod
V tomto tutoriálu vás provedeme procesem převodu souborů PSD (Photoshop Document) do formátu PDF pomocí knihovny GroupDocs.Conversion pro .NET. Budete-li se řídit těmito podrobnými pokyny, budete moci snadno převádět soubory PSD na soubory PDF.
## Předpoklady
Než začneme, ujistěte se, že máte nastaveny následující předpoklady:
1.  Instalace knihovny GroupDocs.Conversion: Ujistěte se, že jste nainstalovali knihovnu GroupDocs.Conversion pro .NET. Můžete si jej stáhnout z[webová stránka](https://releases.groupdocs.com/conversion/net/).
2. Přístup k souborům PSD: Získejte přístup k souborům PSD, které chcete převést do PDF.

## Import jmenných prostorů
Než se ponoříte do procesu převodu, importujte potřebné jmenné prostory:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Krok 1: Definujte výstupní složku a soubor
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "psd-converted-to.pdf");
```
 V tomto kroku určete výstupní složku, kam chcete uložit převedený soubor PDF. Ujistěte se, že jste vyměnili`"Your Document Directory"` se skutečnou cestou k adresáři.
## Krok 2: Načtěte zdrojový soubor PSD
```csharp
using (var converter = new GroupDocs.Conversion.Converter("Path_to_your_PSD_file.psd"))
{
    var options = new PdfConvertOptions();
    // Uložit převedený soubor PDF
    converter.Convert(outputFile, options);
}
```
 Zde inicializujete`Converter` objekt s cestou k vašemu souboru PSD. Nahradit`"Path_to_your_PSD_file.psd"` se skutečnou cestou k vašemu souboru PSD. Poté vytvořte instanci`PdfConvertOptions` specifikovat nastavení převodu. Nakonec zavolejte na`Convert` způsob převodu souboru PSD do formátu PDF a jeho uložení do určeného výstupního souboru.
## Krok 3: Zkontrolujte dokončení konverze
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```
Tento krok jednoduše vytiskne zprávu do konzole potvrzující úspěšné dokončení procesu převodu a označí umístění, kam je převedený soubor PDF uložen.

## Závěr
tomto tutoriálu jsme si ukázali, jak převést soubory PSD do formátu PDF pomocí knihovny GroupDocs.Conversion for .NET. Podle uvedených kroků můžete bez námahy převést soubory PSD na soubory PDF, což umožní snadnější sdílení a prohlížení vašich dokumentů.
## FAQ

### Mohu pomocí GroupDocs.Conversion převést více souborů PSD najednou?
Ano, pomocí GroupDocs.Conversion můžete dávkově převést více souborů PSD do PDF nebo jiných formátů.

### Podporuje GroupDocs.Conversion jiné výstupní formáty kromě PDF?
Ano, GroupDocs.Conversion podporuje širokou škálu výstupních formátů včetně DOCX, XLSX, PPTX, JPEG, PNG a dalších.

### Je GroupDocs.Conversion kompatibilní s různými verzemi .NET?
Ano, GroupDocs.Conversion je kompatibilní s různými verzemi .NET včetně .NET Core a .NET Framework.

### Mohu přizpůsobit možnosti převodu pro větší kontrolu nad výstupem?
Ano, GroupDocs.Conversion poskytuje rozsáhlé možnosti přizpůsobení, jako je určení velikosti stránky, orientace, kvality a další.

### Je k dispozici zkušební verze pro testování před zakoupením?
Ano, můžete získat bezplatnou zkušební verzi GroupDocs.Conversion z[webová stránka](https://releases.groupdocs.com/conversion/net/) k otestování jeho funkcí před nákupem.