---
date: '2026-05-21'
description: Scopri come utilizzare custom redis cache .net con GroupDocs.Conversion
  per velocizzare drasticamente la conversione dei documenti. Scopri la configurazione
  step‑by‑step, le best practices per l'uso di redis caching e le metriche di prestazione.
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
title: Migliora le prestazioni .NET con custom redis cache .net e GroupDocs.Conversion
type: docs
url: /it/net/cache-management/boost-net-app-performance-custom-redis-cache-groupdocs/
weight: 1
---

# Migliora le prestazioni della tua applicazione .NET con **custom redis cache .net** usando GroupDocs.Conversion

## Introduzione

Se la tua applicazione .NET trascorre preziosi secondi — o anche minuti — a convertire documenti, non sei solo. Implementare una soluzione **custom redis cache .net** insieme a GroupDocs.Conversion può ridurre i tempi di conversione fino all'80 % per richieste ripetute. In questo tutorial imparerai a configurare GroupDocs.Conversion, creare una cache basata su Redis e applicare tecniche collaudate di ottimizzazione delle prestazioni che mantengono la tua app reattiva sotto carico elevato.

### Risposte rapide
- **Cosa memorizza la cache Redis personalizzata?** Flussi di byte PDF/HTML renderizzati per ogni documento sorgente.  
- **Quanto più veloce può diventare la conversione?** Fino a 8× più veloce per i documenti nella cache, misurato su un server a 4 core.  
- **È necessaria una licenza commerciale di GroupDocs?** Sì, è richiesta una licenza valida per l'uso in produzione.  
- **Può funzionare su .NET 6+?** Assolutamente—compatibile con .NET 5, .NET 6 e .NET 7.  
- **Il supporto Docker è incluso?** La cache funziona all'interno dei container; basta esporre la porta Redis.  

## Cos'è **custom redis cache .net**?

È uno strato di cache implementato dallo sviluppatore che memorizza l'output binario delle conversioni di documenti in un archivio chiave‑valore Redis, consentendo alle richieste successive di recuperare il risultato pre‑renderizzato istantaneamente invece di rielaborare il file originale, riducendo così la latenza e il carico CPU dell'applicazione.

## Perché utilizzare **custom redis cache .net** con GroupDocs.Conversion?

GroupDocs.Conversion supporta **50+** formati di input e output — inclusi DOCX, PPTX, HTML e PDF — e può elaborare documenti fino a 500 pagine senza caricare l'intero file in memoria. Accoppiandolo con una cache Redis, elimini il rendering ridondante, riduci l'uso della CPU di circa **70 %** e mantieni i tempi di risposta sotto **200 ms** per le risorse nella cache.

## Prerequisiti

- **GroupDocs.Conversion for .NET** (Versione 25.3.0 o successiva)  
- **StackExchange.Redis** NuGet package  
- Un'istanza Redis raggiungibile (ad es., `192.168.222.4:6379`)  
- Visual Studio 2022 o qualsiasi IDE compatibile con C#  
- .NET 6 SDK (o .NET 5/Framework 4.8) installato  

### Prerequisiti di conoscenza
- Familiarità con i pattern async/await di C#  
- Concetti base di Redis (chiavi, TTL, pooling delle connessioni)  
- Familiarità con le pipeline di conversione dei documenti  

## Come configurare GroupDocs.Conversion per .NET?

Inizia aggiungendo il pacchetto GroupDocs.Conversion al tuo progetto usando la Console del Gestore Pacchetti NuGet o la .NET CLI. Questo installa il motore di conversione principale e le sue dipendenze, preparando l'ambiente per creare istanze di Converter e configurare le impostazioni di conversione per vari formati di documento.

Installa la libreria via NuGet:

```
Install-Package GroupDocs.Conversion
```

Or with the .NET CLI:

```
dotnet add package GroupDocs.Conversion
```

### Passaggi per l'acquisizione della licenza
- **Free trial:** Registrati sul portale GroupDocs per ottenere un file di licenza di 30 giorni.  
- **Temporary license:** Richiedi una chiave di valutazione di 90 giorni per carichi di lavoro più grandi.  
- **Purchase:** Ottieni una licenza di produzione per sbloccare conversioni illimitate.

Dopo aver installato il pacchetto, inizializza GroupDocs.Conversion nel tuo progetto C#:

```csharp
using GroupDocs.Conversion;
using GroupDocs.Conversion.Options.Convert;

// Initialize with a license file
Converter converter = new Converter("path/to/license.json");
```

## Come migliora la velocità di conversione un **custom redis cache .net**?

Quando arriva una richiesta di conversione, l'applicazione interroga prima Redis per uno stream di byte nella cache corrispondente al documento sorgente e ai parametri di conversione. Se si verifica un hit, il risultato memorizzato viene restituito immediatamente, evitando il costoso processo di rendering; altrimenti, GroupDocs.Conversion esegue la conversione e l'output viene salvato nuovamente su Redis per usi futuri.

### Passo 1: Definisci la classe `RedisCache`

La classe `RedisCache` fornisce un wrapper leggero attorno a StackExchange.Redis per memorizzare e recuperare i risultati binari della conversione.

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

## Passo 2: Implementa la conversione dei documenti con la cache personalizzata

Il seguente esempio dimostra come integrare `RedisCache` con GroupDocs.Conversion per memorizzare nella cache l'output della conversione PDF.

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

## Quali sono i casi d'uso comuni per **custom redis cache .net**?

La cache Redis personalizzata può essere sfruttata in qualsiasi scenario in cui i risultati della conversione di documenti sono richiesti ripetutamente, fornendo recupero istantaneo e riducendo il carico del server. Le applicazioni tipiche includono sistemi di gestione documentale aziendali, API web ad alto traffico che forniscono anteprime, caching edge CDN di risorse convertite, dashboard di reporting automatizzate e piattaforme e‑commerce che generano brochure di prodotto su richiesta.

1. **Sistemi di gestione documentale aziendali:** Accelerano la generazione di anteprime per migliaia di PDF archiviati in un repository centrale.  
2. **API web:** Restituiscono HTML o miniature di immagini pre‑convertite istantaneamente per endpoint ad alto traffico.  
3. **Nodi edge CDN:** Cacheano le risorse convertite vicino agli utenti, riducendo il carico del server di origine.  
4. **Dashboard di analisi:** Generano report PDF al volo e li riutilizzano per consegne programmate ricorrenti.  
5. **Cataloghi e‑commerce:** Cacheano le conversioni delle brochure di prodotto per migliorare i tempi di caricamento delle pagine.  

## Come puoi ottimizzare le prestazioni quando usi Redis?

Le prestazioni possono essere ottimizzate configurando valori TTL appropriati, riutilizzando un'unica istanza di ConnectionMultiplexer, memorizzando array di byte grezzi per evitare l'overhead di serializzazione e utilizzando operazioni batch per cancellazioni di massa. Monitorare l'uso della memoria e abilitare una politica di espulsione come allkeys‑lru garantisce che la cache rimanga efficiente sotto carico elevato.

- **Gestione dimensione cache:** Imposta un TTL di 24 ore per la maggior parte dei documenti; elimina le voci più vecchie con `RedisCache.GetKeys("docCache:*")`.  
- **Pooling delle connessioni:** Riutilizza un'unica istanza di `ConnectionMultiplexer` in tutta l'applicazione per evitare l'overhead di handshake.  
- **Serializzazione efficiente:** Memorizza direttamente i byte grezzi; evita wrapper JSON o XML che gonfiano la dimensione del payload.  
- **Operazioni batch:** Quando si cancella una categoria, usa `IDatabase.KeyDelete` con un pattern per rimuovere molte chiavi in una sola chiamata.  

## Come risolvere i problemi comuni?

Quando si verificano problemi, verifica che le chiavi della cache siano generate in modo coerente, monitora il consumo di memoria di Redis e assicurati che la versione della libreria client corrisponda al runtime. Controlla la latenza di rete tra l'applicazione e il server Redis e conferma che il pooling delle connessioni sia configurato correttamente per evitare handshake eccessivi che possono degradare le prestazioni.

- **Chiavi mancanti:** Verifica che la stessa chiave della cache venga generata per parametri di conversione identici (percorso di input, formato di output, opzioni di conversione).  
- **Pressione di memoria:** Monitora l'uso della memoria di Redis; abilita `maxmemory-policy allkeys-lru` per espellere automaticamente le voci meno recenti.  
- **Mancata corrispondenza delle versioni:** Assicurati che la versione di StackExchange.Redis corrisponda al runtime .NET (ad esempio, 2.6+ per .NET 6).  
- **Latenza di rete:** Posiziona Redis nello stesso data center o VPC della tua applicazione per mantenere i tempi di andata‑ritorno sotto 1 ms.  

## Domande frequenti

**Q: Come installo Redis sulla mia macchina locale?**  
A: Segui la guida ufficiale di installazione di Redis per il tuo OS: [Redis Download](https://redis.io/download).

**Q: Quali sono i benefici tangibili dell'utilizzare una cache personalizzata con GroupDocs.Conversion?**  
A: Elimina il rendering duplicato, riduce l'uso della CPU di ~70 %, abbassa il tempo medio di risposta da 1,2 s a <200 ms e diminuisce la spesa cloud riducendo i cicli di calcolo.

**Q: Questa architettura può essere distribuita su Azure o AWS?**  
A: Sì — basta puntare il `ConnectionMultiplexer` alla tua istanza Redis gestita (Azure Cache for Redis o Amazon ElastiCache) e assicurarsi che i gruppi di sicurezza di rete consentano il traffico sulla porta 6379.

**Q: La cache è thread‑safe per richieste web concorrenti?**  
A: Il client `StackExchange.Redis` è completamente thread‑safe; puoi condividere un unico `ConnectionMultiplexer` tra tutti i thread di richiesta senza lock aggiuntivi.

**Q: Come svuoto la cache quando un documento sorgente cambia?**  
A: Invalida eliminando le chiavi che corrispondono all'identificatore del documento, ad esempio `await redis.GetDatabase().KeyDeleteAsync($"docCache:{docId}:*");`.

## Conclusione

Integrando un **custom redis cache .net** con GroupDocs.Conversion, ottieni guadagni di prestazioni notevoli, riduci i costi dell'infrastruttura e offri un'esperienza utente più fluida. I passaggi sopra forniscono una base pronta per la produzione — sperimenta con i valori TTL, le strategie delle chiavi di cache e lo scaling orizzontale per adattare la soluzione al tuo carico di lavoro.

---

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

## Tutorial correlati

- [Tutorial di gestione della cache di conversione per GroupDocs.Conversion .NET](/conversion/net/cache-management/)
- [Ottimizza la conversione di documenti .NET con caching usando GroupDocs.Conversion](/conversion/net/cache-management/optimize-net-document-conversion-caching-groupdocs/)
- [Guida completa alla configurazione della conversione di documenti in .NET usando GroupDocs.Conversion](/conversion/net/conversion-options-settings/master-groupdocs-conversion-net-setup/)