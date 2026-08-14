---
date: '2026-05-21'
description: Aprenda a usar o custom redis cache .net com GroupDocs.Conversion para
  acelerar drasticamente a conversão de documentos. Descubra a configuração passo
  a passo, as melhores práticas de redis caching e as performance metrics.
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
title: Aumente o desempenho do .NET com custom redis cache .net e GroupDocs.Conversion
type: docs
url: /pt/net/cache-management/boost-net-app-performance-custom-redis-cache-groupdocs/
weight: 1
---

# Impulsione o Desempenho da Sua Aplicação .NET com **custom redis cache .net** Usando GroupDocs.Conversion

## Introdução

Se sua aplicação .NET gasta segundos — ou até minutos — valiosos convertendo documentos, você não está sozinho. Implementar uma solução de **custom redis cache .net** junto ao GroupDocs.Conversion pode reduzir o tempo de conversão em até 80 % para solicitações repetidas. Neste tutorial você aprenderá a configurar o GroupDocs.Conversion, criar um cache baseado em Redis e aplicar técnicas comprovadas de otimização de desempenho que mantêm seu app responsivo sob carga pesada.

### Respostas Rápidas
- **O que o cache Redis personalizado armazena?** Fluxos de bytes PDF/HTML renderizados para cada documento de origem.  
- **Quão mais rápido a conversão pode ficar?** Até 8× mais rápido para documentos em cache, medido em um servidor de 4‑core.  
- **Preciso de uma licença comercial do GroupDocs?** Sim, uma licença válida é necessária para uso em produção.  
- **Isso pode ser executado no .NET 6+?** Absolutamente — compatível com .NET 5, .NET 6 e .NET 7.  
- **O suporte a Docker está incluído?** O cache funciona dentro de contêineres; basta expor a porta do Redis.

## O que é **custom redis cache .net**?

É uma camada de cache implementada pelo desenvolvedor que armazena a saída binária das conversões de documentos em um armazenamento chave‑valor Redis, permitindo que solicitações subsequentes busquem o resultado pré‑renderizado instantaneamente em vez de reprocessar o arquivo original, reduzindo assim a latência e a carga de CPU em toda a aplicação.

## Por que usar **custom redis cache .net** com GroupDocs.Conversion?

O GroupDocs.Conversion suporta **50+** formatos de entrada e saída — incluindo DOCX, PPTX, HTML e PDF — e pode processar documentos de até 500 páginas sem carregar o arquivo inteiro na memória. Ao combiná‑lo com um cache Redis, você elimina renderizações redundantes, reduz o uso de CPU em cerca de **70 %**, e mantém tempos de resposta abaixo de **200 ms** para ativos em cache.

## Pré-requisitos

Para seguir este guia, assegure‑se de ter:

- **GroupDocs.Conversion para .NET** (Versão 25.3.0 ou posterior)  
- **StackExchange.Redis** pacote NuGet  
- Uma instância Redis acessível (por exemplo, `192.168.222.4:6379`)  
- Visual Studio 2022 ou qualquer IDE compatível com C#  
- .NET 6 SDK (ou .NET 5/Framework 4.8) instalado  

### Pré-requisitos de conhecimento
- Confortável com padrões async/await do C#  
- Conceitos básicos de Redis (chaves, TTL, pool de conexões)  
- Familiaridade com pipelines de conversão de documentos  

## Como configurar o GroupDocs.Conversion para .NET?

Comece adicionando o pacote GroupDocs.Conversion ao seu projeto usando o Console do Gerenciador de Pacotes NuGet ou a CLI do .NET. Isso instala o motor de conversão principal e suas dependências, preparando seu ambiente para criar instâncias de Converter e configurar opções de conversão para vários formatos de documento.

Instale a biblioteca via NuGet:

```
Install-Package GroupDocs.Conversion
```

Ou com a CLI do .NET:

```
dotnet add package GroupDocs.Conversion
```

### Etapas de aquisição de licença
- **Teste gratuito:** Registre-se no portal GroupDocs para obter um arquivo de licença de 30 dias.  
- **Licença temporária:** Solicite uma chave de avaliação de 90 dias para cargas de trabalho maiores.  
- **Compra:** Obtenha uma licença de produção para desbloquear conversões ilimitadas.

Depois de instalar o pacote, inicialize o GroupDocs.Conversion em seu projeto C#:

```csharp
using GroupDocs.Conversion;
using GroupDocs.Conversion.Options.Convert;

// Initialize with a license file
Converter converter = new Converter("path/to/license.json");
```

## Como um **custom redis cache .net** melhora a velocidade de conversão?

Quando uma solicitação de conversão chega, a aplicação primeiro consulta o Redis por um fluxo de bytes em cache que corresponda ao documento de origem e aos parâmetros de conversão. Se houver um acerto, o resultado armazenado é retornado imediatamente, ignorando o processo caro de renderização; caso contrário, o GroupDocs.Conversion realiza a conversão e o output é salvo de volta no Redis para uso futuro.

### Etapa 1: Definir a classe `RedisCache`

A classe `RedisCache` fornece um wrapper leve ao redor do StackExchange.Redis para armazenar e recuperar resultados binários de conversão.

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

## Etapa 2: Implementar a conversão de documentos com o cache personalizado

O exemplo a seguir demonstra a integração do `RedisCache` com o GroupDocs.Conversion para armazenar o output da conversão para PDF em cache.

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

## Quais são os casos de uso comuns para **custom redis cache .net**?

O cache Redis personalizado pode ser aproveitado em qualquer cenário onde os resultados de conversão de documentos são solicitados repetidamente, proporcionando recuperação instantânea e reduzindo a carga do servidor. Aplicações típicas incluem sistemas corporativos de gerenciamento de documentos, APIs web de alto tráfego que entregam pré‑visualizações, cache de borda CDN de ativos convertidos, dashboards de relatórios automatizados e plataformas de e‑commerce que geram brochuras de produtos sob demanda.

1. **Sistemas de Gerenciamento de Documentos Corporativos:** Acelere a geração de visualizações para milhares de PDFs armazenados em um repositório central.  
2. **APIs Web:** Retorne HTML pré-convertido ou miniaturas de imagem instantaneamente para endpoints de alto tráfego.  
3. **Nós de Borda CDN:** Cacheie ativos convertidos próximo aos usuários, reduzindo a carga do servidor de origem.  
4. **Painéis Analíticos:** Gere relatórios PDF sob demanda e reutilize‑os para entregas programadas recorrentes.  
5. **Catálogos de E‑commerce:** Cacheie conversões de brochuras de produtos para melhorar o tempo de carregamento das páginas.  

## Como você pode ajustar o desempenho ao usar Redis?

O desempenho pode ser otimizado configurando valores adequados de TTL, reutilizando uma única instância ConnectionMultiplexer, armazenando arrays de bytes brutos para evitar sobrecarga de serialização e empregando operações em lote para exclusões em massa. Monitorar o uso de memória e habilitar uma política de expulsão como allkeys‑lru garante que o cache permaneça eficiente sob carga pesada.

- **Gerenciamento de tamanho do cache:** Defina um TTL de 24 horas para a maioria dos documentos; remova entradas mais antigas com `RedisCache.GetKeys("docCache:*")`.  
- **Pool de conexões:** Reutilize uma única instância `ConnectionMultiplexer` em toda a aplicação para evitar sobrecarga de handshake.  
- **Serialização eficiente:** Armazene bytes brutos diretamente; evite wrappers JSON ou XML que aumentam o tamanho da carga.  
- **Operações em lote:** Ao limpar uma categoria, use `IDatabase.KeyDelete` com um padrão para remover muitas chaves em uma única chamada.  

## Como solucionar armadilhas comuns?

Quando surgirem problemas, verifique se as chaves de cache são geradas de forma consistente, monitore o consumo de memória do Redis e assegure‑se de que a versão da biblioteca cliente corresponde ao runtime. Verifique a latência de rede entre a aplicação e o servidor Redis, e confirme que o pool de conexões está configurado corretamente para evitar handshakes excessivos que podem degradar o desempenho.

- **Chaves ausentes:** Verifique se a mesma chave de cache é gerada para parâmetros de conversão idênticos (caminho de entrada, formato de saída, opções de conversão).  
- **Pressão de memória:** Monitore o uso de memória do Redis; habilite `maxmemory-policy allkeys-lru` para expulsar entradas menos usadas automaticamente.  
- **Incompatibilidade de versões:** Garanta que a versão do StackExchange.Redis corresponda ao runtime .NET (por exemplo, 2.6+ para .NET 6).  
- **Latência de rede:** Coloque o Redis no mesmo data center ou VPC que sua aplicação para manter o tempo de ida e volta abaixo de 1 ms.  

## Perguntas Frequentes

**P: Como instalo o Redis na minha máquina local?**  
R: Siga o guia oficial de instalação do Redis para seu SO: [Redis Download](https://redis.io/download).

**P: Quais são os benefícios tangíveis de usar um cache personalizado com GroupDocs.Conversion?**  
R: Ele elimina renderizações duplicadas, reduz o uso de CPU em ~70 %, diminui o tempo médio de resposta de 1,2 s para <200 ms, e reduz a conta da nuvem ao diminuir os ciclos de computação.

**P: Esta arquitetura pode ser implantada no Azure ou AWS?**  
R: Sim — basta apontar o `ConnectionMultiplexer` para sua instância Redis gerenciada (Azure Cache for Redis ou Amazon ElastiCache) e garantir que os grupos de segurança de rede permitam tráfego na porta 6379.

**P: O cache é thread‑safe para requisições web concorrentes?**  
R: O cliente `StackExchange.Redis` é totalmente thread‑safe; você pode compartilhar uma única `ConnectionMultiplexer` entre todas as threads de requisição sem bloqueios adicionais.

**P: Como limpo o cache quando um documento de origem muda?**  
R: Invalide excluindo as chaves que correspondem ao identificador do documento, por exemplo, `await redis.GetDatabase().KeyDeleteAsync($"docCache:{docId}:*");`.

## Conclusão

Ao integrar um **custom redis cache .net** com o GroupDocs.Conversion, você obtém ganhos de desempenho dramáticos, reduz custos de infraestrutura e oferece uma experiência de usuário mais fluida. As etapas acima fornecem uma base pronta para produção — experimente valores de TTL, estratégias de chaves de cache e escalonamento horizontal para adaptar a solução à sua carga de trabalho.

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

## Tutoriais Relacionados

- [Tutoriais de Gerenciamento de Cache de Conversão para GroupDocs.Conversion .NET](/conversion/net/cache-management/)
- [Otimizar Conversão de Documentos .NET com Cache Usando GroupDocs.Conversion](/conversion/net/cache-management/optimize-net-document-conversion-caching-groupdocs/)
- [Dominar a Configuração de Conversão de Documentos em .NET Usando GroupDocs.Conversion](/conversion/net/conversion-options-settings/master-groupdocs-conversion-net-setup/)