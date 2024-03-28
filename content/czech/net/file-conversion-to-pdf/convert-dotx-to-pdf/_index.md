---
title: Převést DOTX Word šablony do PDF
linktitle: Převést DOTX Word šablony do PDF
second_title: GroupDocs.Conversion .NET API
description: Převeďte bez námahy šablony DOTX Word do PDF pomocí GroupDocs.Conversion for .NET. Zjednodušte si úkoly správy dokumentů.
type: docs
weight: 27
url: /cs/net/file-conversion-to-pdf/convert-dotx-to-pdf/
---
## Úvod
Dokumenty Microsoft Word jsou široce používány pro různé účely, včetně vytváření šablon ve formátu DOTX. Mohou však nastat případy, kdy budete muset tyto šablony DOTX převést do formátu PDF pro snadnější sdílení, tisk nebo archivaci. V tomto tutoriálu vás provedeme procesem převodu šablon DOTX Word do PDF pomocí GroupDocs.Conversion for .NET.
## Předpoklady
Než se pustíme do procesu převodu, ujistěte se, že máte následující předpoklady:
1.  Knihovna GroupDocs.Conversion for .NET: Stáhněte a nainstalujte knihovnu GroupDocs.Conversion for .NET z[odkaz ke stažení](https://releases.groupdocs.com/conversion/net/).
2. Zdrojový soubor DOTX: Budete potřebovat soubor DOTX, který chcete převést do PDF. Ujistěte se, že máte cestu k tomuto souboru připravenou pro proces převodu.

## Import jmenných prostorů
Než budete pokračovat v převodu, ujistěte se, že jste do svého projektu .NET importovali potřebné jmenné prostory:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```

## Krok 1: Nastavte výstupní složku a název souboru
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "dotx-converted-to.pdf");
```
Ujistěte se, že jste určili adresář, kam chcete uložit převedený soubor PDF, a definujte název výstupního souboru.
## Krok 2: Načtěte zdrojový soubor DOTX a převeďte jej
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_DOTX))
{
    var options = new PdfConvertOptions();
    converter.Convert(outputFile, options);
}
```
 Inicializujte novou instanci souboru`Converter` třídy předáním cesty ke zdrojovému souboru DOTX. Poté nakonfigurujte možnosti převodu a určete, že chcete převést do PDF. Nakonec zavolejte na`Convert` způsob provedení převodu.
## Krok 3: Zkontrolujte dokončení konverze
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
Po úspěšném dokončení procesu převodu zobrazte zprávu o dokončení a umístění, kde lze převedený soubor PDF nalézt.

## Závěr
Převod šablon DOTX Word do PDF je s GroupDocs.Conversion for .NET jednoduchý proces. Dodržováním jednoduchých kroků uvedených v tomto návodu můžete efektivně převést soubory DOTX do formátu PDF, což umožní snadnější sdílení, distribuci a archivaci vašich dokumentů.
## FAQ
### Dokáže GroupDocs.Conversion zpracovat velké soubory DOTX?
GroupDocs.Conversion je optimalizován pro práci se soubory různých velikostí, včetně velkých souborů DOTX, což zajišťuje efektivní a spolehlivé procesy konverze.
### Je GroupDocs.Conversion kompatibilní se všemi verzemi .NET?
Ano, GroupDocs.Conversion je kompatibilní s více verzemi .NET a poskytuje flexibilitu vývojářům pracujícím s různými prostředími.
### Podporuje GroupDocs.Conversion jiné výstupní formáty kromě PDF?
Ano, GroupDocs.Conversion podporuje širokou škálu výstupních formátů, včetně DOCX, XLSX, PPTX, JPG, PNG a dalších, které splňují různé potřeby převodu.
### Mohu upravit možnosti převodu podle svých požadavků?
Ano, GroupDocs.Conversion nabízí rozsáhlé možnosti přizpůsobení, které vám umožní doladit proces převodu na základě vašich konkrétních preferencí a požadavků.
### Je k dispozici zkušební verze pro GroupDocs.Conversion?
 Ano, můžete využít bezplatnou zkušební verzi GroupDocs.Conversion z[webová stránka](https://releases.groupdocs.com/), což vám umožní prozkoumat jeho funkce před rozhodnutím o nákupu.