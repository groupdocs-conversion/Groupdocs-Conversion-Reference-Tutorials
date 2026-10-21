---
date: '2026-10-21'
description: Dowiedz się, jak utworzyć cache key Java i zintegrować Redis z GroupDocs.Conversion,
  aby zwiększyć rendering performance, skrócić conversion time oraz skonfigurować
  TTLs w prostym projekcie Java.
images:
- /java/cache-management/custom-cache-redis-groupdocs-java/og-image.png
keywords:
- create cache key java
- java redis caching
- groupdocs conversion cache
- redis ttl java
lastmod: '2026-10-21'
og_description: Utwórz cache key Java w tym przewodniku krok po kroku, który pokazuje,
  jak zintegrować Redis z GroupDocs.Conversion, aby cache'ować bajty dokumentu, zwiększyć
  rendering performance i skrócić conversion time. Skonfiguruj TTLs i zmierz przyrosty
  prędkości.
og_image_alt: 'Developer guide: create cache key Java using Redis and GroupDocs'
og_title: Utwórz cache key Java – cache docs z Redis i GroupDocs
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
title: Utwórz cache key Java – cache docs w Java z Redis
type: docs
url: /pl/java/cache-management/custom-cache-redis-groupdocs-java/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz klucz pamięci podręcznej Java – buforuj dokumenty w Javie przy użyciu Redis

W nowoczesnych aplikacjach internetowych serwowanie tego samego przetworzonego dokumentu wielokrotnie może marnować cykle CPU i wydłużać czasy odpowiedzi. **Tworzenie klucza pamięci podręcznej w Javie** pozwala przechowywać wynik konwersji raz i natychmiast go pobierać przy kolejnych żądaniach. Ten tutorial pokazuje, jak podłączyć Redis do przepływu pracy GroupDocs.Conversion, generować niezawodne klucze pamięci podręcznej, konfigurować TTL oraz mierzyć oczekiwane zyski wydajnościowe.

## Szybkie odpowiedzi
- **Co obejmuje ten tutorial?** Kompletny tutorial dotyczący buforowania java redis, który integruje Redis z GroupDocs.Conversion.  
- **Dlaczego używać Redis?** Zapewnia opóźnienie poniżej milisekundy, obsługuje wygasanie TTL i skaluje się poziomo na wiele instancji aplikacji.  
- **Czy potrzebuję licencji GroupDocs?** Licencja próbna lub tymczasowa wystarczy do testów; pełna licencja jest wymagana w środowiskach produkcyjnych.  
- **Jakie są główne kroki?** Dodaj zależności Maven, skonfiguruj `JedisPool`, zbuduj metody pomocnicze pamięci podręcznej i podłącz pamięć podręczną do potoku konwersji.  
- **Która wersja Javy jest wspierana?** Java 8+ (kompatybilna z najnowszymi wydaniami GroupDocs.Conversion).

## Czym jest buforowanie dokumentów przy użyciu Redis?
Buforowanie dokumentów przy użyciu Redis oznacza przechowywanie binarnego wyniku konwersji (np. tablicy bajtów PDF) w Redis, tak aby identyczne przyszłe żądania mogły pobrać zapisane bajty zamiast ponownie uruchamiać silnik konwersji. Eliminuje to zbędną pracę CPU, zmniejsza zużycie pasma sieciowego i zapewnia płynniejsze doświadczenie końcowego użytkownika.

## Dlaczego wdrożyć pamięć podręczną Redis w Javie?
Załadowanie dokumentu raz, zapisanie wyniku i natychmiastowe serwowanie przy kolejnych żądaniach może **skrócić czas konwersji nawet o 90 %** dla często używanych plików, **obniżyć koszty infrastruktury** poprzez zmniejszenie zużycia CPU oraz **zapewnić jedyne źródło prawdy** dla wszystkich węzłów aplikacji w środowisku klastrowym. Redis potrafi przetworzyć ponad 200 k operacji na sekundę na jednym węźle, gwarantując pod-milisekundowe wyszukiwania.

## Wymagania wstępne
- **GroupDocs.Conversion** – wersja 25.2 lub nowsza (obsługuje **120+** formatów wejściowych i wyjściowych).  
- **Jedis** (oficjalny klient Redis dla Javy).  
- Działająca instancja Redis (lokalne środowisko deweloperskie może używać domyślnego `localhost:6379`).  
- Maven do zarządzania zależnościami.  
- Podstawowa znajomość obsługi wyjątków w Javie oraz strumieni I/O.

## Konfiguracja GroupDocs.Conversion dla Javy

`GroupDocs.Conversion` to biblioteka Java, która konwertuje i renderuje dokumenty do szerokiego zakresu formatów, automatycznie zachowując układ, osadzając czcionki i wyodrębniając obrazy.

Add the GroupDocs repository and dependency to your `pom.xml`:

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

### Uzyskanie licencji
Możesz rozpocząć od **Free Trial**, poprosić o **Temporary License** w celu oceny lub zakupić pełną **License** do użytku produkcyjnego.

Initialize GroupDocs.Conversion in your Java code:

```java
import com.groupdocs.conversion.*;

ConversionConfig config = new ConversionConfig();
config.setLicensePath("path/to/license/file.lic");
ConversionApi conversionApi = new ConversionApi(config);
```

## Przewodnik implementacji

### Tworzenie własnej pamięci podręcznej przy użyciu Redis

#### Przegląd
Własna pamięć podręczna Redis przechowuje bajty wyrenderowanego dokumentu, umożliwiając natychmiastowe pobranie przy kolejnych żądaniach.

#### Konfiguracja JedisPool
JedisPool to wątkowo‑bezpieczna pula wielokrotnego użytku połączeń Redis, która minimalizuje narzut socketów i zwiększa przepustowość.

```java
import redis.clients.jedis.JedisPool;
import redis.clients.jedis.JedisPoolConfig;

JedisPoolConfig poolConfig = new JedisPoolConfig();
poolConfig.setMaxTotal(20);               // maximum active connections
poolConfig.setMaxIdle(10);                // maximum idle connections
poolConfig.setMinIdle(2);                 // minimum idle connections
JedisPool jedisPool = new JedisPool(poolConfig, "localhost", 6379);
```

#### Przechowywanie i pobieranie danych z pamięci podręcznej
Poniższe metody pomocnicze serializują tablicę bajtów do ciągu Base64 w celu bezpiecznego przechowywania i odczytują ją z powrotem do tablicy bajtów.

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

#### Integracja z GroupDocs.Conversion
Teraz podłącz pamięć podręczną do przepływu pracy konwersji. Metoda najpierw sprawdza pamięć podręczną; w przypadku braku trafienia wykonuje konwersję, zapisuje wynik i zwraca bajty.

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

## Jak utworzyć klucz pamięci podręcznej w Javie dla buforowania Redis?
Wygeneruj deterministyczny klucz, łącząc ścieżkę pliku źródłowego, wybrane wartości `ConvertOptions` oraz opcjonalny znacznik wersji, a następnie zahashuj ciąg przy użyciu SHA‑256. Ten klucz jednoznacznie identyfikuje każdą konfigurację konwersji, zapewniając, że identyczne żądania trafiają do pamięci podręcznej, a różne opcje generują odrębne wpisy.

Klasa `ConversionApi` jest podstawowym komponentem w GroupDocs.Conversion, który wykonuje konwersje dokumentów. Możesz utworzyć klucz pamięci podręcznej, odszukać go w Redis i wywołać `ConversionApi.convert` tylko wtedy, gdy klucz nie istnieje, co dramatycznie skraca czas konwersji i obciążenie serwera.

## Jak zaimplementować buforowanie Redis w Javie?
`ConversionApi` jest główną klasą w GroupDocs.Conversion, realizującą operacje konwersji dokumentów. Załaduj dokument źródłowy, wygeneruj deterministyczny klucz pamięci podręcznej, odszukaj go w Redis i wywołaj `ConversionApi` tylko wtedy, gdy klucz jest nieobecny. Ten wzorzec gwarantuje, że każda unikalna konwersja jest wykonywana raz, a następnie serwowana z pamięci podręcznej przez czas określony w TTL.

## Wskazówki rozwiązywania problemów
- Sprawdź, czy serwer Redis jest dostępny (`redis-cli ping` powinien zwrócić `PONG`).  
- Upewnij się, że host i port `JedisPool` odpowiadają Twojej instalacji Redis.  
- Otaczaj wywołania pamięci podręcznej blokami try‑catch, aby obsłużyć problemy z połączeniem bez przerywania procesu konwersji.  
- Monitoruj pamięć Redis (`INFO memory`) i ustaw polityki `maxmemory` (np. `volatile-lru`), aby łagodnie usuwać stare wpisy.  
- Jeśli napotkasz `OutOfMemoryError` w JVM, zwiększ rozmiar sterty lub włącz `-XX:+UseCompressedOops`.

## Praktyczne zastosowania

1. **Portale o dużym ruchu** – Natychmiastowo serwuj często żądane PDF-y (katalogi, białe księgi).  
2. **Enterprise DMS** – Zmniejsz obciążenie, gdy użytkownicy wielokrotnie przeglądają te same umowy lub dokumenty polityk.  
3. **E‑commerce** – Buforuj generowane faktury lub katalogi produktów, aby przyspieszyć proces zakupowy.  
4. **Platformy edukacyjne** – Dostarczaj notatki z wykładów i e‑książki bez ponownego renderowania przy każdym żądaniu studenta.  
5. **Usługi prawne** – Przyspiesz dystrybucję akt spraw, jednocześnie utrzymując niskie koszty przechowywania.

## Rozważania dotyczące wydajności

- **Dostosuj Redis** – Dostosuj `maxmemory`, wybierz politykę usuwania, taką jak `allkeys-lru`, i ustaw odpowiednie wartości `timeout` w zależności od wzorca ruchu.  
- **Śledź współczynniki trafień/odrzuceń pamięci podręcznej** – Użyj `INFO stats` lub liczników `keyspace_hits` / `keyspace_misses` Redis, aby precyzyjnie dostroić TTL.  
- **Rozmiar sterty JVM** – Upewnij się, że sterta może pomieścić bufory GroupDocs; ogólna zasada to 1 GB sterty na każde 100 MB jednoczesnego ładunku konwersji.  
- **Konwersje wsadowe** – Przy konwersji wielu plików, ponownie używaj jednej instancji `Jedis` na wątek, aby zminimalizować obciążenie socketów.

## Najczęściej zadawane pytania

**Q: Czy mogę używać tego podejścia z innymi formatami wyjściowymi GroupDocs?**  
A: Oczywiście. Ten sam wzorzec buforowania działa dla DOCX, HTML, obrazów i innych – wystarczy zmienić typ `ConvertOptions`.

**Q: Jak wybrać dobry klucz pamięci podręcznej?**  
A: Połącz ścieżkę pliku źródłowego, opcje konwersji oraz ewentualne identyfikatory wersji. To zapewnia unikalność dla każdej konfiguracji.

**Q: Co się stanie, jeśli dokument zmieni się po zapisaniu w pamięci podręcznej?**  
A: Inwaliduj pamięć podręczną ręcznie (np. usuń klucz) lub użyj krótszego TTL, aby przestarzałe dane szybko wygasły.

**Q: Czy Redis jest jedyną opcją buforowania?**  
A: Nie, ale Redis oferuje niskie opóźnienia, wbudowane TTL i szerokie wsparcie klientów Java, co czyni go popularnym wyborem w tym scenariuszu.

**Q: Czy to zwiększa zużycie pamięci na serwerze aplikacji?**  
A: Minimalnie. Największe obciążenie spoczywa na Redis; aplikacja utrzymuje jedynie krótkotrwałe połączenia przez Jedis.

## Podsumowanie
Masz teraz kompletny **java redis caching** tutorial, który pokazuje, jak buforować dokumenty przy użyciu Redis i GroupDocs.Conversion. Przechowując wyrenderowany wynik w Redis, **zwiększysz wydajność renderowania**, **skracasz czas konwersji** i zapewnisz płynniejsze doświadczenie użytkownikom końcowym. Eksperymentuj z różnymi wartościami TTL, monitoruj metryki pamięci podręcznej i rozszerz wzorzec na inne formaty dokumentów w miarę rozwoju aplikacji.

---

**Last Updated:** 2026-10-21  
**Tested With:** GroupDocs.Conversion 25.2, Jedis 4.2.3  
**Author:** GroupDocs

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

## Powiązane tutoriale

- [Implementacja własnej pamięci podręcznej Java – pamięć podręczna GroupDocs Conversion](/conversion/java/cache-management/)
- [Jak używać pamięci podręcznej Redis w Javie z GroupDocs.Conversion](/conversion/java/cache-management/redis-cache-java-groupdocs-conversion-guide/)
- [Jak buforować pliki w Javie z GroupDocs.Conversion – Kompletny przewodnik po efektywnej konwersji dokumentów](/conversion/java/cache-management/implement-java-file-caching-groupdocs-conversion-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}