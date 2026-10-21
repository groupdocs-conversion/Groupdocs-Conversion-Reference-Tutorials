---
date: '2026-10-21'
description: Aprenda cómo crear cache key Java e integrar Redis con GroupDocs.Conversion
  para mejorar el rendimiento de renderizado, reducir el tiempo de conversión y configurar
  TTLs en un proyecto Java sencillo.
images:
- /java/cache-management/custom-cache-redis-groupdocs-java/og-image.png
keywords:
- create cache key java
- java redis caching
- groupdocs conversion cache
- redis ttl java
lastmod: '2026-10-21'
og_description: Cree cache key Java con esta guía paso a paso que muestra cómo integrar
  Redis con GroupDocs.Conversion para almacenar en caché los bytes del documento,
  mejorar el rendimiento de renderizado y reducir el tiempo de conversión. Configure
  TTLs y mida las ganancias de velocidad.
og_image_alt: 'Developer guide: create cache key Java using Redis and GroupDocs'
og_title: Crear cache key Java – cachear documentos con Redis y GroupDocs
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
title: Crear cache key Java – cachear documentos en Java con Redis
type: docs
url: /es/java/cache-management/custom-cache-redis-groupdocs-java/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear clave de caché Java – almacenar documentos en caché en Java con Redis

En las aplicaciones web modernas, servir el mismo documento convertido repetidamente puede desperdiciar ciclos de CPU e inflar los tiempos de respuesta. **Crear una clave de caché en Java** le permite almacenar la salida de la conversión una vez y recuperarla instantáneamente en solicitudes posteriores. Este tutorial le muestra cómo integrar Redis en un flujo de trabajo de GroupDocs.Conversion, generar claves de caché confiables, configurar TTLs y medir las mejoras de rendimiento que puede esperar.

## Respuestas rápidas
- **¿Qué cubre este tutorial?** Un tutorial completo de caché java redis que integra Redis con GroupDocs.Conversion.  
- **¿Por qué usar Redis?** Proporciona latencia submilisegundo, admite expiración TTL y escala horizontalmente a través de múltiples instancias de la aplicación.  
- **¿Necesito una licencia de GroupDocs?** Una licencia de prueba o temporal está bien para pruebas; se requiere una licencia completa para implementaciones en producción.  
- **¿Cuáles son los pasos principales?** Añadir dependencias Maven, configurar un `JedisPool`, crear métodos auxiliares de caché e integrar la caché en el pipeline de conversión.  
- **¿Qué versión de Java es compatible?** Java 8+ (compatible con las últimas versiones de GroupDocs.Conversion).

## ¿Qué es el almacenamiento en caché de documentos con Redis?
Almacenar documentos en caché con Redis significa persistir la salida binaria de una conversión (p. ej., un arreglo de bytes PDF) en Redis para que solicitudes futuras idénticas puedan recuperar los bytes en caché en lugar de volver a ejecutar el motor de conversión. Esto elimina trabajo redundante de CPU, reduce el ancho de banda de la red y ofrece una experiencia de usuario final más fluida.

## ¿Por qué implementar caché Redis en Java?
Cargar un documento una vez, almacenar el resultado y servirlo instantáneamente en accesos repetidos puede **reducir el tiempo de conversión hasta en un 90 %** para archivos de acceso frecuente, **bajar los costos de infraestructura** al reducir el uso de CPU y **proporcionar una única fuente de verdad** para todos los nodos de la aplicación en un entorno agrupado. Redis puede procesar más de 200 k operaciones por segundo en un solo nodo, garantizando búsquedas submilisegundo.

## Requisitos previos
- **GroupDocs.Conversion** – versión 25.2 o posterior (soporta **120+** formatos de entrada y salida).  
- **Jedis** (el cliente oficial de Redis para Java).  
- Una instancia de Redis en ejecución (el desarrollo local puede usar el valor predeterminado `localhost:6379`).  
- Maven para la gestión de dependencias.  
- Familiaridad básica con el manejo de excepciones en Java y flujos de E/S.

## Configuración de GroupDocs.Conversion para Java

`GroupDocs.Conversion` es una biblioteca Java que convierte y renderiza documentos a una amplia gama de formatos, manejando la preservación del diseño, la incrustación de fuentes y la extracción de imágenes automáticamente.

Añada el repositorio de GroupDocs y la dependencia a su `pom.xml`:

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

### Obtención de licencia
Puede comenzar con una **Prueba gratuita**, solicitar una **Licencia temporal** para evaluación, o comprar una **Licencia** completa para uso en producción.

Inicialice GroupDocs.Conversion en su código Java:

```java
import com.groupdocs.conversion.*;

ConversionConfig config = new ConversionConfig();
config.setLicensePath("path/to/license/file.lic");
ConversionApi conversionApi = new ConversionApi(config);
```

## Guía de implementación

### Creación de una caché personalizada usando Redis

#### Visión general
Una caché Redis personalizada almacena los bytes del documento renderizado, permitiendo una recuperación instantánea en solicitudes repetidas.

#### Configuración de JedisPool
JedisPool es un pool de conexiones Redis reutilizables y seguro para subprocesos que minimiza la sobrecarga de sockets y mejora el rendimiento.

```java
import redis.clients.jedis.JedisPool;
import redis.clients.jedis.JedisPoolConfig;

JedisPoolConfig poolConfig = new JedisPoolConfig();
poolConfig.setMaxTotal(20);               // maximum active connections
poolConfig.setMaxIdle(10);                // maximum idle connections
poolConfig.setMinIdle(2);                 // minimum idle connections
JedisPool jedisPool = new JedisPool(poolConfig, "localhost", 6379);
```

#### Almacenamiento y recuperación de datos en caché
Los métodos auxiliares a continuación serializan un arreglo de bytes a una cadena Base64 para un almacenamiento seguro y lo recuperan de nuevo en un arreglo de bytes.

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

#### Integración con GroupDocs.Conversion
Ahora vincule la caché al flujo de trabajo de conversión. El método verifica la caché primero; si ocurre un fallo, realiza la conversión, almacena el resultado y devuelve los bytes.

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

## ¿Cómo crear una clave de caché Java para el almacenamiento en caché con Redis?
Genere una clave determinista concatenando la ruta del archivo fuente, los valores seleccionados de `ConvertOptions` y una etiqueta de versión opcional, luego aplique hash SHA‑256 a la cadena. Esta clave identifica de forma única cada configuración de conversión, asegurando que las solicitudes idénticas accedan a la caché mientras que diferentes opciones generen entradas separadas.

La clase `ConversionApi` es el componente central en GroupDocs.Conversion que ejecuta conversiones de documentos. Puede crear una clave de caché, buscarla en Redis y solo invocar `ConversionApi.convert` cuando la clave no exista, reduciendo drásticamente el tiempo de conversión y la carga del servidor.

## ¿Cómo implementar el almacenamiento en caché Java con Redis?
`ConversionApi` es la clase principal en GroupDocs.Conversion que ejecuta operaciones de conversión de documentos. Cargue su documento fuente, genere una clave de caché determinista, búsquela en Redis y solo invoque `ConversionApi` cuando la clave esté ausente. Este patrón garantiza que cada conversión única se realice una sola vez, y luego se sirva desde la caché durante la duración del TTL configurado.

## Consejos de solución de problemas
- Verifique que el servidor Redis sea accesible (`redis-cli ping` debería devolver `PONG`).  
- Asegúrese de que el host y puerto de `JedisPool` coincidan con su despliegue de Redis.  
- Envuelva las llamadas a la caché en bloques try‑catch para manejar interrupciones de conectividad sin romper el flujo de conversión.  
- Monitoree la memoria de Redis (`INFO memory`) y configure políticas `maxmemory` (p. ej., `volatile-lru`) para eliminar entradas antiguas de forma ordenada.  
- Si encuentra `OutOfMemoryError` en la JVM, aumente el tamaño del heap o habilite `-XX:+UseCompressedOops`.

## Aplicaciones prácticas

1. **Portales de alto tráfico** – Sirva PDFs solicitados con frecuencia (catálogos, libros blancos) instantáneamente.  
2. **DMS empresarial** – Reduzca la carga cuando los usuarios visualizan repetidamente los mismos contratos o documentos de políticas.  
3. **E‑commerce** – Cache facturas generadas o catálogos de productos para acelerar el proceso de compra.  
4. **Plataformas de aprendizaje** – Entregue notas de clase y libros electrónicos sin volver a renderizar en cada solicitud de estudiante.  
5. **Servicios legales** – Acelere la distribución de expedientes de casos mientras mantiene bajos los costos de almacenamiento.

## Consideraciones de rendimiento

- **Ajustar Redis** – Modifique `maxmemory`, elija una política de expulsión como `allkeys-lru` y establezca valores de `timeout` apropiados según su patrón de tráfico.  
- **Rastrear ratios de aciertos/fallos de caché** – Use `INFO stats` o los contadores `keyspace_hits` / `keyspace_misses` de Redis para afinar los TTL.  
- **Dimensionamiento del heap JVM** – Asegúrese de que el heap pueda acomodar los buffers de GroupDocs; una regla práctica es 1 GB de heap por cada 100 MB de carga de conversión concurrente.  
- **Conversiones por lotes** – Al convertir muchos archivos, reutilice una única instancia `Jedis` por hilo para minimizar el consumo de sockets.

## Preguntas frecuentes

**Q: ¿Puedo usar este enfoque con otros formatos de salida de GroupDocs?**  
A: Por supuesto. El mismo patrón de caché funciona para DOCX, HTML, imágenes y más – simplemente cambie el tipo `ConvertOptions`.

**Q: ¿Cómo elijo una buena clave de caché?**  
A: Combine la ruta del archivo fuente, las opciones de conversión y cualquier identificador de versión. Esto garantiza la unicidad por configuración.

**Q: ¿Qué pasa si un documento cambia después de haber sido almacenado en caché?**  
A: Invalide la caché manualmente (p. ej., elimine la clave) o use un TTL más corto para que los datos obsoletos expiren rápidamente.

**Q: ¿Es Redis la única opción para caché?**  
A: No, pero Redis ofrece baja latencia, TTL incorporado y amplio soporte de clientes Java, lo que lo convierte en una opción popular para este escenario.

**Q: ¿Esto aumenta el uso de memoria en el servidor de la aplicación?**  
A: Mínimo. El trabajo pesado lo realiza Redis; la aplicación solo mantiene conexiones de corta duración a través de Jedis.

## Conclusión
Ahora tiene un tutorial completo de **caché java redis** que muestra cómo almacenar documentos en caché usando Redis y GroupDocs.Conversion. Al persistir la salida renderizada en Redis, **mejorará el rendimiento de renderizado**, **reducirá el tiempo de conversión** y proporcionará una experiencia más fluida a los usuarios finales. Experimente con diferentes valores de TTL, monitoree las métricas de caché y extienda el patrón a otros formatos de documento a medida que su aplicación crezca.

---

**Última actualización:** 2026-10-21  
**Probado con:** GroupDocs.Conversion 25.2, Jedis 4.2.3  
**Autor:** GroupDocs

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

## Tutoriales relacionados

- [Implementar caché personalizada Java – Caché de GroupDocs Conversion](/conversion/java/cache-management/)
- [Cómo usar caché Redis en Java con GroupDocs.Conversion](/conversion/java/cache-management/redis-cache-java-groupdocs-conversion-guide/)
- [Cómo almacenar archivos en caché en Java con GroupDocs.Conversion – Guía completa para una conversión de documentos eficiente](/conversion/java/cache-management/implement-java-file-caching-groupdocs-conversion-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}