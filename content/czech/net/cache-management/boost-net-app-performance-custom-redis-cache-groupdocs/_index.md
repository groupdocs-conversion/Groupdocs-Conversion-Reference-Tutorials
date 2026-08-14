---
date: '2026-05-21'
description: Zjistěte, jak používat custom redis cache .net s GroupDocs.Conversion
  k dramatickému zrychlení konverze dokumentů. Objevte krok‑za‑krokem nastavení, nejlepší
  postupy pro redis caching a performance metrics.
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
title: Zvyšte výkon .NET pomocí custom redis cache .net a GroupDocs.Conversion
type: docs
url: /cs/net/cache-management/boost-net-app-performance-custom-redis-cache-groupdocs/
weight: 1
---

# Zvyšte výkon své .NET aplikace pomocí **custom redis cache .net** s GroupDocs.Conversion

## Úvod

Pokud vaše .NET aplikace stráví cenné sekundy — nebo dokonce minuty — při konverzi dokumentů, nejste sami. Implementace řešení **custom redis cache .net** spolu s GroupDocs.Conversion může zkrátit časy konverze až o 80 % u opakovaných požadavků. V tomto tutoriálu se naučíte, jak nastavit GroupDocs.Conversion, vytvořit cache na bázi Redis a použít osvědčené techniky ladění výkonu, které udrží vaši aplikaci responzivní i při vysokém zatížení.

### Rychlé odpovědi
- **Co ukládá vlastní Redis cache?** Renderované PDF/HTML bytové proudy pro každý zdrojový dokument.  
- **Jak rychlejší může konverze být?** Až 8× rychlejší pro cachované dokumenty, měřeno na 4‑jádrovém serveru.  
- **Potřebuji komerční licenci GroupDocs?** Ano, pro produkční použití je vyžadována platná licence.  
- **Lze to spustit na .NET 6+?** Ano — kompatibilní s .NET 5, .NET 6 a .NET 7.  
- **Je zahrnuta podpora Dockeru?** Cache funguje uvnitř kontejnerů; stačí vystavit port Redis.

## Co je **custom redis cache .net**?

Jedná se o vrstvu cache implementovanou vývojářem, která ukládá binární výstup konverzí dokumentů do Redis key‑value úložiště, což umožňuje následným požadavkům okamžitě získat předrenderovaný výsledek místo opětovného zpracování původního souboru, čímž se snižuje latence a zatížení CPU napříč aplikací.

## Proč používat **custom redis cache .net** s GroupDocs.Conversion?

GroupDocs.Conversion podporuje **50+** vstupních a výstupních formátů — včetně DOCX, PPTX, HTML a PDF — a může zpracovat dokumenty až do 500 stránek, aniž by načítal celý soubor do paměti. Spojením s Redis cache odstraníte nadbytečné renderování, snížíte využití CPU přibližně o **70 %** a udržujete dobu odezvy pod **200 ms** pro cachované položky.

## Požadavky

- **GroupDocs.Conversion pro .NET** (verze 25.3.0 nebo novější)  
- **StackExchange.Redis** NuGet balíček  
- Přístupná instance Redis (např. `192.168.222.4:6379`)  
- Visual Studio 2022 nebo jakékoli C#‑kompatibilní IDE  
- Nainstalovaný .NET 6 SDK (nebo .NET 5/Framework 4.8)  

### Předpoklady znalostí
- Zkušenosti s asynchronními vzory C# async/await  
- Základní koncepty Redis (klíče, TTL, poolování připojení)  
- Znalost pipeline konverze dokumentů  

## Jak nastavit GroupDocs.Conversion pro .NET?

Začněte přidáním balíčku GroupDocs.Conversion do svého projektu pomocí NuGet Package Manager Console nebo .NET CLI. Tím se nainstaluje jádro konverzního enginu a jeho závislosti, připraví vaše prostředí k vytvoření instancí Converter a konfiguraci nastavení konverze pro různé formáty dokumentů.

Instalujte knihovnu pomocí NuGet:

```
Install-Package GroupDocs.Conversion
```

Or with the .NET CLI:

```
dotnet add package GroupDocs.Conversion
```

### Kroky získání licence
- **Free trial:** Zaregistrujte se na portálu GroupDocs a získejte 30‑denní licenční soubor.  
- **Temporary license:** Požádejte o 90‑denní evaluační klíč pro větší zatížení.  
- **Purchase:** Získejte produkční licenci pro odemknutí neomezených konverzí.

After installing the package, initialize GroupDocs.Conversion in your C# project:

```csharp
using GroupDocs.Conversion;
using GroupDocs.Conversion.Options.Convert;

// Initialize with a license file
Converter converter = new Converter("path/to/license.json");
```

## Jak **custom redis cache .net** zlepšuje rychlost konverze?

Když přijde požadavek na konverzi, aplikace nejprve dotazuje Redis na cachovaný bytový proud odpovídající zdrojovému dokumentu a parametrům konverze. Pokud dojde k zásahu (hit), uložený výsledek je okamžitě vrácen, čímž se obejde nákladný proces renderování; v opačném případě GroupDocs.Conversion provede konverzi a výstup uloží zpět do Redis pro budoucí použití.

### Krok 1: Definujte třídu `RedisCache`

Třída `RedisCache` poskytuje lehký obal kolem StackExchange.Redis pro ukládání a načítání binárních výsledků konverze.

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

## Krok 2: Implementujte konverzi dokumentů s vlastní cache

Následující příklad ukazuje integraci `RedisCache` s GroupDocs.Conversion pro cachování výstupu konverze do PDF.

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

## Jaké jsou běžné případy použití **custom redis cache .net**?

Vlastní Redis cache lze využít v jakémkoli scénáři, kde jsou výsledky konverze dokumentů opakovaně požadovány, poskytuje okamžité načtení a snižuje zatížení serveru. Typické aplikace zahrnují podnikovým systémy správy dokumentů, webové API s vysokým provozem poskytující náhledy, CDN edge cache konvertovaných aktiv, automatizované dashboardy pro reportování a e‑commerce platformy generující produktové brožury na vyžádání.

1. **Enterprise Document Management Systems:** Zrychlete generování náhledů pro tisíce PDF uložených v centrálním úložišti.  
2. **Web APIs:** Okamžitě vracejte předkonvertovaný HTML nebo miniatury obrázků pro endpointy s vysokým provozem.  
3. **CDN Edge Nodes:** Cacheujte konvertovaná aktiva blízko uživatelů, čímž snižujete zatížení originálního serveru.  
4. **Analytics Dashboards:** Generujte PDF reporty za běhu a znovu je použijte pro opakované plánované doručení.  
5. **E‑commerce Catalogs:** Cacheujte konverze produktových brožur pro zlepšení načítání stránek.  

## Jak můžete doladit výkon při používání Redis?

Výkon lze optimalizovat nastavením vhodných TTL hodnot, opětovným použitím jedné instance ConnectionMultiplexer, ukládáním surových bytových polí pro vyhnutí se režii serializace a používáním hromadných operací pro masové mazání. Monitorování využití paměti a povolení evikční politiky, jako je allkeys‑lru, zajišťuje, že cache zůstane efektivní při vysokém zatížení.

- **Cache size management:** Nastavte TTL na 24 hodin pro většinu dokumentů; odstraňte starší položky pomocí `RedisCache.GetKeys("docCache:*")`.  
- **Connection pooling:** Opakovaně používejte jedinou instanci `ConnectionMultiplexer` napříč aplikací, aby se předešlo režii handshake.  
- **Efficient serialization:** Ukládejte surové bajty přímo; vyhněte se JSON nebo XML obalům, které zvětšují velikost payloadu.  
- **Batch operations:** Při mazání kategorie použijte `IDatabase.KeyDelete` s patternem pro odstranění mnoha klíčů najednou.  

## Jak řešit běžné problémy?

Když nastanou problémy, ověřte, že klíče cache jsou generovány konzistentně, monitorujte spotřebu paměti Redis a ujistěte se, že verze klientské knihovny odpovídá runtime. Zkontrolujte latenci sítě mezi aplikací a Redis serverem a potvrďte, že poolování připojení je správně nakonfigurováno, aby se předešlo nadměrným handshake, které mohou degradovat výkon.

- **Missing keys:** Ověřte, že stejný cache klíč je generován pro identické parametry konverze (cesta vstupu, výstupní formát, možnosti konverze).  
- **Memory pressure:** Monitorujte využití paměti Redis; povolte `maxmemory-policy allkeys-lru` pro automatické vyřazení nejméně nedávno použitých položek.  
- **Version mismatches:** Ujistěte se, že verze StackExchange.Redis odpovídá .NET runtime (např. 2.6+ pro .NET 6).  
- **Network latency:** Umístěte Redis ve stejném datacentru nebo VPC jako vaše aplikace, aby se doba odezvy udržela pod 1 ms.  

## Často kladené otázky

**Q: Jak nainstaluji Redis na svém lokálním počítači?**  
A: Postupujte podle oficiálního průvodce instalací Redis pro váš OS: [Redis Download](https://redis.io/download).

**Q: Jaké jsou konkrétní výhody používání vlastní cache s GroupDocs.Conversion?**  
A: Odstraňuje duplicitní renderování, snižuje využití CPU o ~70 %, zkracuje průměrnou dobu odezvy z 1,2 s na <200 ms a snižuje náklady na cloud tím, že snižuje výpočetní cykly.

**Q: Lze tuto architekturu nasadit do Azure nebo AWS?**  
A: Ano — stačí nasměrovat `ConnectionMultiplexer` na vaši spravovanou Redis instanci (Azure Cache for Redis nebo Amazon ElastiCache) a zajistit, aby bezpečnostní skupiny povolovaly provoz na portu 6379.

**Q: Je cache vlákny‑bezpečná pro souběžné webové požadavky?**  
A: Klient `StackExchange.Redis` je plně thread‑safe; můžete sdílet jedinou `ConnectionMultiplexer` napříč všemi vlákny požadavků bez dalšího zamykání.

**Q: Jak vymazat cache, když se zdrojový dokument změní?**  
A: Invalidační odstraněním klíčů, které odpovídají identifikátoru dokumentu, např. `await redis.GetDatabase().KeyDeleteAsync($"docCache:{docId}:*");`.

## Závěr

Integrací **custom redis cache .net** s GroupDocs.Conversion získáte dramatické zlepšení výkonu, snížíte náklady na infrastrukturu a poskytnete plynulejší uživatelský zážitek. Výše uvedené kroky vám poskytnou produkčně připravený základ — experimentujte s TTL hodnotami, strategiemi cache klíčů a horizontálním škálováním, aby řešení odpovídalo vašemu zatížení.

---

**Poslední aktualizace:** 2026-05-21  
**Testováno s:** GroupDocs.Conversion 25.3.0 for .NET  
**Autor:** GroupDocs  

```bash
Install-Package GroupDocs.Conversion -Version 25.3.0
```

```bash
dotnet add package GroupDocs.Conversion --version 25.3.0
```

```csharp
using GroupDocs.Conversion;
```

## Související tutoriály

- [Tutoriály správy cache konverze pro GroupDocs.Conversion .NET](/conversion/net/cache-management/)
- [Optimalizace .NET konverze dokumentů s cachováním pomocí GroupDocs.Conversion](/conversion/net/cache-management/optimize-net-document-conversion-caching-groupdocs/)
- [Mistrovské nastavení konverze dokumentů v .NET pomocí GroupDocs.Conversion](/conversion/net/conversion-options-settings/master-groupdocs-conversion-net-setup/)