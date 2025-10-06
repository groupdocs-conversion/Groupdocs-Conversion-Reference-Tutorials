---
"date": "2025-04-28"
"description": "Dowiedz się, jak zwiększyć wydajność aplikacji .NET, implementując niestandardową pamięć podręczną Redis do konwersji dokumentów za pomocą GroupDocs.Conversion. Zwiększ wydajność i szybkość już dziś!"
"title": "Zwiększ wydajność aplikacji .NET i wdróż niestandardową pamięć podręczną Redis za pomocą GroupDocs.Conversion"
"url": "/pl/net/cache-management/boost-net-app-performance-custom-redis-cache-groupdocs/"
"weight": 1
type: docs
---
# Zwiększ wydajność swojej aplikacji .NET dzięki niestandardowemu buforowaniu Redis przy użyciu GroupDocs.Conversion

## Wstęp

Czy doświadczasz powolnych procesów konwersji dokumentów w swoich aplikacjach .NET? Zwiększ wydajność i efektywność, wykorzystując niestandardową pamięć podręczną Redis wraz z GroupDocs.Conversion dla .NET. Ten samouczek przeprowadzi Cię przez operacje buforowania w celu przyspieszenia renderowania dokumentów.

**Czego się nauczysz:**
- Konfigurowanie GroupDocs.Conversion dla .NET
- Implementacja niestandardowej pamięci podręcznej Redis do konwersji dokumentów
- Optymalizacja wydajności przy użyciu efektywnych strategii buforowania

Przeprowadzimy Cię przez proces zwiększania wydajności Twojej aplikacji za pomocą tych potężnych narzędzi. Zanim zaczniemy, upewnij się, że rozumiesz wymagania wstępne.

## Wymagania wstępne

Aby skorzystać z tego samouczka, upewnij się, że posiadasz:

### Wymagane biblioteki i wersje:
- **GroupDocs.Conversion dla .NET** (Wersja 25.3.0)
- **StackExchange.Redis** biblioteka do operacji Redis
- Działająca instancja serwera Redis (np. `192.168.222.4:6379`)

### Wymagania dotyczące konfiguracji środowiska:
- Visual Studio lub inne kompatybilne środowisko IDE obsługujące język C#
- Zainstalowano .NET Framework lub .NET Core

### Wymagania wstępne dotyczące wiedzy:
- Podstawowa znajomość programowania w językach C# i .NET
- Znajomość Redis jako rozwiązania do buforowania
- Doświadczenie w procesach konwersji dokumentów w aplikacjach programowych

## Konfigurowanie GroupDocs.Conversion dla .NET

Aby rozpocząć korzystanie z pakietu GroupDocs.Conversion, zainstaluj go za pomocą konsoli Menedżera pakietów NuGet lub interfejsu wiersza poleceń .NET.

**Konsola Menedżera Pakietów NuGet:**
```bash
Install-Package GroupDocs.Conversion -Version 25.3.0
```

**Interfejs wiersza poleceń .NET:**
```bash
dotnet add package GroupDocs.Conversion --version 25.3.0
```

### Etapy uzyskania licencji:
- **Bezpłatna wersja próbna:** Przetestuj funkcje i funkcjonalności przy użyciu licencji tymczasowej.
- **Licencja tymczasowa:** Pobierz w celu rozszerzonej oceny bez ograniczeń.
- **Zakup:** W przypadku długoterminowego użytkowania należy rozważyć zakup pełnej licencji.

Po instalacji zainicjuj GroupDocs.Conversion w swojej aplikacji C#:

```csharp
using GroupDocs.Conversion;
```

## Przewodnik wdrażania

### Niestandardowa implementacja pamięci podręcznej przy użyciu Redis

tej sekcji pokazano, jak utworzyć niestandardową pamięć podręczną przy użyciu Redis do operacji renderowania dokumentów w celu zwiększenia szybkości i wydajności konwersji.

#### Przegląd
Wdrożymy mechanizm buforowania oparty na Redis, który będzie przechowywał renderowane dokumenty, co pozwoli uniknąć zbędnego przetwarzania i znacznie przyspieszy czas konwersji.

##### Krok 1: Zdefiniuj klasę RedisCache

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

    // Ustaw dane w pamięci podręcznej za pomocą określonego klucza
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

    // Spróbuj pobrać dane z pamięci podręcznej za pomocą klucza
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

    // Pobierz wszystkie klucze, które pasują do wzorca filtru z pamięci podręcznej
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

**Wyjaśnienie:**
- **Ustaw metodę:** Zapisuje dane w Redis przy użyciu określonego klucza pamięci podręcznej.
- **Metoda TryGetValue:** Pobiera dane z pamięci podręcznej, jeśli są dostępne.
- **Metoda GetKeys:** Pobiera klucze pasujące do określonego wzorca.

##### Krok 2: Wdrażanie konwersji dokumentów z niestandardową pamięcią podręczną

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

**Wyjaśnienie:**
- **Inicjalizacja RedisCache:** Konfiguruje pamięć podręczną z prefiksem klucza.
- **Ustawienia konwertera:** Integruje niestandardową pamięć podręczną z ustawieniami GroupDocs.Conversion.
- **Proces konwersji:** Mierzy i demonstruje poprawę wydajności poprzez buforowanie wyników konwersji.

## Zastosowania praktyczne

### Przykłady zastosowań:
1. **Systemy zarządzania dokumentacją przedsiębiorstwa:** Zwiększ szybkość renderowania dokumentów w aplikacjach na dużą skalę.
2. **Usługi sieciowe:** Skróć czas reakcji interfejsów API obsługujących częste konwersje plików PDF.
3. **Sieci dostarczania treści (CDN):** Szybkie buforowanie i dostarczanie wstępnie przekonwertowanych dokumentów.
4. **Platformy analityki danych:** Przyspiesz generowanie raportów obejmujących konwersję danych do formatów wizualnych.
5. **Witryny e-commerce:** Zoptymalizuj przetwarzanie katalogu produktów, buforując przekonwertowane obrazy lub podglądy dokumentów.

### Możliwości integracji:
- Połącz z innymi frameworkami .NET, np. ASP.NET Core, w przypadku aplikacji internetowych.
- Zintegruj się z architekturą mikrousług za pomocą Dockera i Kubernetesa.

## Rozważania dotyczące wydajności

Aby zoptymalizować wydajność, należy wziąć pod uwagę następujące kwestie:

- **Zarządzanie rozmiarem pamięci podręcznej:** Regularnie usuwaj stare wpisy, aby zapobiec przepełnieniu pamięci.
- **Pula połączeń:** Użyj puli połączeń w Redis, aby efektywnie zarządzać zasobami.
- **Serializacja danych:** Wybierz wydajne formaty serializacji (np. bufory protokołów) do przechowywania danych w Redis.

## Wniosek

Implementacja niestandardowej pamięci podręcznej Redis z GroupDocs.Conversion dla .NET może znacznie zwiększyć wydajność konwersji dokumentów w Twojej aplikacji. Ten samouczek zawiera wskazówki krok po kroku dotyczące konfigurowania i wykorzystywania tych potężnych narzędzi w celu optymalizacji operacji.

**Następne kroki:**
- Eksperymentuj z różnymi konfiguracjami pamięci podręcznej.
- Poznaj zaawansowane funkcje GroupDocs.Conversion przeznaczone do bardziej złożonych przypadków użycia.

Gotowy na zwiększenie wydajności swojej aplikacji? Zacznij wdrażać to rozwiązanie już dziś!

## Sekcja FAQ

1. **Jak zainstalować Redis na moim komputerze lokalnym?**
   - Postępuj zgodnie z oficjalną instrukcją instalacji Redis dla swojego systemu operacyjnego: [Pobierz Redis](https://redis.io/download).
2. **Jakie są korzyści ze stosowania niestandardowej pamięci podręcznej z GroupDocs.Conversion?**
   - Zmniejsza ilość zbędnego przetwarzania, przyspiesza czas konwersji i obniża wykorzystanie zasobów.
3. **Czy mogę używać tej konfiguracji w środowiskach chmurowych?**
   - Oczywiście! Upewnij się, że Twoja instancja Redis jest dostępna ze środowiska aplikacji.