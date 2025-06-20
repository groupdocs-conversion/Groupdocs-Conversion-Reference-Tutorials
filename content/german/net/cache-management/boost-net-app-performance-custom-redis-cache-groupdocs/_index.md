---
"date": "2025-04-28"
"description": "Erfahren Sie, wie Sie die Leistung Ihrer .NET-App verbessern, indem Sie einen benutzerdefinierten Redis-Cache für die Dokumentkonvertierung mit GroupDocs.Conversion implementieren. Steigern Sie noch heute Effizienz und Geschwindigkeit!"
"title": "Steigern Sie die Leistung von .NET-Anwendungen&#58; Implementieren Sie benutzerdefinierten Redis Cache mit GroupDocs.Conversion"
"url": "/de/net/cache-management/boost-net-app-performance-custom-redis-cache-groupdocs/"
"weight": 1
---

# Steigern Sie die Leistung Ihrer .NET-Anwendung mit benutzerdefiniertem Redis-Caching mithilfe von GroupDocs.Conversion

## Einführung

Erleben Sie langsame Dokumentkonvertierungsprozesse in Ihren .NET-Anwendungen? Steigern Sie Leistung und Effizienz durch die Nutzung eines benutzerdefinierten Redis-Caches zusammen mit GroupDocs.Conversion für .NET. Dieses Tutorial führt Sie durch Caching-Vorgänge zur Beschleunigung der Dokumentdarstellung.

**Was Sie lernen werden:**
- Einrichten von GroupDocs.Conversion für .NET
- Implementieren eines benutzerdefinierten Redis-Cache für die Dokumentkonvertierung
- Leistungsoptimierung mit effektiven Caching-Strategien

Wir zeigen Ihnen Schritt für Schritt, wie Sie die Effizienz Ihrer Anwendung mit diesen leistungsstarken Tools steigern. Bevor wir beginnen, stellen Sie sicher, dass Sie die Voraussetzungen verstehen.

## Voraussetzungen

Um diesem Tutorial folgen zu können, stellen Sie sicher, dass Sie über Folgendes verfügen:

### Erforderliche Bibliotheken und Versionen:
- **GroupDocs.Conversion für .NET** (Version 25.3.0)
- **StackExchange.Redis** Bibliothek für Redis-Operationen
- Eine laufende Instanz eines Redis-Servers (z. B. `192.168.222.4:6379`)

### Anforderungen für die Umgebungseinrichtung:
- Visual Studio oder eine andere kompatible IDE, die C# unterstützt
- .NET Framework oder .NET Core installiert

### Erforderliche Kenntnisse:
- Grundlegende Kenntnisse der C#- und .NET-Programmierung
- Vertrautheit mit Redis als Caching-Lösung
- Erfahrung mit Dokumentkonvertierungsprozessen in Softwareanwendungen

## Einrichten von GroupDocs.Conversion für .NET

Um GroupDocs.Conversion zu verwenden, installieren Sie es über die NuGet Package Manager-Konsole oder die .NET-CLI.

**NuGet-Paket-Manager-Konsole:**
```bash
Install-Package GroupDocs.Conversion -Version 25.3.0
```

**.NET-CLI:**
```bash
dotnet add package GroupDocs.Conversion --version 25.3.0
```

### Schritte zum Lizenzerwerb:
- **Kostenlose Testversion:** Testen Sie Features und Funktionen mit einer temporären Lizenz.
- **Temporäre Lizenz:** Zum längeren Testen ohne Einschränkungen herunterladen.
- **Kaufen:** Für eine langfristige Nutzung sollten Sie den Erwerb einer Volllizenz in Erwägung ziehen.

Initialisieren Sie nach der Installation GroupDocs.Conversion in Ihrer C#-Anwendung:

```csharp
using GroupDocs.Conversion;
```

## Implementierungshandbuch

### Benutzerdefinierte Cache-Implementierung mit Redis

In diesem Abschnitt wird die Erstellung eines benutzerdefinierten Caches mit Redis für Dokument-Rendering-Vorgänge gezeigt, um die Konvertierungsgeschwindigkeit und -effizienz zu verbessern.

#### Überblick
Wir implementieren einen auf Redis basierenden Caching-Mechanismus, der gerenderte Dokumente speichert, redundante Verarbeitung vermeidet und die Konvertierungszeiten erheblich beschleunigt.

##### Schritt 1: Definieren der RedisCache-Klasse

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

    // Daten im Cache mit einem bestimmten Schlüssel festlegen
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

    // Versuchen Sie, Daten mithilfe eines Schlüssels aus dem Cache abzurufen
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

    // Alle Schlüssel, die einem Filtermuster entsprechen, aus dem Cache abrufen
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

**Erläuterung:**
- **Methode festlegen:** Speichert Daten in Redis unter Verwendung eines bestimmten Cache-Schlüssels.
- **TryGetValue-Methode:** Ruft zwischengespeicherte Daten ab, sofern verfügbar.
- **GetKeys-Methode:** Ruft Schlüssel ab, die einem angegebenen Muster entsprechen.

##### Schritt 2: Implementieren der Dokumentkonvertierung mit benutzerdefiniertem Cache

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

**Erläuterung:**
- **RedisCache-Initialisierung:** Richtet einen Cache mit einem Schlüsselpräfix ein.
- **Konvertereinstellungen:** Integriert den benutzerdefinierten Cache in die GroupDocs.Conversion-Einstellungen.
- **Konvertierungsprozess:** Misst und demonstriert Leistungsverbesserungen durch das Zwischenspeichern von Konvertierungsergebnissen.

## Praktische Anwendungen

### Anwendungsfälle:
1. **Enterprise-Dokumentenmanagementsysteme:** Verbessern Sie die Geschwindigkeit der Dokumentwiedergabe für groß angelegte Anwendungen.
2. **Webdienste:** Verbessern Sie die Reaktionszeiten für APIs, die häufige PDF-Konvertierungen verarbeiten.
3. **Content Delivery Networks (CDNs):** Zwischenspeichern und liefern Sie vorkonvertierte Dokumente schnell.
4. **Datenanalyseplattformen:** Beschleunigen Sie die Berichterstellung, indem Sie Daten in visuelle Formate konvertieren.
5. **E-Commerce-Sites:** Optimieren Sie die Produktkatalogverarbeitung, indem Sie konvertierte Bilder oder Dokumentvorschauen zwischenspeichern.

### Integrationsmöglichkeiten:
- Kombinieren Sie es mit anderen .NET-Frameworks wie ASP.NET Core für Webanwendungen.
- Integrieren Sie mit Docker und Kubernetes in die Microservices-Architektur.

## Überlegungen zur Leistung

Um die Leistung zu optimieren, sollten Sie Folgendes beachten:

- **Cache-Größenverwaltung:** Löschen Sie regelmäßig alte Einträge, um einen Speicherüberlauf zu verhindern.
- **Verbindungspooling:** Verwenden Sie Verbindungspooling in Redis, um Ressourcen effizient zu verwalten.
- **Datenserialisierung:** Entscheiden Sie sich für effiziente Serialisierungsformate (z. B. Protokollpuffer) zum Speichern von Daten in Redis.

## Abschluss

Die Implementierung eines benutzerdefinierten Redis-Cache mit GroupDocs.Conversion für .NET kann die Dokumentkonvertierungsleistung Ihrer Anwendung deutlich steigern. Dieses Tutorial bietet eine Schritt-für-Schritt-Anleitung zur Einrichtung und Nutzung dieser leistungsstarken Tools zur Optimierung von Abläufen.

**Nächste Schritte:**
- Experimentieren Sie mit verschiedenen Cache-Konfigurationen.
- Entdecken Sie die erweiterten Funktionen von GroupDocs.Conversion für komplexere Anwendungsfälle.

Sind Sie bereit, die Effizienz Ihrer Anwendung zu steigern? Beginnen Sie noch heute mit der Implementierung dieser Lösung!

## FAQ-Bereich

1. **Wie installiere ich Redis auf meinem lokalen Computer?**
   - Befolgen Sie die offizielle Redis-Installationsanleitung für Ihr Betriebssystem: [Redis herunterladen](https://redis.io/download).
2. **Welche Vorteile bietet die Verwendung eines benutzerdefinierten Caches mit GroupDocs.Conversion?**
   - Reduziert redundante Verarbeitung, beschleunigt Konvertierungszeiten und senkt die Ressourcennutzung.
3. **Kann ich dieses Setup in Cloud-Umgebungen verwenden?**
   - Auf jeden Fall! Stellen Sie sicher, dass Ihre Redis-Instanz von Ihrer Anwendungsumgebung aus zugänglich ist.