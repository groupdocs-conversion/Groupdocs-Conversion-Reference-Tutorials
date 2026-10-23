---
date: '2026-10-21'
description: Scopri come creare cache key Java e integrare Redis con GroupDocs.Conversion
  per aumentare le prestazioni di rendering, ridurre i tempi di conversione e configurare
  i TTL in un semplice progetto Java.
images:
- /java/cache-management/custom-cache-redis-groupdocs-java/og-image.png
keywords:
- create cache key java
- java redis caching
- groupdocs conversion cache
- redis ttl java
lastmod: '2026-10-21'
og_description: Crea cache key Java in questa guida passo‑passo che mostra come integrare
  Redis con GroupDocs.Conversion per memorizzare nella cache i byte dei documenti,
  aumentare le prestazioni di rendering e ridurre i tempi di conversione. Configura
  i TTL e misura i guadagni di velocità.
og_image_alt: 'Developer guide: create cache key Java using Redis and GroupDocs'
og_title: Crea cache key Java – cache dei documenti con Redis e GroupDocs
schemas:
- author: GroupDocs
  dateModified: '2026-10-21'
  description: Learn how to create cache key Java and integrate Redis with GroupDocs.Conversion
    to boost rendering performance, reduce conversion time, and configure TTLs.
  headline: Create cache key Java – cache docs with Redis and GroupDocs
  type: TechArticle
- description: Learn how to create cache key Java and integrate Redis with GroupDocs.Conversion
    to boost rendering performance, reduce conversion time, and configure TTLs.
  name: Create cache key Java – cache docs with Redis and GroupDocs
  steps:
  - name: '**High‑traffic portals** – Serve frequently requested PDFs (catalogs, whitepapers)
      instantly.'
    text: '**High‑traffic portals** – Serve frequently requested PDFs (catalogs, whitepapers)
      instantly.'
  - name: '**Enterprise DMS** – Reduce load when users repeatedly view the same contracts
      or policy documents.'
    text: '**Enterprise DMS** – Reduce load when users repeatedly view the same contracts
      or policy documents.'
  - name: '**E‑commerce** – Cache generated invoices or product catalogs to speed
      up checkout.'
    text: '**E‑commerce** – Cache generated invoices or product catalogs to speed
      up checkout.'
  - name: '**Learning platforms** – Deliver lecture notes and e‑books without re‑rendering
      on every student request.'
    text: '**Learning platforms** – Deliver lecture notes and e‑books without re‑rendering
      on every student request.'
  - name: '**Legal services** – Accelerate distribution of case files while keeping
      storage costs low.'
    text: '**Legal services** – Accelerate distribution of case files while keeping
      storage costs low.'
  type: HowTo
- questions:
  - answer: Absolutely. The same caching pattern works for DOCX, HTML, images, and
      more – just change the `ConvertOptions` type.
    question: Can I use this approach with other GroupDocs output formats?
  - answer: Combine the source file path, conversion options, and any version identifiers.
      This guarantees uniqueness per configuration.
    question: How do I choose a good cache key?
  - answer: Invalidate the cache manually (e.g., delete the key) or use a shorter
      TTL so stale data expires quickly.
    question: What if a document changes after it’s cached?
  - answer: No, but Redis offers low latency, built‑in TTL, and wide Java client support,
      making it a popular choice for this scenario.
    question: Is Redis the only option for caching?
  - answer: Minimal. The heavy lifting is done by Redis; the app only holds short‑lived
      connections via Jedis.
    question: Does this increase memory usage on the application server?
  type: FAQPage
tags:
- create cache key java
- java redis cache
- groupdocs conversion
- document rendering
title: Crea cache key Java – cache dei documenti in Java con Redis
type: docs
url: /it/java/cache-management/custom-cache-redis-groupdocs-java/
weight: 1
---

# Crea chiave cache Java – memorizza i documenti in Java con Redis

Nelle moderne applicazioni web, servire lo stesso documento convertito ripetutamente può sprecare cicli CPU e aumentare i tempi di risposta. **Creare una chiave cache in Java** ti consente di memorizzare l'output della conversione una volta e recuperarlo istantaneamente nelle richieste successive. Questo tutorial mostra come integrare Redis in un flusso di lavoro GroupDocs.Conversion, generare chiavi cache affidabili, configurare i TTL e misurare i miglioramenti di prestazioni che puoi aspettarti.

## Risposte rapide
- **Di cosa tratta questo tutorial?** Un tutorial completo sul caching java redis che integra Redis con GroupDocs.Conversion.  
- **Perché usare Redis?** Offre latenza sub‑millisecondo, supporta la scadenza TTL e si scala orizzontalmente su più istanze dell'app.  
- **Ho bisogno di una licenza GroupDocs?** Una licenza di prova o temporanea è sufficiente per i test; è necessaria una licenza completa per le distribuzioni in produzione.  
- **Quali sono i passaggi principali?** Aggiungi le dipendenze Maven, configura un `JedisPool`, crea i metodi helper per la cache e collega la cache al flusso di conversione.  
- **Quale versione di Java è supportata?** Java 8+ (compatibile con le ultime versioni di GroupDocs.Conversion).

## Cos'è il caching dei documenti con Redis?
Caching dei documenti con Redis significa persistere l'output binario di una conversione (ad esempio, un array di byte PDF) in Redis in modo che richieste future identiche possano recuperare i byte memorizzati invece di rieseguire il motore di conversione. Questo elimina lavoro CPU ridondante, riduce la larghezza di banda di rete e offre un'esperienza utente più fluida.

## Perché implementare la cache Redis in Java?
Caricare un documento una volta, memorizzare il risultato e servirlo istantaneamente su richieste ripetute può **ridurre il tempo di conversione fino al 90 %** per file frequentemente accessi, **abbassare i costi infrastrutturali** riducendo l'uso della CPU, e **fornire una fonte unica di verità** per tutti i nodi dell'applicazione in un ambiente clusterizzato. Redis può elaborare più di 200 k operazioni al secondo su un singolo nodo, garantendo ricerche sub‑millisecondo.

## Prerequisiti
- **GroupDocs.Conversion** – versione 25.2 o successiva (supporta **120+** formati di input e output).  
- **Jedis** (il client Redis ufficiale per Java).  
- Un'istanza Redis in esecuzione (lo sviluppo locale può usare il valore predefinito `localhost:6379`).  
- Maven per la gestione delle dipendenze.  
- Familiarità di base con la gestione delle eccezioni Java e gli stream I/O.

## Configurare GroupDocs.Conversion per Java

`GroupDocs.Conversion` è una libreria Java che converte e rende i documenti in un'ampia gamma di formati, gestendo automaticamente la conservazione del layout, l'incorporamento dei font e l'estrazione delle immagini.

Aggiungi il repository GroupDocs e la dipendenza al tuo `pom.xml`:

```xml
<repositories>
    <repository>
        <id>groupdocs-maven</id>
        <url>https://repo.groupdocs.com/maven</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-conversion</artifactId>
        <version>25.2.0</version>
    </dependency>
    <dependency>
        <groupId>redis.clients</groupId>
        <artifactId>jedis</artifactId>
        <version>4.2.3</version>
    </dependency>
</dependencies>
```

### Acquisizione della licenza
Puoi iniziare con una **Free Trial**, richiedere una **Temporary License** per la valutazione, o acquistare una **License** completa per l'uso in produzione.

Inizializza GroupDocs.Conversion nel tuo codice Java:

```java
import com.groupdocs.conversion.*;

ConversionConfig config = new ConversionConfig();
config.setLicensePath("path/to/license/file.lic");
ConversionApi conversionApi = new ConversionApi(config);
```

## Guida all'implementazione

### Creare una cache personalizzata usando Redis

#### Panoramica
Una cache Redis personalizzata conserva i byte del documento renderizzato, consentendo il recupero istantaneo su richieste ripetute.

#### Configurare JedisPool
`JedisPool` è un pool thread‑safe di connessioni Redis riutilizzabili che minimizza l'overhead dei socket e migliora il throughput.

```java
import redis.clients.jedis.JedisPool;
import redis.clients.jedis.JedisPoolConfig;

JedisPoolConfig poolConfig = new JedisPoolConfig();
poolConfig.setMaxTotal(20);               // maximum active connections
poolConfig.setMaxIdle(10);                // maximum idle connections
poolConfig.setMinIdle(2);                 // minimum idle connections
JedisPool jedisPool = new JedisPool(poolConfig, "localhost", 6379);
```

#### Memorizzare e recuperare i dati cache
I metodi helper seguenti serializzano un array di byte in una stringa Base64 per una memorizzazione sicura e lo recuperano nuovamente in un array di byte.

```java
import java.util.Base64;
import redis.clients.jedis.Jedis;

public class RedisCacheHelper {

    private final JedisPool pool;
    private final int ttlSeconds; // time‑to‑live for cached entries

    public RedisCacheHelper(JedisPool pool, int ttlSeconds) {
        this.pool = pool;
        this.ttlSeconds = ttlSeconds;
    }

    public void put(String key, byte[] data) {
        try (Jedis jedis = pool.getResource()) {
            String encoded = Base64.getEncoder().encodeToString(data);
            jedis.setex(key, ttlSeconds, encoded); // configure redis ttl
        }
    }

    public byte[] get(String key) {
        try (Jedis jedis = pool.getResource()) {
            String encoded = jedis.get(key);
            return encoded != null ? Base64.getDecoder().decode(encoded) : null;
        }
    }
}
```

#### Integrazione con GroupDocs.Conversion
Ora collega la cache al flusso di lavoro di conversione. Il metodo controlla prima la cache; se si verifica un miss, esegue la conversione, memorizza il risultato e restituisce i byte.

```java
import com.groupdocs.conversion.options.convertoptions.PdfConvertOptions;

public class DocumentService {

    private final ConversionApi conversionApi;
    private final RedisCacheHelper cacheHelper;

    public DocumentService(ConversionApi conversionApi, RedisCacheHelper cacheHelper) {
        this.conversionApi = conversionApi;
        this.cacheHelper = cacheHelper;
    }

    public byte[] convertToPdf(String sourcePath, PdfConvertOptions options) throws Exception {
        // Build a deterministic cache key
        String cacheKey = "pdf:" + sourcePath + ":" + options.hashCode();

        // Attempt to fetch from Redis
        byte[] cached = cacheHelper.get(cacheKey);
        if (cached != null) {
            // Cache hit – return stored bytes
            return cached;
        }

        // Cache miss – perform conversion
        byte[] result = conversionApi.convert(sourcePath, options).toByteArray();

        // Store result for future calls
        cacheHelper.put(cacheKey, result);
        return result;
    }
}
```

## Come creare una chiave cache Java per il caching Redis?
Genera una chiave deterministica concatenando il percorso del file sorgente, i valori selezionati di `ConvertOptions` e un tag di versione opzionale, quindi hash la stringa con SHA‑256. Questa chiave identifica in modo univoco ogni configurazione di conversione, garantendo che le richieste identiche colpiscano la cache mentre opzioni diverse generano voci separate.

La classe `ConversionApi` è il componente centrale in GroupDocs.Conversion che esegue le conversioni dei documenti. Puoi creare una chiave cache, cercarla in Redis e invocare `ConversionApi.convert` solo quando la chiave è assente, riducendo drasticamente il tempo di conversione e il carico del server.

## Come implementare il caching Redis in Java?
`ConversionApi` è la classe principale in GroupDocs.Conversion che esegue le operazioni di conversione dei documenti. Carica il tuo documento sorgente, genera una chiave cache deterministica, cercala in Redis e invoca `ConversionApi` solo quando la chiave è assente. Questo modello garantisce che ogni conversione unica venga eseguita una sola volta, poi servita dalla cache per la durata del TTL configurato.

## Suggerimenti per la risoluzione dei problemi
- Verifica che il server Redis sia raggiungibile (`redis-cli ping` dovrebbe restituire `PONG`).  
- Assicurati che host e porta di `JedisPool` corrispondano al tuo deployment Redis.  
- Avvolgi le chiamate alla cache in blocchi try‑catch per gestire interruzioni di connettività senza interrompere il flusso di conversione.  
- Monitora la memoria di Redis (`INFO memory`) e imposta le politiche `maxmemory` (ad es., `volatile-lru`) per espellere le vecchie voci in modo graduale.  
- Se incontri `OutOfMemoryError` sulla JVM, aumenta la dimensione dell'heap o abilita `-XX:+UseCompressedOops`.

## Applicazioni pratiche

1. **Portali ad alto traffico** – Servi PDF richiesti frequentemente (cataloghi, whitepaper) istantaneamente.  
2. **DMS aziendale** – Riduci il carico quando gli utenti visualizzano ripetutamente gli stessi contratti o documenti di policy.  
3. **E‑commerce** – Cache le fatture generate o i cataloghi di prodotto per velocizzare il checkout.  
4. **Piattaforme di apprendimento** – Consegna appunti delle lezioni e e‑book senza ri‑renderizzare ad ogni richiesta degli studenti.  
5. **Servizi legali** – Accelerare la distribuzione dei fascicoli dei casi mantenendo bassi i costi di archiviazione.

## Considerazioni sulle prestazioni

- **Ottimizza Redis** – Regola `maxmemory`, scegli una politica di espulsione come `allkeys-lru` e imposta valori `timeout` appropriati in base al tuo modello di traffico.  
- **Monitora i rapporti hit/miss della cache** – Usa `INFO stats` o i contatori `keyspace_hits` / `keyspace_misses` di Redis per affinare i TTL.  
- **Dimensionamento dell'heap JVM** – Assicurati che l'heap possa contenere i buffer di GroupDocs; una regola pratica è 1 GB di heap per ogni 100 MB di payload di conversione concorrente.  
- **Conversioni batch** – Quando converti molti file, riutilizza una singola istanza `Jedis` per thread per ridurre al minimo il churn dei socket.

## Domande frequenti

**Q: Posso usare questo approccio con altri formati di output di GroupDocs?**  
A: Assolutamente. Lo stesso schema di caching funziona per DOCX, HTML, immagini e altro – basta cambiare il tipo `ConvertOptions`.

**Q: Come scelgo una buona chiave cache?**  
A: Combina il percorso del file sorgente, le opzioni di conversione e eventuali identificatori di versione. Questo garantisce l'unicità per configurazione.

**Q: Cosa succede se un documento cambia dopo essere stato memorizzato nella cache?**  
A: Invalida la cache manualmente (ad es., elimina la chiave) o utilizza un TTL più breve così i dati obsoleti scadono rapidamente.

**Q: Redis è l'unica opzione per il caching?**  
A: No, ma Redis offre bassa latenza, TTL integrato e ampio supporto client Java, rendendolo una scelta popolare per questo scenario.

**Q: Questo aumenta l'uso di memoria sul server dell'applicazione?**  
A: Minimo. L'elaborazione pesante è svolta da Redis; l'app mantiene solo connessioni di breve durata tramite Jedis.

## Conclusione
Ora hai un tutorial completo sul **java redis caching** che mostra come memorizzare nella cache i documenti usando Redis e GroupDocs.Conversion. Persistendo l'output renderizzato in Redis, **aumenterai le prestazioni di rendering**, **ridurrai il tempo di conversione** e offrirai un'esperienza più fluida agli utenti finali. Sperimenta con diversi valori TTL, monitora le metriche della cache e estendi lo schema ad altri formati di documento man mano che la tua applicazione cresce.

---

**Ultimo aggiornamento:** 2026-10-21  
**Testato con:** GroupDocs.Conversion 25.2, Jedis 4.2.3  
**Autore:** GroupDocs

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

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.convert.PdfConvertOptions;

public class DocumentConversion {
    public static void main(String[] args) {
        // Initialize the Converter with a document path
        Converter converter = new Converter("input.docx");
        
        // Set up conversion options for PDF
        PdfConvertOptions options = new PdfConvertOptions();
        converter.convert("output.pdf", options);
    }
}
```

```java
import redis.clients.jedis.JedisPool;

public class CacheManager {
    private static JedisPool jedisPool = new JedisPool("localhost", 6379);
    
    public static void main(String[] args) {
        // Additional cache setup code here
    }
}
```

```java
import redis.clients.jedis.Jedis;

public class CacheManager {

    public static void storeDocument(String key, String documentContent) {
        try (Jedis jedis = jedisPool.getResource()) {
            // Set the content in Redis cache with an expiration time of one hour
            jedis.setex(key, 3600, documentContent);
        }
    }

    public static String retrieveDocument(String key) {
        try (Jedis jedis = jedisPool.getResource()) {
            return jedis.get(key); // Retrieve cached content if available
        }
    }
}
```

```java
public class DocumentConversion {

    public static void convertWithCache(String inputPath, String outputPath) {
        Converter converter = new Converter(inputPath);
        PdfConvertOptions options = new PdfConvertOptions();

        // Generate a cache key based on the document path and conversion settings
        String cacheKey = "doc:" + inputPath;

        // Check if the converted document is already cached
        String cachedDocument = CacheManager.retrieveDocument(cacheKey);

        if (cachedDocument != null) {
            System.out.println("Using cached version of the document.");
            // Save cached content to output file
            Files.write(Paths.get(outputPath), cachedDocument.getBytes());
        } else {
            // Perform conversion and cache the result
            converter.convert(output -> {
                String documentContent = new String(output.toByteArray());
                CacheManager.storeDocument(cacheKey, documentContent);
                Files.write(Paths.get(outputPath), output.toByteArray());
            }, options);
        }
    }

    public static void main(String[] args) {
        convertWithCache("input.docx", "output.pdf");
    }
}
```

## Tutorial correlati

- [Implementare cache personalizzata Java – Cache GroupDocs Conversion](/conversion/java/cache-management/)
- [Come utilizzare la cache Redis in Java con GroupDocs.Conversion](/conversion/java/cache-management/redis-cache-java-groupdocs-conversion-guide/)
- [Come memorizzare nella cache i file in Java con GroupDocs.Conversion – Guida completa per una conversione documenti efficiente](/conversion/java/cache-management/implement-java-file-caching-groupdocs-conversion-guide/)
