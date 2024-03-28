---
title: Converteer SVG naar PDF
linktitle: Converteer SVG naar PDF
second_title: GroupDocs.Conversion .NET API
description: Leer hoe u moeiteloos SVG naar PDF kunt converteren met GroupDocs.Conversion voor .NET. Stroomlijn uw documentbeheerproces.
type: docs
weight: 15
url: /nl/net/file-format-conversion-tutorials/convert-svg-to-pdf/
---
## Invoering
In de programmeerwereld is het converteren van bestanden van het ene formaat naar het andere een veel voorkomende taak. Of u nu te maken heeft met afbeeldingen, documenten of andere media, het is van cruciaal belang dat u naadloos tussen formaten kunt converteren. In deze zelfstudie gaan we dieper in op het converteren van SVG-bestanden (Scalable Vector Graphics) naar PDF (Portable Document Format) met behulp van GroupDocs.Conversion voor .NET.
## Vereisten
Voordat u in het conversieproces duikt, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:
### 1. Installeer GroupDocs.Conversion voor .NET
Zorg ervoor dat GroupDocs.Conversion voor .NET in uw ontwikkelomgeving is geïnstalleerd. Als u dat nog niet heeft gedaan, kunt u deze downloaden via de[website](https://releases.groupdocs.com/conversion/net/).
### 2. Verkrijg een voorbeeld-SVG-bestand
U hebt een voorbeeld-SVG-bestand nodig om naar PDF te converteren. Als u er geen heeft, kunt u eenvoudig online SVG-bestanden vinden of er een maken met behulp van verschillende grafische ontwerptools.
### 3. Basiskennis van C#
Maak uzelf vertrouwd met de basisbeginselen van de programmeertaal C#, aangezien we deze zullen gebruiken om de conversiecode te schrijven.

## Naamruimten importeren
Laten we eerst de benodigde naamruimten importeren:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Stap 1: Definieer de uitvoermap en het bestand
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "svg-converted-to.pdf");
```
 Zorg ervoor dat u deze vervangt`"Your Document Directory"` met het pad naar de gewenste uitvoermap.
## Stap 2: Laad het bron-SVG-bestand
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_SVG))
{
    // De conversiecode komt hier
}
```
 Vervangen`Constants.SAMPLE_SVG` met het pad naar uw SVG-bestand.
## Stap 3: Conversieopties instellen
```csharp
var options = new PdfConvertOptions();
```
Hier stellen we conversieopties specifiek voor PDF-uitvoer in. U kunt deze opties aanpassen op basis van uw vereisten.
## Stap 4: Voer de conversie uit
```csharp
converter.Convert(outputFile, options);
```
Deze regel voert het conversieproces uit, neemt het bron-SVG-bestand en converteert het naar PDF met de opgegeven opties.
## Stap 5: Controleer of de conversie is voltooid
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
Deze regel geeft een bericht weer waarin de succesvolle voltooiing van het conversieproces wordt bevestigd, samen met de map waar het geconverteerde PDF-bestand zich bevindt.

## Conclusie
In deze zelfstudie hebben we geleerd hoe u SVG-bestanden naar PDF kunt converteren met GroupDocs.Conversion voor .NET. Door de stapsgewijze handleiding te volgen en ervoor te zorgen dat u aan de vereisten voldoet, kunt u de conversiemogelijkheden van bestandsindelingen naadloos in uw .NET-toepassingen integreren.
## Veelgestelde vragen
### Is GroupDocs.Conversion voor .NET compatibel met alle .NET-frameworks?
Ja, GroupDocs.Conversion voor .NET ondersteunt meerdere .NET-frameworks, waaronder .NET Core en .NET Framework.
### Kan ik de conversieopties voor specifieke uitvoerformaten aanpassen?
Absoluut! GroupDocs.Conversion voor .NET biedt uitgebreide aanpassingsopties voor elk ondersteund uitvoerformaat.
### Ondersteunt GroupDocs.Conversion voor .NET batchconversie?
Ja, u kunt meerdere bestanden tegelijkertijd converteren met GroupDocs.Conversion voor .NET.
### Is er een proefversie beschikbaar voor testdoeleinden?
 Ja, u heeft toegang tot een gratis proefversie van[hier](https://releases.groupdocs.com/).
### Waar kan ik technische ondersteuning krijgen voor GroupDocs.Conversion voor .NET?
Technische ondersteuning en assistentie vindt u op het GroupDocs-forum[hier](https://forum.groupdocs.com/c/conversion/11).