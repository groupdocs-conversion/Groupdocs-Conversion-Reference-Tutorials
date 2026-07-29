---
date: '2026-07-29'
description: Ontdek hoe u formaten kunt opsommen en alle mogelijke conversies kunt
  ophalen met GroupDocs.Conversion voor Java, ideaal voor cloudopslag‑bestandsconversieworkflows.
keywords:
- how to list formats
- cloud storage file conversion
- GroupDocs.Conversion Java
lastmod: '2026-07-29'
og_description: Leer hoe u formaten kunt opsommen en alle mogelijke conversies kunt
  ophalen met GroupDocs.Conversion voor Java. Ideaal voor cloudopslag‑bestandsconversiepijplijnen.
og_image_alt: 'Guide: List formats and get conversion matrix with GroupDocs.Conversion
  Java'
og_title: Hoe formaten opsommen met GroupDocs.Conversion voor Java
schemas:
- author: GroupDocs
  dateModified: '2026-07-29'
  description: Discover how to list formats and retrieve all possible conversions
    using GroupDocs.Conversion for Java, ideal for cloud storage file conversion workflows.
  headline: How to List Formats with GroupDocs.Conversion for Java
  type: TechArticle
- description: Discover how to list formats and retrieve all possible conversions
    using GroupDocs.Conversion for Java, ideal for cloud storage file conversion workflows.
  name: How to List Formats with GroupDocs.Conversion for Java
  steps:
  - name: '**Dynamic Format Detection:** When a file lands in cloud storage, you can
      instantly query whether the desired target format is supported.'
    text: '**Dynamic Format Detection:** When a file lands in cloud storage, you can
      instantly query whether the desired target format is supported.'
  - name: '**Batch Migration:** Move large document libraries to a unified format
      (e.g., PDF/A) by iterating over supported source types.'
    text: '**Batch Migration:** Move large document libraries to a unified format
      (e.g., PDF/A) by iterating over supported source types.'
  - name: '**User‑Driven Export:** Offer end‑users a dropdown of only the formats
      their current document can be exported to, reducing errors and improving UX.'
    text: '**User‑Driven Export:** Offer end‑users a dropdown of only the formats
      their current document can be exported to, reducing errors and improving UX.'
  type: HowTo
- questions:
  - answer: It is a server‑side library that supports 200+ input and 200+ output formats,
      enabling fast, license‑free document conversion without external software.
    question: What is GroupDocs.Conversion for Java?
  - answer: Set up your Maven project, add the dependency shown earlier, load a license
      file, and instantiate the `Converter` class as demonstrated in the initialization
      section.
    question: How do I start with GroupDocs.Conversion?
  - answer: Yes—through the API’s extensibility points you can register custom converters
      or plug‑in third‑party handlers for proprietary formats.
    question: Can I convert custom file types using GroupDocs.Conversion?
  - answer: Forgetting to close the `Converter`, using an old JAR version, or overlooking
      memory usage for very large PDFs. Follow the resource‑management tips above.
    question: What are common pitfalls when implementing conversions?
  - answer: Visit the official [documentation](https://docs.groupdocs.com/conversion/java/)
      or ask questions in the GroupDocs community forum.
    question: Where can I get more help?
  type: FAQPage
tags:
- convert formats
- GroupDocs.Conversion
- Java document conversion
- cloud storage conversion
title: Hoe formaten opsommen met GroupDocs.Conversion voor Java
type: docs
url: /nl/java/conversion-options/groupdocs-conversion-java-retrieve-possible-conversions/
weight: 1
---

# Hoe formaten te vermelden en alle mogelijke conversies op te halen met GroupDocs.Conversion voor Java

In veel document‑verwerkingsprojecten is de eerste stap te weten **hoe formaten te vermelden** die de conversie‑engine ondersteunt. Deze tutorial laat je stap voor stap zien hoe je GroupDocs.Conversion voor Java kunt raadplegen, elk bron‑naar‑doel‑paar kunt ophalen, en die kennis kunt toepassen in cloud‑opslag bestandsconversiepijplijnen. Aan het einde heb je een herbruikbare methode die de volledige conversiematrix retourneert, plus praktische tips voor prestaties en foutafhandeling.

## Snelle antwoorden
- **Wat betekent “list formats”?** Het retourneert elk bron‑naar‑doel‑conversie‑paar dat de bibliotheek kan verwerken.  
- **Heb ik een licentie nodig?** Een gratis proefversie werkt voor testen; een betaalde licentie is vereist voor productie.  
- **Kan dit helpen bij cloud‑opslag bestandsconversie?** Ja—kennis van ondersteunde formaten stelt je in staat om conversies te automatiseren in cloud‑opslag pijplijnen.  
- **Welke Java‑versie is vereist?** JDK 8 of hoger.  
- **Is de functie thread‑safe?** De `Converter`‑instantie kan worden hergebruikt over threads, maar maak bronnen vrij na gebruik.

## Wat is “hoe formaten te vermelden” in GroupDocs.Conversion?
De **list formats**‑operatie retourneert een collectie die elk bronformaat beschrijft samen met de doelformaten waarin het kan worden omgezet. Deze matrix wordt gegenereerd uit de interne conversieregels van de bibliotheek en is essentieel voor het bouwen van dynamische workflows die zich aanpassen aan de daadwerkelijke mogelijkheden van GroupDocs.Conversion tijdens runtime.

## Waarom GroupDocs.Conversion voor Java gebruiken?
GroupDocs.Conversion voor Java ondersteunt **200+ invoerformaten** en **200+ uitvoerformaten**, die alles dekken van DOCX en PPTX tot PDF/A en beeldformaten. Het draait volledig op de server, dus Microsoft Office of Adobe‑producten zijn niet vereist. De API is thread‑safe, kan documenten van honderden pagina's verwerken zonder het volledige bestand in het geheugen te laden, en integreert naadloos met cloud‑opslagdiensten zoals AWS S3, Azure Blob en Google Cloud Storage.

## Voorvereisten
- **Java Development Kit (JDK):** Versie 8 of nieuwer.  
- **Maven:** Correct geconfigureerd in je IDE (IntelliJ IDEA, Eclipse, NetBeans, enz.).  
- **GroupDocs.Conversion voor Java:** Toegevoegd als Maven‑dependency (zie hieronder).  

## GroupDocs.Conversion voor Java instellen

Voeg de GroupDocs-repository en dependency toe aan je `pom.xml`:

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
Begin met een gratis proefversie om de API te verkennen. Voor productie‑workloads moet je een licentie aanschaffen of een tijdelijke evaluatielicentie aanvragen.

### Basisinitialisatie en configuratie

```java
import com.groupdocs.conversion.Converter;

public class ConversionSetup {
    public static void main(String[] args) {
        // Initialize the Converter object
        Converter converter = new Converter();
        
        System.out.println("GroupDocs.Conversion for Java has been initialized successfully.");
    }
}
```

## Hoe formaten te vermelden met GroupDocs.Conversion voor Java
`Converter` is de kernklasse die conversies uitvoert en formatinformatie levert. `getAllPossibleConversions()` retourneert een lijst van alle ondersteunde bron‑naar‑doel‑conversie‑paren. `ConversionInfo` vertegenwoordigt een enkele conversie‑mapping tussen een bron‑ en een doelformaat.

Laad de `Converter`‑engine, roep `getAllPossibleConversions()` aan, en je ontvangt een lijst van `ConversionInfo`‑objecten die elk toegestaan bron‑naar‑doel‑paar beschrijven. Deze enkele oproep is alles wat je nodig hebt om een dropdown met exportopties te bouwen, inkomende bestanden te valideren, of batch‑migratiescripts te ontwerpen.

### Initialiseren en conversies ophalen

De `Converter`‑klasse is de kernengine die conversiemogelijkheden biedt en de `getAllPossibleConversions()`‑methode blootlegt.

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.contracts.PossibleConversions;

public class GetAllPossibleConversionsFeature {
    public static void run() {
        // Initialize the Converter object
        Converter converter = new Converter();
```

### Over mogelijke conversies itereren

```java
// Retrieve all possible conversions supported by the library
for (PossibleConversions conversions : converter.getAllPossibleConversions()) {
    // Print source format description
    System.out.print(String.format("Source format: %s \n", conversions.getSource().getDescription()));
```

### Conversietypen bepalen

```java
// Iterate through each target conversion available for the source format
for (TargetConversion conversion : conversions.getAll()) {
    // Determine if it's a primary or secondary conversion and print details
    System.out.print(String.format("\t...can be converted to %s format as %s conversion.\n",
            conversion.getFormat(),
            conversion.isPrimary() ? "primary" : "secondary"));
}
```

### Volledige functie

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.contracts.PossibleConversions;
import com.groupdocs.conversion.contracts.TargetConversion;

public class GetAllPossibleConversionsFeature {
    public static void run() {
        // Initialize the Converter object
        Converter converter = new Converter();

        // Retrieve all possible conversions supported by the library
        for (PossibleConversions conversions : converter.getAllPossibleConversions()) {
            // Print source format description
            System.out.print(String.format("Source format: %s \n", conversions.getSource().getDescription()));

            // Iterate through each target conversion available for the source format
            for (TargetConversion conversion : conversions.getAll()) {
                // Determine if it's a primary or secondary conversion and print details
                System.out.print(String.format("\t...can be converted to %s format as %s conversion.\n",
                        conversion.getFormat(),
                        conversion.isPrimary() ? "primary" : "secondary"));
            }
        }
    }
}
```

## Use‑cases voor cloud‑opslag bestandsconversie
Het kennen van de volledige conversiematrix is vooral waardevol bij het bouwen van **cloud‑opslag bestandsconversie**‑services:

1. **Dynamische formaatdetectie:** Wanneer een bestand in cloud‑opslag terechtkomt, kun je onmiddellijk controleren of het gewenste doelformaat wordt ondersteund.  
2. **Batch‑migratie:** Verplaats grote documentbibliotheken naar een uniform formaat (bijv. PDF/A) door te itereren over ondersteunde brontypen.  
3. **Gebruikersgestuurde export:** Bied eindgebruikers een dropdown met alleen de formaten waarnaar hun huidige document kan worden geëxporteerd, waardoor fouten worden verminderd en de UX verbetert.

## Prestatie‑overwegingen
- **Resource‑beheer:** Maak de `Converter`‑instantie vrij of gebruik try‑with‑resources als je veel kort‑levende converters maakt.  
- **Batchverwerking:** Groepeer meerdere bestanden in één taak om overhead te verminderen.  
- **Caching:** Cache het resultaat van `getAllPossibleConversions()` als je het vaak opvraagt; de conversiematrix verandert zelden tijdens runtime.  

## Veelvoorkomende problemen en oplossingen

| Symptom | Likely Cause | Fix |
|---------|--------------|-----|
| Geen uitvoer verschijnt | `Converter` niet correct geïnitialiseerd | Zorg ervoor dat de bibliotheek‑JAR op het classpath staat en de licentie is geladen. |
| `TargetConversion`‑lijst is leeg | Gebruik van een verouderde bibliotheekversie | Upgrade naar de nieuwste GroupDocs.Conversion‑release. |
| Geheugenspieken bij grote documenten | Converter‑resources niet vrijgegeven | Roep `converter.close()` aan of gebruik try‑with‑resources. |

## Veelgestelde vragen

**Q: Wat is GroupDocs.Conversion voor Java?**  
A: Het is een server‑side bibliotheek die 200+ invoer‑ en 200+ uitvoerformaten ondersteunt, waardoor snelle, licentievrije documentconversie mogelijk is zonder externe software.

**Q: Hoe begin ik met GroupDocs.Conversion?**  
A: Stel je Maven‑project in, voeg de eerder getoonde dependency toe, laad een licentiebestand, en instantieer de `Converter`‑klasse zoals getoond in de initialisatie‑sectie.

**Q: Kan ik aangepaste bestandstypen converteren met GroupDocs.Conversion?**  
A: Ja—via de uitbreidingspunten van de API kun je aangepaste converters registreren of plug‑in van derden gebruiken voor propriëtaire formaten.

**Q: Wat zijn veelvoorkomende valkuilen bij het implementeren van conversies?**  
A: Het vergeten te sluiten van de `Converter`, het gebruiken van een oude JAR‑versie, of het over het hoofd zien van geheugengebruik bij zeer grote PDF‑bestanden. Volg de bovenstaande tips voor resource‑beheer.

**Q: Waar kan ik meer hulp krijgen?**  
A: Bezoek de officiële [documentatie](https://docs.groupdocs.com/conversion/java/) of stel vragen in het GroupDocs‑communityforum.

---

**Laatst bijgewerkt:** 2026-07-29  
**Getest met:** GroupDocs.Conversion 25.2 for Java  
**Auteur:** GroupDocs

## Gerelateerde tutorials

- [Word naar PDF en andere bestandsformaten converteren met GroupDocs.Conversion voor Java](/conversion/java/)
- [Word naar PDF Java – Wijzigingen verbergen & conversie‑opties](/conversion/java/conversion-options/)
- [Hoe conversievoortgang bij te houden in Java met GroupDocs - Een volledige gids](/conversion/java/conversion-events-logging/java-groupdocs-conversion-progress-listener/)