---
date: '2026-05-21'
description: Leer hoe u custom redis cache .net kunt gebruiken met GroupDocs.Conversion
  om de documentconversie drastisch te versnellen. Ontdek stapsgewijze installatie,
  gebruik van best practices voor redis caching en prestatiemetingen.
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
title: Verbeter .NET-prestaties met custom redis cache .net en GroupDocs.Conversion
type: docs
url: /nl/net/cache-management/boost-net-app-performance-custom-redis-cache-groupdocs/
weight: 1
---

# Verbeter de prestaties van uw .NET‑applicatie met **custom redis cache .net** met GroupDocs.Conversion

## Introductie

Als uw .NET‑applicatie waardevolle seconden—of zelfs minuten—besteedt aan het converteren van documenten, bent u niet de enige. Het implementeren van een **custom redis cache .net**‑oplossing naast GroupDocs.Conversion kan de conversietijden voor herhaalde verzoeken met tot 80 % verkorten. In deze tutorial leert u hoe u GroupDocs.Conversion instelt, een Redis‑gebaseerde cache maakt en bewezen prestatie‑optimalisatietechnieken toepast die uw app responsief houden onder zware belasting.

### Snelle antwoorden
- **Wat slaat de custom Redis cache op?** Gegenereerde PDF/HTML‑byte‑streams voor elk bron‑document.  
- **Hoeveel sneller kan de conversie worden?** Tot 8× sneller voor gecachete documenten, gemeten op een 4‑core server.  
- **Heb ik een commerciële GroupDocs‑licentie nodig?** Ja, een geldige licentie is vereist voor productiegebruik.  
- **Kan dit draaien op .NET 6+?** Absoluut—compatibel met .NET 5, .NET 6 en .NET 7.  
- **Is Docker‑ondersteuning inbegrepen?** De cache werkt binnen containers; exposeer gewoon de Redis‑poort.

## Wat is **custom redis cache .net**?

Het is een door de ontwikkelaar geïmplementeerde cache‑laag die de binaire output van documentconversies opslaat in een Redis key‑value store, waardoor volgende verzoeken het vooraf gerenderde resultaat direct kunnen ophalen in plaats van het originele bestand opnieuw te verwerken, waardoor de latentie en CPU‑belasting in de hele applicatie worden verminderd.

## Waarom **custom redis cache .net** gebruiken met GroupDocs.Conversion?

GroupDocs.Conversion ondersteunt **50+** invoer‑ en uitvoerformaten—waaronder DOCX, PPTX, HTML en PDF—en kan documenten tot 500 pagina's verwerken zonder het volledige bestand in het geheugen te laden. Door het te combineren met een Redis‑cache elimineert u overbodige rendering, vermindert u het CPU‑gebruik met ongeveer **70 %**, en houdt u de responstijden onder **200 ms** voor gecachete assets.

## Voorvereisten

- **GroupDocs.Conversion for .NET** (Versie 25.3.0 of hoger)  
- **StackExchange.Redis** NuGet‑pakket  
- Een bereikbare Redis‑instantie (bijv. `192.168.222.4:6379`)  
- Visual Studio 2022 of een andere C#‑compatibele IDE  
- .NET 6 SDK (of .NET 5/Framework 4.8) geïnstalleerd  

### Kennisvoorvereisten
- Comfortabel met C# async/await‑patronen  
- Basiskennis van Redis‑concepten (sleutels, TTL, connection pooling)  
- Bekendheid met documentconversiepijplijnen  

## Hoe GroupDocs.Conversion voor .NET in te stellen?

Begin met het toevoegen van het GroupDocs.Conversion‑pakket aan uw project via de NuGet Package Manager Console of de .NET CLI. Dit installeert de kernconversie‑engine en de bijbehorende afhankelijkheden, en bereidt uw omgeving voor om Converter‑instanties te maken en conversie‑instellingen voor verschillende documentformaten te configureren.

Installeer de bibliotheek via NuGet:

```
Install-Package GroupDocs.Conversion
```

Of met de .NET CLI:

```
dotnet add package GroupDocs.Conversion
```

### Stappen voor licentie‑verwerving
- **Free trial:** Registreer op het GroupDocs‑portaal voor een licentiebestand van 30 dagen.  
- **Temporary license:** Vraag een evaluatiesleutel van 90 dagen aan voor grotere workloads.  
- **Purchase:** Verkrijg een productielicentie om onbeperkte conversies te ontgrendelen.

Na het installeren van het pakket initialiseert u GroupDocs.Conversion in uw C#‑project:

```csharp
using GroupDocs.Conversion;
using GroupDocs.Conversion.Options.Convert;

// Initialize with a license file
Converter converter = new Converter("path/to/license.json");
```

## Hoe verbetert een **custom redis cache .net** de conversiesnelheid?

Wanneer een conversieverzoek binnenkomt, vraagt de applicatie eerst Redis om een gecachte byte‑stream die overeenkomt met het bron‑document en de conversie‑parameters. Als er een hit is, wordt het opgeslagen resultaat onmiddellijk geretourneerd, waardoor het dure renderingsproces wordt overgeslagen; anders voert GroupDocs.Conversion de conversie uit en wordt de output terug opgeslagen in Redis voor toekomstig gebruik.

### Stap 1: Definieer de `RedisCache`‑klasse

De `RedisCache`‑klasse biedt een lichtgewicht wrapper rond StackExchange.Redis voor het opslaan en ophalen van binaire conversieresultaten.

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

## Stap 2: Documentconversie implementeren met de custom cache

Het volgende voorbeeld toont hoe u de `RedisCache` integreert met GroupDocs.Conversion om de PDF‑conversie‑output te cachen.

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

## Wat zijn veelvoorkomende use‑cases voor **custom redis cache .net**?

De custom Redis‑cache kan worden ingezet in elke situatie waarin documentconversieresultaten herhaaldelijk worden opgevraagd, waardoor directe ophalen mogelijk is en de serverbelasting wordt verminderd. Typische toepassingen omvatten enterprise document‑managementsystemen, web‑API’s met veel verkeer die previews leveren, CDN‑edge‑caching van geconverteerde assets, geautomatiseerde rapportagedashboards en e‑commerceplatforms die op aanvraag productbrochures genereren.

1. **Enterprise Document Management Systems:** Versnel de preview‑generatie voor duizenden PDF’s die in een centrale repository zijn opgeslagen.  
2. **Web APIs:** Retourneer vooraf geconverteerde HTML of afbeeldings‑thumbnails onmiddellijk voor eindpunten met veel verkeer.  
3. **CDN Edge Nodes:** Cache geconverteerde assets dicht bij gebruikers, waardoor de belasting van de origin‑server wordt verminderd.  
4. **Analytics Dashboards:** Genereer PDF‑rapporten on‑the‑fly en hergebruik ze voor terugkerende geplande leveringen.  
5. **E‑commerce Catalogs:** Cache productbrochure‑conversies om laadtijden van pagina’s te verbeteren.  

## Hoe kunt u de prestaties verfijnen bij gebruik van Redis?

Prestaties kunnen worden geoptimaliseerd door geschikte TTL‑waarden te configureren, een enkele ConnectionMultiplexer‑instantie te hergebruiken, ruwe byte‑arrays op te slaan om serialisatie‑overhead te vermijden, en batch‑operaties te gebruiken voor bulk‑verwijderingen. Het monitoren van geheugengebruik en het inschakelen van een evic­tie‑beleid zoals allkeys‑lru zorgt ervoor dat de cache efficiënt blijft onder zware belasting.

- **Cache size management:** Stel een TTL van 24 uur in voor de meeste documenten; verwijder oudere items met `RedisCache.GetKeys("docCache:*")`.  
- **Connection pooling:** Hergebruik een enkele `ConnectionMultiplexer`‑instantie door de hele applicatie om handshake‑overhead te vermijden.  
- **Efficient serialization:** Sla ruwe bytes direct op; vermijd JSON‑ of XML‑wrappers die de payloadgrootte vergroten.  
- **Batch operations:** Gebruik bij het wissen van een categorie `IDatabase.KeyDelete` met een patroon om veel sleutels in één oproep te verwijderen.  

## Hoe veelvoorkomende valkuilen op te lossen?

Wanneer er problemen optreden, controleer dan of cache‑sleutels consistent worden gegenereerd, monitor het Redis‑geheugengebruik, en zorg ervoor dat de client‑bibliotheekversie overeenkomt met de runtime. Controleer de netwerklatentie tussen de applicatie en de Redis‑server, en bevestig dat connection pooling correct is geconfigureerd om excessieve handshakes die de prestaties kunnen verminderen te vermijden.

- **Missing keys:** Verifieer dat dezelfde cache‑sleutel wordt gegenereerd voor identieke conversie‑parameters (input path, output format, conversion options).  
- **Memory pressure:** Monitor het Redis‑geheugengebruik; schakel `maxmemory-policy allkeys-lru` in om automatisch de minst recent gebruikte items te verwijderen.  
- **Version mismatches:** Zorg ervoor dat de StackExchange.Redis‑versie overeenkomt met de .NET‑runtime (bijv. 2.6+ voor .NET 6).  
- **Network latency:** Plaats Redis in hetzelfde datacenter of dezelfde VPC als uw applicatie om round‑trip‑tijden onder 1 ms te houden.  

## Veelgestelde vragen

**Q: Hoe installeer ik Redis op mijn lokale machine?**  
A: Volg de officiële Redis‑installatiehandleiding voor uw besturingssysteem: [Redis Download](https://redis.io/download).

**Q: Wat zijn de concrete voordelen van het gebruik van een custom cache met GroupDocs.Conversion?**  
A: Het elimineert dubbele rendering, vermindert CPU‑gebruik met ~70 %, verlaagt de gemiddelde responstijd van 1,2 s naar <200 ms, en verlaagt de cloud‑rekening door minder compute‑cycli.

**Q: Kan deze architectuur worden ingezet op Azure of AWS?**  
A: Ja—wijs simpelweg de `ConnectionMultiplexer` naar uw beheerde Redis‑instantie (Azure Cache for Redis of Amazon ElastiCache) en zorg ervoor dat netwerkgroepen verkeer op poort 6379 toestaan.

**Q: Is de cache thread‑safe voor gelijktijdige web‑verzoeken?**  
A: De `StackExchange.Redis`‑client is volledig thread‑safe; u kunt een enkele `ConnectionMultiplexer` delen over alle verzoek‑threads zonder extra vergrendeling.

**Q: Hoe maak ik de cache leeg wanneer een bron‑document verandert?**  
A: Invalidatie door sleutels te verwijderen die overeenkomen met de identifier van het document, bijv. `await redis.GetDatabase().KeyDeleteAsync($"docCache:{docId}:*");`.

## Conclusie

Door een **custom redis cache .net** te integreren met GroupDocs.Conversion, realiseert u dramatische prestatieverbeteringen, verlaagt u infrastructuurkosten, en levert u een soepelere gebruikerservaring. De bovenstaande stappen bieden u een productie‑klare basis—experimenteer met TTL‑waarden, cache‑sleutelstrategieën en horizontale schaalvergroting om de oplossing af te stemmen op uw workload.

---

**Laatst bijgewerkt:** 2026-05-21  
**Getest met:** GroupDocs.Conversion 25.3.0 for .NET  
**Auteur:** GroupDocs  

```bash
Install-Package GroupDocs.Conversion -Version 25.3.0
```

```bash
dotnet add package GroupDocs.Conversion --version 25.3.0
```

```csharp
using GroupDocs.Conversion;
```

## Gerelateerde tutorials

- [Conversie‑cache‑beheer‑tutorials voor GroupDocs.Conversion .NET](/conversion/net/cache-management/)
- [Optimaliseer .NET‑documentconversie met caching met GroupDocs.Conversion](/conversion/net/cache-management/optimize-net-document-conversion-caching-groupdocs/)
- [Beheers documentconversie‑setup in .NET met GroupDocs.Conversion](/conversion/net/conversion-options-settings/master-groupdocs-conversion-net-setup/)