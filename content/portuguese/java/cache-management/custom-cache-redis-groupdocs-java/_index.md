---
date: '2026-10-21'
description: Aprenda como criar cache key Java e integrar Redis com GroupDocs.Conversion
  para melhorar o rendering performance, reduzir o conversion time e configurar TTLs
  em um projeto Java simples.
images:
- /java/cache-management/custom-cache-redis-groupdocs-java/og-image.png
keywords:
- create cache key java
- java redis caching
- groupdocs conversion cache
- redis ttl java
lastmod: '2026-10-21'
og_description: Criar cache key Java neste guia passo a passo que mostra como integrar
  Redis com GroupDocs.Conversion para cache document bytes, boost rendering performance
  e reduzir conversion time. Configure TTLs e meça os ganhos de velocidade.
og_image_alt: 'Developer guide: create cache key Java using Redis and GroupDocs'
og_title: Criar cache key Java – cache de documentos com Redis e GroupDocs
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
title: Criar cache key Java – cache de documentos em Java com Redis
type: docs
url: /pt/java/cache-management/custom-cache-redis-groupdocs-java/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar chave de cache Java – armazenar documentos em cache em Java com Redis

Em aplicações web modernas, servir o mesmo documento convertido repetidamente pode desperdiçar ciclos de CPU e inflar os tempos de resposta. **Criar uma chave de cache em Java** permite armazenar a saída da conversão uma vez e recuperá‑la instantaneamente em solicitações subsequentes. Este tutorial mostra como integrar o Redis em um fluxo de trabalho do GroupDocs.Conversion, gerar chaves de cache confiáveis, configurar TTLs e medir os ganhos de desempenho que você pode esperar.

## Respostas rápidas
- **O que este tutorial cobre?** Um tutorial completo de cache java redis que integra o Redis com o GroupDocs.Conversion.  
- **Por que usar o Redis?** Ele oferece latência sub‑milissegundo, suporta expiração TTL e escala horizontalmente em múltiplas instâncias da aplicação.  
- **Preciso de uma licença do GroupDocs?** Uma licença de avaliação ou temporária serve para testes; uma licença completa é necessária para implantações em produção.  
- **Quais são os passos principais?** Adicionar dependências Maven, configurar um `JedisPool`, criar métodos auxiliares de cache e conectar o cache ao pipeline de conversão.  
- **Qual versão do Java é suportada?** Java 8+ (compatível com as versões mais recentes do GroupDocs.Conversion).

## O que é cache de documentos com Redis?
Cachear documentos com Redis significa persistir a saída binária de uma conversão (por exemplo, um array de bytes PDF) no Redis para que solicitações futuras idênticas possam recuperar os bytes em cache em vez de reexecutar o motor de conversão. Isso elimina trabalho redundante de CPU, reduz a largura de banda da rede e oferece uma experiência de usuário final mais fluida.

## Por que implementar cache Redis em Java?
Carregar um documento uma vez, armazenar o resultado e servi‑lo instantaneamente em acessos repetidos pode **reduzir o tempo de conversão em até 90 %** para arquivos frequentemente acessados, **diminuir os custos de infraestrutura** ao reduzir o uso de CPU e **fornecer uma única fonte de verdade** para todos os nós da aplicação em um ambiente em cluster. O Redis pode processar mais de 200 k operações por segundo em um único nó, garantindo buscas sub‑milissegundo.

## Pré‑requisitos
- **GroupDocs.Conversion** – versão 25.2 ou mais recente (suporta **120+** formatos de entrada e saída).  
- **Jedis** (o cliente oficial Redis para Java).  
- Uma instância Redis em execução (o desenvolvimento local pode usar o padrão `localhost:6379`).  
- Maven para gerenciamento de dependências.  
- Familiaridade básica com tratamento de exceções Java e fluxos de I/O.

## Configurando o GroupDocs.Conversion para Java

`GroupDocs.Conversion` é uma biblioteca Java que converte e renderiza documentos para uma ampla variedade de formatos, lidando automaticamente com preservação de layout, incorporação de fontes e extração de imagens.

Adicione o repositório GroupDocs e a dependência ao seu `pom.xml`:

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

### Aquisição de licença
Você pode começar com um **Teste Gratuito**, solicitar uma **Licença Temporária** para avaliação ou adquirir uma **Licença** completa para uso em produção.

Inicialize o GroupDocs.Conversion no seu código Java:

```java
import com.groupdocs.conversion.*;

ConversionConfig config = new ConversionConfig();
config.setLicensePath("path/to/license/file.lic");
ConversionApi conversionApi = new ConversionApi(config);
```

## Guia de implementação

### Criando um cache personalizado usando Redis

#### Visão geral
Um cache Redis personalizado armazena os bytes do documento renderizado, permitindo recuperação instantânea em solicitações repetidas.

#### Configurando JedisPool
JedisPool é um pool thread‑safe de conexões Redis reutilizáveis que minimiza a sobrecarga de sockets e melhora a taxa de transferência.

```java
import redis.clients.jedis.JedisPool;
import redis.clients.jedis.JedisPoolConfig;

JedisPoolConfig poolConfig = new JedisPoolConfig();
poolConfig.setMaxTotal(20);               // maximum active connections
poolConfig.setMaxIdle(10);                // maximum idle connections
poolConfig.setMinIdle(2);                 // minimum idle connections
JedisPool jedisPool = new JedisPool(poolConfig, "localhost", 6379);
```

#### Armazenando e recuperando dados em cache
Os métodos auxiliares abaixo serializam um array de bytes para uma string Base64 para armazenamento seguro e o recuperam de volta para um array de bytes.

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

#### Integração com GroupDocs.Conversion
Agora conecte o cache ao fluxo de trabalho de conversão. O método verifica o cache primeiro; se houver uma falha, ele realiza a conversão, armazena o resultado e retorna os bytes.

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

## Como criar chave de cache Java para cache Redis?
Gere uma chave determinística concatenando o caminho do arquivo fonte, os valores selecionados de `ConvertOptions` e uma tag de versão opcional, então hash a string com SHA‑256. Essa chave identifica exclusivamente cada configuração de conversão, garantindo que solicitações idênticas acessem o cache enquanto opções diferentes gerem entradas separadas.

A classe `ConversionApi` é o componente central no GroupDocs.Conversion que executa conversões de documentos. Você pode criar uma chave de cache, consultá‑la no Redis e invocar `ConversionApi.convert` somente quando a chave estiver ausente, reduzindo drasticamente o tempo de conversão e a carga do servidor.

## Como implementar cache Redis em Java?
`ConversionApi` é a classe principal no GroupDocs.Conversion que executa operações de conversão de documentos. Carregue seu documento fonte, gere uma chave de cache determinística, consulte-a no Redis e invoque `ConversionApi` somente quando a chave estiver ausente. Esse padrão garante que cada conversão única seja realizada uma vez, e então servida a partir do cache durante a duração do TTL configurado.

## Dicas de solução de problemas
- Verifique se o servidor Redis está acessível (`redis-cli ping` deve retornar `PONG`).  
- Certifique‑se de que o host e a porta do `JedisPool` correspondam à sua implantação Redis.  
- Envolva as chamadas de cache em blocos try‑catch para lidar com interrupções de conectividade sem interromper o fluxo de conversão.  
- Monitore a memória do Redis (`INFO memory`) e configure políticas `maxmemory` (por exemplo, `volatile‑lru`) para remover entradas antigas de forma graciosa.  
- Se encontrar `OutOfMemoryError` na JVM, aumente o tamanho do heap ou habilite `-XX:+UseCompressedOops`.

## Aplicações práticas

1. **Portais de alto tráfego** – Servir PDFs solicitados com frequência (catálogos, whitepapers) instantaneamente.  
2. **DMS corporativo** – Reduzir a carga quando usuários visualizam repetidamente os mesmos contratos ou documentos de políticas.  
3. **E‑commerce** – Cachear faturas geradas ou catálogos de produtos para acelerar o checkout.  
4. **Plataformas de aprendizado** – Entregar notas de aula e e‑books sem re‑renderizar a cada solicitação de estudante.  
5. **Serviços jurídicos** – Acelerar a distribuição de arquivos de casos mantendo baixos custos de armazenamento.

## Considerações de desempenho

- **Ajustar Redis** – Modifique `maxmemory`, escolha uma política de expulsão como `allkeys‑lru` e defina valores de `timeout` adequados ao seu padrão de tráfego.  
- **Acompanhar razões de acerto/erro de cache** – Use `INFO stats` ou os contadores `keyspace_hits` / `keyspace_misses` do Redis para afinar os TTLs.  
- **Dimensionamento do heap da JVM** – Garanta que o heap possa acomodar os buffers do GroupDocs; uma regra prática é 1 GB de heap para cada 100 MB de carga de conversão simultânea.  
- **Conversões em lote** – Ao converter muitos arquivos, reutilize uma única instância `Jedis` por thread para minimizar a rotatividade de sockets.

## Perguntas frequentes

**Q: Posso usar esta abordagem com outros formatos de saída do GroupDocs?**  
A: Absolutamente. O mesmo padrão de cache funciona para DOCX, HTML, imagens e mais – basta mudar o tipo `ConvertOptions`.

**Q: Como escolher uma boa chave de cache?**  
A: Combine o caminho do arquivo fonte, as opções de conversão e quaisquer identificadores de versão. Isso garante unicidade por configuração.

**Q: E se um documento mudar após ser armazenado em cache?**  
A: Invalide o cache manualmente (por exemplo, exclua a chave) ou use um TTL mais curto para que dados obsoletos expirem rapidamente.

**Q: O Redis é a única opção para cache?**  
A: Não, mas o Redis oferece baixa latência, TTL incorporado e amplo suporte a clientes Java, tornando‑o uma escolha popular para este cenário.

**Q: Isso aumenta o uso de memória no servidor da aplicação?**  
A: Mínimo. O trabalho pesado é feito pelo Redis; a aplicação mantém apenas conexões de curta duração via Jedis.

## Conclusão
Agora você tem um tutorial completo de **cache java redis** que mostra como armazenar documentos em cache usando Redis e GroupDocs.Conversion. Ao persistir a saída renderizada no Redis, você **aumentará o desempenho de renderização**, **reduzirá o tempo de conversão** e proporcionará uma experiência mais fluida aos usuários finais. Experimente diferentes valores de TTL, monitore as métricas de cache e amplie o padrão para outros formatos de documento à medida que sua aplicação cresce.

---

**Última atualização:** 2026-10-21  
**Testado com:** GroupDocs.Conversion 25.2, Jedis 4.2.3  
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

## Tutoriais relacionados

- [Implementar Cache Personalizado Java – Cache de Conversão GroupDocs](/conversion/java/cache-management/)
- [Como Usar Cache Redis em Java com GroupDocs.Conversion](/conversion/java/cache-management/redis-cache-java-groupdocs-conversion-guide/)
- [Como Cachear Arquivos em Java com GroupDocs.Conversion – Um Guia Abrangente para Conversão Eficiente de Documentos](/conversion/java/cache-management/implement-java-file-caching-groupdocs-conversion-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}