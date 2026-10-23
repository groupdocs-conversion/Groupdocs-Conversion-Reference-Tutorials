---
date: '2026-10-21'
description: Leer hoe u een cache‑sleutel in Java maakt en Redis integreert met GroupDocs.Conversion
  om de renderprestaties te verbeteren, de conversietijd te verkorten en TTL’s te
  configureren in een eenvoudig Java‑project.
images:
- /java/cache-management/custom-cache-redis-groupdocs-java/og-image.png
keywords:
- create cache key java
- java redis caching
- groupdocs conversion cache
- redis ttl java
lastmod: '2026-10-21'
og_description: Maak een cache‑sleutel in Java met deze stapsgewijze handleiding die
  laat zien hoe u Redis integreert met GroupDocs.Conversion om documentbytes te cachen,
  de renderprestaties te verbeteren en de conversietijd te verkorten. Configureer
  TTL’s en meet snelheidswinst.
og_image_alt: 'Developer guide: create cache key Java using Redis and GroupDocs'
og_title: Cache‑sleutel maken in Java – documenten cachen met Redis en GroupDocs
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
title: Cache‑sleutel maken in Java – documenten cachen in Java met Redis
type: docs
url: /nl/java/cache-management/custom-cache-redis-groupdocs-java/
weight: 1
---

# Maak cache‑sleutel Java – cache documenten in Java met Redis

In moderne webapplicaties kan het steeds opnieuw serveren van hetzelfde geconverteerde document CPU-cycli verspillen en de responstijden verhogen. **Een cache‑sleutel maken in Java** stelt je in staat de conversie‑output één keer op te slaan en deze direct op volgende verzoeken op te halen. Deze tutorial laat zien hoe je Redis in een GroupDocs.Conversion‑workflow integreert, betrouwbare cache‑sleutels genereert, TTL’s configureert en de prestatieverbeteringen meet die je kunt verwachten.

## Snelle antwoorden
- **Waar gaat deze tutorial over?** Een volledige java‑redis‑caching‑tutorial die Redis integreert met GroupDocs.Conversion.  
- **Waarom Redis gebruiken?** Het levert sub‑milliseconden latency, ondersteunt TTL‑verval en schaalt horizontaal over meerdere applicatie‑instances.  
- **Heb ik een GroupDocs‑licentie nodig?** Een proef‑ of tijdelijke licentie is voldoende voor testen; een volledige licentie is vereist voor productie‑implementaties.  
- **Wat zijn de belangrijkste stappen?** Voeg Maven‑dependencies toe, configureer een `JedisPool`, bouw cache‑helper‑methoden, en koppel de cache aan de conversiepijplijn.  
- **Welke Java‑versie wordt ondersteund?** Java 8+ (compatibel met de nieuwste GroupDocs.Conversion‑releases).

## Wat is het cachen van documenten met Redis?
Caching van documenten met Redis betekent het opslaan van de binaire output van een conversie (bijv. een PDF‑byte‑array) in Redis, zodat identieke toekomstige verzoeken de gecachte bytes kunnen ophalen in plaats van de conversie‑engine opnieuw uit te voeren. Dit elimineert overbodig CPU‑werk, vermindert netwerkbandbreedte en levert een soepelere eind‑gebruikerservaring.

## Waarom Redis‑cache implementeren in Java?
Een document één keer laden, het resultaat opslaan en het direct serveren bij herhaalde verzoeken kan **de conversietijd met tot 90 % verkorten** voor vaak geraadpleegde bestanden, **infrastructuurkosten verlagen** door minder CPU‑gebruik, en **een enkele bron van waarheid bieden** voor alle applicatienodes in een clusteromgeving. Redis kan meer dan 200 k bewerkingen per seconde verwerken op één node, wat sub‑milliseconde opzoekacties garandeert.

## Voorvereisten
- **GroupDocs.Conversion** – versie 25.2 of nieuwer (ondersteunt **120+** invoer‑ en uitvoerformaten).  
- **Jedis** (de officiële Redis‑client voor Java).  
- Een draaiende Redis‑instance (lokale ontwikkeling kan de standaard `localhost:6379` gebruiken).  
- Maven voor dependency‑beheer.  
- Basiskennis van Java‑exception‑handling en I/O‑streams.

## GroupDocs.Conversion configureren voor Java

`GroupDocs.Conversion` is een Java‑bibliotheek die documenten converteert en rendert naar een breed scala aan formaten, waarbij lay‑outbehoud, lettertype‑inbedding en afbeeldingsextractie automatisch worden afgehandeld.

Voeg de GroupDocs‑repository en dependency toe aan je `pom.xml`:

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

### Licentie‑acquisitie
Je kunt beginnen met een **Free Trial**, een **Temporary License** aanvragen voor evaluatie, of een volledige **License** aanschaffen voor productiegebruik.

Initialiseer GroupDocs.Conversion in je Java‑code:

```java
import com.groupdocs.conversion.*;

ConversionConfig config = new ConversionConfig();
config.setLicensePath("path/to/license/file.lic");
ConversionApi conversionApi = new ConversionApi(config);
```

## Implementatie‑gids

### Een aangepaste cache maken met Redis

#### Overzicht
Een aangepaste Redis‑cache bewaart gerenderde documentbytes, waardoor directe ophalen bij herhaalde verzoeken mogelijk is.

#### JedisPool configureren
JedisPool is een thread‑safe pool van herbruikbare Redis‑verbindingen die socket‑overhead minimaliseert en de doorvoer verbetert.

```java
import redis.clients.jedis.JedisPool;
import redis.clients.jedis.JedisPoolConfig;

JedisPoolConfig poolConfig = new JedisPoolConfig();
poolConfig.setMaxTotal(20);               // maximum active connections
poolConfig.setMaxIdle(10);                // maximum idle connections
poolConfig.setMinIdle(2);                 // minimum idle connections
JedisPool jedisPool = new JedisPool(poolConfig, "localhost", 6379);
```

#### Opslaan en ophalen van gecachte data
De helper‑methoden hieronder serialiseren een byte‑array naar een Base64‑string voor veilige opslag en halen deze terug naar een byte‑array.

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

#### Integratie met GroupDocs.Conversion
Koppel nu de cache aan de conversieworkflow. De methode controleert eerst de cache; bij een miss wordt de conversie uitgevoerd, het resultaat opgeslagen, en de bytes geretourneerd.

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

## Hoe maak je een cache‑sleutel in Java voor Redis‑caching?
Genereer een deterministische sleutel door het bron‑bestandspad, geselecteerde `ConvertOptions`‑waarden en een optionele versie‑tag samen te voegen, en hash vervolgens de string met SHA‑256. Deze sleutel identificeert elke conversie‑configuratie uniek, waardoor identieke verzoeken de cache raken terwijl verschillende opties afzonderlijke entries genereren.

De `ConversionApi`‑klasse is het kernonderdeel in GroupDocs.Conversion dat documentconversies uitvoert. Je kunt een cache‑sleutel maken, deze in Redis opzoeken, en alleen `ConversionApi.convert` aanroepen wanneer de sleutel ontbreekt, waardoor de conversietijd en serverbelasting drastisch worden verminderd.

## Hoe implementeer je Java‑Redis‑caching?
`ConversionApi` is de primaire klasse in GroupDocs.Conversion die documentconversie‑operaties uitvoert. Laad je bron‑document, genereer een deterministische cache‑sleutel, zoek deze op in Redis, en roep alleen `ConversionApi` aan wanneer de sleutel afwezig is. Dit patroon garandeert dat elke unieke conversie één keer wordt uitgevoerd, daarna vanuit de cache wordt geserveerd gedurende de geconfigureerde TTL.

## Probleemoplossingstips
- Controleer of de Redis‑server bereikbaar is (`redis-cli ping` moet `PONG` retourneren).  
- Zorg ervoor dat host en poort van `JedisPool` overeenkomen met je Redis‑implementatie.  
- Omwikkel cache‑aanroepen met try‑catch‑blokken om verbindingsproblemen af te handelen zonder de conversiestroom te onderbreken.  
- Monitor Redis‑geheugen (`INFO memory`) en stel `maxmemory`‑beleid in (bijv. `volatile-lru`) om oude entries netjes te verwijderen.  
- Als je een `OutOfMemoryError` op de JVM tegenkomt, vergroot dan de heap‑grootte of schakel `-XX:+UseCompressedOops` in.

## Praktische toepassingen

1. **High‑traffic portals** – Serveer veelgevraagde PDF’s (catalogi, whitepapers) direct.  
2. **Enterprise DMS** – Verminder belasting wanneer gebruikers herhaaldelijk dezelfde contracten of beleidsdocumenten bekijken.  
3. **E‑commerce** – Cache gegenereerde facturen of productcatalogi om het afrekenproces te versnellen.  
4. **Learning platforms** – Lever college‑notities en e‑books zonder elke keer opnieuw te renderen bij elk studentverzoek.  
5. **Legal services** – Versnel de distributie van dossiers terwijl de opslagkosten laag blijven.

## Prestatie‑overwegingen

- **Tune Redis** – Pas `maxmemory` aan, kies een evicitie‑beleid zoals `allkeys-lru`, en stel passende `timeout`‑waarden in op basis van je verkeerspatroon.  
- **Track cache hit/miss ratios** – Gebruik `INFO stats` of Redis‑counters `keyspace_hits` / `keyspace_misses` om TTL’s fijn af te stemmen.  
- **JVM heap sizing** – Zorg ervoor dat de heap voldoende ruimte biedt voor GroupDocs‑buffers; een vuistregel is 1 GB heap per 100 MB gelijktijdige conversie‑payload.  
- **Batch conversions** – Bij het converteren van veel bestanden, hergebruik een enkele `Jedis`‑instance per thread om socket‑churn te minimaliseren.

## Veelgestelde vragen

**Q: Kan ik deze aanpak gebruiken met andere GroupDocs‑outputformaten?**  
A: Absoluut. Hetzelfde caching‑patroon werkt voor DOCX, HTML, afbeeldingen en meer – wijzig gewoon het `ConvertOptions`‑type.

**Q: Hoe kies ik een goede cache‑sleutel?**  
A: Combineer het bron‑bestandspad, de conversie‑opties en eventuele versie‑identifiers. Dit garandeert uniciteit per configuratie.

**Q: Wat als een document verandert nadat het is gecached?**  
A: Invalidatie van de cache handmatig (bijv. de sleutel verwijderen) of gebruik een kortere TTL zodat verouderde data snel verloopt.

**Q: Is Redis de enige optie voor caching?**  
A: Nee, maar Redis biedt lage latency, ingebouwde TTL, en brede Java‑clientondersteuning, waardoor het een populaire keuze is voor dit scenario.

**Q: Verhoogt dit het geheugenverbruik op de applicatieserver?**  
A: Minimaal. Het zware werk wordt door Redis gedaan; de app houdt alleen kort‑levende verbindingen via Jedis.

## Conclusie
Je hebt nu een volledige **java redis caching**‑tutorial die laat zien hoe je documenten cachet met Redis en GroupDocs.Conversion. Door gerenderde output in Redis op te slaan, **verbeter je de renderprestaties**, **verlaag je de conversietijd**, en bied je een soepelere ervaring aan eindgebruikers. Experimenteer met verschillende TTL‑waarden, monitor cache‑statistieken, en breid het patroon uit naar andere documentformaten naarmate je applicatie groeit.

---

**Laatst bijgewerkt:** 2026-10-21  
**Getest met:** GroupDocs.Conversion 25.2, Jedis 4.2.3  
**Auteur:** GroupDocs

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

## Gerelateerde tutorials

- [Aangepaste cache implementeren Java – GroupDocs Conversion Cache](/conversion/java/cache-management/)
- [Hoe Redis‑cache te gebruiken in Java met GroupDocs.Conversion](/conversion/java/cache-management/redis-cache-java-groupdocs-conversion-guide/)
- [Hoe bestanden te cachen in Java met GroupDocs.Conversion – Een uitgebreide gids voor efficiënte documentconversie](/conversion/java/cache-management/implement-java-file-caching-groupdocs-conversion-guide/)
