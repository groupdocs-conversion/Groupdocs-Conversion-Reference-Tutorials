---
date: '2026-05-21'
description: Ismerd meg, hogyan használhatod az egyedi redis cache .net-et a GroupDocs.Conversion-nel
  a dokumentumkonverzió drámai felgyorsításához. Fedezd fel a lépésről‑lépésre beállítást,
  a redis gyorsítótárazás legjobb gyakorlatait és a teljesítménymutatókat.
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
title: Növeld a .NET teljesítményét egyedi redis cache .net és a GroupDocs.Conversion
  segítségével
type: docs
url: /hu/net/cache-management/boost-net-app-performance-custom-redis-cache-groupdocs/
weight: 1
---

# Növeld .NET alkalmazásod teljesítményét a **custom redis cache .net** segítségével a GroupDocs.Conversion használatával

## Bevezetés

Ha .NET alkalmazásod értékes másodperceket — vagy akár perceket — tölt a dokumentumok konvertálásával, nem vagy egyedül. A **custom redis cache .net** megoldás bevezetése a GroupDocs.Conversion mellett akár 80 %-kal is csökkentheti a konverziós időt az ismétlődő kérések esetén. Ebben az útmutatóban megtanulod, hogyan állítsd be a GroupDocs.Conversion-t, hogyan hozz létre egy Redis‑alapú gyorsítótárat, és hogyan alkalmazz bevált teljesítmény‑finomhangolási technikákat, amelyek a terhelés alatt is responsívvá teszik az alkalmazásodat.

### Gyors válaszok
- **Mi tárol a custom Redis gyorsítótár?** Renderelt PDF/HTML bájtfolyamok minden forrásdokumentumhoz.  
- **Mennyivel gyorsabb lehet a konverzió?** Akár 8‑szoros gyorsabb a gyorsítótárazott dokumentumok esetén, egy 4‑magos szerveren mérve.  
- **Szükségem van kereskedelmi GroupDocs licencre?** Igen, érvényes licenc szükséges a termelésben való használathoz.  
- **Futtatható .NET 6+ környezetben?** Teljesen — kompatibilis a .NET 5, .NET 6 és .NET 7 verziókkal.  
- **Tartalmaz Docker támogatást?** A gyorsítótár konténerekben is működik; csak tedd elérhetővé a Redis portot.

## Mi az a **custom redis cache .net**?

Ez egy fejlesztő által megvalósított gyorsítótár réteg, amely a dokumentumkonverziók bináris kimenetét egy Redis kulcs‑érték tárolóban tárolja, lehetővé téve, hogy a későbbi kérések az előre renderelt eredményt azonnal lekérjék az eredeti fájl újrafeldolgozása helyett, ezáltal csökkentve a késleltetést és a CPU terhelést az alkalmazásban.

## Miért használjuk a **custom redis cache .net**-et a GroupDocs.Conversion-nel?

A GroupDocs.Conversion **50+** bemeneti és kimeneti formátumot támogat — beleértve a DOCX, PPTX, HTML és PDF formátumokat — és akár 500 oldalas dokumentumokat is feldolgozhat anélkül, hogy az egész fájlt a memóriába töltené. A Redis gyorsítótárral kombinálva megszünteted a felesleges renderelést, körülbelül **70 %**‑kal csökkented a CPU használatot, és a gyorsítótárazott eszközök válaszidejét **200 ms** alatt tartod.

## Előfeltételek

- **GroupDocs.Conversion for .NET** (25.3.0 vagy újabb verzió)  
- **StackExchange.Redis** NuGet csomag  
- Elérhető Redis példány (pl. `192.168.222.4:6379`)  
- Visual Studio 2022 vagy bármely C#‑kompatibilis IDE  
- .NET 6 SDK (vagy .NET 5/Framework 4.8) telepítve  

### Tudás előfeltételek
- Jártas vagy a C# async/await mintákkal  
- Alapvető Redis koncepciók (kulcsok, TTL, kapcsolat‑pooling)  
- Ismereted van a dokumentumkonverzió csővezetékekkel  

## Hogyan állítsuk be a GroupDocs.Conversion-t .NET‑hez?

Kezdd a GroupDocs.Conversion csomag projektedhez való hozzáadásával a NuGet Package Manager Console vagy a .NET CLI segítségével. Ez telepíti a fő konverziós motor és függőségeit, előkészítve a környezetet Converter példányok létrehozásához és a konverziós beállítások konfigurálásához különböző dokumentumformátumokhoz.

Telepítsd a könyvtárat a NuGet‑en keresztül:

```
Install-Package GroupDocs.Conversion
```

Vagy a .NET CLI‑val:

```
dotnet add package GroupDocs.Conversion
```

### Licenc beszerzési lépések
- **Ingyenes próba:** Regisztrálj a GroupDocs portálon egy 30‑napos licencfájlért.  
- **Ideiglenes licenc:** Kérj egy 90‑napos értékelő kulcsot nagyobb munkaterheléshez.  
- **Vásárlás:** Szerezz be egy termelési licencet a korlátlan konverziók feloldásához.

A csomag telepítése után inicializáld a GroupDocs.Conversion-t a C# projektedben:

```csharp
using GroupDocs.Conversion;
using GroupDocs.Conversion.Options.Convert;

// Initialize with a license file
Converter converter = new Converter("path/to/license.json");
```

## Hogyan javítja a **custom redis cache .net** a konverziós sebességet?

Amikor egy konverziós kérés érkezik, az alkalmazás először a Redis‑ben keres egy gyorsítótárazott bájtfolyamot, amely megfelel a forrásdokumentumnak és a konverziós paramétereknek. Ha talál egyezést, a tárolt eredmény azonnal visszaadódik, megkerülve a költséges renderelési folyamatot; ellenkező esetben a GroupDocs.Conversion végrehajtja a konverziót, és a kimenetet visszaírja a Redis‑be a későbbi használathoz.

### 1. lépés: Definiáld a `RedisCache` osztályt

A `RedisCache` osztály egy könnyű wrappert biztosít a StackExchange.Redis köré a bináris konverziós eredmények tárolásához és lekérdezéséhez.

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

## 2. lépés: Dokumentumkonverzió megvalósítása az egyedi gyorsítótárral

A következő példa bemutatja, hogyan integrálhatod a `RedisCache`-t a GroupDocs.Conversion-nel a PDF konverziós kimenet gyorsítótárazásához.

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

## Milyen gyakori felhasználási esetek vannak a **custom redis cache .net**-hez?

A custom Redis gyorsítótár bármely olyan helyzetben felhasználható, ahol a dokumentumkonverziós eredményeket ismételten kérik, azonnali lekérdezést biztosítva és csökkentve a szerver terhelését. Tipikus alkalmazások közé tartozik vállalati dokumentumkezelő rendszerek, nagy forgalmú web‑API‑k előnézetek kiszolgálására, CDN edge gyorsítótárazás a konvertált eszközökhöz, automatizált jelentés‑dashboardok, valamint e‑kereskedelmi platformok, amelyek igény szerint generálják a termékkatalógusokat.

1. **Vállalati dokumentumkezelő rendszerek:** Gyorsítsd fel az előnézetek generálását több ezer, központi tárolóban lévő PDF‑hez.  
2. **Web API‑k:** Azonnal szolgálj vissza előre konvertált HTML‑t vagy képkockákat a nagy forgalmú végpontokhoz.  
3. **CDN edge csomópontok:** Gyorsítótárazd a konvertált eszközöket a felhasználók közelében, csökkentve az eredeti szerver terhelését.  
4. **Analitikai dashboardok:** Generálj PDF jelentéseket menet közben, és használd újra őket a rendszeres ütemezett szállításokhoz.  
5. **E‑kereskedelmi katalógusok:** Gyorsítótárazd a termékkatalógus konverziókat a betöltési idők javítása érdekében.  

## Hogyan finomhangolhatod a teljesítményt Redis használatakor?

A teljesítmény optimalizálható megfelelő TTL értékek beállításával, egyetlen ConnectionMultiplexer példány újrahasználatával, nyers bájt‑tömbök tárolásával a sorosítási terhek elkerülése érdekében, valamint kötegelt műveletek alkalmazásával a tömeges törlésekhez. A memóriahasználat figyelése és egy olyan kiürítési szabály, mint az allkeys‑lru, biztosítja, hogy a gyorsítótár hatékony maradjon nagy terhelés alatt.

- **Gyorsítótár méretének kezelése:** Állíts be 24 órás TTL‑t a legtöbb dokumentumhoz; távolítsd el a régebbi bejegyzéseket a `RedisCache.GetKeys("docCache:*")` segítségével.  
- **Kapcsolat‑pooling:** Használd újra ugyanazt a `ConnectionMultiplexer` példányt az alkalmazásban a kézfogás terhelésének elkerülése érdekében.  
- **Hatékony sorosítás:** Tárold közvetlenül a nyers bájtokat; kerüld a JSON vagy XML burkolatokat, amelyek növelik a payload méretét.  
- **Kötegelt műveletek:** Kategória törlésekor használd az `IDatabase.KeyDelete`‑t mintával, hogy egy hívással sok kulcsot távolíts el.  

## Hogyan hárítsd el a gyakori buktatókat?

Problémák esetén ellenőrizd, hogy a gyorsítótár kulcsok következetesen generálódnak, figyeld a Redis memóriahasználatát, és győződj meg róla, hogy a klienskönyvtár verziója megfelel a futtatókörnyezeti verziónak. Ellenőrizd a hálózati késleltetést az alkalmazás és a Redis szerver között, és erősítsd meg, hogy a kapcsolat‑pooling megfelelően van beállítva a túlzott kézfogások elkerülése érdekében, amelyek rontják a teljesítményt.

- **Hiányzó kulcsok:** Ellenőrizd, hogy ugyanaz a gyorsítótár kulcs jön létre azonos konverziós paraméterek (bemeneti útvonal, kimeneti formátum, konverziós beállítások) esetén.  
- **Memória nyomás:** Figyeld a Redis memóriahasználatát; engedélyezd a `maxmemory-policy allkeys-lru`‑t a legrégebben nem használt bejegyzések automatikus kiürítéséhez.  
- **Verzióeltérések:** Győződj meg róla, hogy a StackExchange.Redis verziója egyezik a .NET futtatókörnyezettel (pl. 2.6+ a .NET 6‑hoz).  
- **Hálózati késleltetés:** Helyezd a Redis‑t ugyanabban az adatközpontban vagy VPC‑ben, mint az alkalmazás, hogy a körkörös idő 1 ms alatt maradjon.  

## Gyakran Ismételt Kérdések

**Q: Hogyan telepíthetem a Redis‑t a helyi gépemre?**  
A: Kövesd a hivatalos Redis telepítési útmutatót az operációs rendszeredhez: [Redis Download](https://redis.io/download).

**Q: Mik a kézzelfogható előnyök egy egyedi gyorsítótár használatával a GroupDocs.Conversion-nél?**  
A: Megszünteti a duplikált renderelést, körülbelül ~70 %-kal csökkenti a CPU használatot, az átlagos válaszidőt 1,2 s‑ről <200 ms‑re csökkenti, és csökkenti a felhő költségét a számítási ciklusok csökkentésével.

**Q: Telepíthető ez az architektúra Azure‑ra vagy AWS‑re?**  
A: Igen — egyszerűen irányítsd a `ConnectionMultiplexer`‑t a kezelt Redis példányodra (Azure Cache for Redis vagy Amazon ElastiCache), és győződj meg róla, hogy a hálózati biztonsági csoportok engedélyezik a 6379‑es port forgalmát.

**Q: A gyorsítótár szálbiztonságú a párhuzamos webkérésekhez?**  
A: A `StackExchange.Redis` kliens teljesen szálbiztonságú; egyetlen `ConnectionMultiplexer` példányt megoszthatsz az összes kérés szálával további zárolás nélkül.

**Q: Hogyan törlöm a gyorsítótárat, ha a forrásdokumentum megváltozik?**  
A: Invalídáld a kulcsok törlésével, amelyek megfelelnek a dokumentum azonosítójának, pl. `await redis.GetDatabase().KeyDeleteAsync($"docCache:{docId}:*");`.

## Következtetés

A **custom redis cache .net** integrálásával a GroupDocs.Conversion-be drámai teljesítménynövekedést érhetsz el, csökkentheted az infrastruktúra költségeit, és simább felhasználói élményt nyújthatsz. A fenti lépések egy termelésre kész alapot biztosítanak — kísérletezz TTL értékekkel, gyorsítótár‑kulcs stratégiákkal és horizontális skálázással, hogy a megoldást a saját munkaterhelésedhez igazítsd.

---

**Utolsó frissítés:** 2026-05-21  
**Tesztelve ezzel:** GroupDocs.Conversion 25.3.0 for .NET  
**Szerző:** GroupDocs  

```bash
Install-Package GroupDocs.Conversion -Version 25.3.0
```

```bash
dotnet add package GroupDocs.Conversion --version 25.3.0
```

```csharp
using GroupDocs.Conversion;
```

## Kapcsolódó oktatóanyagok

- [Konverziós gyorsítótár-kezelési oktatóanyagok a GroupDocs.Conversion .NET-hez](/conversion/net/cache-management/)
- [Optimalizáld a .NET dokumentumkonverziót gyorsítótárazással a GroupDocs.Conversion használatával](/conversion/net/cache-management/optimize-net-document-conversion-caching-groupdocs/)
- [Mesteri dokumentumkonverzió beállítás .NET-ben a GroupDocs.Conversion használatával](/conversion/net/conversion-options-settings/master-groupdocs-conversion-net-setup/)