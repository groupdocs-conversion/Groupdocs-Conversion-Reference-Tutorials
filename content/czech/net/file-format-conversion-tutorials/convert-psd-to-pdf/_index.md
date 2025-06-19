---
"description": "Naučte se, jak snadno převést soubory PSD do PDF pomocí GroupDocs.Conversion pro .NET. Postupujte podle našeho podrobného návodu."
"linktitle": "Převod PSD do PDF"
"second_title": "GroupDocs.Conversion .NET API"
"title": "Převod PSD do PDF"
"url": "/cs/net/file-format-conversion-tutorials/convert-psd-to-pdf/"
"weight": 10
---

# Převod PSD do PDF

## Zavedení
V tomto tutoriálu vás provedeme procesem převodu souborů PSD (dokumenty Photoshopu) do formátu PDF pomocí knihovny GroupDocs.Conversion pro .NET. Dodržováním těchto podrobných pokynů budete schopni bez problémů převést soubory PSD do formátu PDF.
## Předpoklady
Než začneme, ujistěte se, že máte nastaveny následující předpoklady:
1. Instalace knihovny GroupDocs.Conversion: Ujistěte se, že máte nainstalovanou knihovnu GroupDocs.Conversion pro .NET. Můžete si ji stáhnout z [webové stránky](https://releases.groupdocs.com/conversion/net/).
2. Přístup k souborům PSD: Mějte přístup k souborům PSD, které chcete převést do formátu PDF.

## Importovat jmenné prostory
Než se ponoříme do procesu konverze, importujte potřebné jmenné prostory:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Krok 1: Definování výstupní složky a souboru
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "psd-converted-to.pdf");
```
tomto kroku určete výstupní složku, kam chcete uložit převedený soubor PDF. Ujistěte se, že jste nahradili `"Your Document Directory"` se skutečnou cestou k adresáři.
## Krok 2: Načtěte zdrojový soubor PSD
```csharp
using (var converter = new GroupDocs.Conversion.Converter("Path_to_your_PSD_file.psd"))
{
    var options = new PdfConvertOptions();
    // Uložit převedený soubor PDF
    converter.Convert(outputFile, options);
}
```
Zde inicializujete `Converter` objekt cestou k vašemu souboru PSD. Nahraďte `"Path_to_your_PSD_file.psd"` se skutečnou cestou k vašemu souboru PSD. Poté vytvořte instanci `PdfConvertOptions` pro určení nastavení převodu. Nakonec zavolejte `Convert` metoda pro převod souboru PSD do PDF a jeho uložení do zadaného výstupního souboru.
## Krok 3: Kontrola dokončení konverze
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```
Tento krok jednoduše vypíše do konzole zprávu potvrzující úspěšné dokončení procesu převodu a označující umístění, kam je převedený soubor PDF uložen.

## Závěr
tomto tutoriálu jsme si ukázali, jak převést soubory PSD do formátu PDF pomocí knihovny GroupDocs.Conversion pro .NET. Dodržením uvedených kroků můžete snadno převést soubory PSD do formátu PDF, což usnadní sdílení a prohlížení vašich dokumentů.
## Často kladené otázky

### Mohu převést více souborů PSD najednou pomocí GroupDocs.Conversion?
Ano, můžete dávkově převést více souborů PSD do PDF nebo jiných formátů pomocí GroupDocs.Conversion.

### Podporuje GroupDocs.Conversion i jiné výstupní formáty kromě PDF?
Ano, GroupDocs.Conversion podporuje širokou škálu výstupních formátů včetně DOCX, XLSX, PPTX, JPEG, PNG a dalších.

### Je GroupDocs.Conversion kompatibilní s různými verzemi .NET?
Ano, GroupDocs.Conversion je kompatibilní s různými verzemi .NET, včetně .NET Core a .NET Framework.

### Mohu si přizpůsobit možnosti převodu pro větší kontrolu nad výstupem?
Ano, GroupDocs.Conversion nabízí rozsáhlé možnosti přizpůsobení, jako je určení velikosti stránky, orientace, kvality a dalších.

### Je k dispozici zkušební verze pro vyzkoušení před zakoupením?
Ano, můžete získat bezplatnou zkušební verzi GroupDocs.Conversion z [webové stránky](https://releases.groupdocs.com/conversion/net/) vyzkoušet jeho funkce před nákupem.