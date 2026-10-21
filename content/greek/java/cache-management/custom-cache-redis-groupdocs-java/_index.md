---
date: '2026-10-21'
description: Μάθετε πώς να δημιουργήσετε κλειδί cache Java και να ενσωματώσετε το
  Redis με το GroupDocs.Conversion για να ενισχύσετε την απόδοση rendering, να μειώσετε
  το χρόνο μετατροπής και να διαμορφώσετε TTLs σε ένα απλό έργο Java.
images:
- /java/cache-management/custom-cache-redis-groupdocs-java/og-image.png
keywords:
- create cache key java
- java redis caching
- groupdocs conversion cache
- redis ttl java
lastmod: '2026-10-21'
og_description: Δημιουργήστε κλειδί cache Java σε αυτόν τον step‑by‑step οδηγό που
  δείχνει πώς να ενσωματώσετε το Redis με το GroupDocs.Conversion για να cache bytes
  εγγράφων, να ενισχύσετε την απόδοση rendering και να μειώσετε το χρόνο μετατροπής.
  Διαμορφώστε TTLs και μετρήστε τα κέρδη σε ταχύτητα.
og_image_alt: 'Developer guide: create cache key Java using Redis and GroupDocs'
og_title: Δημιουργία κλειδιού cache Java – cache εγγράφων με Redis και GroupDocs
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
title: Δημιουργία κλειδιού cache Java – cache εγγράφων σε Java με Redis
type: docs
url: /el/java/cache-management/custom-cache-redis-groupdocs-java/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία κλειδιού cache Java – αποθήκευση εγγράφων στην Java με Redis

Σε σύγχρονες web εφαρμογές, η εξυπηρέτηση του ίδιου μετατρεπόμενου εγγράφου επανειλημμένα μπορεί να σπαταλήσει κύκλους CPU και να αυξήσει τους χρόνους απόκρισης. **Δημιουργώντας ένα κλειδί cache στην Java** μπορείτε να αποθηκεύσετε το αποτέλεσμα της μετατροπής μία φορά και να το ανακτήσετε άμεσα σε επόμενα αιτήματα. Αυτό το tutorial δείχνει πώς να ενσωματώσετε το Redis σε μια ροή εργασίας GroupDocs.Conversion, να δημιουργήσετε αξιόπιστα κλειδιά cache, να διαμορφώσετε TTLs και να μετρήσετε τα κέρδη απόδοσης που μπορείτε να περιμένετε.

## Γρήγορες απαντήσεις
- **What does this tutorial cover?** Ένα πλήρες tutorial caching java redis που ενσωματώνει το Redis με το GroupDocs.Conversion.  
- **Why use Redis?** Παρέχει υπο‑χιλιοσκοπική καθυστέρηση, υποστηρίζει λήξη TTL και κλιμακώνεται οριζόντια σε πολλαπλά instances εφαρμογών.  
- **Do I need a GroupDocs license?** Μια δοκιμαστική ή προσωρινή άδεια είναι επαρκής για δοκιμές· απαιτείται πλήρης άδεια για παραγωγικές αναπτύξεις.  
- **What are the main steps?** Προσθέστε εξαρτήσεις Maven, διαμορφώστε ένα `JedisPool`, δημιουργήστε μεθόδους βοηθών cache και ενσωματώστε το cache στη διαδικασία μετατροπής.  
- **Which Java version is supported?** Java 8+ (συμβατό με τις τελευταίες εκδόσεις GroupDocs.Conversion).

## Τι είναι η αποθήκευση εγγράφων στην Redis;
Η αποθήκευση εγγράφων στην Redis σημαίνει την διατήρηση του δυαδικού αποτελέσματος μιας μετατροπής (π.χ. πίνακα byte PDF) στο Redis, ώστε μελλοντικά πανομοιότυπα αιτήματα να μπορούν να ανακτήσουν τα αποθηκευμένα bytes αντί να εκτελούν ξανά τη μηχανή μετατροπής. Αυτό εξαλείφει περιττή εργασία CPU, μειώνει το εύρος ζώνης δικτύου και προσφέρει πιο ομαλή εμπειρία χρήστη.

## Γιατί να υλοποιήσετε cache Redis στην Java;
Φορτώνοντας ένα έγγραφο μία φορά, αποθηκεύοντας το αποτέλεσμα και εξυπηρετώντάς το άμεσα σε επαναλαμβανόμενες κλήσεις, μπορείτε **να μειώσετε το χρόνο μετατροπής έως και 90 %** για συχνά προσπελαζόμενα αρχεία, **να μειώσετε το κόστος υποδομής** μειώνοντας τη χρήση CPU, και **να παρέχετε μια ενιαία πηγή αλήθειας** για όλους τους κόμβους της εφαρμογής σε περιβάλλον cluster. Το Redis μπορεί να επεξεργαστεί πάνω από 200 k λειτουργίες ανά δευτερόλεπτο σε έναν μόνο κόμβο, εξασφαλίζοντας υπο‑χιλιοσκοπικές αναζητήσεις.

## Προαπαιτούμενα
- **GroupDocs.Conversion** – έκδοση 25.2 ή νεότερη (υποστηρίζει **120+** μορφές εισόδου και εξόδου).  
- **Jedis** (ο επίσημος πελάτης Redis για Java).  
- Μια ενεργή παρουσία Redis (για τοπική ανάπτυξη μπορείτε να χρησιμοποιήσετε το προεπιλεγμένο `localhost:6379`).  
- Maven για διαχείριση εξαρτήσεων.  
- Βασική εξοικείωση με τη διαχείριση εξαιρέσεων Java και τα ρεύματα I/O.

## Ρύθμιση GroupDocs.Conversion για Java

`GroupDocs.Conversion` είναι μια βιβλιοθήκη Java που μετατρέπει και αποδίδει έγγραφα σε ευρύ φάσμα μορφών, διαχειριζόμενη τη διατήρηση διάταξης, την ενσωμάτωση γραμματοσειρών και την εξαγωγή εικόνων αυτόματα.

Προσθέστε το αποθετήριο GroupDocs και την εξάρτηση στο `pom.xml`:

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

### Απόκτηση άδειας
Μπορείτε να ξεκινήσετε με **Δωρεάν Δοκιμή**, να ζητήσετε **Προσωρινή Άδεια** για αξιολόγηση, ή να αγοράσετε πλήρη **Άδεια** για παραγωγική χρήση.

Αρχικοποιήστε το GroupDocs.Conversion στον κώδικά σας Java:

```java
import com.groupdocs.conversion.*;

ConversionConfig config = new ConversionConfig();
config.setLicensePath("path/to/license/file.lic");
ConversionApi conversionApi = new ConversionApi(config);
```

## Οδηγός υλοποίησης

### Δημιουργία προσαρμοσμένου cache χρησιμοποιώντας Redis

#### Επισκόπηση
Ένα προσαρμοσμένο cache Redis αποθηκεύει τα bytes του αποδοθέντος εγγράφου, επιτρέποντας άμεση ανάκτηση σε επαναλαμβανόμενα αιτήματα.

#### Ρύθμιση JedisPool
Το JedisPool είναι μια ασφαλής προς νήματα δεξαμενή επαναχρησιμοποιήσιμων συνδέσεων Redis που ελαχιστοποιεί το κόστος socket και βελτιώνει τη διαπερατότητα.

```java
import redis.clients.jedis.JedisPool;
import redis.clients.jedis.JedisPoolConfig;

JedisPoolConfig poolConfig = new JedisPoolConfig();
poolConfig.setMaxTotal(20);               // maximum active connections
poolConfig.setMaxIdle(10);                // maximum idle connections
poolConfig.setMinIdle(2);                 // minimum idle connections
JedisPool jedisPool = new JedisPool(poolConfig, "localhost", 6379);
```

#### Αποθήκευση και ανάκτηση δεδομένων cache
Οι βοηθητικές μεθόδους παρακάτω σειριοποιούν έναν πίνακα byte σε συμβολοσειρά Base64 για ασφαλή αποθήκευση και τον επαναφέρουν σε πίνακα byte.

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

#### Ενσωμάτωση με GroupDocs.Conversion
Τώρα συνδέστε το cache στη ροή εργασίας μετατροπής. Η μέθοδος ελέγχει πρώτα το cache· εάν λείπει, εκτελεί τη μετατροπή, αποθηκεύει το αποτέλεσμα και επιστρέφει τα bytes.

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

## Πώς να δημιουργήσετε κλειδί cache Java για αποθήκευση Redis;
Δημιουργήστε ένα ντετερμινιστικό κλειδί συνενώνοντας τη διαδρομή του αρχείου προέλευσης, τις τιμές των επιλεγμένων `ConvertOptions` και ένα προαιρετικό tag έκδοσης, στη συνέχεια κάντε hash τη συμβολοσειρά με SHA‑256. Αυτό το κλειδί ταυτοποιεί μοναδικά κάθε διαμόρφωση μετατροπής, διασφαλίζοντας ότι τα ίδια αιτήματα χτυπούν το cache ενώ διαφορετικές επιλογές δημιουργούν ξεχωριστές εγγραφές.

Η κλάση `ConversionApi` είναι το κεντρικό στοιχείο στο GroupDocs.Conversion που εκτελεί τις μετατροπές εγγράφων. Μπορείτε να δημιουργήσετε ένα κλειδί cache, να το αναζητήσετε στο Redis και να καλέσετε το `ConversionApi.convert` μόνο όταν το κλειδί λείπει, μειώνοντας δραστικά το χρόνο μετατροπής και το φορτίο του διακομιστή.

## Πώς να υλοποιήσετε caching Java Redis;
Η `ConversionApi` είναι η κύρια κλάση στο GroupDocs.Conversion που εκτελεί λειτουργίες μετατροπής εγγράφων. Φορτώστε το πηγαίο έγγραφο, δημιουργήστε ένα ντετερμινιστικό κλειδί cache, αναζητήστε το στο Redis και καλέστε το `ConversionApi` μόνο όταν το κλειδί δεν υπάρχει. Αυτό το μοτίβο εγγυάται ότι κάθε μοναδική μετατροπή εκτελείται μία φορά και στη συνέχεια εξυπηρετείται από το cache για τη διάρκεια του καθορισμένου TTL.

## Συμβουλές αντιμετώπισης προβλημάτων
- Επαληθεύστε ότι ο διακομιστής Redis είναι προσβάσιμος (`redis-cli ping` πρέπει να επιστρέφει `PONG`).  
- Βεβαιωθείτε ότι το host και η θύρα του `JedisPool` ταιριάζουν με την ανάπτυξη Redis.  
- Τυλίξτε τις κλήσεις cache σε μπλοκ try‑catch για να διαχειριστείτε διακοπές σύνδεσης χωρίς να διακόπτετε τη ροή μετατροπής.  
- Παρακολουθήστε τη μνήμη Redis (`INFO memory`) και ορίστε πολιτικές `maxmemory` (π.χ. `volatile-lru`) για ευγενική εκκένωση παλαιών εγγραφών.  
- Εάν αντιμετωπίσετε `OutOfMemoryError` στη JVM, αυξήστε το μέγεθος heap ή ενεργοποιήστε `-XX:+UseCompressedOops`.

## Πρακτικές εφαρμογές

1. **High‑traffic portals** – Εξυπηρετήστε άμεσα συχνά ζητούμενα PDF (καταλόγους, whitepapers).  
2. **Enterprise DMS** – Μειώστε το φορτίο όταν οι χρήστες προβάλλουν επανειλημμένα τα ίδια συμβόλαια ή έγγραφα πολιτικής.  
3. **E‑commerce** – Cache παραγόμενα τιμολόγια ή καταλόγους προϊόντων για ταχύτερο checkout.  
4. **Learning platforms** – Παρέχετε σημειώσεις διαλέξεων και e‑books χωρίς επανασχεδίαση σε κάθε αίτημα μαθητή.  
5. **Legal services** – Επιταχύνετε τη διανομή φακέλων υποθέσεων διατηρώντας χαμηλό κόστος αποθήκευσης.

## Σκέψεις απόδοσης

- **Tune Redis** – Προσαρμόστε το `maxmemory`, επιλέξτε πολιτική εκκένωσης όπως `allkeys-lru` και ορίστε κατάλληλες τιμές `timeout` βάσει του προτύπου κυκλοφορίας σας.  
- **Track cache hit/miss ratios** – Χρησιμοποιήστε `INFO stats` ή τους μετρητές `keyspace_hits` / `keyspace_misses` του Redis για να βελτιστοποιήσετε τα TTL.  
- **JVM heap sizing** – Βεβαιωθείτε ότι το heap μπορεί να φιλοξενήσει τα buffers του GroupDocs· ένας κανόνας είναι 1 GB heap ανά 100 MB ταυτόχρονου φορτίου μετατροπής.  
- **Batch conversions** – Όταν μετατρέπετε πολλά αρχεία, επαναχρησιμοποιήστε μια ενιαία παρουσία `Jedis` ανά νήμα για ελαχιστοποίηση του socket churn.

## Συχνές ερωτήσεις

**Q: Can I use this approach with other GroupDocs output formats?**  
A: Absolutely. The same caching pattern works for DOCX, HTML, images, and more – just change the `ConvertOptions` type.

**Q: How do I choose a good cache key?**  
A: Combine the source file path, conversion options, and any version identifiers. This guarantees uniqueness per configuration.

**Q: What if a document changes after it’s cached?**  
A: Invalidate the cache manually (e.g., delete the key) or use a shorter TTL so stale data expires quickly.

**Q: Is Redis the only option for caching?**  
A: No, but Redis offers low latency, built‑in TTL, and wide Java client support, making it a popular choice for this scenario.

**Q: Does this increase memory usage on the application server?**  
A: Minimal. The heavy lifting is done by Redis; the app only holds short‑lived connections via Jedis.

## Συμπέρασμα
Τώρα έχετε έναν πλήρη **java redis caching** tutorial που δείχνει πώς να αποθηκεύετε έγγραφα χρησιμοποιώντας το Redis και το GroupDocs.Conversion. Με την αποθήκευση του αποδοθέντος αποτελέσματος στο Redis, θα **βελτιώσετε την απόδοση απόδοσης**, **μειώσετε το χρόνο μετατροπής**, και θα προσφέρετε μια πιο ομαλή εμπειρία στους τελικούς χρήστες. Πειραματιστείτε με διαφορετικές τιμές TTL, παρακολουθήστε τα μετρικά του cache, και επεκτείνετε το μοτίβο σε άλλες μορφές εγγράφων καθώς η εφαρμογή σας μεγαλώνει.

---

**Last Updated:** 2026-10-21  
**Tested With:** GroupDocs.Conversion 25.2, Jedis 4.2.3  
**Author:** GroupDocs

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

## Σχετικοί οδηγοί

- [Implement Custom Cache Java – GroupDocs Conversion Cache](/conversion/java/cache-management/)
- [How to Use Redis Cache in Java with GroupDocs.Conversion](/conversion/java/cache-management/redis-cache-java-groupdocs-conversion-guide/)
- [How to Cache Files in Java with GroupDocs.Conversion – A Comprehensive Guide for Efficient Document Conversion](/conversion/java/cache-management/implement-java-file-caching-groupdocs-conversion-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}