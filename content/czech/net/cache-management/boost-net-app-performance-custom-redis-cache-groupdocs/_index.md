---
"date": "2025-04-28"
"description": "Naučte se, jak zlepšit výkon vaší .NET aplikace implementací vlastní mezipaměti Redis pro převod dokumentů pomocí GroupDocs.Conversion. Zvyšte efektivitu a rychlost ještě dnes!"
"title": "Zvýšení výkonu .NET aplikací – implementace vlastní mezipaměti Redis pomocí GroupDocs.Conversion"
"url": "/cs/net/cache-management/boost-net-app-performance-custom-redis-cache-groupdocs/"
"weight": 1
type: docs
---
# Zvyšte výkon svých .NET aplikací pomocí vlastního ukládání do mezipaměti Redis s využitím GroupDocs.Conversion

## Zavedení

Máte ve svých .NET aplikacích problémy s pomalou konverzí dokumentů? Zvyšte výkon a efektivitu využitím vlastní mezipaměti Redis spolu s GroupDocs.Conversion pro .NET. Tento tutoriál vás provede operacemi ukládání do mezipaměti a urychlí vykreslování dokumentů.

**Co se naučíte:**
- Nastavení GroupDocs.Conversion pro .NET
- Implementace vlastní mezipaměti Redis pro převod dokumentů
- Optimalizace výkonu pomocí efektivních strategií ukládání do mezipaměti

Provedeme vás zvyšováním efektivity vaší aplikace pomocí těchto výkonných nástrojů. Než začneme, ujistěte se, že rozumíte předpokladům.

## Předpoklady

Abyste mohli postupovat podle tohoto tutoriálu, ujistěte se, že máte:

### Požadované knihovny a verze:
- **GroupDocs.Conversion pro .NET** (Verze 25.3.0)
- **StackExchange.Redis** knihovna pro operace Redis
- Spuštěná instance Redis serveru (např. `192.168.222.4:6379`)

### Požadavky na nastavení prostředí:
- Visual Studio nebo jiné kompatibilní IDE s podporou C#
- Nainstalovaný .NET Framework nebo .NET Core

### Předpoklady znalostí:
- Základní znalost programování v C# a .NET
- Znalost Redisu jako řešení pro ukládání do mezipaměti
- Zkušenosti s procesy konverze dokumentů v softwarových aplikacích

## Nastavení GroupDocs.Conversion pro .NET

Chcete-li začít používat GroupDocs.Conversion, nainstalujte si ho pomocí konzole NuGet Package Manager nebo rozhraní .NET CLI.

**Konzola Správce balíčků NuGet:**
```bash
Install-Package GroupDocs.Conversion -Version 25.3.0
```

**Rozhraní příkazového řádku .NET:**
```bash
dotnet add package GroupDocs.Conversion --version 25.3.0
```

### Kroky pro získání licence:
- **Bezplatná zkušební verze:** Otestujte si funkce a možnosti s dočasnou licencí.
- **Dočasná licence:** Získejte pro rozšířené vyhodnocení bez omezení.
- **Nákup:** Pro dlouhodobé používání zvažte zakoupení plné licence.

Po instalaci inicializujte GroupDocs.Conversion ve vaší aplikaci C#:

```csharp
using GroupDocs.Conversion;
```

## Průvodce implementací

### Implementace vlastní mezipaměti pomocí Redisu

Tato část ukazuje vytvoření vlastní mezipaměti pomocí Redisu pro operace vykreslování dokumentů za účelem zvýšení rychlosti a efektivity konverze.

#### Přehled
Implementujeme mechanismus ukládání do mezipaměti založený na Redisu, který ukládá vykreslené dokumenty, čímž se zabrání redundantnímu zpracování a výrazně se zrychlí doba konverze.

##### Krok 1: Definování třídy RedisCache

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

    // Nastavení dat v mezipaměti pomocí specifického klíče
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

    // Zkuste načíst data z mezipaměti pomocí klíče
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

    // Načíst všechny klíče, které odpovídají zadanému filtrovacímu vzoru, z mezipaměti
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

**Vysvětlení:**
- **Metoda nastavení:** Ukládá data v Redisu pomocí specifického klíče mezipaměti.
- **Metoda TryGetValue:** Načte data z mezipaměti, pokud jsou k dispozici.
- **Metoda GetKeys:** Načte klíče odpovídající zadanému vzoru.

##### Krok 2: Implementace převodu dokumentů s vlastní mezipamětí

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

**Vysvětlení:**
- **Inicializace RedisCache:** Nastaví mezipaměť s předponou klíče.
- **Nastavení převodníku:** Integruje vlastní mezipaměť do nastavení GroupDocs.Conversion.
- **Proces konverze:** Měří a demonstruje zlepšení výkonu ukládáním výsledků konverzí do mezipaměti.

## Praktické aplikace

### Případy použití:
1. **Systémy pro správu podnikových dokumentů:** Zlepšete rychlost vykreslování dokumentů pro rozsáhlé aplikace.
2. **Webové služby:** Zlepšete dobu odezvy API, která se zabývají častými konverzemi PDF.
3. **Sítě pro doručování obsahu (CDN):** Ukládejte do mezipaměti a rychle doručujte předem převedené dokumenty.
4. **Platformy pro analýzu dat:** Zrychlete generování sestav, které zahrnuje převod dat do vizuálních formátů.
5. **Stránky elektronického obchodování:** Optimalizujte zpracování katalogu produktů ukládáním převedených obrázků nebo náhledů dokumentů do mezipaměti.

### Možnosti integrace:
- Kombinujte s dalšími .NET frameworky, jako je ASP.NET Core, pro webové aplikace.
- Integrace do architektury mikroslužeb pomocí Dockeru a Kubernetes.

## Úvahy o výkonu

Pro optimalizaci výkonu zvažte následující:

- **Správa velikosti mezipaměti:** Pravidelně mazejte staré záznamy, abyste zabránili přeplnění paměti.
- **Sdružování připojení:** Pro efektivní správu zdrojů použijte sdružování připojení v Redisu.
- **Serializace dat:** Pro ukládání dat v Redisu zvolte efektivní formáty serializace (např. Protocol Buffers).

## Závěr

Implementace vlastní mezipaměti Redis s GroupDocs.Conversion pro .NET může výrazně zvýšit výkon vaší aplikace při převodu dokumentů. Tento tutoriál poskytl podrobné pokyny k nastavení a používání těchto výkonných nástrojů k optimalizaci provozu.

**Další kroky:**
- Experimentujte s různými konfiguracemi mezipaměti.
- Prozkoumejte pokročilé funkce GroupDocs.Conversion pro složitější případy použití.

Jste připraveni zvýšit efektivitu vaší aplikace? Začněte s implementací tohoto řešení ještě dnes!

## Sekce Často kladených otázek

1. **Jak nainstaluji Redis na svůj lokální počítač?**
   - Postupujte podle oficiálního průvodce instalací Redisu pro váš operační systém: [Stažení Redisu](https://redis.io/download).
2. **Jaké jsou výhody použití vlastní mezipaměti s GroupDocs.Conversion?**
   - Snižuje redundantní zpracování, zrychluje dobu konverze a snižuje využití zdrojů.
3. **Mohu toto nastavení použít v cloudovém prostředí?**
   - Rozhodně! Ujistěte se, že je vaše instance Redis přístupná z prostředí vaší aplikace.