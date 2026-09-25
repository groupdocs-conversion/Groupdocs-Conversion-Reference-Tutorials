---
date: '2026-09-25'
description: Leer hoe je eml naar pdf java kunt converteren met GroupDocs.Conversion,
  waarbij je een tijdzone‑offset toepast om correcte tijdstempels te behouden. Stapsgewijze
  gids voor Java‑ontwikkelaars.
keywords:
- convert eml to pdf java
- email to pdf conversion
- timezone offset java
lastmod: '2026-09-25'
og_description: Leer hoe je eml naar pdf java kunt converteren met GroupDocs.Conversion,
  waarbij je een tijdzone‑offset toepast om correcte tijdstempels te behouden. Gedetailleerde
  Java‑gids voor ontwikkelaars.
og_image_alt: 'Java guide: convert eml to pdf with timezone offset using GroupDocs.Conversion'
og_title: Converteer eml naar pdf java met tijdzone‑offset met behulp van GroupDocs
schemas:
- author: GroupDocs
  dateModified: '2026-09-25'
  description: Learn how to convert eml to pdf java with GroupDocs.Conversion, applying
    a timezone offset to preserve correct timestamps. Step‑by‑step guide for Java
    developers.
  headline: How to convert eml to pdf java with timezone offset
  type: TechArticle
- description: Learn how to convert eml to pdf java with GroupDocs.Conversion, applying
    a timezone offset to preserve correct timestamps. Step‑by‑step guide for Java
    developers.
  name: How to convert eml to pdf java with timezone offset
  steps:
  - name: '**Libraries & dependencies**'
    text: '**Libraries & dependencies**'
  - name: '**Environment**'
    text: '**Environment**'
  - name: '**Knowledge**'
    text: '**Knowledge**'
  type: HowTo
- questions:
  - answer: It’s a powerful library that enables document conversion across dozens
      of formats, including email to PDF, with built‑in timezone handling.
    question: What is GroupDocs.Conversion for Java?
  - answer: Use `EmailLoadOptions.setTimeZoneOffset(milliseconds)` before initializing
      the `Converter`.
    question: How do I set the timezone offset for emails?
  - answer: Yes, the library supports `.eml`, `.msg`, and other common email file
      types.
    question: Can I convert multiple email formats with this setup?
  - answer: Missing dependencies, incorrect file paths, and providing the offset in
      the wrong unit (seconds vs. milliseconds).
    question: What are common pitfalls during conversion?
  - answer: Visit the [official documentation](https://docs.groupdocs.com/conversion/java/)
      for detailed guides and API references.
    question: Where can I find more resources on GroupDocs.Conversion?
  type: FAQPage
tags:
- convert eml
- GroupDocs.Conversion
- Java email conversion
- timezone offset
- PDF generation
title: Hoe eml naar pdf java te converteren met tijdzone‑offset
type: docs
url: /nl/java/email-formats/email-to-pdf-conversion-java-groupdocs/
weight: 1
---

# Hoe eml naar pdf java te converteren met tijdzone‑offset

In deze tutorial ontdek je hoe je **eml naar pdf java** kunt converteren terwijl je de tijdstempel correct aanpast voor elk tijdzoneverschil. Met GroupDocs.Conversion voor Java zie je een volledige end‑to‑end workflow — van Maven‑installatie, via het laden van een e‑mail met een aangepaste offset, tot het streamen van de resulterende PDF‑bestanden. De stappen zijn geschreven voor Java 8+ ontwikkelaars die betrouwbare, archief‑klare PDF’s nodig hebben die de juiste lokale tijd weergeven.

## Snelle antwoorden
- **Welke bibliotheek verwerkt de conversie?** GroupDocs.Conversion for Java.  
- **Welke primaire methode stelt de tijdzone in?** `EmailLoadOptions.setTimeZoneOffset`.  
- **Heb ik een licentie nodig?** Een gratis proefversie werkt voor testen; een volledige licentie is vereist voor productie.  
- **Kan ik veel e‑mails in batch verwerken?** Ja — wikkel de conversielus in een batch‑routine.  
- **Welke Java‑versie is vereist?** JDK 8 of hoger.  

## Wat is convert eml to pdf java?
De uitdrukking “convert eml to pdf java” beschrijft het proces waarbij een e‑mailbestand (meestal `.eml` of `.msg`) wordt omgezet naar een PDF‑document met Java‑code. Deze conversie is essentieel voor archivering, wettelijke naleving en cross‑platform delen, omdat PDF’s de lay-out behouden en overal leesbaar zijn.

## Waarom GroupDocs.Conversion voor Java gebruiken?
GroupDocs.Conversion ondersteunt **70+** invoer‑ en uitvoerformaten, waaronder `.eml`, `.msg`, `.pdf`, `.docx` en afbeeldingsformaten. De ingebouwde `EmailLoadOptions` stelt je in staat een tijdzone‑offset in milliseconden op te geven, waardoor de PDF‑tijdstempels overeenkomen met de beoogde lokale tijd. De bibliotheek verwerkt bestanden in een streaming‑modus, wat het geheugenverbruik tot **80 %** vermindert vergeleken met het volledig in RAM laden van het document.

## Voorwaarden
Zorg ervoor dat je het volgende hebt voordat je begint:

1. **Bibliotheken & afhankelijkheden**  
   - GroupDocs.Conversion voor Java versie **25.2** of hoger.  

2. **Omgeving**  
   - JDK 8+ geïnstalleerd en geconfigureerd op je machine.  
   - Maven als build‑automatiseringstool.  

3. **Kennis**  
   - Basis Java‑programmering, vooral bestands‑I/O.  
   - Vertrouwd met de structuur van Maven’s `pom.xml`.

## GroupDocs.Conversion voor Java instellen

### Installatie‑informatie
Voeg de GroupDocs‑repository en de conversie‑afhankelijkheid toe aan je `pom.xml`:

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/conversion/java/</url>
   </repository>
</repositories>
<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-conversion</artifactId>
      <version>25.2</version>
   </dependency>
</dependencies>
```

### Licentie‑acquisitie
Je kunt beginnen met een gratis proefversie of een tijdelijke licentie aanvragen voor het testen van volledige functionaliteit:

- **Gratis proefversie** – Download de bibliotheek en verken de basisfuncties.  
- **Tijdelijke licentie** – Vraag een tijdelijke licentie aan via de [temporary license page](https://purchase.groupdocs.com/temporary-license/).  
- **Aankoop** – Voor langdurig gebruik kun je een licentie aanschaffen via de [official site](https://purchase.groupdocs.com/buy).

### Basisinitialisatie
Hieronder staat de minimale code die je nodig hebt om een `Converter`‑instantie te maken en een e‑mail met een tijdzone‑offset te laden:

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.load.EmailLoadOptions;

// Initialize GroupDocs.Conversion with necessary load options for email files
EmailLoadOptions loadOptions = new EmailLoadOptions();
loadOptions.setTimeZoneOffset(7200000.0); // Set timezone offset in milliseconds (e.g., 2 hours)
```

## Hoe stel je de tijdzone‑offset in?
`EmailLoadOptions` is een configuratieklasse die bepaalt hoe e‑mailbestanden worden geladen voor conversie. Laad je e‑mail met een aangepaste offset vóór de conversie. De `setTimeZoneOffset`‑methode accepteert de offset in **milliseconden**, dus een verschuiving van +2 uur is gelijk aan `7200000`. Deze aanpassing herschrijft de weergegeven tijdstempel in de gegenereerde PDF. Door de offset op te geven, berekent de bibliotheek de weergegeven verzend‑ en ontvangsttijden opnieuw, zodat de gegenereerde PDF de lokale tijdzone van de ontvanger weergeeft. Dit is vooral nuttig voor multinationale teams die gearchiveerde communicatie beoordelen.

```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
loadOptions.setTimeZoneOffset(7200000.0); // Set to 2 hours ahead (in milliseconds)
```

## Hoe initialiseert u het Converter‑object?
`Converter` is de hoofdklasse die documentconversie uitvoert met de opgegeven laadopties. Maak een `Converter` aan door het bronbestandspad en een lambda te geven die de eerder gedefinieerde `loadOptions` levert. Dit koppelt de tijdzone‑instelling aan het conversieproces. Het leest de bron‑e‑mail, past de `EmailLoadOptions`‑instellingen toe — inclusief de tijdzone‑offset — en bereidt de output‑stream voor PDF‑generatie voor. Het gebruik van een lambda zorgt ervoor dat de opties op het moment van conversie worden geëvalueerd, wat handig is bij het verwerken van meerdere bestanden met verschillende instellingen.

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.convert.PdfConvertOptions;

String sourceFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.eml"; // Path to the email document.
String outputPattern = "YOUR_OUTPUT_DIRECTORY/ConvertEmailWithTimezoneOffset-%d.pdf";

List<OutputStream> streamPool = new ArrayList<>();
Converter converter = new Converter(sourceFilePath, () -> loadOptions);
PdfConvertOptions options = new PdfConvertOptions();
```

## Hoe voer je de conversie uit en stream je PDF‑pagina's?
`PdfConvertOptions` specificeert instellingen voor PDF‑output zoals paginagrootte, compressie en beeldkwaliteit. Roep de `convert`‑methode aan, waarbij je een `PdfConvertOptions`‑instantie en een output‑stream voor elke pagina opgeeft. Het `try‑finally`‑blok garandeert dat alle streams worden gesloten, waardoor resource‑lekken worden voorkomen. Na het configureren van de opties, iterereert de `convert`‑methode over elke pagina van de e‑mail en schrijft de PDF‑gegevens naar afzonderlijke output‑streams. Deze aanpak maakt het mogelijk grote e‑mails efficiënt te verwerken, omdat elke pagina afzonderlijk wordt verwerkt en weggeschreven, waardoor het geheugenverbruik wordt geminimaliseerd.

```java
try {
    converter.convert((SaveDocumentStreamForFileType) t -> {
        try {
            OutputStream outputStream = Files.newOutputStream(Paths.get(String.format(outputPattern, streamPool.size())));
            streamPool.add(outputStream);
            return outputStream;
        } catch (IOException e) {
            throw new RuntimeException(e);
        }
    }, options);
} finally {
    for (OutputStream outputStream : streamPool) {
        if (outputStream != null) {
            outputStream.close();
        }
    }
}
```

## Praktische toepassingen
- **E‑mails archiveren** – Bewaar PDF’s met nauwkeurige tijdstempels voor juridische of auditdoeleinden.  
- **Cross‑timezone samenwerking** – Teams wereldwijd zien dezelfde lokale tijd in geconverteerde documenten.  
- **E‑mailrapportage** – Genereer PDF‑rapporten die de oorspronkelijke verzend‑/ontvangsttijden behouden voor naleving.

Je kunt deze workflow integreren in CRM‑systemen, document‑beheersplatformen of geautomatiseerde batch‑taken om je document‑pipeline te stroomlijnen.

## Prestatie‑overwegingen
- **Resource‑beheer** – Sluit streams direct (zoals getoond) om geheugen vrij te maken.  
- **Batch‑verwerking** – Loop over een verzameling `.eml`‑bestanden en hergebruik een enkele `Converter`‑instantie wanneer mogelijk.  
- **JVM‑afstemming** – Pas de heap‑grootte (`-Xmx`) aan voor grote batches om `OutOfMemoryError` te voorkomen.  

## Veelvoorkomende problemen en oplossingen

| Symptoom | Waarschijnlijke oorzaak | Oplossing |
|----------|--------------------------|-----------|
| `NullPointerException` at `loadOptions` | Laadopties niet correct doorgegeven | Zorg ervoor dat de lambda `() -> loadOptions` wordt gebruikt bij het aanmaken van `Converter`. |
| PDF‑output is leeg | Pad naar invoerbestand onjuist of bestand ontbreekt | Controleer of `sourceFilePath` naar een bestaand `.eml`‑bestand wijst. |
| Tijdzone niet weergegeven | Verkeerde offsetwaarde (bijv. seconden in plaats van milliseconden) | Geef de offset op in **milliseconden** (bijv. `7200000` voor +2 h). |

## Veelgestelde vragen
**Q: Wat is GroupDocs.Conversion voor Java?**  
A: Het is een krachtige bibliotheek die documentconversie mogelijk maakt over tientallen formaten, inclusief e‑mail naar PDF, met ingebouwde tijdzone‑afhandeling.

**Q: Hoe stel ik de tijdzone‑offset in voor e‑mails?**  
A: Gebruik `EmailLoadOptions.setTimeZoneOffset(milliseconds)` vóór het initialiseren van de `Converter`.

**Q: Kan ik meerdere e‑mailformaten converteren met deze setup?**  
A: Ja, de bibliotheek ondersteunt `.eml`, `.msg` en andere gangbare e‑mailbestandsformaten.

**Q: Wat zijn veelvoorkomende valkuilen tijdens conversie?**  
A: Ontbrekende afhankelijkheden, onjuiste bestandspaden, en het opgeven van de offset in de verkeerde eenheid (seconden vs. milliseconden).

**Q: Waar kan ik meer bronnen vinden over GroupDocs.Conversion?**  
A: Bezoek de [official documentation](https://docs.groupdocs.com/conversion/java/) voor gedetailleerde handleidingen en API‑referenties.

## Aanvullende bronnen
- **Documentatie**: Verken meer op [GroupDocs Documentation](https://docs.groupdocs.com/conversion/java/)  
- **API‑referentie**: Gedetailleerde API‑referentie beschikbaar op [API reference](https://reference.groupdocs.com/conversion/java/)  
- **GroupDocs.Conversion downloaden**: Begin met de bibliotheek via de [GroupDocs.Conversion download page](https://releases.groupdocs.com/conversion/java/)  
- **Aankoop**: Voor langdurig gebruik kun je een licentie aanschaffen op de [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy)  
- **Gratis proefversie & licentie**: Probeer het gratis of vraag een tijdelijke licentie aan via [GroupDocs Free Trial](https://releases.groupdocs.com/conversion/java/) en [Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Ondersteuning**: Voor hulp kun je het [GroupDocs Forum](https://forum.groupdocs.com/c/conversion/10) bezoeken

Omarm de kracht van GroupDocs.Conversion voor je Java‑applicaties en geniet vandaag nog van nauwkeurige, tijdzone‑bewuste PDF‑conversies!

---

**Laatst bijgewerkt:** 2026-09-25  
**Getest met:** GroupDocs.Conversion 25.2  
**Auteur:** GroupDocs

## Gerelateerde tutorials
- [msg to pdf java – Email Formats Conversion with GroupDocs](/conversion/java/email-formats/)
- [eml to pdf java – Convert Email to PDF with GroupDocs](/conversion/java/pdf-conversion/convert-emails-to-pdfs-groupdocs-java/)
- [Convert Multiple File Types with GroupDocs.Conversion Java – Master Guide](/conversion/java/document-operations/groupdocs-conversion-java-master-document-conversion/)