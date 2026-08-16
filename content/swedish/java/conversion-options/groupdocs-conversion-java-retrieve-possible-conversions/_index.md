---
date: '2026-07-29'
description: Upptäck hur du listar format och hämtar alla möjliga konverteringar med
  GroupDocs.Conversion for Java, idealiskt för cloud storage file conversion workflows.
keywords:
- how to list formats
- cloud storage file conversion
- GroupDocs.Conversion Java
lastmod: '2026-07-29'
og_description: Lär dig hur du listar format och hämtar alla möjliga konverteringar
  med GroupDocs.Conversion for Java. Ideal för cloud storage file conversion pipelines.
og_image_alt: 'Guide: List formats and get conversion matrix with GroupDocs.Conversion
  Java'
og_title: Hur man listar format med GroupDocs.Conversion for Java
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
title: Hur man listar format med GroupDocs.Conversion for Java
type: docs
url: /sv/java/conversion-options/groupdocs-conversion-java-retrieve-possible-conversions/
weight: 1
---

# Hur man listar format och hämtar alla möjliga konverteringar med GroupDocs.Conversion för Java

I många dokument‑bearbetningsprojekt är första steget att veta **hur man listar format** som konverteringsmotorn stödjer. Denna handledning visar dig, steg för steg, hur du frågar GroupDocs.Conversion för Java, hämtar varje källa‑till‑mål‑par och använder den kunskapen i molnlagrings‑filkonverterings‑pipelines. I slutet har du en återanvändbar metod som returnerar hela konverteringsmatrisen, samt praktiska tips för prestanda och felhantering.

## Snabba svar
- **Vad betyder “list formats”?** Den returnerar varje källa‑till‑mål‑konverteringspar som biblioteket kan hantera.  
- **Behöver jag en licens?** En gratis provperiod fungerar för testning; en betald licens krävs för produktion.  
- **Kan detta hjälpa med molnlagrings‑filkonvertering?** Ja—att känna till stödda format låter dig automatisera konverteringar i molnlagrings‑pipelines.  
- **Vilken Java‑version krävs?** JDK 8 eller senare.  
- **Är funktionen trådsäker?** `Converter`‑instansen kan återanvändas över trådar, men resurser bör frigöras efter användning.

## Vad är “how to list formats” i GroupDocs.Conversion?
Operationen **list formats** returnerar en samling som beskriver varje källformat tillsammans med de målformat som det kan omvandlas till. Denna matris genereras från bibliotekets interna konverteringsregler och är avgörande för att bygga dynamiska arbetsflöden som anpassar sig till de faktiska möjligheterna i GroupDocs.Conversion vid körning.

## Varför använda GroupDocs.Conversion för Java?
GroupDocs.Conversion för Java stödjer **200+ inmatningsformat** och **200+ utmatningsformat**, och täcker allt från DOCX och PPTX till PDF/A och bildtyper. Det körs helt på servern, så ingen Microsoft Office eller Adobe‑produkter behövs. API:et är trådsäkert, kan bearbeta dokument med hundratals sidor utan att ladda hela filen i minnet, och integreras sömlöst med molnlagringstjänster som AWS S3, Azure Blob och Google Cloud Storage.

## Förutsättningar
- **Java Development Kit (JDK):** Version 8 eller nyare.  
- **Maven:** Korrekt konfigurerad i din IDE (IntelliJ IDEA, Eclipse, NetBeans, etc.).  
- **GroupDocs.Conversion för Java:** Tillagd som ett Maven‑beroende (se nedan).  

## Installera GroupDocs.Conversion för Java

Lägg till GroupDocs‑arkivet och beroendet i din `pom.xml`:

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

### Licensanskaffning
Börja med en gratis provperiod för att utforska API:et. För produktionsarbetsbelastningar, köp en licens eller begär en tillfällig utvärderingslicens.

### Grundläggande initiering och konfiguration

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

## Hur man listar format med GroupDocs.Conversion för Java
`Converter` är kärnklassen som utför konverteringar och tillhandahåller formatinformation. `getAllPossibleConversions()` returnerar en lista med alla stödda källa‑till‑mål‑konverteringspar. `ConversionInfo` representerar en enskild konverteringsmappning mellan ett käll- och ett målformat.

Läs in `Converter`‑motorn, anropa `getAllPossibleConversions()`, och du får en lista med `ConversionInfo`‑objekt som beskriver varje tillåtet källa‑till‑mål‑par. Detta enda anrop är allt du behöver för att bygga en rullgardinsmeny med exportalternativ, validera inkommande filer eller designa batch‑migrationsskript.

### Initiera och hämta konverteringar
`Converter`‑klassen är kärnmotorn som tillhandahåller konverteringsmöjligheter och exponerar metoden `getAllPossibleConversions()`.

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.contracts.PossibleConversions;

public class GetAllPossibleConversionsFeature {
    public static void run() {
        // Initialize the Converter object
        Converter converter = new Converter();
```

### Iterera över möjliga konverteringar

```java
// Retrieve all possible conversions supported by the library
for (PossibleConversions conversions : converter.getAllPossibleConversions()) {
    // Print source format description
    System.out.print(String.format("Source format: %s \n", conversions.getSource().getDescription()));
```

### Bestäm konverteringstyper

```java
// Iterate through each target conversion available for the source format
for (TargetConversion conversion : conversions.getAll()) {
    // Determine if it's a primary or secondary conversion and print details
    System.out.print(String.format("\t...can be converted to %s format as %s conversion.\n",
            conversion.getFormat(),
            conversion.isPrimary() ? "primary" : "secondary"));
}
```

### Komplett funktion

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

## Användningsfall för molnlagrings‑filkonvertering
Att känna till hela konverteringsmatrisen är särskilt värdefullt när man bygger **molnlagrings‑filkonvertering**‑tjänster:

1. **Dynamisk formatdetektering:** När en fil landar i molnlagring kan du omedelbart fråga om det önskade målformatet stöds.  
2. **Batch‑migration:** Flytta stora dokumentbibliotek till ett enhetligt format (t.ex. PDF/A) genom att iterera över stödda källtyper.  
3. **Användarstyrd export:** Erbjud slutanvändare en rullgardinsmeny med endast de format som deras aktuella dokument kan exporteras till, vilket minskar fel och förbättrar användarupplevelsen.

## Prestandaöverväganden
- **Resurshantering:** Frigör `Converter`‑instansen eller använd try‑with‑resources om du skapar många kortlivade konverterare.  
- **Batch‑bearbetning:** Gruppera flera filer i ett enda jobb för att minska overhead.  
- **Cachning:** Cacha resultatet av `getAllPossibleConversions()` om du frågar det ofta; konverteringsmatrisen förändras sällan vid körning.  

## Vanliga problem och lösningar
| Symptom | Trolig orsak | Åtgärd |
|---------|--------------|-----|
| Ingen utdata visas | `Converter` inte initierad korrekt | Se till att bibliotekets JAR finns på classpath och att licensen är laddad. |
| `TargetConversion`‑listan är tom | Använder en föråldrad biblioteksversion | Uppgradera till den senaste GroupDocs.Conversion‑utgåvan. |
| Minnespikar vid stora dokument | Resurser för konverteraren frigörs inte | Anropa `converter.close()` eller använd try‑with‑resources. |

## Vanliga frågor

**Q: Vad är GroupDocs.Conversion för Java?**  
A: Det är ett server‑sidigt bibliotek som stödjer 200+ inmatnings- och 200+ utmatningsformat, vilket möjliggör snabb, licensfri dokumentkonvertering utan extern programvara.

**Q: Hur kommer jag igång med GroupDocs.Conversion?**  
A: Ställ in ditt Maven‑projekt, lägg till beroendet som visas tidigare, ladda en licensfil och skapa en instans av `Converter`‑klassen som demonstrerat i initieringsavsnittet.

**Q: Kan jag konvertera anpassade filtyper med GroupDocs.Conversion?**  
A: Ja—genom API:ets utbyggnadspunkter kan du registrera anpassade konverterare eller plugga in tredjeparts‑hanterare för proprietära format.

**Q: Vilka är vanliga fallgropar vid implementering av konverteringar?**  
A: Att glömma att stänga `Converter`, använda en gammal JAR‑version eller förbise minnesanvändning för mycket stora PDF‑filer. Följ tipsen för resurshantering ovan.

**Q: Var kan jag få mer hjälp?**  
A: Besök den officiella [dokumentationen](https://docs.groupdocs.com/conversion/java/) eller ställ frågor i GroupDocs‑community‑forumet.

---

**Senast uppdaterad:** 2026-07-29  
**Testad med:** GroupDocs.Conversion 25.2 for Java  
**Författare:** GroupDocs

## Relaterade handledningar

- [Konvertera Word till PDF och andra filformat med GroupDocs.Conversion för Java](/conversion/java/)
- [Word till PDF Java – Dölj spårade ändringar & konverteringsalternativ](/conversion/java/conversion-options/)
- [Hur man spårar konverteringsframsteg i Java med GroupDocs – En komplett guide](/conversion/java/conversion-events-logging/java-groupdocs-conversion-progress-listener/)