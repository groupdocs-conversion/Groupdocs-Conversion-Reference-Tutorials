---
title: Převést JPG do PDF
linktitle: Převést JPG do PDF
second_title: GroupDocs.Conversion .NET API
description: Převeďte JPG do PDF bez námahy pomocí GroupDocs.Conversion for .NET. Postupujte podle tohoto podrobného návodu pro bezproblémový převod dokumentů.
type: docs
weight: 14
url: /cs/net/document-conversion/convert-jpg-to-pdf/
---
## Úvod

Hledáte převést soubory JPG do PDF bez námahy pomocí GroupDocs.Conversion for .NET? Tento tutoriál vás provede procesem krok za krokem. GroupDocs.Conversion for .NET je výkonné rozhraní API, které vám umožňuje snadno převádět různé formáty dokumentů, včetně obrázků, do PDF. Pojďme se ponořit!

## Předpoklady

Než začneme, ujistěte se, že máte následující předpoklady:

1.  GroupDocs.Conversion for .NET: Ujistěte se, že jste nainstalovali GroupDocs.Conversion for .NET. Můžete si jej stáhnout z[tady](https://releases.groupdocs.com/conversion/net/).
2. Vývojové prostředí: Nechte si nastavit vývojové prostředí, jako je Visual Studio, spolu s .NET Framework nebo .NET Core.
3. Ukázkový soubor JPG: Připravte si ukázkový soubor JPG, který chcete převést do PDF.

## Import jmenných prostorů

Nejprve importujme potřebné jmenné prostory:

```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```

Nyní si rozdělme proces převodu do jednoduchých kroků:

## Krok 1: Definujte výstupní adresář a název souboru

```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "jpg-converted-to.pdf");
```

Ujistěte se, že jste určili adresář, kam chcete uložit převedený soubor PDF, a požadovaný název výstupního souboru.

## Krok 2: Načtěte zdrojový soubor JPG a převeďte jej do PDF

```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_JPG))
{
    var options = new PdfConvertOptions();
    converter.Convert(outputFile, options);
}
```

 Inicializujte`Converter` objekt s cestou k vašemu ukázkovému souboru JPG. Poté nakonfigurujte možnosti převodu, například určete možnosti převodu PDF. Nakonec zavolejte na`Convert` předání cesty k výstupnímu souboru a možností převodu.

## Krok 3: Zobrazte zprávu o dokončení konverze

```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```

Po dokončení převodu zobrazte zprávu o úspěšném převodu a umístění převedeného souboru PDF.

## Závěr

Převod souborů JPG do PDF pomocí GroupDocs.Conversion for .NET je jednoduchý s několika řádky kódu. Podle tohoto kurzu můžete do svých aplikací .NET bez problémů integrovat možnosti převodu dokumentů.

## FAQ

### Otázka: Mohu převést více souborů JPG do PDF současně?

Odpověď: Ano, můžete převést více souborů JPG do PDF iterací každého souboru a provedením procesu převodu popsaného v tutoriálu.

### Otázka: Podporuje GroupDocs.Conversion jiné formáty obrázků kromě JPG?

Odpověď: Ano, GroupDocs.Conversion podporuje různé formáty obrázků, jako jsou mimo jiné PNG, TIFF, BMP a GIF.

### Otázka: Mohu přizpůsobit výstupní soubor PDF pomocí možností převodu?

A: Rozhodně! GroupDocs.Conversion poskytuje širokou škálu možností převodu, které vám umožní přizpůsobit výstupní PDF podle vašich požadavků.

### Otázka: Je k dispozici zkušební verze pro GroupDocs.Conversion for .NET?

Odpověď: Ano, máte přístup k bezplatné zkušební verzi GroupDocs.Conversion for .NET z[tady](https://releases.groupdocs.com/).

### Otázka: Kde mohu vyhledat pomoc, pokud během procesu převodu narazím na nějaké problémy?

 A: Pokud narazíte na nějaké problémy nebo máte dotazy týkající se GroupDocs.Conversion for .NET, neváhejte navštívit[GroupDocs.Conversion fórum](https://forum.groupdocs.com/c/conversion/11) pro pomoc.