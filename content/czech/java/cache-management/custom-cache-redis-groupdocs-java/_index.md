---
date: '2026-07-19'
description: Objevte krok‑za‑krokem návod na java redis caching, který integruje Redis
  s GroupDocs.Conversion a zvyšuje výkon vykreslování, snižuje dobu konverze a zjednodušuje
  správu mezipaměti.
keywords:
- java redis caching
- boost rendering performance
- configure redis ttl
- reduce conversion time
- cache documents java
lastmod: '2026-07-19'
og_description: Naučte se java redis caching s GroupDocs.Conversion. Tento návod ukazuje,
  jak zvýšit výkon vykreslování, snížit dobu konverze a nastavit Redis TTL v jednoduchém
  projektu v Javě.
og_image_alt: 'Guide: java redis caching with GroupDocs and Redis'
og_title: java redis caching – ukládání dokumentů do mezipaměti v Javě s Redis
schemas:
- author: GroupDocs
  dateModified: '2026-07-19'
  description: Discover a step‑by‑step java redis caching tutorial that integrates
    Redis with GroupDocs.Conversion to boost rendering performance, reduce conversion
    time, and simplify cache management.
  headline: 'java redis caching: Cache Docs in Java with Redis'
  type: TechArticle
- description: Discover a step‑by‑step java redis caching tutorial that integrates
    Redis with GroupDocs.Conversion to boost rendering performance, reduce conversion
    time, and simplify cache management.
  name: 'java redis caching: Cache Docs in Java with Redis'
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
- java redis cache
- GroupDocs.Conversion
- document rendering
- performance optimization
title: 'java redis caching: ukládání dokumentů do mezipaměti v Javě s Redis'
type: docs
url: /cs/java/cache-management/custom-cache-redis-groupdocs-java/
weight: 1
---

# java redis caching: Ukládání dokumentů v Javě s Redis

V moderních webových aplikacích může opakované poskytování stejného převedeného dokumentu plýtvat cykly CPU a prodlužovat dobu odezvy. **java redis caching** řeší tento problém ukládáním výstupu konverze do rychlého, paměťového úložiště, takže následné požadavky jsou obslouženy okamžitě. V tomto tutoriálu se naučíte, jak propojit Redis s workflow GroupDocs.Conversion, nakonfigurovat TTL a změřit očekávané výkonnostní zisky.

## Rychlé odpovědi
- **Co tento tutoriál pokrývá?** Kompletní java redis caching tutoriál, který integruje Redis s GroupDocs.Conversion.  
- **Proč používat Redis?** Poskytuje submilisekundovou latenci, podporuje expiraci TTL a horizontálně škáluje napříč více instancemi aplikace.  
- **Potřebuji licenci GroupDocs?** Zkušební nebo dočasná licence stačí pro testování; plná licence je vyžadována pro produkční nasazení.  
- **Jaké jsou hlavní kroky?** Přidejte Maven závislosti, nakonfigurujte `JedisPool`, vytvořte pomocné metody pro mezipaměť a zapojte mezipaměť do konverzního pipeline.  
- **Která verze Javy je podporována?** Java 8+ (kompatibilní s nejnovějšími verzemi GroupDocs.Conversion).

## Co je cachování dokumentů s Redis?
Cachování dokumentů s Redis znamená ukládání binárního výstupu konverze (např. pole bajtů PDF) do Redis, aby identické budoucí požadavky mohly získat uložené bajty místo opětovného spuštění konverzního enginu. To eliminuje nadbytečnou práci CPU, snižuje síťovou šířku pásma a poskytuje plynulejší uživatelský zážitek.

## Proč implementovat Redis cache v Javě?
Načtěte dokument jednou, uložte výsledek a při opakovaných požadavcích jej obsloužte okamžitě. Cachování založené na Redis může **zkrátit dobu konverze až o 90 %** pro často přistupované soubory, **snížit náklady na infrastrukturu** snížením využití CPU a **poskytnout jediný zdroj pravdy** pro všechny uzly aplikace v klastrovém prostředí.

## Předpoklady
- **GroupDocs.Conversion** – verze 25.2 nebo novější (podporuje **120+** vstupních a výstupních formátů).  
- **Jedis** (oficiální Redis klient pro Javu).  
- Běžící instance Redis (lokální vývoj může použít výchozí `localhost:6379`).  
- Maven pro správu závislostí.  
- Základní znalost zpracování výjimek v Javě a I/O streamů.

## Nastavení GroupDocs.Conversion pro Javu

`GroupDocs.Conversion` je Java knihovna, která převádí a renderuje dokumenty do široké škály formátů, automaticky zachovává rozvržení, vkládá fonty a extrahuje obrázky.

Přidejte repozitář GroupDocs a závislost do vašeho `pom.xml`:

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

### Získání licence
Můžete začít s **Free Trial**, požádat o **Temporary License** pro vyhodnocení, nebo zakoupit plnou **License** pro produkční použití.

Inicializujte GroupDocs.Conversion ve vašem Java kódu:

```java
import com.groupdocs.conversion.*;

ConversionConfig config = new ConversionConfig();
config.setLicensePath("path/to/license/file.lic");
ConversionApi conversionApi = new ConversionApi(config);
```

## Průvodce implementací

### Vytvoření vlastního cache pomocí Redis

#### Přehled
Vlastní Redis cache uchovává bajty renderovaného dokumentu, což umožňuje okamžité načtení při opakovaných požadavcích.

#### Nastavení JedisPool
`JedisPool` je vlákny‑bezpečný pool opakovaně použitelných Redis spojení, který minimalizuje režii socketů a zvyšuje propustnost.

```java
import redis.clients.jedis.JedisPool;
import redis.clients.jedis.JedisPoolConfig;

JedisPoolConfig poolConfig = new JedisPoolConfig();
poolConfig.setMaxTotal(20);               // maximum active connections
poolConfig.setMaxIdle(10);                // maximum idle connections
poolConfig.setMinIdle(2);                 // minimum idle connections
JedisPool jedisPool = new JedisPool(poolConfig, "localhost", 6379);
```

#### Ukládání a načítání cachovaných dat
Níže uvedené pomocné metody serializují pole bajtů do Base64 řetězce pro bezpečné uložení a načtou jej zpět do pole bajtů.

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

#### Integrace s GroupDocs.Conversion
Nyní propojte cache s konverzním workflow. Metoda nejprve kontroluje cache; pokud dojde k minutu, provede konverzi, uloží výsledek a vrátí bajty.

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

## Jak implementovat java redis caching?
`ConversionApi` je hlavní třída v GroupDocs.Conversion, která provádí operace konverze dokumentů.

Načtěte svůj zdrojový dokument, vygenerujte deterministický klíč cache, vyhledejte jej v Redis a `ConversionApi` zavolejte pouze když klíč chybí. Tento vzor zaručuje, že každá unikátní konverze je provedena jednou a poté obsloužena z cache po dobu nastaveného TTL.

## Tipy pro řešení problémů
- Ověřte, že Redis server je dostupný (`redis-cli ping` by měl vrátit `PONG`).  
- Ujistěte se, že host a port `JedisPool` odpovídají vašemu nasazení Redis.  
- Zabalte volání cache do try‑catch bloků, aby se zvládly výpadky připojení bez přerušení konverzního toku.  
- Sledujte paměť Redis (`INFO memory`) a nastavte politiky `maxmemory` (např. `volatile-lru`) pro elegantní odstraňování starých položek.  
- Pokud narazíte na `OutOfMemoryError` na JVM, zvětšete velikost haldy nebo povolte `-XX:+UseCompressedOops`.

## Praktické aplikace
1. **Portály s vysokým provozem** – Okamžitě poskytujte často požadované PDF (katalogy, bílé knihy).  
2. **Enterprise DMS** – Snižte zátěž, když uživatelé opakovaně prohlížejí stejné smlouvy nebo dokumenty politik.  
3. **E‑commerce** – Cachujte generované faktury nebo produktové katalogy pro urychlení pokladny.  
4. **Vzdělávací platformy** – Dodávejte přednáškové materiály a e‑knihy bez opětovného renderování při každém požadavku studenta.  
5. **Právní služby** – Zrychlete distribuci soudních spisů při nízkých nákladech na úložiště.

## Úvahy o výkonu
- **Ladění Redis** – Upravte `maxmemory`, zvolte politiku vyřazení jako `allkeys-lru` a nastavte vhodné hodnoty `timeout` podle vašeho provozního vzoru.  
- **Sledování poměru hit/miss cache** – Použijte `INFO stats` nebo počítadla Redis `keyspace_hits` / `keyspace_misses` pro jemné ladění TTL.  
- **Velikost haldy JVM** – Zajistěte, aby halda pojmula buffery GroupDocs; obecně se doporučuje 1 GB haldy na každých 100 MB souběžného konverzního zatížení.  
- **Dávkové konverze** – Při konverzi mnoha souborů znovu použijte jednu instanci `Jedis` na vlákno, aby se minimalizovalo přepínání socketů.

## Často kladené otázky
**Q: Mohu tento přístup použít s jinými výstupními formáty GroupDocs?**  
A: Rozhodně. Stejný vzor cachování funguje pro DOCX, HTML, obrázky a další – stačí změnit typ `ConvertOptions`.

**Q: Jak vybrat dobrý klíč cache?**  
A: Kombinujte cestu ke zdrojovému souboru, možnosti konverze a jakékoli identifikátory verze. To zaručuje jedinečnost pro každou konfiguraci.

**Q: Co když se dokument změní po jeho uložení do cache?**  
A: Invalidejte cache ručně (např. smažte klíč) nebo použijte kratší TTL, aby zastaralá data rychle vypršela.

**Q: Je Redis jedinou možností pro cachování?**  
A: Ne, ale Redis nabízí nízkou latenci, vestavěné TTL a širokou podporu Java klientů, což z něj dělá oblíbenou volbu pro tento scénář.

**Q: Zvyšuje to využití paměti na aplikačním serveru?**  
A: Minimální. Těžkou práci provádí Redis; aplikace drží jen krátkodobé spojení přes Jedis.

## Závěr
Nyní máte kompletní **java redis caching** tutoriál, který ukazuje, jak cachovat dokumenty pomocí Redis a GroupDocs.Conversion. Ukládáním renderovaného výstupu do Redis **zvýšíte výkon renderování**, **zkrátíte dobu konverze** a poskytnete plynulejší zážitek koncovým uživatelům. Experimentujte s různými hodnotami TTL, sledujte metriky cache a rozšiřujte vzor na další formáty dokumentů, jak vaše aplikace roste.

---

**Poslední aktualizace:** 2026-07-19  
**Testováno s:** GroupDocs.Conversion 25.2, Jedis 4.2.3  
**Autor:** GroupDocs

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

## Související tutoriály

- [Implementace vlastního cache v Javě – GroupDocs Conversion Cache](/conversion/java/cache-management/)
- [Jak použít Redis cache v Javě s GroupDocs.Conversion](/conversion/java/cache-management/redis-cache-java-groupdocs-conversion-guide/)
- [Jak cachovat soubory v Javě s GroupDocs.Conversion – Kompletní průvodce pro efektivní konverzi dokumentů](/conversion/java/cache-management/implement-java-file-caching-groupdocs-conversion-guide/)