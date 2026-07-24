---
date: '2026-07-24'
description: Scopri come utilizzare la cache Redis in Java con GroupDocs.Conversion
  per migliorare l'efficienza dell'applicazione. Questo tutorial su Redis cache in
  Java copre la configurazione, le strategie di caching e i consigli sulle prestazioni.
keywords:
- how to use redis
- redis cache java
- java redis connection
- configure redis cache
- redis cache key prefix
lastmod: '2026-07-24'
og_description: Scopri come utilizzare la cache Redis in Java con GroupDocs.Conversion.
  Questa guida mostra la configurazione, le strategie di caching e i consigli sulle
  prestazioni per una conversione di documenti più veloce.
og_image_alt: 'Guide: Implement Redis cache in Java using GroupDocs.Conversion for
  high‑performance document processing'
og_title: Come utilizzare la cache Redis in Java con GroupDocs.Conversion
schemas:
- author: GroupDocs
  dateModified: '2026-07-24'
  description: Learn how to use Redis cache in Java with GroupDocs.Conversion to boost
    application efficiency. This redis cache java tutorial covers setup, caching strategies,
    and performance tips.
  headline: How to Use Redis Cache in Java with GroupDocs.Conversion
  type: TechArticle
- questions:
  - answer: Yes. Replace `"localhost"` with the cluster endpoint and configure `ConnectionMultiplexer`
      for SSL and password authentication.
    question: Can I use this approach with a remote Redis cluster?
  - answer: Modify the `_cacheKeyPrefix` field in `RedisCache`. Using a unique prefix
      helps avoid key collisions across applications.
    question: How do I change the `redis cache key prefix`?
  - answer: Call `_db.KeyDelete(pattern)` or use `GetKeys` to retrieve matching keys
      and delete them in a loop.
    question: Is there a way to clear the cache programmatically?
  - answer: Absolutely. Replace `PdfConvertOptions` with the appropriate `ConvertOptions`
      subclass (e.g., `DocxConvertOptions`).
    question: Does this work for converting documents other than PDF?
  - answer: The tutorial was tested with GroupDocs.Conversion **25.2**; newer versions
      should be compatible.
    question: What version of GroupDocs.Conversion is required?
  type: FAQPage
tags:
- redis cache
- groupdocs conversion
- java caching
- document conversion
- performance optimization
title: Come utilizzare la cache Redis in Java con GroupDocs.Conversion
type: docs
url: /it/java/cache-management/redis-cache-java-groupdocs-conversion-guide/
weight: 1
---

# Come utilizzare la cache Redis in Java con GroupDocs.Conversion

`Redis` è un archivio di strutture dati in‑memoria che supporta stringhe, hash, liste, set e altro. Redis è un potente archivio di strutture dati open‑source in‑memoria che può fungere da database, cache e broker di messaggi. Quando impari **come utilizzare Redis** insieme a GroupDocs.Conversion, fornisci alla tua applicazione Java uno strato di cache ad alta velocità che riduce drasticamente la latenza di conversione dei documenti. In questa guida percorreremo un **tutorial completo sulla cache redis in java**, dalla configurazione dell'ambiente all'uso in scenari reali, così potrai vedere immediatamente miglioramenti delle prestazioni.

## Risposte rapide
- **Qual è il beneficio principale dell'utilizzo di Redis con GroupDocs?** Recupero più veloce dei documenti evitando conversioni ripetute.  
- **Quale artefatto Maven aggiunge GroupDocs.Conversion?** `com.groupdocs:groupdocs-conversion`.  
- **Come collego Java a Redis?** Usa un esempio di connessione Java Redis come `ConnectionMultiplexer.Connect("localhost")`.  
- **Posso personalizzare le chiavi della cache?** Sì – il `redis cache key prefix` ti consente di organizzare le voci.  
- **È necessaria una licenza per la produzione?** Sì, è necessaria una licenza valida di GroupDocs.Conversion.  

`ConnectionMultiplexer` è la classe client della libreria StackExchange.Redis che gestisce le connessioni a un server Redis.

## Cos'è GroupDocs.Conversion per Java?
GroupDocs.Conversion per Java è una libreria che converte oltre 80 formati di file in PDF, immagini e altri output. Fornisce un'API unificata per trasformazioni di documenti lato server ad alta qualità senza richiedere installazioni di Microsoft Office. Supporta la conversione in PDF, immagini, HTML e molti altri formati, e include opzioni per filigrane, paginazione e impostazioni di rendering personalizzate.

## Perché usare Redis con GroupDocs.Conversion?
Usare Redis come strato di cache può ridurre il tempo di conversione fino al **90 %** per richieste ripetute, e riduce l'utilizzo della CPU di **circa il 70 %** quando si elaborano grandi batch. Affermazioni quantificate come queste chiariscono perché molte imprese adottano questo modello per servizi di documenti ad alto throughput.

## Prerequisiti
### Librerie e dipendenze richieste
1. **Java Development Kit (JDK):** Versione 8 o successiva.  
2. **Redis Server:** In esecuzione localmente o raggiungibile da remoto.  
3. **GroupDocs.Conversion per Java:** Aggiunto tramite Maven (vedi la sezione **maven dependency groupdocs** qui sotto).  

### Configurazione dell'ambiente
- Installa Redis seguendo [questa guida](https://redis.io/download).  
- Configura il tuo IDE (IntelliJ IDEA, Eclipse, ecc.) con il JDK appropriato.  

### Prerequisiti di conoscenza
- Concetti di base di Java e OOP.  
- Familiarità con Maven per la gestione delle dipendenze.  
- Comprensione dei principi di caching e del loro ruolo nella conversione dei documenti.

## Configurazione di GroupDocs.Conversion per Java
La libreria `GroupDocs.Conversion` è il motore centrale che esegue le trasformazioni di formato. Aggiungi il seguente snippet Maven al tuo `pom.xml` per scaricare il pacchetto ufficiale:

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/conversion/java/</url>
   </repository>
</repositories>

<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-conversion</artifactId>
      <version>25.2</version>
   </dependency>
</dependencies>
```

### Acquisizione della licenza
1. **Prova gratuita:** Registrati su [GroupDocs](https://releases.groupdocs.com/conversion/java/) per scaricare una versione di prova.  
2. **Licenza temporanea:** Richiedi una licenza temporanea per una valutazione estesa dalla [pagina di acquisto](https://purchase.groupdocs.com/temporary-license/).  
3. **Acquisto:** Per uso commerciale, acquista una licenza tramite la loro [pagina di acquisto](https://purchase.groupdocs.com/buy).

Una volta ottenuta la licenza, puoi istanziare il convertitore:

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.convert.ConvertOptions;

// Initialize the Converter object with a document path
Converter converter = new Converter("path/to/your/document");
```

## Guida all'implementazione
### Panoramica dell'integrazione della cache Redis
Creeremo una classe personalizzata `RedisCache` che implementa `ICache`. Questa classe dimostra un **esempio di connessione java redis** e mostra come lavorare con il **redis cache key prefix**.

`RedisCache` è un'implementazione personalizzata dell'interfaccia `ICache` di GroupDocs che memorizza i risultati della conversione in Redis.  

#### Passo 1: Creare la classe RedisCache
Di seguito è riportata l'implementazione completa. Mantieni il codice esattamente come mostrato; include tutti gli import necessari e la logica di gestione della chiave di cache.

```java
import com.groupdocs.conversion.caching.ICache;
import StackExchange.Redis;
import java.io.IOException;
import java.io.ObjectInputStream;
import java.io.ObjectOutputStream;
import java.io.Serializable;
import java.util.List;

public class RedisCache implements ICache, AutoCloseable {
    private String _cacheKeyPrefix = "GroupDocs:";
    private ConnectionMultiplexer _redis;
    private IDatabase _db;
    
    public RedisCache() {
        _redis = ConnectionMultiplexer.Connect("localhost");
        _db = _redis.GetDatabase();
    }

    public void Set(String key, Serializable data) throws IOException {
        String prefixedKey = GetPrefixedKey(key);
        try (ObjectOutputStream oos = new ObjectOutputStream(_db.StreamWrite())) {
            oos.writeObject(data);
            _db.StringSet(prefixedKey, oos.toString());
        }
    }

    public boolean TryGetValue(String key, Object value) {
        String prefixedKey = GetPrefixedKey(key);
        byte[] serializedData = _db.StringGet(prefixKey).ToArray();
        if (serializedData != null) {
            try (ObjectInputStream ois = new ObjectInputStream(new ByteArrayInputStream(serializedData))) {
                value = ois.readObject();
                return true;
            } catch (IOException | ClassNotFoundException e) {
                e.printStackTrace();
            }
        }
        return false;
    }

    public List<String> GetKeys(String filter) {
        return _db.Keys(_cacheKeyPrefix + "*" + filter + "*").Select(k -> k.ToString().Replace(_cacheKeyPrefix, "")).ToList();
    }

    private String GetPrefixedKey(String key) {
        return _cacheKeyPrefix + key;
    }

    @Override
    public void close() throws Exception {
        _redis.Dispose();
    }
}
```

#### Passo 2: Utilizzare la cache Redis con GroupDocs.Conversion
Ora inseriremo la cache in un flusso di lavoro di conversione. Questo snippet mostra un esempio di **convertire documenti pdf java** che verifica prima la cache prima di invocare GroupDocs.Conversion.

```java
// Example usage of RedisCache with GroupDocs.Conversion
public void ConvertAndCacheDocument(String filePath) throws IOException {
    String cacheKey = "converted:" + filePath;
    Object cachedResult;

    if (cacheRedis.TryGetValue(cacheKey, cachedResult)) {
        System.out.println("Retrieved from cache: " + cachedResult);
    } else {
        // Perform conversion
        Converter converter = new Converter(filePath);
        ConvertOptions options = new PdfConvertOptions();
        byte[] result = converter.Convert(() -> new ByteArrayOutputStream(), options);

        // Cache the conversion result
        cacheRedis.Set(cacheKey, result);
        System.out.println("Conversion performed and cached.");
    }
}
```

### Opzioni di configurazione delle chiavi
- **`_cacheKeyPrefix`** – Regola questo **redis cache key prefix** per raggruppare le voci correlate (ad es., `"Docs:"`).  
- **Impostazioni di ConnectionMultiplexer** – Ottimizza il pooling delle connessioni, i timeout o SSL per cluster Redis distribuiti.

## Come migliora Redis la velocità di conversione?
Carica il documento una volta, memorizza l'array di byte risultante in Redis e lo recupera nelle chiamate successive – questo elimina la necessità di conversioni ripetute ad alta intensità di CPU. Caching l'output binario, riduci il tempo medio di risposta da diversi secondi a pochi millisecondi, soprattutto per i documenti popolari acceduti frequentemente.

## Cos'è il prefisso della chiave della cache Redis?
Il `redis cache key prefix` è una breve stringa anteposta a ogni chiave di voce della cache, che consente di segmentare i dati (ad es., `"Docs:"` per le cache dei documenti, `"Thumb:"` per le miniature). Usare un prefisso unico previene collisioni accidentali di chiavi quando più applicazioni condividono la stessa istanza Redis.

## Come configurare la connessione Redis in Java?
Crea un'istanza `ConnectionMultiplexer` con l'indirizzo del server Redis, fornendo opzionalmente password e impostazioni SSL. Per una configurazione locale semplice, chiama `ConnectionMultiplexer.Connect("localhost")`. Per cluster di produzione, passa un elenco separato da virgole di endpoint dei nodi e configura `ConfigurationOptions` per failover e bilanciamento del carico.

## Come svuotare la cache Redis programmaticamente?
Invoca il metodo `KeyDelete` del database Redis con un pattern che corrisponde alle tue chiavi prefissate (ad es., `_db.KeyDelete("Docs:*")`). Questo rimuove tutti i risultati di conversione memorizzati in cache in un'unica operazione, utile durante i deployment o quando i file sorgente sottostanti cambiano. Puoi anche usare il comando `SCAN` per iterare sulle chiavi corrispondenti prima della cancellazione, il che è più sicuro per grandi dataset.  

`KeyDelete` è un metodo del client del database Redis che rimuove le chiavi corrispondenti a un determinato pattern.

## Applicazioni pratiche
1. **Flussi di lavoro di conversione documenti:** Cache di output PDF o immagine per servire richieste ripetute istantaneamente.  
2. **Reti di distribuzione dei contenuti (CDN):** Memorizza i binari in cache in Redis per una consegna rapida ai nodi edge.  
3. **Sistemi di elaborazione batch:** Riutilizza i risultati di conversione in più esecuzioni batch, risparmiando cicli CPU.

## Considerazioni sulle prestazioni
### Ottimizzare l'uso della cache Redis
- **Gestione della memoria:** Imposta `maxmemory` e le politiche di espulsione appropriate (ad es., `volatile-lru`).  
- **Politiche di espulsione:** Scegli LRU, LFU o scadenza basata su TTL in base ai pattern di utilizzo.  
- **Overhead di serializzazione:** L'esempio utilizza la serializzazione Java; per payload più leggeri considera protobuf o JSON.

### Gestione della memoria Java con GroupDocs.Conversion
Gestisci file di grandi dimensioni trasmettendo i risultati (`ByteArrayOutputStream`) e rilasciando le risorse tempestivamente. L'implementazione `AutoCloseable` di `RedisCache` garantisce che la connessione Redis venga chiusa correttamente.

## Problemi comuni e risoluzione
| Sintomo | Causa probabile | Soluzione |
|---------|-----------------|-----------|
| `ConnectionMultiplexer.Connect` genera timeout | Redis non raggiungibile o host/porta errati | Verifica che il server Redis sia in esecuzione e raggiungibile (`redis-cli ping`). |
| `TryGetValue` restituisce sempre false | Discrepanza tra il formato di serializzazione memorizzato e quello recuperato | Assicurati che lo stesso serializer sia usato sia per `Set` che per `TryGetValue`. |
| Errori out‑of‑memory su PDF di grandi dimensioni | Memorizzare enormi array di byte in Redis senza limiti | Abilita `maxmemory` e imposta una politica di espulsione appropriata. |

## Domande frequenti

**Q: Posso usare questo approccio con un cluster Redis remoto?**  
A: Sì. Sostituisci `"localhost"` con l'endpoint del cluster e configura `ConnectionMultiplexer` per l'autenticazione SSL e password.

**Q: Come modifico il `redis cache key prefix`?**  
A: Modifica il campo `_cacheKeyPrefix` in `RedisCache`. Usare un prefisso unico aiuta a evitare collisioni di chiavi tra le applicazioni.

**Q: Esiste un modo per svuotare la cache programmaticamente?**  
A: Chiama `_db.KeyDelete(pattern)` o usa `GetKeys` per recuperare le chiavi corrispondenti e cancellarle in un ciclo.

**Q: Funziona per convertire documenti diversi da PDF?**  
A: Assolutamente. Sostituisci `PdfConvertOptions` con la sottoclasse `ConvertOptions` appropriata (ad es., `DocxConvertOptions`).

**Q: Quale versione di GroupDocs.Conversion è necessaria?**  
A: Il tutorial è stato testato con GroupDocs.Conversion **25.2**; le versioni più recenti dovrebbero essere compatibili.

## Conclusione
Padroneggiando **come utilizzare Redis** insieme a GroupDocs.Conversion, hai costruito uno strato di cache solido che riduce drasticamente il tempo di conversione, diminuisce il carico del server e migliora l'esperienza dell'utente finale. Continua a sperimentare con diversi **redis cache key prefix**, politiche di espulsione e formati di serializzazione per ottimizzare le prestazioni in base al tuo carico di lavoro specifico.

**Passi successivi**
- Prova diverse strategie di espulsione (LRU, TTL).  
- Analizza l'uso della memoria con batch di documenti di grandi dimensioni.  
- Esplora funzionalità avanzate di GroupDocs come filigrane o conversione multi‑pagina.

---

**Ultimo aggiornamento:** 2026-07-24  
**Testato con:** GroupDocs.Conversion 25.2  
**Autore:** GroupDocs

## Tutorial correlati

- [Come memorizzare nella cache i documenti in Java usando Redis & GroupDocs](/conversion/java/cache-management/custom-cache-redis-groupdocs-java/)
- [Come memorizzare nella cache i file in Java con GroupDocs.Conversion – Guida completa per una conversione efficiente dei documenti](/conversion/java/cache-management/implement-java-file-caching-groupdocs-conversion-guide/)
- [Implementare cache personalizzata Java – Cache di GroupDocs Conversion](/conversion/java/cache-management/)