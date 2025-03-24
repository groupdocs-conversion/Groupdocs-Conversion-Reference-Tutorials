---
title: Converteer DOC Word-documenten naar PDF
linktitle: Converteer DOC Word-documenten naar PDF
second_title: GroupDocs.Conversion .NET API
description: Converteer DOC Word-documenten moeiteloos naar PDF met GroupDocs.Conversion voor .NET. Volg onze stapsgewijze handleiding voor een naadloze documentconversie.
weight: 23
url: /nl/net/file-conversion-to-pdf/convert-doc-to-pdf/
---
## Invoering
In het huidige digitale tijdperk is de mogelijkheid om documenten naadloos van het ene formaat naar het andere te converteren essentieel voor zowel bedrijven als particulieren. Of u nu te maken heeft met Word-documenten, PDF's of andere bestandstypen, de juiste hulpmiddelen kunnen het verschil maken. Eén zo'n tool is GroupDocs.Conversion voor .NET, een krachtige bibliotheek die ontwikkelaars de mogelijkheid biedt om documenten gemakkelijk te converteren.
## Vereisten
Voordat u in het conversieproces duikt met GroupDocs.Conversion voor .NET, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:
1.  Download en installeer GroupDocs.Conversion voor .NET: Navigeer naar het[download link](https://releases.groupdocs.com/conversion/net/) en volg de meegeleverde installatie-instructies.
2. Verkrijg een licentie: u hebt een licentie nodig om GroupDocs.Conversion voor .NET in uw toepassingen te gebruiken. Als u net begint, kunt u gebruik maken van een[tijdelijke licentie](https://purchase.groupdocs.com/temporary-license/) voor testdoeleinden of koop een licentie voor productiegebruik.
3. Bekendheid met de .NET-omgeving: Basiskennis van het .NET-framework en de programmeertaal C# wordt aanbevolen om samen met de voorbeelden te volgen.
4. Toegang tot brondocumenten: Zorg ervoor dat u over de brondocumenten beschikt die u wilt converteren. Voor demonstratiedoeleinden converteren we DOC Word-documenten naar PDF-formaat.

## Naamruimten importeren
Voordat we met het conversieproces beginnen, importeren we de benodigde naamruimten in ons .NET-project:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Stap 1: Definieer de uitvoermap en het bestand
Geef eerst de uitvoermap op waar u het geconverteerde PDF-bestand wilt opslaan, samen met de gewenste naam van het uitvoerbestand.
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "doc-converted-to.pdf");
```
## Stap 2: Laad het bron-DOC-bestand
Laad vervolgens het bron-DOC-bestand met behulp van de klasse GroupDocs.Conversion.Converter.
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_DOC))
```
## Stap 3: Conversieopties configureren
Configureer de conversieopties volgens uw vereisten. Voor het converteren van DOC naar PDF gebruiken we PdfConvertOptions.
```csharp
var options = new PdfConvertOptions();
```
## Stap 4: Voer conversie uit
Voer het conversieproces uit door de Convert-methode van het converterobject aan te roepen, waarbij u het uitvoerbestandspad en de conversie-opties doorgeeft.
```csharp
converter.Convert(outputFile, options);
```
## Stap 5: Controleer of de conversie is voltooid
Zodra de conversie is voltooid, geeft u een succesbericht weer samen met de locatie van de uitvoermap.
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```

## Conclusie
GroupDocs.Conversion voor .NET vereenvoudigt het proces van het converteren van documenten tussen verschillende formaten. Door de stappen in deze zelfstudie te volgen, kunt u eenvoudig DOC Word-documenten naadloos naar PDF converteren.
## Veelgestelde vragen
### Is GroupDocs.Conversion voor .NET compatibel met alle versies van .NET?
GroupDocs.Conversion voor .NET is compatibel met .NET Framework 2.0 en latere versies, inclusief .NET Core en .NET 5+.
### Kan ik meerdere documenten tegelijkertijd converteren met GroupDocs.Conversion voor .NET?
Ja, GroupDocs.Conversion voor .NET ondersteunt batchconversie, waardoor u meerdere documenten in één keer kunt converteren.
### Heeft GroupDocs.Conversion voor .NET een internetverbinding nodig?
Nee, GroupDocs.Conversion voor .NET werkt lokaal op uw computer en vereist geen internetverbinding voor conversie.
### Kan ik de conversieopties aanpassen aan specifieke vereisten?
Ja, GroupDocs.Conversion voor .NET biedt uitgebreide mogelijkheden om het conversieproces aan te passen aan uw specifieke behoeften.
### Is er technische ondersteuning beschikbaar voor GroupDocs.Conversion voor .NET?
 Ja, technische ondersteuning voor GroupDocs.Conversion voor .NET is beschikbaar via de[forum](https://forum.groupdocs.com/c/conversion/11) waar u hulp en begeleiding kunt zoeken bij de gemeenschap en experts.