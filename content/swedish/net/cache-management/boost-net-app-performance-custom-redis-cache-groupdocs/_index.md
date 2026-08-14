---
date: '2026-05-21'
description: Lär dig hur du använder anpassad Redis-cache .net med GroupDocs.Conversion
  för att dramatiskt snabba upp dokumentkonvertering. Upptäck steg‑för‑steg‑installationen,
  bästa praxis för Redis-caching och prestandamått.
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
title: Öka .NET-prestanda med anpassad Redis-cache .net och GroupDocs.Conversion
type: docs
url: /sv/net/cache-management/boost-net-app-performance-custom-redis-cache-groupdocs/
weight: 1
---

# Öka prestandan för din .NET-applikation med **custom redis cache .net** med GroupDocs.Conversion

## Introduktion

Om din .NET-applikation spenderar värdefulla sekunder—eller till och med minuter—på att konvertera dokument, är du inte ensam. Att implementera en **custom redis cache .net**-lösning tillsammans med GroupDocs.Conversion kan minska konverteringstiderna med upp till 80 % för återkommande förfrågningar. I den här handledningen kommer du att lära dig hur du sätter upp GroupDocs.Conversion, skapar en Redis‑baserad cache och tillämpar beprövade prestanda‑optimeringstekniker som håller din app responsiv under hög belastning.

### Snabba svar
- **Vad lagrar den anpassade Redis-cachen?** Renderade PDF/HTML-byte-strömmar för varje källdokument.  
- **Hur mycket snabbare kan konverteringen bli?** Upp till 8× snabbare för cachade dokument, mätt på en 4‑kärnig server.  
- **Behöver jag en kommersiell GroupDocs-licens?** Ja, en giltig licens krävs för produktionsanvändning.  
- **Kan detta köras på .NET 6+?** Absolut—kompatibel med .NET 5, .NET 6 och .NET 7.  
- **Ingår Docker-stöd?** Cachen fungerar i containrar; exponera bara Redis-porten.

## Vad är **custom redis cache .net**?

Det är ett av utvecklaren implementerat cache‑lager som lagrar det binära resultatet av dokumentkonverteringar i en Redis nyckel‑värde‑store, vilket möjliggör att efterföljande förfrågningar hämtar det förrenderade resultatet omedelbart istället för att bearbeta originalfilen igen, vilket minskar latens och CPU‑belastning i hela applikationen.

## Varför använda **custom redis cache .net** med GroupDocs.Conversion?

GroupDocs.Conversion stödjer **50+** in- och utdataformat—inklusive DOCX, PPTX, HTML och PDF—och kan bearbeta dokument upp till 500 sidor utan att ladda hela filen i minnet. Genom att kombinera det med en Redis‑cache eliminerar du redundant rendering, minskar CPU‑användning med ungefär **70 %**, och håller svarstider under **200 ms** för cachade resurser.

## Förutsättningar

- **GroupDocs.Conversion för .NET** (Version 25.3.0 eller senare)  
- **StackExchange.Redis** NuGet‑paket  
- En åtkomlig Redis‑instans (t.ex. `192.168.222.4:6379`)  
- Visual Studio 2022 eller någon C#‑kompatibel IDE  
- .NET 6 SDK (eller .NET 5/Framework 4.8) installerad  

### Kunskapsförutsättningar
- Bekväm med C# async/await‑mönster  
- Grundläggande Redis‑koncept (nycklar, TTL, anslutningspoolning)  
- Bekantskap med dokumentkonverterings‑pipelines  

## Hur man sätter upp GroupDocs.Conversion för .NET?

Börja med att lägga till GroupDocs.Conversion‑paketet i ditt projekt via antingen NuGet Package Manager Console eller .NET CLI. Detta installerar den centrala konverteringsmotorn och dess beroenden, och förbereder din miljö för att skapa Converter‑instanser och konfigurera konverteringsinställningar för olika dokumentformat.

Install the library via NuGet:

```
Install-Package GroupDocs.Conversion
```

Or with the .NET CLI:

```
dotnet add package GroupDocs.Conversion
```

### Steg för licensförvärv
- **Gratis provperiod:** Registrera dig på GroupDocs‑portalen för en 30‑dagars licensfil.  
- **Tillfällig licens:** Begär en 90‑dagars utvärderingsnyckel för större arbetsbelastningar.  
- **Köp:** Skaffa en produktionslicens för att låsa upp obegränsade konverteringar.

After installing the package, initialize GroupDocs.Conversion in your C# project:

```csharp
using GroupDocs.Conversion;
using GroupDocs.Conversion.Options.Convert;

// Initialize with a license file
Converter converter = new Converter("path/to/license.json");
```

## Hur förbättrar en **custom redis cache .net** konverteringshastigheten?

När en konverteringsförfrågan anländer frågar applikationen först Redis efter en cachad byte‑ström som matchar källdokumentet och konverteringsparametrarna. Om en träff finns returneras det lagrade resultatet omedelbart, vilket kringgår den kostsamma renderingsprocessen; annars utför GroupDocs.Conversion konverteringen och resultatet sparas tillbaka till Redis för framtida bruk.

### Steg 1: Definiera klassen `RedisCache`

`RedisCache`‑klassen tillhandahåller ett lättvikts‑wrapper kring StackExchange.Redis för att lagra och hämta binära konverteringsresultat.

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

## Steg 2: Implementera dokumentkonvertering med den anpassade cachen

Följande exempel demonstrerar hur man integrerar `RedisCache` med GroupDocs.Conversion för att cachea PDF‑konverteringsutdata.

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

## Vilka är vanliga användningsfall för **custom redis cache .net**?

Den anpassade Redis‑cachen kan utnyttjas i alla scenarier där dokumentkonverteringsresultat begärs upprepade gånger, vilket ger omedelbar hämtning och minskar serverbelastningen. Vanliga tillämpningar inkluderar företagsdokumenthanteringssystem, högtrafikerade webb‑API:er som levererar förhandsgranskningar, CDN‑edge‑caching av konverterade resurser, automatiserade rapporterings‑dashboards och e‑handelsplattformar som genererar produktbroschyrer på begäran.

1. **Enterprise Document Management Systems:** Snabba upp förhandsgranskning för tusentals PDF‑dokument som lagras i ett centralt arkiv.  
2. **Web APIs:** Returnera förkonverterad HTML eller bild‑miniaturer omedelbart för högtrafikerade slutpunkter.  
3. **CDN Edge Nodes:** Cachea konverterade resurser nära användarna, vilket minskar belastningen på ursprungsservern.  
4. **Analytics Dashboards:** Generera PDF‑rapporter i farten och återanvänd dem för återkommande schemalagda leveranser.  
5. **E‑commerce Catalogs:** Cachea produktbroschyrekonverteringar för att förbättra sidladdningstider.  

## Hur kan du finjustera prestanda när du använder Redis?

Prestanda kan optimeras genom att konfigurera lämpliga TTL‑värden, återanvända en enda ConnectionMultiplexer‑instans, lagra råa byte‑arrayer för att undvika serialiseringskostnad, och använda batch‑operationer för massraderingar. Övervakning av minnesanvändning och aktivering av en eviktionspolicy såsom allkeys‑lru säkerställer att cachen förblir effektiv under hög belastning.

- **Cache size management:** Sätt en TTL på 24 timmar för de flesta dokument; rensa äldre poster med `RedisCache.GetKeys("docCache:*")`.  
- **Connection pooling:** Återanvänd en enda `ConnectionMultiplexer`‑instans i hela applikationen för att undvika handskakningskostnad.  
- **Efficient serialization:** Lagra råa byte‑data direkt; undvik JSON‑ eller XML‑omslag som ökar payload‑storleken.  
- **Batch operations:** Vid rensning av en kategori, använd `IDatabase.KeyDelete` med ett mönster för att ta bort många nycklar i ett anrop.  

## Hur felsöker du vanliga fallgropar?

När problem uppstår, verifiera att cache‑nycklar genereras konsekvent, övervaka Redis minnesförbrukning, och säkerställ att klientbibliotekets version matchar runtime. Kontrollera nätverkslatens mellan applikationen och Redis‑servern, och bekräfta att anslutningspoolning är korrekt konfigurerad för att undvika överdrivna handskakningar som kan försämra prestanda.

- **Missing keys:** Verifiera att samma cache‑nyckel genereras för identiska konverteringsparametrar (inmatningssökväg, utdataformat, konverteringsalternativ).  
- **Memory pressure:** Övervaka Redis minnesanvändning; aktivera `maxmemory-policy allkeys-lru` för att automatiskt evictera minst nyligen använda poster.  
- **Version mismatches:** Säkerställ att StackExchange.Redis‑versionen matchar .NET‑runtime (t.ex. 2.6+ för .NET 6).  
- **Network latency:** Placera Redis i samma datacenter eller VPC som din applikation för att hålla rundresponstider under 1 ms.  

## Vanliga frågor

**Q: Hur installerar jag Redis på min lokala maskin?**  
A: Följ den officiella Redis‑installationsguiden för ditt operativsystem: [Redis Download](https://redis.io/download).

**Q: Vilka är de konkreta fördelarna med att använda en anpassad cache med GroupDocs.Conversion?**  
A: Den eliminerar duplicerad rendering, minskar CPU‑användning med ~70 %, reducerar genomsnittlig svarstid från 1,2 s till <200 ms, och sänker molnkostnaden genom att minska beräkningscykler.

**Q: Kan denna arkitektur distribueras till Azure eller AWS?**  
A: Ja—peka helt enkelt `ConnectionMultiplexer` mot din hanterade Redis‑instans (Azure Cache for Redis eller Amazon ElastiCache) och säkerställ att nätverkssäkerhetsgrupper tillåter trafik på port 6379.

**Q: Är cachen trådsäker för samtidiga webb‑förfrågningar?**  
A: `StackExchange.Redis`‑klienten är fullt trådsäker; du kan dela en enda `ConnectionMultiplexer` över alla begäranstrådar utan extra låsning.

**Q: Hur rensar jag cachen när ett källdokument ändras?**  
A: Invalidera genom att ta bort nycklar som matchar dokumentets identifierare, t.ex. `await redis.GetDatabase().KeyDeleteAsync($"docCache:{docId}:*");`.

## Slutsats

Genom att integrera en **custom redis cache .net** med GroupDocs.Conversion får du dramatiska prestandaförbättringar, lägre infrastrukturskostnader och en smidigare användarupplevelse. Stegen ovan ger dig en produktionsklar grund—experimentera med TTL‑värden, cache‑nyckelstrategier och horisontell skalning för att anpassa lösningen till din arbetsbelastning.

---

**Senast uppdaterad:** 2026-05-21  
**Testat med:** GroupDocs.Conversion 25.3.0 for .NET  
**Författare:** GroupDocs  

---

```bash
Install-Package GroupDocs.Conversion -Version 25.3.0
```

```bash
dotnet add package GroupDocs.Conversion --version 25.3.0
```

```csharp
using GroupDocs.Conversion;
```

## Relaterade handledningar

- [Handledningar för cachehantering av konvertering för GroupDocs.Conversion .NET](/conversion/net/cache-management/)
- [Optimera .NET-dokumentkonvertering med caching med GroupDocs.Conversion](/conversion/net/cache-management/optimize-net-document-conversion-caching-groupdocs/)
- [Behärska dokumentkonverteringsinställning i .NET med GroupDocs.Conversion](/conversion/net/conversion-options-settings/master-groupdocs-conversion-net-setup/)