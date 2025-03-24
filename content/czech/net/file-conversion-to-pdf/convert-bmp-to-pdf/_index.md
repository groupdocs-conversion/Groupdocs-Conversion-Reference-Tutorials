---
title: Převést obrázky BMP do PDF
linktitle: Převést obrázky BMP do PDF
second_title: GroupDocs.Conversion .NET API
description: Bezproblémově převádějte obrázky BMP do PDF pomocí GroupDocs.Conversion for .NET. Přizpůsobitelné možnosti pro optimální výstup.
weight: 11
url: /cs/net/file-conversion-to-pdf/convert-bmp-to-pdf/
---
## Úvod
GroupDocs.Conversion for .NET poskytuje výkonné řešení pro bezproblémový převod obrázků BMP do formátu PDF. Tento tutoriál vás provede procesem krok za krokem.
### Předpoklady
Než začneme, ujistěte se, že máte následující:
1.  GroupDocs.Conversion for .NET: Nainstalujte knihovnu jejím stažením z[odkaz ke stažení](https://releases.groupdocs.com/conversion/net/).
2. Zdrojový soubor BMP: Připravte soubor obrázku BMP, který chcete převést.

## Import jmenných prostorů
Nejprve importujte potřebné jmenné prostory pro přístup k požadovaným třídám a metodám:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Krok 1: Nastavte výstupní složku a název souboru
Definujte cestu výstupní složky a název převedeného souboru PDF:
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "bmp-converted-to.pdf");
```
## Krok 2: Načtěte zdrojový soubor BMP
 Načtěte zdrojový soubor BMP pomocí`Converter` třída:
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_BMP))
{
    // Konverzní logika je zde
}
```
## Krok 3: Nakonfigurujte možnosti převodu
 Zadejte možnosti převodu. V tomto případě použijeme`PdfConvertOptions` pro převod do formátu PDF:
```csharp
var options = new PdfConvertOptions();
```
## Krok 4: Převeďte BMP do PDF
Proveďte převod a uložte převedený soubor PDF:
```csharp
converter.Convert(outputFile, options);
```
## Krok 5: Ověřte převod
Zkontrolujte, zda je převod úspěšný a zobrazte cestu výstupní složky:
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
Gratulujeme! Úspěšně jste převedli obrázek BMP do PDF pomocí GroupDocs.Conversion for .NET.

## Závěr
Na závěr, GroupDocs.Conversion for .NET nabízí jednoduché, ale výkonné řešení pro převod obrázků BMP do formátu PDF. Podle kroků uvedených v tomto kurzu můžete tuto funkci bez problémů integrovat do svých aplikací .NET.
## FAQ
### Je GroupDocs.Conversion for .NET kompatibilní se všemi formáty obrázků BMP?
GroupDocs.Conversion for .NET podporuje širokou škálu obrazových formátů BMP, což zajišťuje kompatibilitu s většinou souborů BMP.
### Mohu přizpůsobit možnosti převodu pro větší kontrolu nad výstupním PDF?
Ano, můžete přizpůsobit různé možnosti převodu, jako je DPI, velikost stránky, orientace a další, abyste přizpůsobili výstupní PDF podle svých požadavků.
### Vyžaduje GroupDocs.Conversion for .NET nějaké další závislosti?
Ne, GroupDocs.Conversion for .NET je samostatná knihovna, která nevyžaduje žádné další závislosti pro základní úlohy převodu.
### Je k dispozici zkušební verze pro testování před zakoupením?
 Ano, můžete si stáhnout bezplatnou zkušební verzi z[stránka vydání](https://releases.groupdocs.com/) před nákupem zhodnotit funkce knihovny.
### Kde mohu získat podporu nebo pomoc, pokud narazím na nějaké problémy?
 Můžete navštívit[GroupDocs.Conversion fórum](https://forum.groupdocs.com/c/conversion/11) pro pomoc od komunity nebo se obraťte přímo na podporu pro personalizovanou pomoc.