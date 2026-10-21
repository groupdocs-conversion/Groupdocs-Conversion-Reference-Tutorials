---
date: '2026-10-21'
description: Erfahren Sie, wie Sie cache key Java erstellen und Redis mit GroupDocs.Conversion
  integrieren, um die Rendering‑Performance zu steigern, die Konvertierungszeit zu
  verkürzen und TTLs in einem einfachen Java‑Projekt zu konfigurieren.
images:
- /java/cache-management/custom-cache-redis-groupdocs-java/og-image.png
keywords:
- create cache key java
- java redis caching
- groupdocs conversion cache
- redis ttl java
lastmod: '2026-10-21'
og_description: Erstellen Sie cache key Java in dieser Schritt‑für‑Schritt‑Anleitung,
  die zeigt, wie Redis mit GroupDocs.Conversion integriert wird, um Dokumentbytes
  zu cachen, die Rendering‑Performance zu steigern und die Konvertierungszeit zu verkürzen.
  Konfigurieren Sie TTLs und messen Sie Geschwindigkeitsgewinne.
og_image_alt: 'Developer guide: create cache key Java using Redis and GroupDocs'
og_title: Create cache key Java – cache docs mit Redis und GroupDocs
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
title: Create cache key Java – cache docs in Java mit Redis
type: docs
url: /de/java/cache-management/custom-cache-redis-groupdocs-java/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erstellen Sie einen Cache‑Schlüssel in Java – Dokumente in Java mit Redis cachen

In modernen Webanwendungen kann das wiederholte Bereitstellen desselben konvertierten Dokuments CPU‑Zyklen verschwenden und die Antwortzeiten erhöhen. **Erstellen eines Cache‑Schlüssels in Java** ermöglicht es, das Konvertierungsergebnis einmal zu speichern und bei nachfolgenden Anfragen sofort abzurufen. Dieses Tutorial zeigt, wie Redis in einen GroupDocs.Conversion‑Workflow eingebunden, zuverlässige Cache‑Schlüssel generiert, TTLs konfiguriert und die zu erwartenden Leistungsgewinne gemessen werden.

## Schnelle Antworten
- **Worum geht es in diesem Tutorial?** Ein vollständiges Java‑Redis‑Caching‑Tutorial, das Redis in GroupDocs.Conversion integriert.  
- **Warum Redis verwenden?** Es liefert Latenzzeiten im Sub‑Millisekunden‑Bereich, unterstützt TTL‑Ablauf und skaliert horizontal über mehrere Anwendungsinstanzen.  
- **Benötige ich eine GroupDocs‑Lizenz?** Eine Test‑ oder temporäre Lizenz ist für Tests ausreichend; für den Produktionseinsatz ist eine Voll‑Lizenz erforderlich.  
- **Was sind die Hauptschritte?** Maven‑Abhängigkeiten hinzufügen, einen `JedisPool` konfigurieren, Cache‑Hilfsmethoden erstellen und den Cache in die Konvertierungspipeline einbinden.  
- **Welche Java‑Version wird unterstützt?** Java 8+ (kompatibel mit den neuesten GroupDocs.Conversion‑Versionen).

## Was ist das Caching von Dokumenten mit Redis?
Caching von Dokumenten mit Redis bedeutet, die binäre Ausgabe einer Konvertierung (z. B. ein PDF‑Byte‑Array) in Redis zu speichern, sodass identische zukünftige Anfragen die zwischengespeicherten Bytes abrufen können, anstatt die Konvertierungs‑Engine erneut auszuführen. Dies eliminiert redundante CPU‑Arbeit, reduziert den Netzwerk‑Durchsatz und bietet ein reibungsloseres End‑User‑Erlebnis.

## Warum Redis‑Cache in Java implementieren?
Ein Dokument einmal zu laden, das Ergebnis zu speichern und bei wiederholten Zugriffen sofort bereitzustellen, kann die Konvertierungszeit für häufig genutzte Dateien um **bis zu 90 %** reduzieren, **die Infrastrukturkosten** senken, indem die CPU‑Auslastung verringert wird, und **eine einzige Quelle der Wahrheit** für alle Anwendungs‑Knoten in einer Cluster‑Umgebung bereitstellen. Redis kann auf einem einzelnen Knoten mehr als 200 k Operationen pro Sekunde verarbeiten und garantiert Sub‑Millisekunden‑Look‑ups.

## Voraussetzungen
- **GroupDocs.Conversion** – Version 25.2 oder neuer (unterstützt **120+** Eingabe‑ und Ausgabeformate).  
- **Jedis** (der offizielle Redis‑Client für Java).  
- Eine laufende Redis‑Instanz (lokale Entwicklung kann den Standard `localhost:6379` verwenden).  
- Maven für das Abhängigkeits‑Management.  
- Grundlegende Kenntnisse in Java‑Exception‑Handling und I/O‑Streams.

## Einrichtung von GroupDocs.Conversion für Java

`GroupDocs.Conversion` ist eine Java‑Bibliothek, die Dokumente in ein breites Spektrum von Formaten konvertiert und rendert, dabei Layout‑Erhaltung, Schrift‑Einbettung und Bild‑Extraktion automatisch übernimmt.

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

### Lizenzbeschaffung
Sie können mit einer **Kostenlosen Testversion** beginnen, eine **Temporäre Lizenz** zur Evaluierung anfordern oder eine vollständige **Lizenz** für den Produktionseinsatz erwerben.

Initialize GroupDocs.Conversion in your Java code:

```java
import com.groupdocs.conversion.*;

ConversionConfig config = new ConversionConfig();
config.setLicensePath("path/to/license/file.lic");
ConversionApi conversionApi = new ConversionApi(config);
```

## Implementierungsleitfaden

### Erstellen eines benutzerdefinierten Caches mit Redis

#### Überblick
Ein benutzerdefinierter Redis‑Cache speichert gerenderte Dokument‑Bytes und ermöglicht bei wiederholten Anfragen die sofortige Wiederherstellung.

#### Einrichtung von JedisPool
JedisPool ist ein thread‑sicherer Pool wiederverwendbarer Redis‑Verbindungen, der den Socket‑Overhead minimiert und den Durchsatz erhöht.

```java
import redis.clients.jedis.JedisPool;
import redis.clients.jedis.JedisPoolConfig;

JedisPoolConfig poolConfig = new JedisPoolConfig();
poolConfig.setMaxTotal(20);               // maximum active connections
poolConfig.setMaxIdle(10);                // maximum idle connections
poolConfig.setMinIdle(2);                 // minimum idle connections
JedisPool jedisPool = new JedisPool(poolConfig, "localhost", 6379);
```

#### Speichern und Abrufen von zwischengespeicherten Daten
Die nachstehenden Hilfsmethoden serialisieren ein Byte‑Array in einen Base64‑String für sichere Speicherung und wandeln es zurück in ein Byte‑Array.

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

#### Integration mit GroupDocs.Conversion
Binden Sie nun den Cache in den Konvertierungs‑Workflow ein. Die Methode prüft zuerst den Cache; bei einem Fehlgriff wird die Konvertierung durchgeführt, das Ergebnis gespeichert und die Bytes zurückgegeben.

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

## Wie erstellt man einen Cache‑Schlüssel in Java für Redis‑Caching?
Erzeugen Sie einen deterministischen Schlüssel, indem Sie den Quelldateipfad, ausgewählte `ConvertOptions`‑Werte und ein optionales Versions‑Tag zusammenfügen und die Zeichenkette anschließend mit SHA‑256 hashen. Dieser Schlüssel identifiziert jede Konfigurations‑Konvertierung eindeutig, sodass identische Anfragen den Cache treffen, während unterschiedliche Optionen separate Einträge erzeugen.

Die Klasse `ConversionApi` ist die Kernkomponente in GroupDocs.Conversion, die Dokumentkonvertierungen ausführt. Sie können einen Cache‑Schlüssel erstellen, in Redis nachschlagen und `ConversionApi.convert` nur aufrufen, wenn der Schlüssel fehlt, wodurch die Konvertierungszeit und die Serverlast erheblich reduziert werden.

## Wie implementiert man Java‑Redis‑Caching?
`ConversionApi` ist die primäre Klasse in GroupDocs.Conversion, die Dokumentkonvertierungs‑Operationen ausführt. Laden Sie Ihr Quelldokument, erzeugen Sie einen deterministischen Cache‑Schlüssel, suchen Sie ihn in Redis und rufen Sie `ConversionApi` nur auf, wenn der Schlüssel nicht vorhanden ist. Dieses Muster stellt sicher, dass jede eindeutige Konvertierung einmal durchgeführt und anschließend für die Dauer des konfigurierten TTL aus dem Cache bereitgestellt wird.

## Tipps zur Fehlersuche
- Stellen Sie sicher, dass der Redis‑Server erreichbar ist (`redis-cli ping` sollte `PONG` zurückgeben).  
- Vergewissern Sie sich, dass Host und Port von `JedisPool` mit Ihrer Redis‑Bereitstellung übereinstimmen.  
- Umwickeln Sie Cache‑Aufrufe mit try‑catch‑Blöcken, um Verbindungsprobleme zu behandeln, ohne den Konvertierungsablauf zu unterbrechen.  
- Überwachen Sie den Redis‑Speicher (`INFO memory`) und setzen Sie `maxmemory`‑Richtlinien (z. B. `volatile-lru`), um alte Einträge elegant zu entfernen.  
- Falls Sie einen `OutOfMemoryError` in der JVM erhalten, erhöhen Sie die Heap‑Größe oder aktivieren Sie `-XX:+UseCompressedOops`.

## Praktische Anwendungsfälle

1. **Portale mit hohem Traffic** – Häufig angeforderte PDFs (Kataloge, Whitepapers) sofort bereitstellen.  
2. **Enterprise DMS** – Belastung reduzieren, wenn Benutzer wiederholt dieselben Verträge oder Richtliniendokumente ansehen.  
3. **E‑Commerce** – Generierte Rechnungen oder Produktkataloge cachen, um den Checkout zu beschleunigen.  
4. **Lernplattformen** – Vorlesungsnotizen und E‑Books bereitstellen, ohne bei jeder Studenten‑Anfrage neu zu rendern.  
5. **Rechtsdienstleistungen** – Verteilung von Akten beschleunigen und dabei die Speicherkosten niedrig halten.

## Leistungsüberlegungen

- **Redis abstimmen** – `maxmemory` anpassen, eine Eviktions‑Richtlinie wie `allkeys-lru` wählen und geeignete `timeout`‑Werte basierend auf Ihrem Traffic‑Muster festlegen.  
- **Cache‑Hit/Miss‑Verhältnisse verfolgen** – `INFO stats` oder Redis‑Zähler `keyspace_hits` / `keyspace_misses` nutzen, um TTLs fein abzustimmen.  
- **JVM‑Heap‑Größe** – Sicherstellen, dass der Heap die GroupDocs‑Puffer aufnehmen kann; eine Faustregel ist 1 GB Heap pro 100 MB gleichzeitiger Konvertierungs‑Payload.  
- **Batch‑Konvertierungen** – Beim Konvertieren vieler Dateien ein einzelnes `Jedis`‑Instanz pro Thread wiederverwenden, um Socket‑Wechsel zu minimieren.

## Häufig gestellte Fragen

**F: Kann ich diesen Ansatz mit anderen GroupDocs‑Ausgabeformaten verwenden?**  
A: Absolut. Das gleiche Caching‑Muster funktioniert für DOCX, HTML, Bilder und mehr – einfach den `ConvertOptions`‑Typ ändern.

**F: Wie wähle ich einen guten Cache‑Schlüssel?**  
A: Kombinieren Sie den Quelldateipfad, die Konvertierungsoptionen und etwaige Versions‑Kennungen. Das garantiert Eindeutigkeit pro Konfiguration.

**F: Was passiert, wenn sich ein Dokument nach dem Caching ändert?**  
A: Invalideren Sie den Cache manuell (z. B. Schlüssel löschen) oder verwenden Sie ein kürzeres TTL, sodass veraltete Daten schnell ablaufen.

**F: Ist Redis die einzige Option für Caching?**  
A: Nein, aber Redis bietet niedrige Latenz, integriertes TTL und breite Java‑Client‑Unterstützung, was es zu einer beliebten Wahl für dieses Szenario macht.

**F: Erhöht dies den Speicherverbrauch auf dem Anwendungs‑Server?**  
A: Minimal. Die schwere Arbeit wird von Redis erledigt; die Anwendung hält nur kurzlebige Verbindungen über Jedis.

## Fazit
Sie haben nun ein vollständiges **Java‑Redis‑Caching**‑Tutorial, das zeigt, wie Dokumente mit Redis und GroupDocs.Conversion gecached werden. Durch das Persistieren der gerenderten Ausgabe in Redis **steigern Sie die Rendering‑Leistung**, **reduzieren die Konvertierungszeit** und bieten End‑Usern ein reibungsloseres Erlebnis. Experimentieren Sie mit verschiedenen TTL‑Werten, überwachen Sie Cache‑Metriken und erweitern Sie das Muster auf weitere Dokumentformate, wenn Ihre Anwendung wächst.

---

**Zuletzt aktualisiert:** 2026-10-21  
**Getestet mit:** GroupDocs.Conversion 25.2, Jedis 4.2.3  
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

## Verwandte Tutorials

- [Benutzerdefinierten Cache in Java implementieren – GroupDocs Conversion Cache](/conversion/java/cache-management/)
- [Wie man Redis‑Cache in Java mit GroupDocs.Conversion verwendet](/conversion/java/cache-management/redis-cache-java-groupdocs-conversion-guide/)
- [Wie man Dateien in Java mit GroupDocs.Conversion cached – Ein umfassender Leitfaden für effiziente Dokumentkonvertierung](/conversion/java/cache-management/implement-java-file-caching-groupdocs-conversion-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}