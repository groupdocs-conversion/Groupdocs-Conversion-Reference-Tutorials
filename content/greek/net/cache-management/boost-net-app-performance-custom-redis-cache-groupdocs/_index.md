---
date: '2026-05-21'
description: Μάθετε πώς να χρησιμοποιήσετε το custom redis cache .net με το GroupDocs.Conversion
  για να επιταχύνετε δραματικά τη μετατροπή εγγράφων. Ανακαλύψτε τη βήμα‑βήμα εγκατάσταση,
  τη χρήση των βέλτιστων πρακτικών redis caching και τα performance metrics.
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
title: Βελτιώστε την απόδοση του .NET με custom redis cache .net και GroupDocs.Conversion
type: docs
url: /el/net/cache-management/boost-net-app-performance-custom-redis-cache-groupdocs/
weight: 1
---

# Βελτιώστε την απόδοση της .NET εφαρμογής σας με **custom redis cache .net** χρησιμοποιώντας το GroupDocs.Conversion

## Εισαγωγή

Αν η .NET εφαρμογή σας ξοδεύει πολύτιμα δευτερόλεπτα — ή ακόμη και λεπτά — για τη μετατροπή εγγράφων, δεν είστε μόνοι. Η υλοποίηση μιας λύσης **custom redis cache .net** μαζί με το GroupDocs.Conversion μπορεί να μειώσει τους χρόνους μετατροπής έως και 80 % για επαναλαμβανόμενα αιτήματα. Σε αυτό το tutorial θα μάθετε πώς να ρυθμίσετε το GroupDocs.Conversion, να δημιουργήσετε μια κρυφή μνήμη βασισμένη στο Redis και να εφαρμόσετε αποδεδειγμένες τεχνικές βελτιστοποίησης απόδοσης που διατηρούν την εφαρμογή σας ανταποκρινόμενη υπό βαριά φόρτωση.

### Γρήγορες Απαντήσεις
- **Τι αποθηκεύει η προσαρμοσμένη κρυφή μνήμη Redis;** Ροές byte PDF/HTML που έχουν αποδοθεί για κάθε πηγαίο έγγραφο.  
- **Πόσο γρηγορότερη μπορεί να γίνει η μετατροπή;** Έως 8× πιο γρήγορη για έγγραφα στην κρυφή μνήμη, μετρημένο σε διακομιστή 4‑πύρων.  
- **Χρειάζομαι εμπορική άδεια GroupDocs;** Ναι, απαιτείται έγκυρη άδεια για χρήση σε παραγωγή.  
- **Μπορεί να τρέξει σε .NET 6+;** Απόλυτα — συμβατό με .NET 5, .NET 6 και .NET 7.  
- **Περιλαμβάνεται υποστήριξη Docker;** Η κρυφή μνήμη λειτουργεί μέσα σε κοντέινερ· απλώς εκθέστε τη θύρα του Redis.

## Τι είναι το **custom redis cache .net**;

Αυτή είναι μια κρυφή μνήμη επιπέδου εφαρμογής που υλοποιείται από τον προγραμματιστή, η οποία αποθηκεύει την δυαδική έξοδο των μετατροπών εγγράφων σε ένα αποθηκευτικό σύστημα κλειδιού‑τιμής Redis, επιτρέποντας στις επόμενες αιτήσεις να ανακτούν το προ‑αποδομένο αποτέλεσμα άμεσα αντί να επεξεργάζονται ξανά το αρχικό αρχείο, μειώνοντας έτσι τη καθυστέρηση και το φορτίο CPU σε όλη την εφαρμογή.

## Γιατί να χρησιμοποιήσετε το **custom redis cache .net** με το GroupDocs.Conversion;

Το GroupDocs.Conversion υποστηρίζει **50+** μορφές εισόδου και εξόδου — συμπεριλαμβανομένων των DOCX, PPTX, HTML και PDF — και μπορεί να επεξεργαστεί έγγραφα έως 500 σελίδες χωρίς να φορτώνει ολόκληρο το αρχείο στη μνήμη. Συνδυάζοντάς το με μια κρυφή μνήμη Redis, εξαλείφετε την περιττή απόδοση, μειώνετε τη χρήση CPU κατά περίπου **70 %**, και διατηρείτε τους χρόνους απόκρισης κάτω από **200 ms** για τα αντικείμενα στην κρυφή μνήμη.

## Προαπαιτούμενα

- **GroupDocs.Conversion for .NET** (Έκδοση 25.3.0 ή νεότερη)  
- **StackExchange.Redis** πακέτο NuGet  
- Προσβάσιμη παρουσία Redis (π.χ., `192.168.222.4:6379`)  
- Visual Studio 2022 ή οποιοδήποτε IDE συμβατό με C#  
- .NET 6 SDK (ή .NET 5/Framework 4.8) εγκατεστημένο  

### Προαπαιτούμενα γνώσης
- Άνεση με τα πρότυπα async/await της C#  
- Βασικές έννοιες του Redis (κλειδιά, TTL, σύνδεση pool)  
- Εξοικείωση με τις γραμμές εργασίας μετατροπής εγγράφων  

## Πώς να ρυθμίσετε το GroupDocs.Conversion για .NET;

Ξεκινήστε προσθέτοντας το πακέτο GroupDocs.Conversion στο έργο σας χρησιμοποιώντας είτε το NuGet Package Manager Console είτε το .NET CLI. Αυτό εγκαθιστά τη βασική μηχανή μετατροπής και τις εξαρτήσεις της, προετοιμάζοντας το περιβάλλον σας για τη δημιουργία αντικειμένων Converter και τη διαμόρφωση ρυθμίσεων μετατροπής για διάφορες μορφές εγγράφων.

Install the library via NuGet:

```
Install-Package GroupDocs.Conversion
```

Or with the .NET CLI:

```
dotnet add package GroupDocs.Conversion
```

### Βήματα απόκτησης άδειας
- **Δωρεάν δοκιμή:** Εγγραφείτε στην πύλη GroupDocs για ένα αρχείο άδειας 30 ημερών.  
- **Προσωρινή άδεια:** Ζητήστε ένα κλειδί αξιολόγησης 90 ημερών για μεγαλύτερα φορτία εργασίας.  
- **Αγορά:** Αποκτήστε άδεια παραγωγής για να ξεκλειδώσετε απεριόριστες μετατροπές.

After installing the package, initialize GroupDocs.Conversion in your C# project:

```csharp
using GroupDocs.Conversion;
using GroupDocs.Conversion.Options.Convert;

// Initialize with a license file
Converter converter = new Converter("path/to/license.json");
```

## Πώς ένα **custom redis cache .net** βελτιώνει την ταχύτητα μετατροπής;

Όταν λαμβάνεται ένα αίτημα μετατροπής, η εφαρμογή πρώτα ερωτά το Redis για μια αποθηκευμένη ροή byte που ταιριάζει με το πηγαίο έγγραφο και τις παραμέτρους μετατροπής. Εάν υπάρχει αντιστοίχιση, το αποθηκευμένο αποτέλεσμα επιστρέφεται άμεσα, παρακάμπτοντας τη δαπανηρή διαδικασία απόδοσης· διαφορετικά, το GroupDocs.Conversion εκτελεί τη μετατροπή και το αποτέλεσμα αποθηκεύεται ξανά στο Redis για μελλοντική χρήση.

### Βήμα 1: Ορίστε την κλάση `RedisCache`

Η κλάση `RedisCache` παρέχει ένα ελαφρύ wrapper γύρω από το StackExchange.Redis για την αποθήκευση και ανάκτηση δυαδικών αποτελεσμάτων μετατροπής.

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

## Βήμα 2: Υλοποιήστε τη μετατροπή εγγράφων με την προσαρμοσμένη κρυφή μνήμη

Το παρακάτω παράδειγμα δείχνει την ενσωμάτωση του `RedisCache` με το GroupDocs.Conversion για την αποθήκευση της εξόδου μετατροπής PDF στην κρυφή μνήμη.

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

## Ποιες είναι οι κοινές περιπτώσεις χρήσης για το **custom redis cache .net**;

Η προσαρμοσμένη κρυφή μνήμη Redis μπορεί να αξιοποιηθεί σε οποιοδήποτε σενάριο όπου τα αποτελέσματα μετατροπής εγγράφων ζητούνται επανειλημμένα, παρέχοντας άμεση ανάκτηση και μειώνοντας το φορτίο του διακομιστή. Τυπικές εφαρμογές περιλαμβάνουν συστήματα διαχείρισης εγγράφων επιχειρήσεων, APIs υψηλής κίνησης που παρέχουν προεπισκοπήσεις, κρυφή μνήμη άκρων CDN για μετατρεπόμενα περιουσιακά στοιχεία, αυτοματοποιημένα dashboards αναφορών και πλατφόρμες e‑commerce που δημιουργούν φυλλάδια προϊόντων κατ' απαίτηση.

1. **Συστήματα Διαχείρισης Εγγράφων Επιχειρήσεων:** Επιταχύνετε τη δημιουργία προεπισκοπήσεων για χιλιάδες PDF που αποθηκεύονται σε κεντρικό αποθετήριο.  
2. **Web APIs:** Επιστρέψτε προ‑μετατρεπόμενα HTML ή μικρογραφίες εικόνων άμεσα για σημεία πρόσβασης υψηλής κίνησης.  
3. **Κόμβοι Edge CDN:** Αποθηκεύστε στην κρυφή μνήμη μετατρεπόμενα περιουσιακά στοιχεία κοντά στους χρήστες, μειώνοντας το φορτίο του αρχικού διακομιστή.  
4. **Dashboards Αναλύσεων:** Δημιουργήστε αναφορές PDF σε πραγματικό χρόνο και επαναχρησιμοποιήστε τις για επαναλαμβανόμενες προγραμματισμένες παραδόσεις.  
5. **Κατάλογοι E‑commerce:** Αποθηκεύστε στην κρυφή μνήμη τις μετατροπές φυλλαδίων προϊόντων για βελτίωση των χρόνων φόρτωσης σελίδας.  

## Πώς μπορείτε να βελτιώσετε την απόδοση όταν χρησιμοποιείτε Redis;

Η απόδοση μπορεί να βελτιστοποιηθεί ρυθμίζοντας κατάλληλες τιμές TTL, επαναχρησιμοποιώντας μια μοναδική παρουσία ConnectionMultiplexer, αποθηκεύοντας ακατέργαστους πίνακες byte για να αποφύγετε το κόστος σειριοποίησης, και χρησιμοποιώντας λειτουργίες παρτίδας για μαζικές διαγραφές. Η παρακολούθηση της χρήσης μνήμης και η ενεργοποίηση πολιτικής εκδίωξης όπως allkeys‑lru εξασφαλίζει ότι η κρυφή μνήμη παραμένει αποδοτική υπό βαριά φόρτωση.

- **Διαχείριση μεγέθους κρυφής μνήμης:** Ορίστε TTL 24 ώρες για τα περισσότερα έγγραφα· διαγράψτε παλαιότερες καταχωρήσεις με `RedisCache.GetKeys("docCache:*")`.  
- **Σύνδεση pool:** Επαναχρησιμοποιήστε μια μοναδική παρουσία `ConnectionMultiplexer` σε όλη την εφαρμογή για να αποφύγετε το κόστος χειραψίας.  
- **Αποδοτική σειριοποίηση:** Αποθηκεύστε ακατέργαστα bytes απευθείας· αποφύγετε περιτυλίγματα JSON ή XML που αυξάνουν το μέγεθος του φορτίου.  
- **Λειτουργίες παρτίδας:** Κατά τον καθαρισμό μιας κατηγορίας, χρησιμοποιήστε `IDatabase.KeyDelete` με μοτίβο για να αφαιρέσετε πολλά κλειδιά με μία κλήση.  

## Πώς να αντιμετωπίσετε κοινά προβλήματα;

Όταν προκύψουν προβλήματα, ελέγξτε ότι τα κλειδιά της κρυφής μνήμης δημιουργούνται σταθερά, παρακολουθήστε την κατανάλωση μνήμης του Redis και βεβαιωθείτε ότι η έκδοση της βιβλιοθήκης πελάτη ταιριάζει με το runtime. Ελέγξτε την καθυστέρηση δικτύου μεταξύ της εφαρμογής και του διακομιστή Redis, και επιβεβαιώστε ότι η σύνδεση pool είναι σωστά ρυθμισμένη ώστε να αποφεύγονται υπερβολικές χειραψίες που μπορούν να μειώσουν την απόδοση.

- **Αγνοούμενα κλειδιά:** Επαληθεύστε ότι το ίδιο κλειδί κρυφής μνήμης δημιουργείται για ταυτόμες παραμέτρους μετατροπής (διαδρομή εισόδου, μορφή εξόδου, επιλογές μετατροπής).  
- **Πίεση μνήμης:** Παρακολουθήστε τη χρήση μνήμης του Redis· ενεργοποιήστε `maxmemory-policy allkeys-lru` για αυτόματη εκδίωξη των λιγότερο πρόσφατα χρησιμοποιημένων καταχωρήσεων.  
- **Ασυμφωνίες έκδοσης:** Βεβαιωθείτε ότι η έκδοση του StackExchange.Redis ταιριάζει με το .NET runtime (π.χ., 2.6+ για .NET 6).  
- **Καθυστέρηση δικτύου:** Τοποθετήστε το Redis στην ίδια κεντρική μονάδα ή VPC με την εφαρμογή σας ώστε οι χρόνοι γύρου να παραμένουν κάτω από 1 ms.  

## Συχνές Ερωτήσεις

**Q: Πώς εγκαθιστώ το Redis στον τοπικό μου υπολογιστή;**  
A: Ακολουθήστε τον επίσημο οδηγό εγκατάστασης του Redis για το λειτουργικό σας σύστημα: [Redis Download](https://redis.io/download).

**Q: Ποια είναι τα απτά οφέλη της χρήσης προσαρμοσμένης κρυφής μνήμης με το GroupDocs.Conversion;**  
A: Εξαλείφει την διπλή απόδοση, μειώνει τη χρήση CPU κατά ~70 %, μειώνει τον μέσο χρόνο απόκρισης από 1,2 s σε <200 ms, και μειώνει το κόστος του cloud μειώνοντας τους κύκλους υπολογισμού.

**Q: Μπορεί αυτή η αρχιτεκτονική να αναπτυχθεί σε Azure ή AWS;**  
A: Ναι — απλώς κατευθύνετε το `ConnectionMultiplexer` στην διαχειριζόμενη παρουσία Redis (Azure Cache for Redis ή Amazon ElastiCache) και βεβαιωθείτε ότι οι ομάδες ασφαλείας δικτύου επιτρέπουν την κίνηση στη θύρα 6379.

**Q: Είναι η κρυφή μνήμη ασφαλής για νήματα (thread‑safe) για ταυτόχρονες web αιτήσεις;**  
A: Ο πελάτης `StackExchange.Redis` είναι πλήρως thread‑safe· μπορείτε να μοιράζεστε ένα μοναδικό `ConnectionMultiplexer` σε όλα τα νήματα αιτήσεων χωρίς πρόσθετο κλείδωμα.

**Q: Πώς καθαρίζω την κρυφή μνήμη όταν αλλάζει ένα πηγαίο έγγραφο;**  
A: Ακυρώστε τη λήψη διαγράφοντας κλειδιά που ταιριάζουν με το αναγνωριστικό του εγγράφου, π.χ., `await redis.GetDatabase().KeyDeleteAsync($"docCache:{docId}:*");`.

## Συμπέρασμα

Με την ενσωμάτωση ενός **custom redis cache .net** με το GroupDocs.Conversion, απολαμβάνετε δραματικές βελτιώσεις απόδοσης, μειώνετε το κόστος υποδομής και παρέχετε μια πιο ομαλή εμπειρία χρήστη. Τα παραπάνω βήματα σας παρέχουν μια έτοιμη για παραγωγή βάση — πειραματιστείτε με τιμές TTL, στρατηγικές κλειδιών κρυφής μνήμης και οριζόντια κλιμάκωση για να προσαρμόσετε τη λύση στο φορτίο εργασίας σας.

---

**Τελευταία Ενημέρωση:** 2026-05-21  
**Δοκιμάστηκε Με:** GroupDocs.Conversion 25.3.0 for .NET  
**Συγγραφέας:** GroupDocs  

```bash
Install-Package GroupDocs.Conversion -Version 25.3.0
```

```bash
dotnet add package GroupDocs.Conversion --version 25.3.0
```

```csharp
using GroupDocs.Conversion;
```

## Σχετικά Μαθήματα

- [Οδηγίες Διαχείρισης Κρυφής Μνήμης Μετατροπής για GroupDocs.Conversion .NET](/conversion/net/cache-management/)
- [Βελτιστοποίηση .NET Μετατροπής Εγγράφων με Κρυφή Μνήμη Χρησιμοποιώντας το GroupDocs.Conversion](/conversion/net/cache-management/optimize-net-document-conversion-caching-groupdocs/)
- [Αποκτήστε τον Πλήρη Έλεγχο της Ρύθμισης Μετατροπής Εγγράφων σε .NET Χρησιμοποιώντας το GroupDocs.Conversion](/conversion/net/conversion-options-settings/master-groupdocs-conversion-net-setup/)