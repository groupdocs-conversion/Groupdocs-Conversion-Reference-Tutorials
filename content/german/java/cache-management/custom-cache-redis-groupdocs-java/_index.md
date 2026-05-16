---
date: '2026-01-23'
description: Erfahren Sie, wie Sie Dokumente in Java mithilfe von GroupDocs.Conversion
  in einem Redis-Cache zwischenspeichern. Steigern Sie die Rendering‑Leistung und
  verbessern Sie die Effizienz.
keywords:
- Custom Caching Java
- GroupDocs.Conversion Java
- Redis Cache Implementation
title: Wie man Dokumente in Java mit Redis & GroupDocs zwischenspeichert
type: docs
url: /de/java/cache-management/custom-cache-redis-groupdocs-java/
weight: 1
---

# Wie man Dokumente in Java mit Redis & GroupDocs cached

Wenn Sie **Dokumente effizient cachen** müssen, insbesondere bei einer hohen Dokumentenrendering‑Last, kann ein gut gestalteter Cache die Verarbeitungszeit drastisch verkürzen. In diesem Tutorial führen wir Sie durch ein vollständiges **java redis cache tutorial**, das Redis mit GroupDocs.Conversion integriert und Ihnen hilft, die **Renderleistung** für PDF, DOCX und andere Formate zu **steigern**.

## Schnelle Antworten
- **Worum geht es in diesem Tutorial?** Implementierung eines Redis‑basierten Caches für GroupDocs.Conversion in Java.  
- **Warum Redis verwenden?** Es bietet schnellen In‑Memory‑Speicher, TTL‑Unterstützung und einfache Skalierbarkeit.  
- **Benötige ich eine GroupDocs‑Lizenz?** Eine Test‑; für die Produktion ist eine Voll‑Lizenz erforderlich.  
- **Was sind die Hauptschritte?** Maven‑Abhängigkeiten einrichten, Jedis konfigurieren, Cache‑Hilfsklassen erstellen und das Caching in den Konvertierungs den neuesten GroupDocs.Conversion‑Releases).

## Was ist das Caching von Dokumenten mit Redis?
Caching speichert das Ergebnis einer Dokumentkonvertierung (z. B. ein erzeugtes PDF) in Redis, sodass nachfolgende Anfragen für dieselbe Quelldatei sofort bedient werden können, ohne die Verarbeitung erneut durchzuführen. Dies reduziert die CPU‑Auslastung, den Netzwerkverkehr und verbessert die Benutzererfahrung.

## Warum ein Redis‑Cache in Java implementieren?
- **Renderleistung steigern** durch Vermeidung doppelter Konvertierungen.  
- **Infrastrukturkosten senken** – weniger CPU‑Zyklen und geringere Speicherbelastung.  
- **Skalierbar über mehrere Anwendungsinstanzen** dank Redis als zentralem Speicher.  
- **Feinkörnige Kontrolle** über Ablaufrichtlinien, die ein Gleichgewicht zwischen Aktualität und Geschwindigkeit ermöglichen.

## Voraussetzungen

- **GroupDocs.Conversion** – Version 25.2 oder neuer.  
- **Jedis** ( für das Abhängigkeitsmanagement.  
- Grundlegende Java‑Kenntnisse und Vertrautheit mit Konzepten der Dokumentkonvertierung.

## EinrichtungFügen Sie das GroupDocs‑Repository und die Abhängigkeit zu Ihrer `pom.xml` hinzu:

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

### Lizenzbeschaffung
Sie können mit einer **Free Trial** beginnen, eine **Temporary License** für die Evaluierung anfordern oder eine vollständige **License** für den Produktionseinsatz erwerben.

Initialisieren Sie GroupDocs.Conversion in Ihrem Java‑Code:

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

## Implementierungs‑Leitfaden

### Erstellen eines benutzerdefinierten Caches mit Redis

#### Überblick
Ein benutzerdefinierter Redis‑Cache speichert die gerenderten Dokumentbytes und ermöglicht eine sofortige Abrufung bei wiederholten Anfragen.

#### Einrichtung von JedisPool
Zunächst erstellen Sie einen Verbindungspool, um Redis‑Verbindungen effizient zu verwalten:

```java
import redis.clients.jedis.JedisPool;

public class CacheManager {
    private static JedisPool jedisPool = new JedisPool("localhost", 6379);
    
    public static void main(String[] args) {
        // Additional cache setup code here
    }
}
```

#### Speichern und Abrufen von zwischengespeicherten Daten
Verwenden Sie einfache Hilfsmethoden, um Dokumente in Redis zu speichern und abzurufen:

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

#### Integration mit GroupDocs.Conversion
Binden Sie nun den Cache in den Konvertierungs‑Workflow ein:

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

### Tipps zur Fehlersuche
- Überprüfen Sie, ob der Redis‑Server erreichbar ist (`ping` vom Host).  
- Stellen Sie sicher, dass Host/Port von `JedisPool` mit Ihrer Redis‑Instanz übereinstimmen.  
- Umschließen Sie Cache‑Aufrufe in try‑catch‑Blöcken, um Verbindungsprobleme elegant zu behandeln.  
- Überwachen Sie den Redis‑Speicherverbrauch; erwägen Sie `maxmemory`‑Richtlinien für die Produktion.

## Praktische Anwendungsfälle

1. **Hochfrequente Portale** – Häufig angeforderte PDFs sofort bereitstellen.  
2. **Enterprise DMS** – Belastung der Konvertierungsserver reduzieren, wenn Nutzer wiederholt dieselbenleunigen und gleichzeitig die Leistungsüberlegungen

- **Redis optimieren** – `maxmemory`, `eviction-policy` und Timeout‑Einstellungen basierend auf Ihrer Arbeitslast anpassen.  
- **Cache‑Hit/Miss‑Verhältnisse verfolgen** – Redis‑`INFO`‑Statistiken nutzen, um Schlüssel‑TTLs fein abzustimmen.  
- **JVM‑Heap‑Größe** – Sicherstellen, dass der Heap die Konvertierungsbibliothek plus eventuelle In‑Process‑Puffer aufnehmen kann.

## Häufig gestellte Fragen

**Q: Kann ich diesen Ansatz mit anderen GroupDocs‑Ausgabeformaten verwenden?**  
A: Absolut. Das gleiche Caching‑Muster funktioniert für DOCX, HTML, Bilder und mehr – einfach den `ConvertOptions`‑Typ ändern.

**Q: Wie wähle ich einen guten Cache‑Schlüssel?**  
A: Kombinieren Sie den Pfad der Quelldatei, die Konvertierungsoptionen und etwaige Versionskennzeichen. Das garantiert Eindeutigkeit pro Konfiguration.

**Q: Was passiert, wenn sich ein Dokument nach dem Caching ändert?**  
A: Invalide den Cache manuell (z. B. den Schlüssel löschen) oder verwenden Sie eine kürzere TTL, damit veraltete Daten schnell ablaufen.

**Q: Ist Redis die einzige Option zum Caching?**  
A: Nein, aber Redis bietet niedrige Latenz, integrierte TTL und breite Java‑Client‑Unterstützung, was es zu einer beliebten Wahl für dieses Szenario macht.

**Q: Erhöht dies den Speicherverbrauch auf dem Anwendungs‑Server?**  
A: Minimal. Die Hauptarbeit übernimmt Redis; die Anwendung hält nur kurzlebige Verbindungen über Jedis.

## Fazit

Sie haben nun ein vollständiges **java redis cache tutorial**, das zeigt, **wie man Dokumente** mit Redis und GroupDocs.Conversion cached. Durch das Speichern der gerenderten Ausgabe in Redis **steigern Sie die Renderleistung**, reduzieren die Serverlast und bieten den Endbenutzern ein reibungsloseres Erlebnis. Experimentieren Sie mit verschiedenen TTL‑Werten, überwachen Sie die Cache‑Metriken und erweitern Sie das Muster bei Bedarf auf andere Dokumentformate.

---

**Zuletzt aktualisiert:** 2026-01-23  
**Getestet mit:** GroupDocs.Conversion 25.2, Jedis 4.2  
**Autor:** GroupDocs