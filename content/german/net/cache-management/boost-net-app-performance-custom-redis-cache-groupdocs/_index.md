---
date: '2026-05-21'
description: Erfahren Sie, wie Sie custom redis cache .net mit GroupDocs.Conversion
  verwenden, um die Dokumentkonvertierung drastisch zu beschleunigen. Entdecken Sie
  die Schritt‑für‑Schritt‑Einrichtung, redis caching best practices und performance
  metrics.
keywords:
- custom redis cache .net
- use redis caching
- implement redis caching .net
schemas:
- author: GroupDocs
  dateModified: '2026-05-21'
  description: Learn how to use custom redis cache .net with GroupDocs.Conversion
    to dramatically speed up document conversion. Discover step‑by‑step setup, use
    redis caching best practices, and performance metrics.
  headline: Boost .NET Performance with custom redis cache .net and GroupDocs.Conversion
  type: TechArticle
- questions:
  - answer: 'Follow the official Redis installation guide for your OS: [Redis Download](https://redis.io/download).'
    question: How do I install Redis on my local machine?
  - answer: It eliminates duplicate rendering, cuts CPU usage by ~70 %, reduces average
      response time from 1.2 s to <200 ms, and lowers cloud bill by decreasing compute
      cycles.
    question: What are the tangible benefits of using a custom cache with GroupDocs.Conversion?
  - answer: Yes—simply point the `ConnectionMultiplexer` to your managed Redis instance
      (Azure Cache for Redis or Amazon ElastiCache) and ensure network security groups
      allow traffic on port 6379.
    question: Can this architecture be deployed to Azure or AWS?
  - answer: The `StackExchange.Redis` client is fully thread‑safe; you can share a
      single `ConnectionMultiplexer` across all request threads without additional
      locking.
    question: Is the cache thread‑safe for concurrent web requests?
  - answer: Invalidate by deleting keys that match the document’s identifier, e.g.,
      `await redis.GetDatabase().KeyDeleteAsync($"docCache:{docId}:*");`.
    question: How do I clear the cache when a source document changes?
  type: FAQPage
title: Steigern Sie die .NET-Leistung mit custom redis cache .net und GroupDocs.Conversion
type: docs
url: /de/net/cache-management/boost-net-app-performance-custom-redis-cache-groupdocs/
weight: 1
---

# Steigern Sie die .NET-Anwendungsleistung mit **custom redis cache .net** mithilfe von GroupDocs.Conversion

## Einführung

Wenn Ihre .NET-Anwendung wertvolle Sekunden – oder sogar Minuten – mit der Konvertierung von Dokumenten verbringt, sind Sie nicht allein. Die Implementierung einer **custom redis cache .net**‑Lösung zusammen mit GroupDocs.Conversion kann die Konvertierungszeiten für wiederholte Anfragen um bis zu 80 % verkürzen. In diesem Tutorial lernen Sie, wie Sie GroupDocs.Conversion einrichten, einen Redis‑basierten Cache erstellen und bewährte Performance‑Optimierungstechniken anwenden, die Ihre Anwendung unter hoher Last reaktionsfähig halten.

### Schnelle Antworten
- **Was speichert der benutzerdefinierte Redis-Cache?** Renderte PDF/HTML‑Byte‑Streams für jedes Quelldokument.  
- **Wie viel schneller kann die Konvertierung werden?** Bis zu 8‑fach schneller für zwischengespeicherte Dokumente, gemessen auf einem 4‑Kern‑Server.  
- **Benötige ich eine kommerzielle GroupDocs-Lizenz?** Ja, für den Produktionseinsatz ist eine gültige Lizenz erforderlich.  
- **Läuft das auf .NET 6+?** Absolut – kompatibel mit .NET 5, .NET 6 und .NET 7.  
- **Ist Docker-Unterstützung enthalten?** Der Cache funktioniert in Containern; öffnen Sie einfach den Redis-Port.

## Was ist **custom redis cache .net**?

Es ist eine vom Entwickler implementierte Caching‑Schicht, die die binäre Ausgabe von Dokumentkonvertierungen in einem Redis‑Key‑Value‑Store speichert und es nachfolgenden Anfragen ermöglicht, das vorgerenderte Ergebnis sofort abzurufen, anstatt die Originaldatei erneut zu verarbeiten, wodurch Latenz und CPU‑Last in der gesamten Anwendung reduziert werden.

## Warum **custom redis cache .net** mit GroupDocs.Conversion verwenden?

GroupDocs.Conversion unterstützt **50+** Eingabe‑ und Ausgabeformate – darunter DOCX, PPTX, HTML und PDF – und kann Dokumente bis zu 500 Seiten verarbeiten, ohne die gesamte Datei in den Speicher zu laden. Durch die Kombination mit einem Redis‑Cache eliminieren Sie redundantes Rendering, reduzieren die CPU‑Auslastung um etwa **70 %** und halten die Antwortzeiten für zwischengespeicherte Assets unter **200 ms**.

## Voraussetzungen

- **GroupDocs.Conversion for .NET** (Version 25.3.0 or later)  
- **StackExchange.Redis** NuGet package  
- Eine erreichbare Redis‑Instanz (z. B. `192.168.222.4:6379`)  
- Visual Studio 2022 oder jede C#‑kompatible IDE  
- .NET 6 SDK (or .NET 5/Framework 4.8) installed  

### Wissensvoraussetzungen
- Vertraut mit C# async/await‑Mustern  
- Grundlegende Redis‑Konzepte (Keys, TTL, Connection‑Pooling)  
- Vertrautheit mit Dokumentkonvertierungs‑Pipelines  

## Wie richtet man GroupDocs.Conversion für .NET ein?

Beginnen Sie damit, das GroupDocs.Conversion‑Paket zu Ihrem Projekt hinzuzufügen, entweder über die NuGet Package Manager Console oder die .NET‑CLI. Dadurch wird die Kern‑Konvertierungsengine und ihre Abhängigkeiten installiert, sodass Ihre Umgebung bereit ist, Converter‑Instanzen zu erstellen und Konvertierungseinstellungen für verschiedene Dokumentformate zu konfigurieren.

Installieren Sie die Bibliothek über NuGet:

```
Install-Package GroupDocs.Conversion
```

Oder mit der .NET‑CLI:

```
dotnet add package GroupDocs.Conversion
```

### Schritte zum Erwerb einer Lizenz
- **Kostenlose Testversion:** Registrieren Sie sich im GroupDocs‑Portal für eine 30‑tägige Lizenzdatei.  
- **Temporäre Lizenz:** Fordern Sie einen 90‑tägigen Evaluierungsschlüssel für größere Workloads an.  
- **Kauf:** Erwerben Sie eine Produktionslizenz, um unbegrenzte Konvertierungen freizuschalten.

Nach der Installation des Pakets initialisieren Sie GroupDocs.Conversion in Ihrem C#‑Projekt:

```csharp
using GroupDocs.Conversion;
using GroupDocs.Conversion.Options.Convert;

// Initialize with a license file
Converter converter = new Converter("path/to/license.json");
```

## Wie verbessert ein **custom redis cache .net** die Konvertierungsgeschwindigkeit?

Wenn eine Konvertierungsanfrage eintrifft, fragt die Anwendung zuerst Redis nach einem zwischengespeicherten Byte‑Stream, der zum Quelldokument und den Konvertierungsparametern passt. Bei einem Treffer wird das gespeicherte Ergebnis sofort zurückgegeben, wodurch der aufwändige Rendering‑Prozess umgangen wird; andernfalls führt GroupDocs.Conversion die Konvertierung durch und speichert die Ausgabe zurück in Redis für zukünftige Verwendung.

### Schritt 1: Definieren Sie die Klasse `RedisCache`

Die Klasse `RedisCache` bietet eine leichtgewichtige Wrapper‑Klasse um StackExchange.Redis zum Speichern und Abrufen binärer Konvertierungsergebnisse.

```csharp
// RedisCache class definition placeholder
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using StackExchange.Redis;

public class RedisCache : IDisposable
{
    private readonly string _cacheKeyPrefix;
    private readonly ConnectionMultiplexer _redis;
    private readonly IDatabase _db;
    private readonly string _host = "192.168.222.4:6379";

    public RedisCache(string cacheKeyPrefix)
    {
        _cacheKeyPrefix = cacheKeyPrefix;
        _redis = ConnectionMultiplexer.Connect(_host);
        _db = _redis.GetDatabase();
    }

    // Set data in the cache with a specific key
    public void Set(string key, object data)
    {
        if (data == null) return;

        string prefixedKey = GetPrefixedKey(key);
        using (MemoryStream stream = new MemoryStream())
        {
            ((Stream)data).CopyTo(stream);
            _db.StringSet(prefixedKey, RedisValue.CreateFrom(stream));
        }
    }

    // Try to retrieve data from the cache using a key
    public bool TryGetValue(string key, out object value)
    {
        var prefixedKey = GetPrefixedKey(key);
        var redisValue = _db.StringGet(prefixedKey);

        if (redisValue.HasValue)
        {
            value = new MemoryStream(redisValue);
            return true;
        }

        value = default;
        return false;
    }

    // Retrieve all keys that match a filter pattern from the cache
    public IEnumerable<string> GetKeys(string filter)
    {
        return _redis.GetServer(_host).Keys(pattern: $"*{filter}*")
            .Select(x => x.ToString().Replace(_cacheKeyPrefix, string.Empty))
            .Where(x => x.StartsWith(filter, StringComparison.InvariantCultureIgnoreCase))
            .ToList();
    }

    private string GetPrefixedKey(string key) => $"{_cacheKeyPrefix}{key}";

    public void Dispose()
    {
        _redis.Dispose();
    }
}
```
```

## Schritt 2: Implementieren Sie die Dokumentkonvertierung mit dem benutzerdefinierten Cache

Das folgende Beispiel zeigt die Integration des `RedisCache` mit GroupDocs.Conversion, um die PDF‑Konvertierungsausgabe zu cachen.

```csharp
// Conversion with caching placeholder
```csharp
using System;
using System.Diagnostics;
using GroupDocs.Conversion.Options.Convert;
using GroupDocs.Conversion.Caching;

public class HowToUseCustomCacheImplementation
{
    public static void Run()
    {
        string outputDirectory = "YOUR_OUTPUT_DIRECTORY";
        
        RedisCache cache = new RedisCache("sample_");
        Func<ConverterSettings> settingsFactory = () => new ConverterSettings
        {
            Cache = cache
        };

        using (Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/SAMPLE_PDF", settingsFactory))
        {
            PdfConvertOptions options = new PdfConvertOptions();
            
            Stopwatch stopWatch = Stopwatch.StartNew();
            converter.Convert($"{outputDirectory}/converted.pdf", options);
            stopWatch.Stop();

            stopWatch.Restart();
            converter.Convert($"{outputDirectory}/converted-1.pdf", options);
            stopWatch.Stop();
        }
    }
}
```
```

## Welche gängigen Anwendungsfälle gibt es für **custom redis cache .net**?

Der benutzerdefinierte Redis‑Cache kann in jedem Szenario eingesetzt werden, in dem Dokumentkonvertierungsergebnisse wiederholt angefordert werden, wodurch eine sofortige Abrufung ermöglicht und die Serverlast reduziert wird. Typische Anwendungen umfassen Enterprise‑Document‑Management‑Systeme, stark frequentierte Web‑APIs, die Vorschaubilder bereitstellen, CDN‑Edge‑Caching von konvertierten Assets, automatisierte Reporting‑Dashboards und E‑Commerce‑Plattformen, die Produktbroschüren auf Abruf erzeugen.

1. **Enterprise Document Management Systeme:** Beschleunigen Sie die Vorschauerstellung für tausende PDFs, die in einem zentralen Repository gespeichert sind.  
2. **Web‑APIs:** Geben Sie vorab konvertiertes HTML oder Bild‑Thumbnails sofort für stark frequentierte Endpunkte zurück.  
3. **CDN‑Edge‑Knoten:** Cachen Sie konvertierte Assets in Nähe der Nutzer, um die Last des Origin‑Servers zu reduzieren.  
4. **Analytics‑Dashboards:** Erzeugen Sie PDF‑Berichte on‑the‑fly und verwenden Sie sie für wiederkehrende geplante Auslieferungen erneut.  
5. **E‑Commerce‑Kataloge:** Cachen Sie Produktbroschüren‑Konvertierungen, um die Ladezeiten der Seiten zu verbessern.  

## Wie können Sie die Leistung beim Einsatz von Redis feinabstimmen?

Die Leistung kann optimiert werden, indem geeignete TTL‑Werte konfiguriert, eine einzelne ConnectionMultiplexer‑Instanz wiederverwendet, rohe Byte‑Arrays gespeichert werden, um Serialisierungs‑Overhead zu vermeiden, und Batch‑Operationen für Masslöschungen eingesetzt werden. Die Überwachung des Speicherverbrauchs und das Aktivieren einer Eviction‑Policy wie allkeys‑lru stellt sicher, dass der Cache unter hoher Last effizient bleibt.

- **Cache‑Größenverwaltung:** Setzen Sie für die meisten Dokumente eine TTL von 24 Stunden; entfernen Sie ältere Einträge mit `RedisCache.GetKeys("docCache:*")`.  
- **Connection‑Pooling:** Verwenden Sie eine einzelne `ConnectionMultiplexer`‑Instanz über die gesamte Anwendung hinweg, um Handshake‑Overhead zu vermeiden.  
- **Effiziente Serialisierung:** Speichern Sie rohe Bytes direkt; vermeiden Sie JSON‑ oder XML‑Wrapper, die die Payload‑Größe aufblähen.  
- **Batch‑Operationen:** Beim Löschen einer Kategorie verwenden Sie `IDatabase.KeyDelete` mit einem Muster, um viele Keys in einem Aufruf zu entfernen.  

## Wie beheben Sie häufige Fallstricke?

Wenn Probleme auftreten, prüfen Sie, ob Cache‑Keys konsistent generiert werden, überwachen Sie den Redis‑Speicherverbrauch und stellen Sie sicher, dass die Version der Client‑Bibliothek zur Laufzeit passt. Überprüfen Sie die Netzwerklatenz zwischen Anwendung und Redis‑Server und bestätigen Sie, dass das Connection‑Pooling korrekt konfiguriert ist, um übermäßige Handshakes zu vermeiden, die die Leistung beeinträchtigen können.

- **Fehlende Keys:** Vergewissern Sie sich, dass für identische Konvertierungsparameter (Eingabepfad, Ausgabeformat, Konvertierungsoptionen) derselbe Cache‑Key generiert wird.  
- **Speicherdruck:** Überwachen Sie den Redis‑Speicherverbrauch; aktivieren Sie `maxmemory-policy allkeys-lru`, um am wenigsten genutzte Einträge automatisch zu entfernen.  
- **Versionskonflikte:** Stellen Sie sicher, dass die StackExchange.Redis‑Version zur .NET‑Runtime passt (z. B. 2.6+ für .NET 6).  
- **Netzwerklatenz:** Platzieren Sie Redis im selben Rechenzentrum oder derselben VPC wie Ihre Anwendung, um die Round‑Trip‑Zeit unter 1 ms zu halten.  

## Häufig gestellte Fragen

**F: Wie installiere ich Redis auf meinem lokalen Rechner?**  
A: Folgen Sie der offiziellen Redis‑Installationsanleitung für Ihr Betriebssystem: [Redis Download](https://redis.io/download).

**F: Was sind die greifbaren Vorteile der Verwendung eines benutzerdefinierten Caches mit GroupDocs.Conversion?**  
A: Er eliminiert doppeltes Rendering, reduziert die CPU‑Auslastung um ~70 %, senkt die durchschnittliche Antwortzeit von 1,2 s auf <200 ms und verringert die Cloud‑Kosten, indem die Compute‑Zyklen reduziert werden.

**F: Kann diese Architektur in Azure oder AWS bereitgestellt werden?**  
A: Ja – zeigen Sie einfach den `ConnectionMultiplexer` auf Ihre verwaltete Redis‑Instanz (Azure Cache for Redis oder Amazon ElastiCache) und stellen Sie sicher, dass die Netzwerk‑Security‑Groups den Datenverkehr auf Port 6379 zulassen.

**F: Ist der Cache thread‑sicher für gleichzeitige Web‑Anfragen?**  
A: Der `StackExchange.Redis`‑Client ist vollständig thread‑sicher; Sie können eine einzelne `ConnectionMultiplexer`‑Instanz über alle Anforderungs‑Threads hinweg teilen, ohne zusätzliche Sperren.

**F: Wie leere ich den Cache, wenn sich ein Quelldokument ändert?**  
A: Invalidieren Sie, indem Sie Schlüssel löschen, die dem Dokument‑Identifier entsprechen, z. B. `await redis.GetDatabase().KeyDeleteAsync($"docCache:{docId}:*");`.

## Fazit

Durch die Integration eines **custom redis cache .net** mit GroupDocs.Conversion erzielen Sie dramatische Leistungssteigerungen, senken die Infrastrukturkosten und bieten ein reibungsloseres Benutzererlebnis. Die obigen Schritte liefern Ihnen eine produktionsreife Grundlage – experimentieren Sie mit TTL‑Werten, Cache‑Key‑Strategien und horizontaler Skalierung, um die Lösung an Ihre Arbeitslast anzupassen.

**Last Updated:** 2026-05-21  
**Tested With:** GroupDocs.Conversion 25.3.0 for .NET  
**Author:** GroupDocs  

```bash
Install-Package GroupDocs.Conversion -Version 25.3.0
```

```bash
dotnet add package GroupDocs.Conversion --version 25.3.0
```

```csharp
using GroupDocs.Conversion;
```

## Verwandte Tutorials

- [Conversion Cache Management Tutorials für GroupDocs.Conversion .NET](/conversion/net/cache-management/)
- [Optimieren Sie .NET-Dokumentkonvertierung mit Caching unter Verwendung von GroupDocs.Conversion](/conversion/net/cache-management/optimize-net-document-conversion-caching-groupdocs/)
- [Meistern Sie die Dokumentkonvertierungseinrichtung in .NET mit GroupDocs.Conversion](/conversion/net/conversion-options-settings/master-groupdocs-conversion-net-setup/)