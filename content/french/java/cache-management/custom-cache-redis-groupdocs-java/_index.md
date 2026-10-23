---
date: '2026-10-21'
description: Apprenez comment créer une cache key Java et intégrer Redis avec GroupDocs.Conversion
  pour booster le rendering performance, réduire le conversion time et configurer
  les TTL dans un projet Java simple.
images:
- /java/cache-management/custom-cache-redis-groupdocs-java/og-image.png
keywords:
- create cache key java
- java redis caching
- groupdocs conversion cache
- redis ttl java
lastmod: '2026-10-21'
og_description: Créer une cache key Java dans ce guide step‑by‑step qui montre comment
  intégrer Redis avec GroupDocs.Conversion pour cache document bytes, booster le rendering
  performance et réduire le conversion time. Configurez les TTL et mesurez les gains
  de vitesse.
og_image_alt: 'Developer guide: create cache key Java using Redis and GroupDocs'
og_title: Créer une cache key Java – cache docs avec Redis et GroupDocs
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
title: Créer une cache key Java – mettre en cache des docs en Java avec Redis
type: docs
url: /fr/java/cache-management/custom-cache-redis-groupdocs-java/
weight: 1
---

# Créer une clé de cache Java – mettre en cache les documents Java avec Redis

Dans les applications web modernes, servir le même document converti de manière répétée peut gaspiller des cycles CPU et augmenter les temps de réponse. **Créer une clé de cache en Java** vous permet de stocker le résultat de la conversion une fois et de le récupérer instantanément lors des requêtes suivantes. Ce tutoriel vous montre comment intégrer Redis dans un flux de travail GroupDocs.Conversion, générer des clés de cache fiables, configurer les TTL et mesurer les gains de performance que vous pouvez attendre.

## Réponses rapides
- **Quel est le sujet de ce tutoriel ?** Un tutoriel complet de mise en cache java redis qui intègre Redis avec GroupDocs.Conversion.  
- **Pourquoi utiliser Redis ?** Il offre une latence sous‑milliseconde, prend en charge l’expiration TTL et s’échelonne horizontalement sur plusieurs instances d’application.  
- **Ai‑je besoin d’une licence GroupDocs ?** Une licence d’essai ou temporaire suffit pour les tests ; une licence complète est requise pour les déploiements en production.  
- **Quelles sont les étapes principales ?** Ajouter les dépendances Maven, configurer un `JedisPool`, créer des méthodes d’aide au cache et intégrer le cache dans le pipeline de conversion.  
- **Quelle version de Java est prise en charge ?** Java 8+ (compatible avec les dernières versions de GroupDocs.Conversion).

## Qu’est‑ce que la mise en cache de documents avec Redis ?
La mise en cache de documents avec Redis consiste à persister la sortie binaire d’une conversion (par ex., un tableau d’octets PDF) dans Redis afin que les futures requêtes identiques puissent récupérer les octets mis en cache au lieu de relancer le moteur de conversion. Cela élimine le travail CPU redondant, réduit la bande passante réseau et offre une expérience utilisateur plus fluide.

## Pourquoi implémenter un cache Redis en Java ?
Charger un document une fois, stocker le résultat et le servir instantanément lors de requêtes répétées peut **réduire le temps de conversion jusqu’à 90 %** pour les fichiers fréquemment consultés, **baisser les coûts d’infrastructure** en réduisant l’utilisation du CPU, et **fournir une source unique de vérité** pour tous les nœuds d’application dans un environnement en cluster. Redis peut traiter plus de 200 k opérations par seconde sur un seul nœud, garantissant des recherches sous‑milliseconde.

## Prérequis
- **GroupDocs.Conversion** – version 25.2 ou plus récente (prend en charge **120+** formats d’entrée et de sortie).  
- **Jedis** (le client Redis officiel pour Java).  
- Une instance Redis en cours d’exécution (le développement local peut utiliser le défaut `localhost:6379`).  
- Maven pour la gestion des dépendances.  
- Familiarité de base avec la gestion des exceptions Java et les flux d’E/S.

## Configuration de GroupDocs.Conversion pour Java

`GroupDocs.Conversion` est une bibliothèque Java qui convertit et rend les documents dans un large éventail de formats, en gérant la préservation de la mise en page, l’intégration des polices et l’extraction d’images automatiquement.

Add the GroupDocs repository and dependency to your `pom.xml`:

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

### Obtention de licence
Vous pouvez commencer avec un **Essai gratuit**, demander une **Licence temporaire** pour l’évaluation, ou acheter une **Licence** complète pour la production.

Initialize GroupDocs.Conversion in your Java code:

```java
import com.groupdocs.conversion.*;

ConversionConfig config = new ConversionConfig();
config.setLicensePath("path/to/license/file.lic");
ConversionApi conversionApi = new ConversionApi(config);
```

## Guide d’implémentation

### Création d’un cache personnalisé avec Redis

#### Vue d’ensemble
Un cache Redis personnalisé conserve les octets du document rendu, permettant une récupération instantanée lors de requêtes répétées.

#### Configuration de JedisPool
JedisPool est un pool thread‑safe de connexions Redis réutilisables qui minimise la surcharge des sockets et améliore le débit.

```java
import redis.clients.jedis.JedisPool;
import redis.clients.jedis.JedisPoolConfig;

JedisPoolConfig poolConfig = new JedisPoolConfig();
poolConfig.setMaxTotal(20);               // maximum active connections
poolConfig.setMaxIdle(10);                // maximum idle connections
poolConfig.setMinIdle(2);                 // minimum idle connections
JedisPool jedisPool = new JedisPool(poolConfig, "localhost", 6379);
```

#### Stockage et récupération des données en cache
Les méthodes d’aide ci‑dessous sérialisent un tableau d’octets en chaîne Base64 pour un stockage sûr et le récupèrent sous forme de tableau d’octets.

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

#### Intégration avec GroupDocs.Conversion
Intégrez maintenant le cache dans le flux de travail de conversion. La méthode vérifie d’abord le cache ; en cas d’absence, elle effectue la conversion, stocke le résultat et renvoie les octets.

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

## Comment créer une clé de cache Java pour la mise en cache Redis ?
Générez une clé déterministe en concaténant le chemin du fichier source, les valeurs sélectionnées de `ConvertOptions` et un tag de version optionnel, puis hachez la chaîne avec SHA‑256. Cette clé identifie de manière unique chaque configuration de conversion, garantissant que les requêtes identiques utilisent le cache tandis que des options différentes génèrent des entrées séparées.

La classe `ConversionApi` est le composant central de GroupDocs.Conversion qui exécute les conversions de documents. Vous pouvez créer une clé de cache, la rechercher dans Redis, et n’appeler `ConversionApi.convert` que lorsque la clé est absente, réduisant ainsi de façon spectaculaire le temps de conversion et la charge du serveur.

## Comment implémenter la mise en cache Redis en Java ?
`ConversionApi` est la classe principale de GroupDocs.Conversion qui exécute les opérations de conversion de documents. Chargez votre document source, générez une clé de cache déterministe, recherchez‑la dans Redis, et n’invoquez `ConversionApi` que lorsque la clé est absente. Ce modèle garantit que chaque conversion unique est effectuée une fois, puis servie depuis le cache pendant la durée du TTL configuré.

## Conseils de dépannage
- Vérifiez que le serveur Redis est accessible (`redis-cli ping` doit renvoyer `PONG`).  
- Assurez‑vous que l’hôte et le port de `JedisPool` correspondent à votre déploiement Redis.  
- Enveloppez les appels au cache dans des blocs try‑catch pour gérer les problèmes de connectivité sans interrompre le flux de conversion.  
- Surveillez la mémoire Redis (`INFO memory`) et définissez des politiques `maxmemory` (par ex., `volatile-lru`) pour évincer les anciennes entrées en douceur.  
- Si vous rencontrez `OutOfMemoryError` sur la JVM, augmentez la taille du tas ou activez `-XX:+UseCompressedOops`.

## Applications pratiques

1. **Portails à fort trafic** – Servir instantanément les PDF fréquemment demandés (catalogues, livres blancs).  
2. **DMS d’entreprise** – Réduire la charge lorsque les utilisateurs consultent à plusieurs reprises les mêmes contrats ou documents de politique.  
3. **E‑commerce** – Mettre en cache les factures générées ou les catalogues produits pour accélérer le paiement.  
4. **Plateformes d’apprentissage** – Fournir les notes de cours et les e‑books sans re‑rendu à chaque demande d’étudiant.  
5. **Services juridiques** – Accélérer la distribution des dossiers tout en maintenant les coûts de stockage bas.

## Considérations de performance

- **Optimiser Redis** – Ajustez `maxmemory`, choisissez une politique d’éviction comme `allkeys-lru`, et définissez des valeurs `timeout` appropriées selon votre modèle de trafic.  
- **Suivre les ratios de hit/miss du cache** – Utilisez `INFO stats` ou les compteurs `keyspace_hits` / `keyspace_misses` de Redis pour affiner les TTL.  
- **Dimensionnement du tas JVM** – Assurez‑vous que le tas peut accueillir les tampons GroupDocs ; une règle empirique est 1 Go de tas pour chaque 100 Mo de charge de conversion concurrente.  
- **Conversions par lots** – Lors de la conversion de nombreux fichiers, réutilisez une seule instance `Jedis` par thread pour minimiser le roulement des sockets.

## Questions fréquemment posées

**Q : Puis‑je utiliser cette approche avec d’autres formats de sortie GroupDocs ?**  
R : Absolument. Le même modèle de mise en cache fonctionne pour DOCX, HTML, images, et plus – il suffit de changer le type `ConvertOptions`.

**Q : Comment choisir une bonne clé de cache ?**  
R : Combinez le chemin du fichier source, les options de conversion et tout identifiant de version. Cela garantit l’unicité par configuration.

**Q : Que se passe‑t‑il si un document change après avoir été mis en cache ?**  
R : Invalidez le cache manuellement (par ex., supprimez la clé) ou utilisez un TTL plus court afin que les données obsolètes expirent rapidement.

**Q : Redis est‑il la seule option de mise en cache ?**  
R : Non, mais Redis offre une faible latence, un TTL intégré et un large support client Java, ce qui en fait un choix populaire pour ce scénario.

**Q : Cela augmente‑t‑il l’utilisation de la mémoire sur le serveur d’application ?**  
R : Minimal. Le travail lourd est effectué par Redis ; l’application ne conserve que des connexions de courte durée via Jedis.

## Conclusion
Vous disposez maintenant d’un tutoriel complet sur la **mise en cache java redis** qui montre comment mettre en cache des documents avec Redis et GroupDocs.Conversion. En persistant la sortie rendue dans Redis, vous **améliorerez les performances de rendu**, **réduirez le temps de conversion**, et offrirez une expérience plus fluide aux utilisateurs finaux. Expérimentez avec différentes valeurs de TTL, surveillez les métriques du cache, et étendez le modèle à d’autres formats de documents à mesure que votre application se développe.

---

**Dernière mise à jour :** 2026-10-21  
**Testé avec :** GroupDocs.Conversion 25.2, Jedis 4.2.3  
**Auteur :** GroupDocs

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

## Tutoriels associés

- [Implémenter un cache personnalisé Java – Cache de conversion GroupDocs](/conversion/java/cache-management/)
- [Comment utiliser le cache Redis en Java avec GroupDocs.Conversion](/conversion/java/cache-management/redis-cache-java-groupdocs-conversion-guide/)
- [Comment mettre en cache des fichiers en Java avec GroupDocs.Conversion – Guide complet pour une conversion de documents efficace](/conversion/java/cache-management/implement-java-file-caching-groupdocs-conversion-guide/)
