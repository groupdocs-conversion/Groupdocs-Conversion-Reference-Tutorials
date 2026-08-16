---
date: '2026-07-24'
description: 'Java-bildkonvertering gjort enkelt: lär dig hur du konverterar CAD-filer
  till TIFF med anpassade dimensioner med hjälp av GroupDocs Conversion Java. Steg‑för‑steg‑guide
  för utvecklare.'
keywords:
- java image conversion
- custom width height
- set image dimensions java
lastmod: '2026-07-24'
og_description: Java-bildkonvertering gjort enkelt. Konvertera CAD-filer till högkvalitativa
  TIFF‑bilder med anpassad bredd och höjd med hjälp av GroupDocs Conversion Java.
  Följ vår detaljerade guide.
og_image_alt: 'Guide: Convert CAD to TIFF with custom dimensions using GroupDocs Conversion
  Java'
og_title: 'Java-bildkonvertering: CAD till TIFF med anpassade dimensioner'
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
title: 'Java-bildkonvertering: CAD till TIFF med anpassade dimensioner'
type: docs
url: /sv/java/cad-formats/cad-conversion-tiff-custom-dimensions-groupdocs-java/
weight: 1
---

# Java bildkonvertering: CAD till TIFF med anpassade dimensioner

Om du behöver omvandla CAD-ritningar till högupplösta TIFF‑bilder samtidigt som du styr den exakta pixelbredden och -höjden, är **java image conversion** nyckeln. Med GroupDocs Conversion Java kan du rasterisera vilket stödjande CAD-format som helst (DWG, DGN, DXF, osv.) till en TIFF‑fil som passar perfekt i rapporter, webbportaler eller utskriftslayouter. Denna guide går igenom varje steg—från projektuppsättning till slutlig konvertering—så att du kan integrera processen i vilket Java‑baserat arbetsflöde som helst.

## Snabba svar
- **Vilket bibliotek bör jag använda för Java image conversion?** GroupDocs Conversion Java, a robust Java image conversion library.  
- **Hur ställer jag in anpassade dimensioner för en CAD‑fil?** Use `CadLoadOptions` and specify `setWidth()` and `setHeight()`.  
- **Kan jag konvertera DWG till TIFF i ett steg?** Yes—load the CAD, set dimensions, then convert with `ImageConvertOptions`.  
- **Behöver jag en licens?** A free trial works for evaluation; a full license unlocks all features.  
- **Vilken Java‑version krävs?** Any Java 8+ runtime is supported.

## Vad är GroupDocs Conversion Java?
Biblioteket `GroupDocs Conversion Java` är en **java image conversion**‑lösning som stödjer över 110 in‑ och utdataformat, inklusive alla större CAD‑ och rasterbildstyper.  
`Converter`‑klassen är kärnkomponenten som initierar filkonverteringsoperationer.  
Den erbjuder server‑sidans rendering, skalning och format‑specifika alternativ, vilket gör att utvecklare kan konvertera filer utan att installera tredjeparts‑visare.

## Varför konvertera CAD till TIFF med anpassade dimensioner?
Att ange explicit bredd och höjd garanterar att den resulterande TIFF‑filen passar exakt i layout‑begränsningarna för efterföljande system. Genom att definiera pixel‑dimensionerna innan rasterisering undviker du skalningsartefakter, behåller linjebreddens konsistens och säkerställer att bilden integreras sömlöst i PDF‑filer, webbsidor eller tryckt material utan ytterligare bearbetning. Detta tillvägagångssätt förenklar också automatiserade pipelines där varje bild måste följa en fördefinierad storleksspecifikation.  

- **Bevarar visuell kvalitet:** Rasterisering vid 1920 × 1080 px (eller någon annan storlek du väljer) behåller linjearbetet och skrafferingen skarpa.  
- **Säkerställer konsekventa layouter:** Bilder infogas rent i PDF‑filer, HTML‑sidor eller utskriftsmallar utan extra omformatering.  
- **Ökar kompatibiliteten:** TIFF accepteras universellt på Windows, macOS, Linux och de flesta designverktyg, vilket minskar problem med formatkonvertering.

## Förutsättningar
Innan du börjar, se till att du har:

1. **GroupDocs Conversion Java** version 25.2 eller senare (den senaste versionen rekommenderas).  
2. En Java‑IDE såsom IntelliJ IDEA eller Eclipse.  
3. Maven installerat för beroendehantering.  
4. Grundläggande kunskaper i Java‑programmering och bekantskap med Maven’s `pom.xml`.  

## Konfigurera GroupDocs Conversion Java

Lägg till GroupDocs Maven‑beroendet i din `pom.xml`:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-conversion</artifactId>
    <version>25.2</version>
</dependency>
```

**Licensförvärv:** Du kan skaffa en gratis provperiod, begära en tillfällig licens för full funktionalitet, eller köpa en permanent licens för att helt låsa upp GroupDocs Conversion‑funktionerna.

När ditt Java‑projekt är korrekt länkat med dessa beroenden är du redo att börja konvertera CAD‑filer!

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

## Så konverterar du CAD till TIFF med anpassade dimensioner?

Att konvertera CAD‑filer till TIFF med exakta dimensioner innebär att ladda källritningen, konfigurera renderingsalternativ och anropa konverterings‑API‑et. Genom att följa en linjär sekvens—sätta bredd och höjd, välja TIFF som utdataformat och utföra konverteringen—säkerställer du att den genererade bilden matchar de exakta storlekskraven för dina efterföljande applikationer, samtidigt som du bevarar originalritningens detaljer och kvalitet.  

1. **Importera de nödvändiga klasserna** (se steg‑för‑steg nedan).  
2. **Skapa en `CadLoadOptions`‑instans** och sätt `width` och `height` till dina mål‑dimensioner.  
3. **Instansiera `ImageConvertOptions`**, med angivelse av `ImageFileType.Tiff`.  
4. **Anropa `convert`‑metoden** på ett `Converter`‑objekt, och skicka in källsökvägen, laddningsalternativen och konverteringsalternativen.  

### Laddar CAD‑dokument med anpassade dimensioner (Hur man ställer in dimensioner)

`CadLoadOptions`‑klassen talar om för GroupDocs hur ritningen ska rasteriseras innan konvertering.

`CadLoadOptions` är konfigurationsobjektet som definierar renderingsparametrar såsom bredd, höjd och DPI för CAD‑filer.

#### Steg 1: Importera nödvändiga bibliotek
```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.filetypes.ImageFileType;
import com.groupdocs.conversion.options.convert.ImageConvertOptions;
import com.groupdocs.conversion.options.load.CadLoadOptions;
```

#### Steg 2: Ställ in laddningsalternativ med anpassade dimensioner
```java
String sourceDocumentPath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DWG_WITH_LAYOUTS_AND_LAYERS";
CadLoadOptions loadOptions = new CadLoadOptions();
loadOptions.setWidth(1920); // Specify the desired width in pixels
loadOptions.setHeight(1080); // Specify the desired height in pixels
Converter converter = new Converter(sourceDocumentPath, () -> loadOptions);
```
*Förklaring:* Genom att konfigurera `CadLoadOptions` talar du om för **GroupDocs Conversion Java** att rasterisera CAD‑ritningen till 1920 × 1080 pixlar innan någon vidare bearbetning.

### Konverterar CAD till TIFF‑bild (Convert CAD to TIFF)

`ImageConvertOptions` styr biblioteket att producera en TIFF‑fil med de inställningar du anger.

`ImageConvertOptions` kapslar in alla bildspecifika konverteringsparametrar, inklusive utdataformat, upplösning och komprimeringsnivå.

#### Steg 3: Konfigurera konverteringsalternativ
```java
String convertedFilePath = "YOUR_OUTPUT_DIRECTORY/ConvertCadAndSpecifyWidthAndHeight.tiff";
ImageConvertOptions options = new ImageConvertOptions();
options.setFormat(ImageFileType.Tiff); // Set the conversion target to TIFF format
```

#### Steg 4: Utför konverteringen
```java
converter.convert(convertedFilePath, options);
```
*Förklaring:* Genom att sätta `ImageFileType.Tiff` instruerar du **GroupDocs Conversion Java** att producera en högkvalitativ TIFF‑fil som respekterar den bredd och höjd du definierade tidigare.

## Felsökningstips & vanliga fallgropar
- **Problem med filsökvägar:** Verifiera att både käll- och destinationssökvägarna är korrekta och att applikationen har läs‑/skrivrättigheter.  
- **Ej stödjade format:** Se till att CAD‑filen är ett av de stödjade formaten (DWG, DGN, DXF, osv.).  
- **Minnesbegränsningar:** Stora ritningar kan kräva att JVM‑heap‑storleken ökas (`-Xmx2g` eller högre).  
- **Kvalitetsproblem:** Justera `ImageConvertOptions`‑upplösningsinställningar om standard‑DPI inte uppfyller dina kvalitetskrav.  

## Praktiska tillämpningar
1. **Arkitektonisk visualisering:** Exportera planritningar som TIFF för högupplösta presentationer.  
2. **Ingenjörsdokumentation:** Generera standardiserade bilder för inkludering i tekniska manualer.  
3. **Automatiserad rapportering:** Bädda in CAD‑genererade TIFF‑filer i PDF‑ eller HTML‑rapporter via en CI‑pipeline.  

## Prestandaöverväganden
- **Optimera minnesanvändning:** Frigör `Converter`‑instansen efter konvertering (`converter.close()` om tillämpligt).  
- **Batch‑behandling:** Loopa igenom en lista med CAD‑filer och återanvänd en enda `Converter`‑konfiguration för att minska overhead.  
- **Håll dig uppdaterad:** Uppgradera regelbundet till den senaste GroupDocs Conversion Java‑utgåvan för att dra nytta av prestandaförbättringar och buggfixar.  

## Vanliga frågor

**Q:** Vilka filformat stödjer GroupDocs Conversion?  
**A:** Den stödjer över 110 format, inklusive CAD‑filer som DWG, DGN, DXF, samt vanliga bild-, dokument- och arkivtyper.

**Q:** Kan jag konvertera flera CAD‑filer samtidigt?  
**A:** Ja—implementera en enkel loop som skapar en ny `Converter` för varje fil eller återanvänd samma instans med olika källsökvägar.

**Q:** Hur hanterar jag stora filstorlekar under konvertering?  
**A:** Öka JVM‑heap‑storleken, bearbeta filer i mindre batcher, eller använd streaming‑alternativ som biblioteket tillhandahåller.

**Q:** Vad gör jag om bildkvaliteten på utdata inte är tillfredsställande?  
**A:** Justera DPI‑ eller skalningsinställningarna i `ImageConvertOptions` för att öka upplösningen.

**Q:** Finns support tillgänglig om jag stöter på problem?  
**A:** GroupDocs erbjuder omfattande dokumentation, community‑forum och direkt support för licensierade kunder.

## Resurser
- [GroupDocs-dokumentation](https://docs.groupdocs.com/conversion/java/)
- [API‑referens](https://reference.groupdocs.com/conversion/java/)
- [Ladda ner senaste versionen](https://releases.groupdocs.com/conversion/java/)
- [Köp licenser](https://purchase.groupdocs.com/buy)
- [Gratis provperiod](https://releases.groupdocs.com/conversion/java/)
- [Begär tillfällig licens](https://purchase.groupdocs.com/temporary-license/)
- [Supportforum](https://forum.groupdocs.com/c/conversion/10)

---

**Senast uppdaterad:** 2026-07-24  
**Testat med:** GroupDocs Conversion Java 25.2  
**Författare:** GroupDocs  

---

## Relaterade handledningar

- [konvertera cad pdf java – CAD-format konverteringshandledningar för GroupDocs.Conversion Java](/conversion/java/cad-formats/)
- [konvertera pdf till jpg java med GroupDocs.Conversion – Guide](/conversion/java/document-operations/convert-pdf-to-jpg-groupdocs-java/)
- [Hur man ställer in licens för GroupDocs.Conversion Java – Steg‑för‑steg‑guide](/conversion/java/getting-started/groupdocs-conversion-java-license-setup-file-path/)