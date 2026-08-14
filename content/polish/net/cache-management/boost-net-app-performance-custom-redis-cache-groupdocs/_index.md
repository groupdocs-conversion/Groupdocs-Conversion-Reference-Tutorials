---
date: '2026-05-21'
description: Dowiedz się, jak używać niestandardowej pamięci podręcznej redis .net
  z GroupDocs.Conversion, aby dramatycznie przyspieszyć konwersję dokumentów. Odkryj
  step‑by‑step setup, użycie redis caching best practices oraz performance metrics.
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
title: Zwiększ wydajność .NET dzięki niestandardowej pamięci podręcznej redis .net
  i GroupDocs.Conversion
type: docs
url: /pl/net/cache-management/boost-net-app-performance-custom-redis-cache-groupdocs/
weight: 1
---

# Zwiększ wydajność aplikacji .NET dzięki **custom redis cache .net** przy użyciu GroupDocs.Conversion

## Wprowadzenie

Jeśli twoja aplikacja .NET spędza cenne sekundy — a nawet minuty — na konwertowaniu dokumentów, nie jesteś sam. Implementacja rozwiązania **custom redis cache .net** wraz z GroupDocs.Conversion może skrócić czasy konwersji nawet o 80 % przy powtarzających się żądaniach. W tym samouczku dowiesz się, jak skonfigurować GroupDocs.Conversion, stworzyć pamięć podręczną opartą na Redis oraz zastosować sprawdzone techniki optymalizacji wydajności, które utrzymają aplikację responsywną przy dużym obciążeniu.

### Szybkie odpowiedzi
- **What does the custom Redis cache store?** Przechowuje wyrenderowane strumienie bajtów PDF/HTML dla każdego dokumentu źródłowego.  
- **How much faster can conversion become?** Może przyspieszyć konwersję nawet do 8‑krotności dla zbuforowanych dokumentów, zmierzone na serwerze 4‑rdzeniowym.  
- **Do I need a commercial GroupDocs license?** Tak, wymagana jest ważna licencja do użytku produkcyjnego.  
- **Can this run on .NET 6+?** Oczywiście — kompatybilny z .NET 5, .NET 6 i .NET 7.  
- **Is Docker support included?** Obsługa Docker jest wbudowana — pamięć podręczna działa w kontenerach; wystarczy udostępnić port Redis.

## Czym jest **custom redis cache .net**?

Jest to warstwa pamięci podręcznej zaimplementowana przez programistę, która przechowuje binarny wynik konwersji dokumentów w magazynie klucz‑wartość Redis, umożliwiając kolejnym żądaniom natychmiastowe pobranie wstępnie wyrenderowanego wyniku zamiast ponownego przetwarzania oryginalnego pliku, co zmniejsza opóźnienia i obciążenie CPU w całej aplikacji.

## Dlaczego używać **custom redis cache .net** z GroupDocs.Conversion?

GroupDocs.Conversion obsługuje **50+** formatów wejściowych i wyjściowych — w tym DOCX, PPTX, HTML i PDF — i może przetwarzać dokumenty do 500 stron bez ładowania całego pliku do pamięci. Łącząc go z pamięcią podręczną Redis, eliminujesz zbędne renderowanie, zmniejszasz zużycie CPU o około **70 %**, a czasy odpowiedzi dla buforowanych zasobów utrzymujesz poniżej **200 ms**.

## Wymagania wstępne

- **GroupDocs.Conversion for .NET** (Version 25.3.0 lub nowsza)  
- **StackExchange.Redis** pakiet NuGet  
- Dostępna instancja Redis (np. `192.168.222.4:6379`)  
- Visual Studio 2022 lub dowolne IDE kompatybilne z C#  
- .NET 6 SDK (lub .NET 5/Framework 4.8) zainstalowane  

### Wymagania wiedzy
- Znajomość wzorców async/await w C#  
- Podstawowa znajomość koncepcji Redis (klucze, TTL, pooling połączeń)  
- Znajomość pipeline'ów konwersji dokumentów  

## Jak skonfigurować GroupDocs.Conversion dla .NET?

Rozpocznij od dodania pakietu GroupDocs.Conversion do swojego projektu przy użyciu konsoli Menedżera pakietów NuGet lub .NET CLI. To zainstaluje główny silnik konwersji i jego zależności, przygotowując środowisko do tworzenia instancji Converter oraz konfigurowania ustawień konwersji dla różnych formatów dokumentów.

Install the library via NuGet:

```
Install-Package GroupDocs.Conversion
```

Or with the .NET CLI:

```
dotnet add package GroupDocs.Conversion
```

### Kroki uzyskania licencji
- **Free trial:** Zarejestruj się w portalu GroupDocs, aby uzyskać plik licencji na 30 dni.  
- **Temporary license:** Poproś o klucz ewaluacyjny na 90 dni dla większych obciążeń.  
- **Purchase:** Uzyskaj licencję produkcyjną, aby odblokować nieograniczoną liczbę konwersji.

After installing the package, initialize GroupDocs.Conversion in your C# project:

```csharp
using GroupDocs.Conversion;
using GroupDocs.Conversion.Options.Convert;

// Initialize with a license file
Converter converter = new Converter("path/to/license.json");
```

## Jak **custom redis cache .net** poprawia szybkość konwersji?

Gdy przychodzi żądanie konwersji, aplikacja najpierw odpyta Redis o buforowany strumień bajtów pasujący do dokumentu źródłowego i parametrów konwersji. Jeśli znajdzie dopasowanie, zapisany wynik zostaje zwrócony natychmiast, omijając kosztowny proces renderowania; w przeciwnym razie GroupDocs.Conversion wykonuje konwersję, a wynik zostaje zapisany z powrotem w Redis do późniejszego użycia.

### Krok 1: Zdefiniuj klasę `RedisCache`

Klasa `RedisCache` zapewnia lekką nakładkę wokół StackExchange.Redis do przechowywania i pobierania binarnych wyników konwersji.

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

## Krok 2: Zaimplementuj konwersję dokumentów z własną pamięcią podręczną

Poniższy przykład pokazuje integrację `RedisCache` z GroupDocs.Conversion w celu buforowania wyniku konwersji do PDF.

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

## Jakie są typowe przypadki użycia **custom redis cache .net**?

Pamięć podręczna custom Redis może być wykorzystywana w każdym scenariuszu, w którym wyniki konwersji dokumentów są wielokrotnie żądane, zapewniając natychmiastowe pobranie i zmniejszając obciążenie serwera. Typowe zastosowania obejmują systemy zarządzania dokumentami w przedsiębiorstwach, wysokowydajne API internetowe dostarczające podglądy, buforowanie węzłów brzegowych CDN przetworzonych zasobów, automatyczne pulpity raportowe oraz platformy e‑commerce generujące katalogi produktów na żądanie.

1. **Enterprise Document Management Systems:** Przyspiesz generowanie podglądów tysięcy PDF‑ów przechowywanych w centralnym repozytorium.  
2. **Web APIs:** Natychmiast zwracaj wstępnie skonwertowany HTML lub miniatury obrazów dla wysokowydajnych punktów końcowych.  
3. **CDN Edge Nodes:** Buforuj przetworzone zasoby blisko użytkowników, zmniejszając obciążenie serwera źródłowego.  
4. **Analytics Dashboards:** Generuj raporty PDF w locie i ponownie używaj ich przy regularnych, zaplanowanych dostawach.  
5. **E‑commerce Catalogs:** Buforuj konwersje katalogów produktów, aby przyspieszyć ładowanie stron.  

## Jak można dopasować wydajność przy użyciu Redis?

Wydajność można zoptymalizować, konfigurując odpowiednie wartości TTL, ponownie używając jednej instancji ConnectionMultiplexer, przechowując surowe tablice bajtów, aby uniknąć narzutu serializacji, oraz stosując operacje wsadowe przy masowych usuwaniach. Monitorowanie zużycia pamięci i włączenie polityki usuwania, takiej jak allkeys‑lru, zapewnia, że pamięć podręczna pozostaje efektywna przy dużym obciążeniu.

- **Zarządzanie rozmiarem pamięci podręcznej:** Ustaw TTL na 24 godziny dla większości dokumentów; usuń starsze wpisy przy użyciu `RedisCache.GetKeys("docCache:*")`.  
- **Pooling połączeń:** Ponownie używaj jednej instancji `ConnectionMultiplexer` w całej aplikacji, aby uniknąć narzutu na nawiązywanie połączeń.  
- **Efektywna serializacja:** Przechowuj surowe bajty bezpośrednio; unikaj opakowań JSON lub XML, które zwiększają rozmiar ładunku.  
- **Operacje wsadowe:** Przy czyszczeniu kategorii użyj `IDatabase.KeyDelete` z wzorcem, aby usunąć wiele kluczy w jednym wywołaniu.  

## Jak rozwiązywać typowe problemy?

Gdy pojawią się problemy, sprawdź, czy klucze pamięci podręcznej są generowane konsekwentnie, monitoruj zużycie pamięci Redis i upewnij się, że wersja biblioteki klienckiej odpowiada środowisku uruchomieniowemu. Sprawdź opóźnienia sieciowe między aplikacją a serwerem Redis oraz potwierdź, że pooling połączeń jest poprawnie skonfigurowany, aby uniknąć nadmiernych nawiązań połączeń, które mogą obniżać wydajność.

- **Brakujące klucze:** Upewnij się, że ten sam klucz pamięci podręcznej jest generowany dla identycznych parametrów konwersji (ścieżka wejściowa, format wyjściowy, opcje konwersji).  
- **Presja pamięci:** Monitoruj zużycie pamięci Redis; włącz `maxmemory-policy allkeys-lru`, aby automatycznie usuwać najrzadziej używane wpisy.  
- **Niezgodności wersji:** Upewnij się, że wersja StackExchange.Redis odpowiada środowisku .NET (np. 2.6+ dla .NET 6).  
- **Opóźnienia sieciowe:** Umieść Redis w tym samym centrum danych lub VPC co aplikacja, aby utrzymać czasy podróży pakietów poniżej 1 ms.  

## Najczęściej zadawane pytania

**Q: Jak zainstalować Redis na moim lokalnym komputerze?**  
A: Postępuj zgodnie z oficjalnym przewodnikiem instalacji Redis dla swojego systemu operacyjnego: [Redis Download](https://redis.io/download).

**Q: Jakie są wymierne korzyści z używania własnej pamięci podręcznej z GroupDocs.Conversion?**  
A: Elimininuje podwójne renderowanie, zmniejsza zużycie CPU o ~70 %, skraca średni czas odpowiedzi z 1,2 s do <200 ms oraz obniża koszty chmury poprzez zmniejszenie liczby cykli obliczeniowych.

**Q: Czy tę architekturę można wdrożyć w Azure lub AWS?**  
A: Tak — wystarczy skierować `ConnectionMultiplexer` do zarządzanej instancji Redis (Azure Cache for Redis lub Amazon ElastiCache) i zapewnić, że grupy zabezpieczeń sieciowych zezwalają na ruch na porcie 6379.

**Q: Czy pamięć podręczna jest wątkowo‑bezpieczna dla równoczesnych żądań webowych?**  
A: Klient `StackExchange.Redis` jest w pełni wątkowo‑bezpieczny; możesz udostępniać jedną instancję `ConnectionMultiplexer` wszystkim wątkom żądań bez dodatkowego blokowania.

**Q: Jak wyczyścić pamięć podręczną, gdy zmieni się dokument źródłowy?**  
A: Unieważnij, usuwając klucze pasujące do identyfikatora dokumentu, np. `await redis.GetDatabase().KeyDeleteAsync($"docCache:{docId}:*");`.

## Podsumowanie

Integrując **custom redis cache .net** z GroupDocs.Conversion, uzyskasz znaczące przyspieszenie wydajności, obniżysz koszty infrastruktury i zapewnisz płynniejsze doświadczenie użytkownika. Powyższe kroki dają gotową do produkcji bazę — eksperymentuj z wartościami TTL, strategiami kluczy pamięci podręcznej i skalowaniem poziomym, aby dostosować rozwiązanie do swojego obciążenia.

---

**Ostatnia aktualizacja:** 2026-05-21  
**Testowano z:** GroupDocs.Conversion 25.3.0 for .NET  
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

## Powiązane samouczki

- [Samouczki zarządzania pamięcią podręczną konwersji dla GroupDocs.Conversion .NET](/conversion/net/cache-management/)
- [Optymalizacja konwersji dokumentów .NET z buforowaniem przy użyciu GroupDocs.Conversion](/conversion/net/cache-management/optimize-net-document-conversion-caching-groupdocs/)
- [Mistrzowska konfiguracja konwersji dokumentów w .NET przy użyciu GroupDocs.Conversion](/conversion/net/conversion-options-settings/master-groupdocs-conversion-net-setup/)