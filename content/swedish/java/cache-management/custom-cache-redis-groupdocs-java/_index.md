---
date: '2026-10-21'
description: Lär dig hur du skapar cache key Java och integrerar Redis med GroupDocs.Conversion
  för att öka rendering performance, minska conversion time och konfigurera TTLs i
  ett enkelt Java‑projekt.
images:
- /java/cache-management/custom-cache-redis-groupdocs-java/og-image.png
keywords:
- create cache key java
- java redis caching
- groupdocs conversion cache
- redis ttl java
lastmod: '2026-10-21'
og_description: Skapa cache key Java i den här step‑by‑step guide som visar hur du
  integrerar Redis med GroupDocs.Conversion för att cache document bytes, öka rendering
  performance och minska conversion time. Konfigurera TTLs och mät speed gains.
og_image_alt: 'Developer guide: create cache key Java using Redis and GroupDocs'
og_title: Skapa cache key Java – cacha dokument med Redis och GroupDocs
schemas:
- author: GroupDocs
  dateModified: '2026-10-21'
  description: Learn how to create cache key Java and integrate Redis with GroupDocs.Conversion
    to boost rendering performance, reduce conversion time, and configure TTLs.
  headline: Create cache key Java – cache docs with Redis and GroupDocs
  type: TechArticle
- description: Learn how to create cache key Java and integrate Redis with GroupDocs.Conversion
    to boost rendering performance, reduce conversion time, and configure TTLs.
  name: Create cache key Java – cache docs with Redis and GroupDocs
  steps:
  - name: '**High‑traffic portals** – Serve frequently requested PDFs (catalogs, whitepapers)
      instantly.'
    text: '**High‑traffic portals** – Serve frequently requested PDFs (catalogs, whitepapers)
      instantly.'
  - name: '**Enterprise DMS** – Reduce load when users repeatedly view the same contracts
      or policy documents.'
    text: '**Enterprise DMS** – Reduce load when users repeatedly view the same contracts
      or policy documents.'
  - name: '**E‑commerce** – Cache generated invoices or product catalogs to speed
      up checkout.'
    text: '**E‑commerce** – Cache generated invoices or product catalogs to speed
      up checkout.'
  - name: '**Learning platforms** – Deliver lecture notes and e‑books without re‑rendering
      on every student request.'
    text: '**Learning platforms** – Deliver lecture notes and e‑books without re‑rendering
      on every student request.'
  - name: '**Legal services** – Accelerate distribution of case files while keeping
      storage costs low.'
    text: '**Legal services** – Accelerate distribution of case files while keeping
      storage costs low.'
  type: HowTo
- questions:
  - answer: Absolutely. The same caching pattern works for DOCX, HTML, images, and
      more – just change the `ConvertOptions` type.
    question: Can I use this approach with other GroupDocs output formats?
  - answer: Combine the source file path, conversion options, and any version identifiers.
      This guarantees uniqueness per configuration.
    question: How do I choose a good cache key?
  - answer: Invalidate the cache manually (e.g., delete the key) or use a shorter
      TTL so stale data expires quickly.
    question: What if a document changes after it’s cached?
  - answer: No, but Redis offers low latency, built‑in TTL, and wide Java client support,
      making it a popular choice for this scenario.
    question: Is Redis the only option for caching?
  - answer: Minimal. The heavy lifting is done by Redis; the app only holds short‑lived
      connections via Jedis.
    question: Does this increase memory usage on the application server?
  type: FAQPage
tags:
- create cache key java
- java redis cache
- groupdocs conversion
- document rendering
title: Skapa cache key Java – cacha dokument i Java med Redis
type: docs
url: /sv/java/cache-management/custom-cache-redis-groupdocs-java/
weight: 1
---

# Skapa cache-nyckel Java – cachea dokument i Java med Redis

I moderna webbapplikationer kan det att leverera samma konverterade dokument upprepade gånger slösa CPU‑cykler och öka svarstiderna. **Att skapa en cache‑nyckel i Java** låter dig lagra konverteringsresultatet en gång och hämta det omedelbart vid efterföljande förfrågningar. Denna handledning visar hur du integrerar Redis i ett GroupDocs.Conversion‑arbetsflöde, genererar pålitliga cache‑nycklar, konfigurerar TTL‑värden och mäter de prestandaförbättringar du kan förvänta dig.

## Snabba svar
- **Vad täcker den här handledningen?** En komplett java redis‑cachninghandledning som integrerar Redis med GroupDocs.Conversion.  
- **Varför använda Redis?** Det levererar sub‑millisekund‑latens, stödjer TTL‑utgång och skalar horisontellt över flera app‑instanser.  
- **Behöver jag en GroupDocs‑licens?** En provperiod eller tillfällig licens räcker för testning; en full licens krävs för produktionsdistributioner.  
- **Vilka är huvudstegen?** Lägg till Maven‑beroenden, konfigurera en `JedisPool`, bygg cache‑hjälpmetoder och anslut cachen till konverterings‑pipen.  
- **Vilken Java‑version stöds?** Java 8+ (kompatibel med de senaste GroupDocs.Conversion‑utgåvorna).

## Vad är cachning av dokument med Redis?
Att cacha dokument med Redis innebär att lagra den binära utdata från en konvertering (t.ex. en PDF‑byte‑array) i Redis så att identiska framtida förfrågningar kan hämta de cachade bytena istället för att köra konverteringsmotorn igen. Detta eliminerar redundant CPU‑arbete, minskar nätverksbandbredd och levererar en smidigare slutanvändarupplevelse.

## Varför implementera Redis‑cache i Java?
Att ladda ett dokument en gång, lagra resultatet och leverera det omedelbart vid återkommande anrop kan **korta konverteringstiden med upp till 90 %** för ofta åtkomna filer, **sänka infrastrukturskostnaderna** genom att minska CPU‑användning, och **ge en enda sanningskälla** för alla applikationsnoder i en klustrad miljö. Redis kan bearbeta mer än 200 k operationer per sekund på en enda nod, vilket garanterar sub‑millisekund‑uppslag.

## Förutsättningar
- **GroupDocs.Conversion** – version 25.2 eller nyare (stödjer **120+** in‑ och utdataformat).  
- **Jedis** (den officiella Redis‑klienten för Java).  
- En körande Redis‑instans (lokal utveckling kan använda standard `localhost:6379`).  
- Maven för beroendehantering.  
- Grundläggande kunskap om Java‑undantagshantering och I/O‑strömmar.

## Konfigurera GroupDocs.Conversion för Java

`GroupDocs.Conversion` är ett Java‑bibliotek som konverterar och renderar dokument till ett brett spektrum av format, hanterar layout‑bevarande, teckensnittsinbäddning och bildextraktion automatiskt.

Lägg till GroupDocs‑förrådet och beroendet i din `pom.xml`:

```xml
<repositories>
    <repository>
        <id>groupdocs-maven</id>
        <url>https://repo.groupdocs.com/maven</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-conversion</artifactId>
        <version>25.2.0</version>
    </dependency>
    <dependency>
        <groupId>redis.clients</groupId>
        <artifactId>jedis</artifactId>
        <version>4.2.3</version>
    </dependency>
</dependencies>
```

### Licensanskaffning
Du kan börja med en **Free Trial**, begära en **Temporary License** för utvärdering, eller köpa en fullständig **License** för produktionsanvändning.

Initiera GroupDocs.Conversion i din Java‑kod:

```java
import com.groupdocs.conversion.*;

ConversionConfig config = new ConversionConfig();
config.setLicensePath("path/to/license/file.lic");
ConversionApi conversionApi = new ConversionApi(config);
```

## Implementeringsguide

### Skapa en anpassad cache med Redis

#### Översikt
En anpassad Redis‑cache lagrar renderade dokument‑byte, vilket möjliggör omedelbar hämtning vid återkommande förfrågningar.

#### Konfigurera JedisPool
JedisPool är en trådsäker pool av återanvändbara Redis‑anslutningar som minimerar socket‑overhead och förbättrar genomströmning.

```java
import redis.clients.jedis.JedisPool;
import redis.clients.jedis.JedisPoolConfig;

JedisPoolConfig poolConfig = new JedisPoolConfig();
poolConfig.setMaxTotal(20);               // maximum active connections
poolConfig.setMaxIdle(10);                // maximum idle connections
poolConfig.setMinIdle(2);                 // minimum idle connections
JedisPool jedisPool = new JedisPool(poolConfig, "localhost", 6379);
```

#### Lagring och hämtning av cachad data
Hjälpmetoderna nedan serialiserar en byte‑array till en Base64‑sträng för säker lagring och hämtar den tillbaka till en byte‑array.

```java
import java.util.Base64;
import redis.clients.jedis.Jedis;

public class RedisCacheHelper {

    private final JedisPool pool;
    private final int ttlSeconds; // time‑to‑live for cached entries

    public RedisCacheHelper(JedisPool pool, int ttlSeconds) {
        this.pool = pool;
        this.ttlSeconds = ttlSeconds;
    }

    public void put(String key, byte[] data) {
        try (Jedis jedis = pool.getResource()) {
            String encoded = Base64.getEncoder().encodeToString(data);
            jedis.setex(key, ttlSeconds, encoded); // configure redis ttl
        }
    }

    public byte[] get(String key) {
        try (Jedis jedis = pool.getResource()) {
            String encoded = jedis.get(key);
            return encoded != null ? Base64.getDecoder().decode(encoded) : null;
        }
    }
}
```

#### Integration med GroupDocs.Conversion
Koppla nu cachen till konverteringsarbetsflödet. Metoden kontrollerar cachen först; om ett miss inträffar utför den konverteringen, lagrar resultatet och returnerar bytena.

```java
import com.groupdocs.conversion.options.convertoptions.PdfConvertOptions;

public class DocumentService {

    private final ConversionApi conversionApi;
    private final RedisCacheHelper cacheHelper;

    public DocumentService(ConversionApi conversionApi, RedisCacheHelper cacheHelper) {
        this.conversionApi = conversionApi;
        this.cacheHelper = cacheHelper;
    }

    public byte[] convertToPdf(String sourcePath, PdfConvertOptions options) throws Exception {
        // Build a deterministic cache key
        String cacheKey = "pdf:" + sourcePath + ":" + options.hashCode();

        // Attempt to fetch from Redis
        byte[] cached = cacheHelper.get(cacheKey);
        if (cached != null) {
            // Cache hit – return stored bytes
            return cached;
        }

        // Cache miss – perform conversion
        byte[] result = conversionApi.convert(sourcePath, options).toByteArray();

        // Store result for future calls
        cacheHelper.put(cacheKey, result);
        return result;
    }
}
```

## Hur skapar man en cache‑nyckel i Java för Redis‑cachning?
Generera en deterministisk nyckel genom att concatenera källfilens sökväg, valda `ConvertOptions`‑värden och en valfri versionstagg, och sedan hash‑a strängen med SHA‑256. Denna nyckel identifierar unikt varje konverteringskonfiguration, vilket säkerställer att identiska förfrågningar träffar cachen medan olika alternativ genererar separata poster.

`ConversionApi`‑klassen är kärnkomponenten i GroupDocs.Conversion som utför dokumentkonverteringar. Du kan skapa en cache‑nyckel, slå upp den i Redis och endast anropa `ConversionApi.convert` när nyckeln saknas, vilket dramatiskt minskar konverteringstid och serverbelastning.

## Hur implementerar man Java Redis‑cachning?
`ConversionApi` är den primära klassen i GroupDocs.Conversion som utför dokumentkonverteringsoperationer. Ladda ditt källdokument, generera en deterministisk cache‑nyckel, slå upp den i Redis och anropa endast `ConversionApi` när nyckeln är frånvarande. Detta mönster garanterar att varje unik konvertering utförs en gång, och sedan levereras från cache under den konfigurerade TTL‑perioden.

## Felsökningstips
- Verifiera att Redis‑servern är nåbar (`redis-cli ping` bör returnera `PONG`).  
- Säkerställ att `JedisPool`‑värd och -port matchar din Redis‑distribution.  
- Omge cache‑anrop med try‑catch‑block för att hantera anslutningsproblem utan att avbryta konverteringsflödet.  
- Övervaka Redis‑minne (`INFO memory`) och sätt `maxmemory`‑policyer (t.ex. `volatile-lru`) för att elegant rensa gamla poster.  
- Om du får `OutOfMemoryError` på JVM, öka heap‑storleken eller aktivera `-XX:+UseCompressedOops`.

## Praktiska tillämpningar

1. **Högtrafikerade portaler** – Leverera ofta begärda PDF‑filer (kataloger, whitepapers) omedelbart.  
2. **Enterprise DMS** – Minska belastning när användare upprepade gånger visar samma kontrakt eller policydokument.  
3. **E‑handel** – Cacha genererade fakturor eller produktkataloger för att snabba upp kassan.  
4. **Lärplattformar** – Leverera föreläsningsanteckningar och e‑böcker utan att rendera om för varje studentförfrågan.  
5. **Juridiska tjänster** – Påskynda distribution av ärenden samtidigt som lagringskostnaderna hålls låga.

## Prestandaöverväganden

- **Optimera Redis** – Justera `maxmemory`, välj en eviktionspolicy som `allkeys-lru`, och sätt lämpliga `timeout`‑värden baserat på ditt trafikmönster.  
- **Spåra cache‑träff/miss‑förhållanden** – Använd `INFO stats` eller Redis‑räknarna `keyspace_hits` / `keyspace_misses` för att finjustera TTL‑värden.  
- **JVM‑heap‑storlek** – Säkerställ att heapen kan rymma GroupDocs‑buffertar; en tumregel är 1 GB heap för varje 100 MB av samtidigt konverteringspayload.  
- **Batch‑konverteringar** – Vid konvertering av många filer, återanvänd en enda `Jedis`‑instans per tråd för att minimera socket‑slitage.

## Vanliga frågor

**Q: Kan jag använda detta tillvägagångssätt med andra GroupDocs‑utdataformat?**  
A: Absolut. Samma cachningsmönster fungerar för DOCX, HTML, bilder och mer – byt bara `ConvertOptions`‑typen.

**Q: Hur väljer jag en bra cache‑nyckel?**  
A: Kombinera källfilens sökväg, konverteringsalternativ och eventuella versionsidentifierare. Detta garanterar unikhet per konfiguration.

**Q: Vad händer om ett dokument ändras efter att det har cachats?**  
A: Invalidera cachen manuellt (t.ex. ta bort nyckeln) eller använd en kortare TTL så att föråldrad data försvinner snabbt.

**Q: Är Redis det enda alternativet för cachning?**  
A: Nej, men Redis erbjuder låg latens, inbyggd TTL och brett Java‑klientstöd, vilket gör det till ett populärt val för detta scenario.

**Q: Ökar detta minnesanvändningen på applikationsservern?**  
A: Minimalt. Det tunga arbetet utförs av Redis; appen håller bara kortlivade anslutningar via Jedis.

## Slutsats
Du har nu en komplett **java redis‑cachning**‑handledning som visar hur du cachar dokument med Redis och GroupDocs.Conversion. Genom att lagra renderat resultat i Redis kommer du att **öka renderingsprestanda**, **reducera konverteringstid** och ge en smidigare upplevelse för slutanvändarna. Experimentera med olika TTL‑värden, övervaka cache‑metrik och utöka mönstret till andra dokumentformat när din applikation växer.

---

**Senast uppdaterad:** 2026-10-21  
**Testat med:** GroupDocs.Conversion 25.2, Jedis 4.2.3  
**Författare:** GroupDocs

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

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.convert.PdfConvertOptions;

public class DocumentConversion {
    public static void main(String[] args) {
        // Initialize the Converter with a document path
        Converter converter = new Converter("input.docx");
        
        // Set up conversion options for PDF
        PdfConvertOptions options = new PdfConvertOptions();
        converter.convert("output.pdf", options);
    }
}
```

```java
import redis.clients.jedis.JedisPool;

public class CacheManager {
    private static JedisPool jedisPool = new JedisPool("localhost", 6379);
    
    public static void main(String[] args) {
        // Additional cache setup code here
    }
}
```

```java
import redis.clients.jedis.Jedis;

public class CacheManager {

    public static void storeDocument(String key, String documentContent) {
        try (Jedis jedis = jedisPool.getResource()) {
            // Set the content in Redis cache with an expiration time of one hour
            jedis.setex(key, 3600, documentContent);
        }
    }

    public static String retrieveDocument(String key) {
        try (Jedis jedis = jedisPool.getResource()) {
            return jedis.get(key); // Retrieve cached content if available
        }
    }
}
```

```java
public class DocumentConversion {

    public static void convertWithCache(String inputPath, String outputPath) {
        Converter converter = new Converter(inputPath);
        PdfConvertOptions options = new PdfConvertOptions();

        // Generate a cache key based on the document path and conversion settings
        String cacheKey = "doc:" + inputPath;

        // Check if the converted document is already cached
        String cachedDocument = CacheManager.retrieveDocument(cacheKey);

        if (cachedDocument != null) {
            System.out.println("Using cached version of the document.");
            // Save cached content to output file
            Files.write(Paths.get(outputPath), cachedDocument.getBytes());
        } else {
            // Perform conversion and cache the result
            converter.convert(output -> {
                String documentContent = new String(output.toByteArray());
                CacheManager.storeDocument(cacheKey, documentContent);
                Files.write(Paths.get(outputPath), output.toByteArray());
            }, options);
        }
    }

    public static void main(String[] args) {
        convertWithCache("input.docx", "output.pdf");
    }
}
```

## Relaterade handledningar

- [Implementera anpassad cache Java – GroupDocs Conversion Cache](/conversion/java/cache-management/)
- [Hur man använder Redis‑cache i Java med GroupDocs.Conversion](/conversion/java/cache-management/redis-cache-java-groupdocs-conversion-guide/)
- [Hur man cachar filer i Java med GroupDocs.Conversion – En omfattande guide för effektiv dokumentkonvertering](/conversion/java/cache-management/implement-java-file-caching-groupdocs-conversion-guide/)
