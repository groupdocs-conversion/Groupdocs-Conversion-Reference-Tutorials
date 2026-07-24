---
date: '2026-07-24'
description: 'Java-afbeeldingsconversie eenvoudig gemaakt: leer hoe u CAD‑bestanden
  naar TIFF converteert met aangepaste afmetingen met behulp van GroupDocs Conversion
  Java. Stapsgewijze handleiding voor ontwikkelaars.'
keywords:
- java image conversion
- custom width height
- set image dimensions java
lastmod: '2026-07-24'
og_description: Java-afbeeldingsconversie eenvoudig gemaakt. Converteer CAD‑bestanden
  naar hoogwaardige TIFF‑afbeeldingen met aangepaste breedte en hoogte met behulp
  van GroupDocs Conversion Java. Volg onze gedetailleerde handleiding.
og_image_alt: 'Guide: Convert CAD to TIFF with custom dimensions using GroupDocs Conversion
  Java'
og_title: 'Java-afbeeldingsconversie: CAD naar TIFF met aangepaste afmetingen'
schemas:
- author: GroupDocs
  dateModified: '2026-07-24'
  description: 'Java image conversion made easy: learn how to convert CAD files to
    TIFF with custom dimensions using GroupDocs Conversion Java. Step‑by‑step guide
    for developers.'
  headline: 'Java Image Conversion: CAD to TIFF with Custom Dimensions'
  type: TechArticle
- questions:
  - answer: GroupDocs Conversion Java, a robust Java image conversion library.
    question: What library should I use for Java image conversion?
  - answer: Use `CadLoadOptions` and specify `setWidth()` and `setHeight()`.
    question: How do I set custom dimensions for a CAD file?
  - answer: Yes—load the CAD, set dimensions, then convert with `ImageConvertOptions`.
    question: Can I convert DWG to TIFF in one step?
  - answer: A free trial works for evaluation; a full license unlocks all features.
    question: Do I need a license?
  - answer: Any Java 8+ runtime is supported.
    question: What Java version is required?
  type: FAQPage
tags:
- convert CAD
- GroupDocs Conversion
- Java image conversion
- TIFF
- CAD processing
title: 'Java-afbeeldingsconversie: CAD naar TIFF met aangepaste afmetingen'
type: docs
url: /nl/java/cad-formats/cad-conversion-tiff-custom-dimensions-groupdocs-java/
weight: 1
---

# Java-afbeeldingsconversie: CAD naar TIFF met aangepaste afmetingen

Als u CAD‑tekeningen wilt omzetten naar hoge‑resolutie TIFF‑afbeeldingen terwijl u de exacte pixelbreedte en -hoogte controleert, is **java image conversion** de sleutel. Met GroupDocs Conversion Java kunt u elk ondersteund CAD‑formaat (DWG, DGN, DXF, enz.) rasteren naar een TIFF‑bestand dat perfect past in rapporten, webportalen of afdruklay‑outs. Deze gids leidt u door elke stap — van projectopzet tot uiteindelijke conversie — zodat u het proces kunt integreren in elke Java‑gebaseerde workflow.

## Snelle antwoorden
- **Welke bibliotheek moet ik gebruiken voor Java image conversion?** GroupDocs Conversion Java, een robuuste Java image conversion bibliotheek.  
- **Hoe stel ik aangepaste afmetingen in voor een CAD‑bestand?** Gebruik `CadLoadOptions` en specificeer `setWidth()` en `setHeight()`.  
- **Kan ik DWG in één stap naar TIFF converteren?** Ja — laad de CAD, stel afmetingen in, en converteer vervolgens met `ImageConvertOptions`.  
- **Heb ik een licentie nodig?** Een gratis proefversie werkt voor evaluatie; een volledige licentie ontgrendelt alle functies.  
- **Welke Java‑versie is vereist?** Elke Java 8+ runtime wordt ondersteund.

## Wat is GroupDocs Conversion Java?
De `GroupDocs Conversion Java` bibliotheek is een **java image conversion** oplossing die meer dan 110 invoer‑ en uitvoerformaten ondersteunt, inclusief alle belangrijke CAD‑ en raster‑beeldtypen.  
De `Converter`‑klasse is de kerncomponent die bestandsconversie‑operaties initieert.  
Het biedt server‑side rendering, schaling en format‑specifieke opties, waardoor ontwikkelaars bestanden kunnen converteren zonder third‑party viewers te installeren.

## Waarom CAD naar TIFF converteren met aangepaste afmetingen?
Het instellen van expliciete breedte en hoogte garandeert dat de resulterende TIFF precies past binnen de lay‑outbeperkingen van downstream‑systemen. Door de pixelafmetingen vóór rasterisatie te definiëren, vermijdt u schaalartefacten, behoudt u de consistentie van lijndiktes en zorgt u ervoor dat de afbeelding naadloos integreert in PDF‑bestanden, webpagina's of gedrukt materiaal zonder extra verwerking. Deze aanpak vereenvoudigt ook geautomatiseerde pipelines waarbij elke afbeelding moet voldoen aan een vooraf gedefinieerde grootte‑specificatie.  

- **Behoudt visuele getrouwheid:** Rasteren op 1920 × 1080 px (of elke door u gekozen grootte) houdt lijnwerk en arcering scherp.  
- **Zorgt voor consistente lay‑outs:** Afbeeldingen worden netjes ingebed in PDF‑bestanden, HTML‑pagina's of afdruksjablonen zonder extra herschaling.  
- **Verhoogt compatibiliteit:** TIFF wordt universeel geaccepteerd op Windows, macOS, Linux en de meeste ontwerptools, waardoor problemen met formaatconversie worden verminderd.

## Voorvereisten
Zorg ervoor dat u het volgende heeft voordat u begint:

1. **GroupDocs Conversion Java** versie 25.2 of later (de nieuwste release wordt aanbevolen).  
2. Een Java‑IDE zoals IntelliJ IDEA of Eclipse.  
3. Maven geïnstalleerd voor afhankelijkheidsbeheer.  
4. Basiskennis van Java‑programmeren en vertrouwdheid met Maven’s `pom.xml`.  

## GroupDocs Conversion Java instellen

Voeg de GroupDocs Maven‑afhankelijkheid toe aan uw `pom.xml`:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-conversion</artifactId>
    <version>25.2</version>
</dependency>
```

**Licentie‑acquisitie:** U kunt een gratis proefversie verkrijgen, een tijdelijke licentie aanvragen voor volledige functionaliteit, of een permanente licentie kopen om alle GroupDocs Conversion‑functies volledig te ontgrendelen.

Zodra uw Java‑project correct is gekoppeld aan deze afhankelijkheden, bent u klaar om CAD‑bestanden te gaan converteren!

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

## Hoe CAD naar TIFF converteren met aangepaste afmetingen?

Het converteren van CAD‑bestanden naar TIFF met precieze afmetingen omvat het laden van de brontekening, het configureren van render‑opties en het aanroepen van de conversie‑API. Door een lineaire volgorde te volgen — breedte en hoogte instellen, TIFF kiezen als uitvoerformaat en de conversie uitvoeren — zorgt u ervoor dat de gegenereerde afbeelding exact voldoet aan de grootte‑vereisten van uw downstream‑toepassingen, terwijl u de details en kwaliteit van de oorspronkelijke tekening behoudt.  

1. **Importeer de vereiste klassen** (zie stap‑voor‑stap hieronder).  
2. **Maak een `CadLoadOptions`‑instantie** en stel `width` en `height` in op uw doelafmetingen.  
3. **Instantieer `ImageConvertOptions`**, met `ImageFileType.Tiff` als specificatie.  
4. **Roep de `convert`‑methode** aan op een `Converter`‑object, waarbij u het bronpad, de load‑options en de convert‑options doorgeeft.

### CAD‑documenten laden met aangepaste afmetingen (Hoe afmetingen instellen)

De `CadLoadOptions`‑klasse vertelt GroupDocs hoe de tekening moet worden gerasterd vóór conversie.

`CadLoadOptions` is het configuratie‑object dat render‑parameters zoals breedte, hoogte en DPI voor CAD‑bestanden definieert.

#### Stap 1: Importeer benodigde bibliotheken
```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.filetypes.ImageFileType;
import com.groupdocs.conversion.options.convert.ImageConvertOptions;
import com.groupdocs.conversion.options.load.CadLoadOptions;
```

#### Stap 2: Stel load‑options in met aangepaste afmetingen
```java
String sourceDocumentPath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DWG_WITH_LAYOUTS_AND_LAYERS";
CadLoadOptions loadOptions = new CadLoadOptions();
loadOptions.setWidth(1920); // Specify the desired width in pixels
loadOptions.setHeight(1080); // Specify the desired height in pixels
Converter converter = new Converter(sourceDocumentPath, () -> loadOptions);
```
*Uitleg:* Door `CadLoadOptions` te configureren, vertelt u **GroupDocs Conversion Java** om de CAD‑tekening te rasteren op 1920 × 1080 pixels vóór verdere verwerking.

### CAD naar TIFF‑afbeelding converteren (CAD naar TIFF converteren)

`ImageConvertOptions` stuurt de bibliotheek aan om een TIFF‑bestand te produceren met de door u opgegeven instellingen.

`ImageConvertOptions` omvat alle afbeelding‑specifieke conversie‑parameters, inclusief uitvoerformaat, resolutie en compressieniveau.

#### Stap 3: Configureer conversie‑opties
```java
String convertedFilePath = "YOUR_OUTPUT_DIRECTORY/ConvertCadAndSpecifyWidthAndHeight.tiff";
ImageConvertOptions options = new ImageConvertOptions();
options.setFormat(ImageFileType.Tiff); // Set the conversion target to TIFF format
```

#### Stap 4: Voer de conversie uit
```java
converter.convert(convertedFilePath, options);
```
*Uitleg:* Het instellen van `ImageFileType.Tiff` zorgt ervoor dat **GroupDocs Conversion Java** een hoogwaardige TIFF‑bestand uitvoert dat de eerder gedefinieerde breedte en hoogte respecteert.

## Tips voor probleemoplossing & veelvoorkomende valkuilen
- **Bestandspad‑problemen:** Controleer of zowel bron‑ als bestemmingspaden correct zijn en dat de applicatie lees‑/schrijfrechten heeft.  
- **Niet‑ondersteunde formaten:** Zorg ervoor dat het CAD‑bestand een van de ondersteunde formaten is (DWG, DGN, DXF, enz.).  
- **Geheugenbeperkingen:** Grote tekeningen kunnen een verhoging van de JVM‑heap‑grootte vereisen (`-Xmx2g` of hoger).  
- **Kwaliteitszorgen:** Pas de resolutie‑instellingen van `ImageConvertOptions` aan als de standaard DPI niet aan uw kwaliteitsnormen voldoet.

## Praktische toepassingen
1. **Architecturale visualisatie:** Exporteer plattegronden als TIFF voor hoge‑resolutie presentaties.  
2. **Technische documentatie:** Genereer gestandaardiseerde afbeeldingen voor opname in technische handleidingen.  
3. **Geautomatiseerde rapportage:** Integreer CAD‑afgeleide TIFF‑bestanden in PDF‑ of HTML‑rapporten via een CI‑pipeline.

## Prestatie‑overwegingen
- **Geheugenverbruik optimaliseren:** Maak de `Converter`‑instantie vrij na conversie (`converter.close()` indien van toepassing).  
- **Batchverwerking:** Loop door een lijst van CAD‑bestanden en hergebruik een enkele `Converter`‑configuratie om overhead te verminderen.  
- **Blijf up‑to‑date:** Upgrade regelmatig naar de nieuwste GroupDocs Conversion Java‑release om te profiteren van prestatie‑verbeteringen en bug‑fixes.

## Veelgestelde vragen

**Q:** Welke bestandsformaten ondersteunt GroupDocs Conversion?  
**A:** Het ondersteunt meer dan 110 formaten, inclusief CAD‑bestanden zoals DWG, DGN, DXF, evenals gangbare afbeelding-, document‑ en archieftypen.

**Q:** Kan ik meerdere CAD‑bestanden tegelijk converteren?  
**A:** Ja — implementeer een eenvoudige lus die voor elk bestand een nieuwe `Converter` maakt of hergebruik dezelfde instantie met verschillende bronpaden.

**Q:** Hoe ga ik om met grote bestandsgroottes tijdens conversie?  
**A:** Verhoog de JVM‑heap‑grootte, verwerk bestanden in kleinere batches, of gebruik streaming‑opties die door de bibliotheek worden aangeboden.

**Q:** Wat als de kwaliteit van de uitvoerafbeelding niet bevredigend is?  
**A:** Pas de DPI‑ of schaalinstellingen in `ImageConvertOptions` aan om de resolutie te verhogen.

**Q:** Is er ondersteuning beschikbaar als ik problemen ondervind?  
**A:** GroupDocs biedt uitgebreide documentatie, community‑forums en directe ondersteuning voor gelicentieerde klanten.

## Bronnen
- [GroupDocs-documentatie](https://docs.groupdocs.com/conversion/java/)
- [API‑referentie](https://reference.groupdocs.com/conversion/java/)
- [Laatste release downloaden](https://releases.groupdocs.com/conversion/java/)
- [Licenties kopen](https://purchase.groupdocs.com/buy)
- [Gratis proeftoegang](https://releases.groupdocs.com/conversion/java/)
- [Tijdelijke licentie aanvragen](https://purchase.groupdocs.com/temporary-license/)
- [Supportforum](https://forum.groupdocs.com/c/conversion/10)

---

**Laatst bijgewerkt:** 2026-07-24  
**Getest met:** GroupDocs Conversion Java 25.2  
**Auteur:** GroupDocs  

---

## Gerelateerde tutorials

- [convert cad pdf java – CAD-formaatconversietutorials voor GroupDocs.Conversion Java](/conversion/java/cad-formats/)
- [convert pdf to jpg java met GroupDocs.Conversion – Gids](/conversion/java/document-operations/convert-pdf-to-jpg-groupdocs-java/)
- [Hoe licentie instellen voor GroupDocs.Conversion Java - Stapsgewijze gids](/conversion/java/getting-started/groupdocs-conversion-java-license-setup-file-path/)