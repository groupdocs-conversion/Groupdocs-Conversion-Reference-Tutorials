---
"description": "Converteer moeiteloos JPG naar PDF met GroupDocs.Conversion voor .NET. Volg deze stapsgewijze handleiding voor naadloze documentconversie."
"linktitle": "JPG naar PDF converteren"
"second_title": "GroupDocs.Conversion .NET API"
"title": "JPG naar PDF converteren"
"url": "/nl/net/document-conversion/convert-jpg-to-pdf/"
"weight": 14
---

# JPG naar PDF converteren

## Invoering

Wilt u moeiteloos JPG-bestanden naar PDF converteren met GroupDocs.Conversion voor .NET? Deze tutorial leidt u stap voor stap door het proces. GroupDocs.Conversion voor .NET is een krachtige API waarmee u verschillende documentformaten, waaronder afbeeldingen, moeiteloos naadloos naar PDF kunt converteren. Laten we beginnen!

## Vereisten

Voordat we beginnen, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:

1. GroupDocs.Conversion voor .NET: Zorg ervoor dat je GroupDocs.Conversion voor .NET hebt geïnstalleerd. Je kunt het downloaden van [hier](https://releases.groupdocs.com/conversion/net/).
2. Ontwikkelomgeving: Zorg dat u een ontwikkelomgeving instelt, bijvoorbeeld Visual Studio, in combinatie met .NET Framework of .NET Core.
3. Voorbeeld-JPG-bestand: maak een voorbeeld-JPG-bestand dat u naar PDF wilt converteren.

## Naamruimten importeren

Laten we eerst de benodigde naamruimten importeren:

```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```

Laten we het conversieproces opsplitsen in eenvoudige stappen:

## Stap 1: Definieer de uitvoermap en bestandsnaam

```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "jpg-converted-to.pdf");
```

Zorg ervoor dat u de map opgeeft waar u het geconverteerde PDF-bestand wilt opslaan en de gewenste naam van het uitvoerbestand.

## Stap 2: Laad het bron-JPG-bestand en converteer naar PDF

```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_JPG))
{
    var options = new PdfConvertOptions();
    converter.Convert(outputFile, options);
}
```

Initialiseer de `Converter` object met het pad naar uw voorbeeld-JPG-bestand. Configureer vervolgens de conversieopties, zoals het specificeren van PDF-conversieopties. Roep ten slotte de `Convert` methode, waarbij het pad van het uitvoerbestand en de conversieopties worden doorgegeven.

## Stap 3: Weergave van het bericht dat de conversie is voltooid

```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```

Nadat de conversie is voltooid, wordt er een bericht weergegeven met de succesvolle conversie en de locatie van het geconverteerde PDF-bestand.

## Conclusie

Het converteren van JPG-bestanden naar PDF met GroupDocs.Conversion voor .NET is eenvoudig en vereist slechts een paar regels code. Door deze tutorial te volgen, kunt u documentconversie naadloos integreren in uw .NET-applicaties.

## Veelgestelde vragen

### V: Kan ik meerdere JPG-bestanden tegelijk naar PDF converteren?

A: Ja, u kunt meerdere JPG-bestanden naar PDF converteren door over elk bestand te itereren en het conversieproces uit te voeren dat in de tutorial wordt beschreven.

### V: Ondersteunt GroupDocs.Conversion andere afbeeldingformaten dan JPG?

A: Ja, GroupDocs.Conversion ondersteunt verschillende afbeeldingsformaten, zoals PNG, TIFF, BMP en GIF.

### V: Kan ik het PDF-uitvoerbestand aanpassen met behulp van conversieopties?

A: Absoluut! GroupDocs.Conversion biedt een breed scala aan conversieopties waarmee u de PDF-uitvoer naar uw wensen kunt aanpassen.

### V: Is er een proefversie beschikbaar voor GroupDocs.Conversion voor .NET?

A: Ja, u kunt een gratis proefversie van GroupDocs.Conversion voor .NET downloaden van [hier](https://releases.groupdocs.com/).

### V: Waar kan ik hulp krijgen als ik problemen ondervind tijdens het conversieproces?

A: Als u problemen ondervindt of vragen hebt over GroupDocs.Conversion voor .NET, kunt u gerust de website bezoeken [GroupDocs.Conversion-forum](https://forum.groupdocs.com/c/conversion/11) voor hulp.