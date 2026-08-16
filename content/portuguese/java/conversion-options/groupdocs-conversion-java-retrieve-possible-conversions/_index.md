---
date: '2026-07-29'
description: Descubra como listar formatos e recuperar todas as conversões possíveis
  usando GroupDocs.Conversion for Java, ideal para fluxos de trabalho de conversão
  de arquivos em armazenamento em nuvem.
keywords:
- how to list formats
- cloud storage file conversion
- GroupDocs.Conversion Java
lastmod: '2026-07-29'
og_description: Aprenda como listar formatos e recuperar todas as conversões possíveis
  usando GroupDocs.Conversion for Java. Ideal para pipelines de conversão de arquivos
  em armazenamento em nuvem.
og_image_alt: 'Guide: List formats and get conversion matrix with GroupDocs.Conversion
  Java'
og_title: Como listar formatos com GroupDocs.Conversion for Java
schemas:
- author: GroupDocs
  dateModified: '2026-07-29'
  description: Discover how to list formats and retrieve all possible conversions
    using GroupDocs.Conversion for Java, ideal for cloud storage file conversion workflows.
  headline: How to List Formats with GroupDocs.Conversion for Java
  type: TechArticle
- description: Discover how to list formats and retrieve all possible conversions
    using GroupDocs.Conversion for Java, ideal for cloud storage file conversion workflows.
  name: How to List Formats with GroupDocs.Conversion for Java
  steps:
  - name: '**Dynamic Format Detection:** When a file lands in cloud storage, you can
      instantly query whether the desired target format is supported.'
    text: '**Dynamic Format Detection:** When a file lands in cloud storage, you can
      instantly query whether the desired target format is supported.'
  - name: '**Batch Migration:** Move large document libraries to a unified format
      (e.g., PDF/A) by iterating over supported source types.'
    text: '**Batch Migration:** Move large document libraries to a unified format
      (e.g., PDF/A) by iterating over supported source types.'
  - name: '**User‑Driven Export:** Offer end‑users a dropdown of only the formats
      their current document can be exported to, reducing errors and improving UX.'
    text: '**User‑Driven Export:** Offer end‑users a dropdown of only the formats
      their current document can be exported to, reducing errors and improving UX.'
  type: HowTo
- questions:
  - answer: It is a server‑side library that supports 200+ input and 200+ output formats,
      enabling fast, license‑free document conversion without external software.
    question: What is GroupDocs.Conversion for Java?
  - answer: Set up your Maven project, add the dependency shown earlier, load a license
      file, and instantiate the `Converter` class as demonstrated in the initialization
      section.
    question: How do I start with GroupDocs.Conversion?
  - answer: Yes—through the API’s extensibility points you can register custom converters
      or plug‑in third‑party handlers for proprietary formats.
    question: Can I convert custom file types using GroupDocs.Conversion?
  - answer: Forgetting to close the `Converter`, using an old JAR version, or overlooking
      memory usage for very large PDFs. Follow the resource‑management tips above.
    question: What are common pitfalls when implementing conversions?
  - answer: Visit the official [documentation](https://docs.groupdocs.com/conversion/java/)
      or ask questions in the GroupDocs community forum.
    question: Where can I get more help?
  type: FAQPage
tags:
- convert formats
- GroupDocs.Conversion
- Java document conversion
- cloud storage conversion
title: Como listar formatos com GroupDocs.Conversion for Java
type: docs
url: /pt/java/conversion-options/groupdocs-conversion-java-retrieve-possible-conversions/
weight: 1
---

# Como listar formatos e recuperar todas as conversões possíveis com GroupDocs.Conversion para Java

Em muitos projetos de processamento de documentos, o primeiro passo é saber **como listar formatos** que o mecanismo de conversão suporta. Este tutorial mostra, passo a passo, como consultar o GroupDocs.Conversion para Java, recuperar cada par origem‑destino e aplicar esse conhecimento em pipelines de conversão de arquivos em armazenamento em nuvem. Ao final, você terá um método reutilizável que retorna a matriz completa de conversões, além de dicas práticas para desempenho e tratamento de erros.

## Respostas Rápidas
- **O que significa “list formats”?** Ele retorna cada par de conversão origem‑destino que a biblioteca pode manipular.  
- **Preciso de uma licença?** Um teste gratuito funciona para testes; uma licença paga é necessária para produção.  
- **Isso pode ajudar na conversão de arquivos em armazenamento em nuvem?** Sim—conhecer os formatos suportados permite automatizar conversões em pipelines de armazenamento em nuvem.  
- **Qual versão do Java é necessária?** JDK 8 ou superior.  
- **A funcionalidade é thread‑safe?** A instância `Converter` pode ser reutilizada em várias threads, mas libere os recursos após o uso.

## O que é “how to list formats” no GroupDocs.Conversion?
A operação **list formats** retorna uma coleção que descreve cada formato de origem junto com os formatos de destino nos quais ele pode ser transformado. Essa matriz é gerada a partir das regras internas de conversão da biblioteca e é essencial para construir fluxos de trabalho dinâmicos que se adaptam às capacidades reais do GroupDocs.Conversion em tempo de execução.

## Por que usar GroupDocs.Conversion para Java?
GroupDocs.Conversion para Java suporta **200+ formatos de entrada** e **200+ formatos de saída**, abrangendo tudo, desde DOCX e PPTX até PDF/A e tipos de imagem. Ele funciona completamente no servidor, portanto não são necessários produtos Microsoft Office ou Adobe. A API é thread‑safe, pode processar documentos com centenas de páginas sem carregar o arquivo inteiro na memória, e integra‑se perfeitamente com serviços de armazenamento em nuvem como AWS S3, Azure Blob e Google Cloud Storage.

## Pré-requisitos
- **Java Development Kit (JDK):** Version 8 ou mais recente.  
- **Maven:** Configurado corretamente no seu IDE (IntelliJ IDEA, Eclipse, NetBeans, etc.).  
- **GroupDocs.Conversion for Java:** Adicionado como dependência Maven (veja abaixo).  

## Configurando GroupDocs.Conversion para Java

Add the GroupDocs repository and dependency to your `pom.xml`:

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

### Aquisição de Licença
Comece com um teste gratuito para explorar a API. Para cargas de trabalho de produção, adquira uma licença ou solicite uma licença de avaliação temporária.

### Inicialização e Configuração Básicas

```java
import com.groupdocs.conversion.Converter;

public class ConversionSetup {
    public static void main(String[] args) {
        // Initialize the Converter object
        Converter converter = new Converter();
        
        System.out.println("GroupDocs.Conversion for Java has been initialized successfully.");
    }
}
```

## Como listar formatos usando GroupDocs.Conversion para Java
`Converter` é a classe principal que realiza conversões e fornece informações de formato. `getAllPossibleConversions()` retorna uma lista de todos os pares de conversão origem‑destino suportados. `ConversionInfo` representa um mapeamento de conversão único entre um formato de origem e um de destino.  

Carregue o mecanismo `Converter`, chame `getAllPossibleConversions()` e você receberá uma lista de objetos `ConversionInfo` que descrevem cada par origem‑destino permitido. Essa única chamada é tudo que você precisa para construir um menu suspenso de opções de exportação, validar arquivos recebidos ou projetar scripts de migração em lote.

### Inicializar e recuperar conversões

The `Converter` class is the core engine that provides conversion capabilities and exposes the `getAllPossibleConversions()` method.  

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.contracts.PossibleConversions;

public class GetAllPossibleConversionsFeature {
    public static void run() {
        // Initialize the Converter object
        Converter converter = new Converter();
```

### Iterar sobre conversões possíveis

```java
// Retrieve all possible conversions supported by the library
for (PossibleConversions conversions : converter.getAllPossibleConversions()) {
    // Print source format description
    System.out.print(String.format("Source format: %s \n", conversions.getSource().getDescription()));
```

### Determinar tipos de conversão

```java
// Iterate through each target conversion available for the source format
for (TargetConversion conversion : conversions.getAll()) {
    // Determine if it's a primary or secondary conversion and print details
    System.out.print(String.format("\t...can be converted to %s format as %s conversion.\n",
            conversion.getFormat(),
            conversion.isPrimary() ? "primary" : "secondary"));
}
```

### Função completa

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.contracts.PossibleConversions;
import com.groupdocs.conversion.contracts.TargetConversion;

public class GetAllPossibleConversionsFeature {
    public static void run() {
        // Initialize the Converter object
        Converter converter = new Converter();

        // Retrieve all possible conversions supported by the library
        for (PossibleConversions conversions : converter.getAllPossibleConversions()) {
            // Print source format description
            System.out.print(String.format("Source format: %s \n", conversions.getSource().getDescription()));

            // Iterate through each target conversion available for the source format
            for (TargetConversion conversion : conversions.getAll()) {
                // Determine if it's a primary or secondary conversion and print details
                System.out.print(String.format("\t...can be converted to %s format as %s conversion.\n",
                        conversion.getFormat(),
                        conversion.isPrimary() ? "primary" : "secondary"));
            }
        }
    }
}
```

## Casos de uso de conversão de arquivos em armazenamento em nuvem
Conhecer a matriz completa de conversões é especialmente valioso ao construir serviços de **cloud storage file conversion**:

1. **Detecção dinâmica de formato:** Quando um arquivo chega ao armazenamento em nuvem, você pode consultar instantaneamente se o formato de destino desejado é suportado.  
2. **Migração em lote:** Mova grandes bibliotecas de documentos para um formato unificado (por exemplo, PDF/A) iterando sobre os tipos de origem suportados.  
3. **Exportação orientada ao usuário:** Ofereça aos usuários finais um menu suspenso apenas com os formatos para os quais seu documento atual pode ser exportado, reduzindo erros e melhorando a experiência do usuário.

## Considerações de desempenho
- **Gerenciamento de recursos:** Libere a instância `Converter` ou use try‑with‑resources se você criar muitos conversores de curta duração.  
- **Processamento em lote:** Agrupe vários arquivos em um único trabalho para reduzir a sobrecarga.  
- **Cache:** Armazene em cache o resultado de `getAllPossibleConversions()` se você consultá‑lo com frequência; a matriz de conversões raramente muda em tempo de execução.  

## Problemas comuns e soluções

| Sintoma | Causa provável | Correção |
|---------|----------------|----------|
| Nenhuma saída aparece | `Converter` não inicializado corretamente | Certifique‑se de que o JAR da biblioteca está no classpath e a licença está carregada. |
| A lista `TargetConversion` está vazia | Usando uma versão desatualizada da biblioteca | Atualize para a versão mais recente do GroupDocs.Conversion. |
| Picos de memória em documentos grandes | Não liberando os recursos do conversor | Chame `converter.close()` ou use try‑with‑resources. |

## Perguntas frequentes

**Q: O que é GroupDocs.Conversion para Java?**  
A: É uma biblioteca server‑side que suporta 200+ formatos de entrada e 200+ formatos de saída, permitindo conversão de documentos rápida e sem licença, sem software externo.

**Q: Como começar com GroupDocs.Conversion?**  
A: Configure seu projeto Maven, adicione a dependência mostrada anteriormente, carregue um arquivo de licença e instancie a classe `Converter` conforme demonstrado na seção de inicialização.

**Q: Posso converter tipos de arquivo personalizados usando GroupDocs.Conversion?**  
A: Sim—através dos pontos de extensibilidade da API você pode registrar conversores personalizados ou integrar manipuladores de terceiros para formatos proprietários.

**Q: Quais são as armadilhas comuns ao implementar conversões?**  
A: Esquecer de fechar o `Converter`, usar uma versão antiga do JAR ou ignorar o uso de memória em PDFs muito grandes. Siga as dicas de gerenciamento de recursos acima.

**Q: Onde posso obter mais ajuda?**  
A: Visite a [documentação](https://docs.groupdocs.com/conversion/java/) oficial ou faça perguntas no fórum da comunidade GroupDocs.

---

**Última atualização:** 2026-07-29  
**Testado com:** GroupDocs.Conversion 25.2 for Java  
**Autor:** GroupDocs

## Tutoriais relacionados

- [Converter Word para PDF e outros formatos de arquivo com GroupDocs.Conversion para Java](/conversion/java/)
- [Word para PDF Java – Ocultar alterações rastreadas e opções de conversão](/conversion/java/conversion-options/)
- [Como rastrear o progresso da conversão em Java com GroupDocs - Um guia completo](/conversion/java/conversion-events-logging/java-groupdocs-conversion-progress-listener/)