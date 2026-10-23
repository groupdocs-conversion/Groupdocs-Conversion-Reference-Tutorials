---
date: '2026-10-21'
description: Ismerje meg, hogyan hozhat létre cache kulcsot Java-ban, és integrálhatja
  a Redis-t a GroupDocs.Conversion-nel a renderelési teljesítmény növelése, a konverziós
  idő csökkentése és a TTL-ek egyszerű Java projektben történő konfigurálása érdekében.
images:
- /java/cache-management/custom-cache-redis-groupdocs-java/og-image.png
keywords:
- create cache key java
- java redis caching
- groupdocs conversion cache
- redis ttl java
lastmod: '2026-10-21'
og_description: Lépésről‑lépésre útmutató, amely bemutatja, hogyan hozhat létre cache
  kulcsot Java-ban, és integrálhatja a Redis-t a GroupDocs.Conversion-nel a dokumentum
  bájtok gyorsítótárazásához, a renderelési teljesítmény növeléséhez és a konverziós
  idő csökkentéséhez. Állítsa be a TTL-eket, és mérje a sebességnyereséget.
og_image_alt: 'Developer guide: create cache key Java using Redis and GroupDocs'
og_title: Cache kulcs létrehozása Java-ban – dokumentumok gyorsítótárazása a Redis-szel
  és a GroupDocs-szal
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
title: Cache kulcs létrehozása Java-ban – dokumentumok gyorsítótárazása Java-ban a
  Redis-szel
type: docs
url: /hu/java/cache-management/custom-cache-redis-groupdocs-java/
weight: 1
---

# Cache kulcs létrehozása Java-ban – dokumentumok gyorsítótárazása Java-ban Redis-szel

A modern webalkalmazásokban ugyanazon átalakított dokumentum ismételt kiszolgálása CPU-ciklusokat pazarolhat és megnövelheti a válaszidőket. **Cache kulcs létrehozása Java-ban** lehetővé teszi, hogy a konverziós kimenetet egyszer tároljuk, és a későbbi kérések során azonnal lekérjük. Ez a bemutató megmutatja, hogyan lehet a Redis-t beilleszteni egy GroupDocs.Conversion munkafolyamatba, megbízható cache kulcsokat generálni, TTL-eket konfigurálni, és mérni a várható teljesítményjavulást.

## Gyors válaszok
- **Mi a bemutató témája?** Egy teljes java redis gyorsítótárazási bemutató, amely integrálja a Redis-t a GroupDocs.Conversion-nel.  
- **Miért használjuk a Redis-t?** Alacsony alá‑ezredmásodperces késleltetést biztosít, támogatja a TTL lejáratot, és vízszintesen skálázható több alkalmazáspéldány között.  
- **Szükségem van GroupDocs licencre?** Egy próba vagy ideiglenes licenc elegendő a teszteléshez; egy teljes licenc szükséges a termelési környezethez.  
- **Mik a fő lépések?** Adja hozzá a Maven függőségeket, konfiguráljon egy `JedisPool`-t, építsen cache segédfüggvényeket, és csatlakoztassa a gyorsítótárat a konverziós csővezetékhez.  
- **Mely Java verzió támogatott?** Java 8+ (kompatibilis a legújabb GroupDocs.Conversion kiadásokkal).

## Mi a dokumentumok gyorsítótárazása Redis-szel?
A dokumentumok Redis-szel történő gyorsítótárazása azt jelenti, hogy a konverzió bináris kimenetét (például egy PDF bájt tömböt) a Redis-ben tároljuk, így az azonos jövőbeli kérések a gyorsítótárazott bájtokat kérhetik le a konverziós motor újrafuttatása helyett. Ez megszünteti a felesleges CPU munkát, csökkenti a hálózati sávszélességet, és simább felhasználói élményt biztosít.

## Miért valósítsuk meg a Redis gyorsítótárat Java-ban?
Egy dokumentum egyszeri betöltése, az eredmény tárolása, és az ismételt kérések során azonnali kiszolgálása **akár 90 %-kal csökkentheti a konverziós időt** gyakran elért fájlok esetén, **csökkentheti az infrastruktúra költségeit** a CPU használat csökkentésével, és **egységes forrást biztosít** az összes alkalmazáscsomópont számára egy klaszter környezetben. A Redis egyetlen csomóponton másodpercenként több mint 200 e műveletet képes feldolgozni, garantálva az alá‑ezredmásodperces lekérdezéseket.

## Előkövetelmények
- **GroupDocs.Conversion** – 25.2 vagy újabb verzió (támogatja a **120+** bemeneti és kimeneti formátumot).  
- **Jedis** (a hivatalos Redis kliens Java-hoz).  
- Futó Redis példány (helyi fejlesztéshez használható az alapértelmezett `localhost:6379`).  
- Maven a függőségkezeléshez.  
- Alapvető ismeretek a Java kivételkezelésről és I/O streamekről.

## A GroupDocs.Conversion beállítása Java-hoz

`GroupDocs.Conversion` egy Java könyvtár, amely dokumentumokat konvertál és renderel számos formátumba, automatikusan megőrizve az elrendezést, beágyazva a betűtípusokat és kivonva a képeket.

Adja hozzá a GroupDocs tárolót és függőséget a `pom.xml`-hez:

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

### Licenc beszerzése
Kezdhet **Ingyenes Próbaverzióval**, kérhet **Ideiglenes Licencet** értékeléshez, vagy vásárolhat teljes **Licencet** a termelési használathoz.

Inicializálja a GroupDocs.Conversion-t a Java kódjában:

```java
import com.groupdocs.conversion.*;

ConversionConfig config = new ConversionConfig();
config.setLicensePath("path/to/license/file.lic");
ConversionApi conversionApi = new ConversionApi(config);
```

## Implementációs útmutató

### Egyedi gyorsítótár létrehozása Redis-szel

#### Áttekintés
Egy egyedi Redis gyorsítótár tárolja a renderelt dokumentum bájtjait, lehetővé téve az azonnali lekérdezést ismételt kérések esetén.

#### JedisPool beállítása
A JedisPool egy szálbiztos újrahasználható Redis kapcsolatokból álló pool, amely minimalizálja a socket terhelést és javítja a áteresztőképességet.

```java
import redis.clients.jedis.JedisPool;
import redis.clients.jedis.JedisPoolConfig;

JedisPoolConfig poolConfig = new JedisPoolConfig();
poolConfig.setMaxTotal(20);               // maximum active connections
poolConfig.setMaxIdle(10);                // maximum idle connections
poolConfig.setMinIdle(2);                 // minimum idle connections
JedisPool jedisPool = new JedisPool(poolConfig, "localhost", 6379);
```

#### Gyorsítótárazott adatok tárolása és lekérése
Az alábbi segédfüggvények egy bájt tömböt Base64 karakterlánccá sorosítanak a biztonságos tárolás érdekében, majd visszaalakítják azt bájt tömbbé.

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

#### Integráció a GroupDocs.Conversion-nel
Most kapcsolja össze a gyorsítótárat a konverziós munkafolyammal. A metódus először ellenőrzi a gyorsítótárat; ha hiány van, végrehajtja a konverziót, tárolja az eredményt, és visszaadja a bájtokat.

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

## Hogyan hozható létre cache kulcs Java-ban Redis gyorsítótárazáshoz?
Generáljon determinisztikus kulcsot a forrásfájl útvonalának, a kiválasztott `ConvertOptions` értékeknek és egy opcionális verziócímkének összefűzésével, majd hash-elje a karakterláncot SHA‑256-tal. Ez a kulcs egyedileg azonosítja minden konverziós konfigurációt, biztosítva, hogy az azonos kérések a gyorsítótárat használják, míg a különböző opciók külön bejegyzéseket hoznak létre.

A `ConversionApi` osztály a GroupDocs.Conversion központi komponense, amely dokumentumkonverziókat hajt végre. Létrehozhat egy cache kulcsot, lekérdezheti azt a Redis-ben, és csak akkor hívja meg a `ConversionApi.convert` metódust, ha a kulcs hiányzik, ezzel drámaian csökkentve a konverziós időt és a szerver terhelését.

## Hogyan valósítsuk meg a Java Redis gyorsítótárazást?
`ConversionApi` a GroupDocs.Conversion elsődleges osztálya, amely dokumentumkonverziós műveleteket hajt végre. Töltse be a forrásdokumentumot, generáljon egy determinisztikus cache kulcsot, keresse meg a Redis-ben, és csak akkor hívja meg a `ConversionApi`-t, ha a kulcs hiányzik. Ez a minta garantálja, hogy minden egyedi konverzió egyszer történik meg, majd a konfigurált TTL időtartamára a gyorsítótárból szolgálja ki.

## Hibaelhárítási tippek
- Ellenőrizze, hogy a Redis szerver elérhető-e (`redis-cli ping`-nek `PONG`-t kell visszaadnia).  
- Győződjön meg róla, hogy a `JedisPool` host és port megegyezik a Redis telepítésével.  
- Csomagolja a gyorsítótár hívásokat try‑catch blokkokba, hogy a kapcsolódási problémákat kezelje anélkül, hogy megszakítaná a konverziós folyamatot.  
- Figyelje a Redis memóriahasználatát (`INFO memory`) és állítson be `maxmemory` szabályokat (pl. `volatile-lru`), hogy a régi bejegyzéseket elegánsan eldobja.  
- Ha `OutOfMemoryError`-t kap a JVM-en, növelje a heap méretét vagy engedélyezze a `-XX:+UseCompressedOops` opciót.

## Gyakorlati alkalmazások

- **Nagy forgalmú portálok** – Gyakran kért PDF-eket (katalógusok, fehér könyvek) szolgáljon ki azonnal.  
- **Vállalati DMS** – Csökkentse a terhelést, amikor a felhasználók ismételten ugyanazokat a szerződéseket vagy szabályzatdokumentumokat tekintik meg.  
- **E‑kereskedelem** – Gyorsítsa a fizetést azzal, hogy a generált számlákat vagy termékkatalógusokat gyorsítótárazza.  
- **Tanulási platformok** – Szállítson előadási jegyzeteket és e‑könyveket anélkül, hogy minden hallgatói kérésnél újra renderelné.  
- **Jogi szolgáltatások** – Gyorsítsa az ügyiratok terjesztését, miközben alacsonyan tartja a tárolási költségeket.

## Teljesítmény szempontok

- **Redis finomhangolása** – Állítsa be a `maxmemory`-t, válasszon eldobási szabályt, például `allkeys-lru`-t, és adja meg a megfelelő `timeout` értékeket a forgalmi mintája alapján.  
- **Cache találati/hiány arányok nyomon követése** – Használja a `INFO stats` vagy a Redis `keyspace_hits` / `keyspace_misses` számlálókat a TTL-ek finomhangolásához.  
- **JVM heap méretezése** – Győződjön meg róla, hogy a heap képes befogadni a GroupDocs puffereket; egy általános szabály, hogy 1 GB heap minden 100 MB egyidejű konverziós terheléshez.  
- **Kötegelt konverziók** – Sok fájl konvertálásakor használjon egyetlen `Jedis` példányt szálanként a socket terhelés minimalizálása érdekében.

## Gyakran ismételt kérdések

**Q: Használhatom ezt a megközelítést más GroupDocs kimeneti formátumokkal?**  
A: Természetesen. Ugyanaz a gyorsítótárazási minta működik DOCX, HTML, képek és egyéb formátumok esetén – csak módosítsa a `ConvertOptions` típust.

**Q: Hogyan válasszak jó cache kulcsot?**  
A: Kombinálja a forrásfájl útvonalát, a konverziós opciókat és bármilyen verzióazonosítót. Ez garantálja az egyediséget konfigurációnként.

**Q: Mi történik, ha egy dokumentum megváltozik a gyorsítótárazás után?**  
A: Érvénytelenítse a gyorsítótárat manuálisan (pl. törölje a kulcsot), vagy használjon rövidebb TTL-t, hogy a régi adatok gyorsan lejárjanak.

**Q: A Redis az egyetlen gyorsítótár lehetőség?**  
A: Nem, de a Redis alacsony késleltetést, beépített TTL-t és széles Java kliens támogatást kínál, így népszerű választás ebben a helyzetben.

**Q: Növeli ez a memóriahasználatot az alkalmazásszerveren?**  
A: Minimális. A nehéz munkát a Redis végzi; az alkalmazás csak rövid életű kapcsolatokat tart fenn a Jedis-en keresztül.

## Következtetés
Most már rendelkezik egy teljes **java redis gyorsítótárazási** bemutatóval, amely megmutatja, hogyan gyorsítótárazhat dokumentumokat a Redis és a GroupDocs.Conversion segítségével. A renderelt kimenet Redis-ben való tárolásával **növelni fogja a renderelés teljesítményét**, **csökkenteni fogja a konverziós időt**, és simább élményt nyújt a végfelhasználóknak. Kísérletezzen különböző TTL értékekkel, figyelje a gyorsítótár metrikákat, és bővítse a mintát más dokumentumformátumokra, ahogy az alkalmazása növekszik.

---

**Utolsó frissítés:** 2026-10-21  
**Tesztelve ezzel:** GroupDocs.Conversion 25.2, Jedis 4.2.3  
**Szerző:** GroupDocs

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

## Kapcsolódó bemutatók

- [Egyedi gyorsítótár implementálása Java-ban – GroupDocs Conversion Cache](/conversion/java/cache-management/)
- [Hogyan használjunk Redis gyorsítótárat Java-ban a GroupDocs.Conversion-nel](/conversion/java/cache-management/redis-cache-java-groupdocs-conversion-guide/)
- [Fájlok gyorsítótárazása Java-ban a GroupDocs.Conversion-nel – Átfogó útmutató a hatékony dokumentumkonverzióhoz](/conversion/java/cache-management/implement-java-file-caching-groupdocs-conversion-guide/)
