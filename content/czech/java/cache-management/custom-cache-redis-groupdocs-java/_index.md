---
date: '2026-01-23'
description: Naučte se, jak ukládat dokumenty do mezipaměti v Javě pomocí implementace
  Redis cache s GroupDocs.Conversion. Zvyšte výkon vykreslování a zlepšete efektivitu.
keywords:
- Custom Caching Java
- GroupDocs.Conversion Java
- Redis Cache Implementation
title: Jak cachovat dokumenty v Javě pomocí Redis a GroupDocs
type: docs
url: /cs/java/cache-management/custom-cache-redis-groupdocs-java/
weight: 1
---

 cachovat renderování dokumentů, dobře navržená cache může dramaticky zkrátit dobu zpracování. V tomto tutoriálu projdeme kompletní **java redis cache tutorial**, který integruje Redis s GroupDocs.Conversion a pomůže vám **zvýšit výkon renderování** pro PDF, DOCX a další formáty.

## Rychlé odpovědi
- **Co tento tutoriál pokrývá?** Implementaci cache na bázi Redis pro GroupDocs.Conversion v Javě.  
- **Proč použít Redis?** Nabízí rychlé úložiště v paměti, podporu TTL a snadnou škálovatelnost.  
- **Potřebuji licenci GroupDocs?** Zkušební nebo dočasná licence stačí pro testování; plná licence je vyžadována pro produkci.  
- **Jaké jsou hlavní kroky?** Nastavit Maven závislosti, nakonfigurovat Jedis, vytvořit pomocníky cache a integrovat cachování do toku konverze pomocí Redis?
Cachování ukládá výstup konverze dokumentu (např. vygenerované PDF) do Redis, takže následné požadavky na stejný zdrojový soubor mohou být obslouženy okamžitě bez opětovného zpracování. Tím se snižuje zatížení CPU, síťový provoz a zlepšuje se zkušenost koncového uživatele.

## Proč implementovat Redis cache v Javě?
- **Zvýšit výkon renderování** vyhnutím se duplicitním konverzím.  
-aní vy 25.2 nebo novější.  
- **Jedis** (Redis klient pro Javu).  
- Běžící Redis server (localhost je v pořádku pro vývoj).  
- Maven pro správu závislostí.  
- Základní znalost Javy a povědomí o konceptech konverze dokumentů.

## Nastavení GroupDocs.Conversion pro Javu

Přidejte repozitář GroupDocs a závislost do vašeho `pom.xml`:

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

### Získání** pro GroupDocs.Conversion ve vašem Java kódu:

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

## Průvodce implementací

### Vytvoření vlastního cache pomocí Redis

#### Přehled
Vlastní Redis cache uchovává bajty renderovaného dokumentu, což umožňuje okamžité načtení při opakovaných požadavcích.

#### Nastavení JedisPool
Nejprve vytvořte pool připojení pro efektivní správu Redis spojení:

```java
import redis.clients.jedis.JedisPool;

public class CacheManager {
    private static JedisPool jedisPool = new JedisPool("localhost", 6379);
    
    public static void main(String[] args) {
        // Additional cache setup code here
    }
}
```

#### Ukládání a načítání cachovaných dat
Použijte jednoduché pomocné metody pro vložení a získání dokumentů z Redis:

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

#### Integrace s GroupDocs.Conversion
Nyní propojte cache s workflow konverze:

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

### Tipy pro řešení problémů
- Ověřte, že je Redis server dosažitelný (`ping` z hostitele).  
- Potvrďte, že host/port `JedisPool` odpovídá vaší Redis instanci.  
- Zabalte volání cache do try‑catch bloků, aby se elegantně řešily problémy s konektivitou.  
- Sledujte využití paměti Redis; zvažte politiky `maxmemory` pro produkci.

## Praktické aplikace

1. **Portály s vysokým provozem** – Okamžitě poskytovat často požadovaná PDF.  
2. **Enterprise DMS** – Snížit zatížení konverzních serverů, když uživatelé opakovaně prohlížejí stejné smlouvy.  
3. **E‑commerce** – Cachovat generované faktury nebo produktové katalogy.  
4. **Vzdělávací platformy** – Zrychlit doručování přednáškových materiálů a e‑knih.  
5. **Právní služby** – Zrychlit distribuci soudních spisů při nízkých nákladech na úložiště.

## Úvahy o výkonu

- **Ladění Redis** – Upravte `maxmemory`, `eviction-policy` a nastavení timeoutu podle vašeho zatížení.  
- **Sledování poměru hit/miss cache** – Použijte statistiky Redis `INFO` pro jemné doladění TTL klíčů.  
- **Velikost haldy JVM** – Zajistěte, aby halda pojmula konverzní knihovnu plus případné v‑procesu buffery.

## Často kladené otázky

**Q: Můžu tento přístup použít s jinými výstupními formáty GroupDocs?**  
A: Rozhodně. Stejný vzor cachování funguje pro DOCX, HTML, obrázky a další – stačí změnit typ `ConvertOptions`.

**Q: Jak si vybrat dobrý klíč cache?**  
A: Kombinujte cestu ke zdrojovému souboruné identifikění po jeho uložení do cache?**  
A: Invalidejte cache ručně (např. smazáním klíče) nebo použijte kratší TTL, aby zastaralá data rychle vypršela.

**Q: Je Redis jedinou možností pro cachování?**  
A: Ne, ale Redis nabízí nízkou latenci, vestavěné TTL a širokou podporu Java klientů, což z něj dělá populární volbu pro tento scénář.

**Q: Zvyšuje to využití paměti na aplikačním serveru?**  
A: Minimální. Náročná část je prováděna Redis; aplikace drží jen krátkodobá spojení přes Jedis.

## Závěr

Nyní máte kompletní **java redis cache tutorial**, který ukazuje **jak cachovat dokumenty** pomocí Redis a GroupDocs.Conversion. Ukládáním renderovaného výstupu do Redis **zvýšíte výkon renderování**, snížíte zatížení serveru a poskytnete uživatelům plynulejší zážitek. Experimentujte s různými hodnotami TTL, sledujte metriky cache a podle potřeby rozšiřte vzor na další formáty dokumentů.

---

**Poslední aktualizace:** 2026-01-23  
**Testováno s:** GroupDocs.Conversion 25.2, Jedis 4.2  
**Autor:** GroupDocs  

---