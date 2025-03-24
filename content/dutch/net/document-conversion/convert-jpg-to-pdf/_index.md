---
title: Converteer JPG naar PDF
linktitle: Converteer JPG naar PDF
second_title: GroupDocs.Conversion .NET API
description: Converteer JPG moeiteloos naar PDF met GroupDocs.Conversion voor .NET. Volg deze stapsgewijze zelfstudie voor een naadloze documentconversie.
weight: 14
url: /nl/net/document-conversion/convert-jpg-to-pdf/
---
## Invoering

Wilt u JPG-bestanden moeiteloos naar PDF converteren met GroupDocs.Conversion voor .NET? Deze tutorial begeleidt u stap voor stap door het proces. GroupDocs.Conversion voor .NET is een krachtige API waarmee u eenvoudig verschillende documentformaten, inclusief afbeeldingen, naadloos naar PDF kunt converteren. Laten we erin duiken!

## Vereisten

Voordat we beginnen, zorg ervoor dat u aan de volgende vereisten voldoet:

1.  GroupDocs.Conversion voor .NET: Zorg ervoor dat u GroupDocs.Conversion voor .NET hebt geïnstalleerd. Je kunt het downloaden van[hier](https://releases.groupdocs.com/conversion/net/).
2. Ontwikkelomgeving: zorg dat u een ontwikkelomgeving hebt opgezet, zoals Visual Studio, samen met .NET Framework of .NET Core.
3. Voorbeeld JPG-bestand: bereid een voorbeeld JPG-bestand voor dat u naar PDF wilt converteren.

## Naamruimten importeren

Laten we eerst de benodigde naamruimten importeren:

```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```

Laten we nu het conversieproces in eenvoudige stappen opsplitsen:

## Stap 1: Definieer de uitvoermap en bestandsnaam

```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "jpg-converted-to.pdf");
```

Zorg ervoor dat u de map opgeeft waar u het geconverteerde PDF-bestand wilt opslaan, en de gewenste naam van het uitvoerbestand.

## Stap 2: Laad het bron-JPG-bestand en converteer naar PDF

```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_JPG))
{
    var options = new PdfConvertOptions();
    converter.Convert(outputFile, options);
}
```

 Initialiseer de`Converter` object met het pad naar uw voorbeeld-JPG-bestand. Configureer vervolgens de conversieopties, zoals het opgeven van PDF-conversieopties. Bel ten slotte de`Convert` methode, waarbij het pad van het uitvoerbestand en de conversie-opties worden doorgegeven.

## Stap 3: Geef het bericht over de voltooiing van de conversie weer

```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```

Nadat de conversie is voltooid, wordt een bericht weergegeven waarin de succesvolle conversie en de locatie van het geconverteerde PDF-bestand worden aangegeven.

## Conclusie

Het converteren van JPG-bestanden naar PDF met GroupDocs.Conversion voor .NET is eenvoudig met slechts een paar regels code. Door deze tutorial te volgen, kunt u de mogelijkheden voor documentconversie naadloos integreren in uw .NET-toepassingen.

## Veelgestelde vragen

### Vraag: Kan ik meerdere JPG-bestanden tegelijkertijd naar PDF converteren?

A: Ja, u kunt meerdere JPG-bestanden naar PDF converteren door elk bestand te herhalen en het conversieproces uit te voeren dat in de tutorial wordt beschreven.

### Vraag: Ondersteunt GroupDocs.Conversion andere afbeeldingsformaten dan JPG?

A: Ja, GroupDocs.Conversion ondersteunt verschillende afbeeldingsformaten, zoals onder andere PNG, TIFF, BMP en GIF.

### Vraag: Kan ik het uitgevoerde PDF-bestand aanpassen met behulp van conversieopties?

EEN: Absoluut! GroupDocs.Conversion biedt een breed scala aan conversieopties waarmee u de uitvoer-PDF kunt aanpassen aan uw vereisten.

### Vraag: Is er een proefversie beschikbaar voor GroupDocs.Conversion voor .NET?

A: Ja, u kunt toegang krijgen tot een gratis proefversie van GroupDocs.Conversion voor .NET vanaf[hier](https://releases.groupdocs.com/).

### Vraag: Waar kan ik hulp zoeken als ik problemen tegenkom tijdens het conversieproces?

 A: Als u problemen ondervindt of vragen heeft over GroupDocs.Conversion voor .NET, bezoek dan gerust de[GroupDocs.Conversion-forum](https://forum.groupdocs.com/c/conversion/11) Voor assistentie.