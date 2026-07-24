---
date: '2026-07-24'
description: 'Conversão de imagem Java facilitada: aprenda como converter arquivos
  CAD para TIFF com dimensões personalizadas usando o GroupDocs Conversion Java. Guia
  passo a passo para desenvolvedores.'
keywords:
- java image conversion
- custom width height
- set image dimensions java
lastmod: '2026-07-24'
og_description: Conversão de imagem Java facilitada. Converta arquivos CAD para imagens
  TIFF de alta qualidade com largura e altura personalizadas usando o GroupDocs Conversion
  Java. Siga nosso guia detalhado.
og_image_alt: 'Guide: Convert CAD to TIFF with custom dimensions using GroupDocs Conversion
  Java'
og_title: 'Conversão de Imagem Java: CAD para TIFF com Dimensões Personalizadas'
schemas:
- author: GroupDocs
  dateModified: '2026-07-24'
  description: 'Java image conversion made easy: learn how to convert CAD files to
    TIFF with custom dimensions using GroupDocs Conversion Java. Step‑by‑step guide
    for developers.'
  headline: 'Java Image Conversion: CAD to TIFF with Custom Dimensions'
  type: TechArticle
- questions:
  - answer: GroupDocs Conversion Java, a robust Java image conversion library.
    question: What library should I use for Java image conversion?
  - answer: Use `CadLoadOptions` and specify `setWidth()` and `setHeight()`.
    question: How do I set custom dimensions for a CAD file?
  - answer: Yes—load the CAD, set dimensions, then convert with `ImageConvertOptions`.
    question: Can I convert DWG to TIFF in one step?
  - answer: A free trial works for evaluation; a full license unlocks all features.
    question: Do I need a license?
  - answer: Any Java 8+ runtime is supported.
    question: What Java version is required?
  type: FAQPage
tags:
- convert CAD
- GroupDocs Conversion
- Java image conversion
- TIFF
- CAD processing
title: 'Conversão de Imagem Java: CAD para TIFF com Dimensões Personalizadas'
type: docs
url: /pt/java/cad-formats/cad-conversion-tiff-custom-dimensions-groupdocs-java/
weight: 1
---

# Conversão de Imagem Java: CAD para TIFF com Dimensões Personalizadas

Se você precisar transformar desenhos CAD em imagens TIFF de alta resolução enquanto controla a largura e altura exatas em pixels, **java image conversion** é a chave. Usando GroupDocs Conversion Java, você pode rasterizar qualquer formato CAD suportado (DWG, DGN, DXF, etc.) em um arquivo TIFF que se encaixa perfeitamente em relatórios, portais web ou layouts de impressão. Este guia orienta você em cada passo — desde a configuração do projeto até a conversão final — para que possa integrar o processo em qualquer fluxo de trabalho baseado em Java.

## Respostas Rápidas
- **Qual biblioteca devo usar para Java image conversion?** GroupDocs Conversion Java, uma biblioteca robusta de conversão de imagem Java.  
- **Como definir dimensões personalizadas para um arquivo CAD?** Use `CadLoadOptions` e especifique `setWidth()` e `setHeight()`.  
- **Posso converter DWG para TIFF em um único passo?** Sim—carregue o CAD, defina as dimensões e então converta com `ImageConvertOptions`.  
- **Preciso de uma licença?** Um teste gratuito funciona para avaliação; uma licença completa desbloqueia todos os recursos.  
- **Qual versão do Java é necessária?** Qualquer runtime Java 8+ é suportado.

## O que é GroupDocs Conversion Java?
A biblioteca `GroupDocs Conversion Java` é uma solução de **java image conversion** que suporta mais de 110 formatos de entrada e saída, incluindo todos os principais tipos de CAD e imagens raster.  
A classe `Converter` é o componente central que inicia as operações de conversão de arquivos.  
Ela fornece renderização no lado do servidor, dimensionamento e opções específicas de formato, permitindo que desenvolvedores convertam arquivos sem instalar visualizadores de terceiros.

## Por que Converter CAD para TIFF com Dimensões Personalizadas?
Definir largura e altura explícitas garante que o TIFF resultante se ajuste às restrições de layout exatas dos sistemas downstream. Ao definir as dimensões em pixels antes da rasterização, você evita artefatos de redimensionamento downstream, mantém a consistência da espessura das linhas e assegura que a imagem se integre perfeitamente em PDFs, páginas web ou material impresso sem processamento adicional. Essa abordagem também simplifica pipelines automatizados onde cada imagem deve obedecer a uma especificação de tamanho predefinida.  

- **Preserva a Fidelidade Visual:** Rasterizar em 1920 × 1080 px (ou qualquer tamanho que você escolher) mantém linhas e hachuras nítidas.  
- **Garante Layouts Consistentes:** Imagens são incorporadas de forma limpa em PDFs, páginas HTML ou modelos de impressão sem redimensionamento adicional.  
- **Aumenta a Compatibilidade:** TIFF é universalmente aceito em Windows, macOS, Linux e na maioria das ferramentas de design, reduzindo dores de cabeça com conversão de formatos.  

## Pré-requisitos
Antes de começar, certifique-se de que você tem:

1. **GroupDocs Conversion Java** versão 25.2 ou posterior (a versão mais recente é recomendada).  
2. Uma IDE Java como IntelliJ IDEA ou Eclipse.  
3. Maven instalado para gerenciamento de dependências.  
4. Conhecimento básico de programação Java e familiaridade com o `pom.xml` do Maven.  

## Configurando o GroupDocs Conversion Java

Adicione a dependência Maven do GroupDocs ao seu `pom.xml`:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-conversion</artifactId>
    <version>25.2</version>
</dependency>
```

**Aquisição de Licença:** Você pode obter um teste gratuito, solicitar uma licença temporária para funcionalidade completa ou comprar uma licença permanente para desbloquear totalmente os recursos do GroupDocs Conversion.

Depois que seu projeto Java estiver vinculado a essas dependências corretamente, você estará pronto para começar a converter arquivos CAD!

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

## Como Converter CAD para TIFF com Dimensões Personalizadas?

Converter arquivos CAD para TIFF com dimensões precisas envolve carregar o desenho fonte, configurar opções de renderização e invocar a API de conversão. Ao seguir uma sequência linear — definindo largura e altura, escolhendo TIFF como formato de saída e executando a conversão — você garante que a imagem gerada corresponda aos requisitos de tamanho exatos de suas aplicações downstream, preservando os detalhes e a qualidade do desenho original.  

1. **Importe as classes necessárias** (veja o passo a passo abaixo).  
2. **Crie uma instância de `CadLoadOptions`** e defina `width` e `height` para as dimensões desejadas.  
3. **Instancie `ImageConvertOptions`**, especificando `ImageFileType.Tiff`.  
4. **Chame o método `convert`** em um objeto `Converter`, passando o caminho de origem, as opções de carregamento e as opções de conversão.

### Carregando Documentos CAD com Dimensões Personalizadas (Como Definir Dimensões)

A classe `CadLoadOptions` informa ao GroupDocs como rasterizar o desenho antes da conversão.

`CadLoadOptions` é o objeto de configuração que define parâmetros de renderização como largura, altura e DPI para arquivos CAD.

#### Etapa 1: Importar Bibliotecas Necessárias
```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.filetypes.ImageFileType;
import com.groupdocs.conversion.options.convert.ImageConvertOptions;
import com.groupdocs.conversion.options.load.CadLoadOptions;
```

#### Etapa 2: Configurar Opções de Carregamento com Dimensões Personalizadas
```java
String sourceDocumentPath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DWG_WITH_LAYOUTS_AND_LAYERS";
CadLoadOptions loadOptions = new CadLoadOptions();
loadOptions.setWidth(1920); // Specify the desired width in pixels
loadOptions.setHeight(1080); // Specify the desired height in pixels
Converter converter = new Converter(sourceDocumentPath, () -> loadOptions);
```
*Explicação:* Ao configurar `CadLoadOptions`, você informa ao **GroupDocs Conversion Java** para rasterizar o desenho CAD em 1920 × 1080 pixels antes de qualquer processamento adicional.

### Convertendo CAD para Imagem TIFF (Converter CAD para TIFF)

`ImageConvertOptions` orienta a biblioteca a produzir um arquivo TIFF com as configurações que você especificar.

`ImageConvertOptions` encapsula todos os parâmetros de conversão específicos de imagem, incluindo formato de saída, resolução e nível de compressão.

#### Etapa 3: Configurar Opções de Conversão
```java
String convertedFilePath = "YOUR_OUTPUT_DIRECTORY/ConvertCadAndSpecifyWidthAndHeight.tiff";
ImageConvertOptions options = new ImageConvertOptions();
options.setFormat(ImageFileType.Tiff); // Set the conversion target to TIFF format
```

#### Etapa 4: Executar a Conversão
```java
converter.convert(convertedFilePath, options);
```
*Explicação:* Definir `ImageFileType.Tiff` direciona o **GroupDocs Conversion Java** a gerar um arquivo TIFF de alta qualidade que respeita a largura e altura definidas anteriormente.

## Dicas de Solução de Problemas e Armadilhas Comuns
- **Problemas de Caminho de Arquivo:** Verifique se os caminhos de origem e destino estão corretos e se a aplicação tem permissões de leitura/gravação.  
- **Formatos Não Suportados:** Certifique-se de que o arquivo CAD seja um dos formatos suportados (DWG, DGN, DXF, etc.).  
- **Restrições de Memória:** Desenhos grandes podem exigir o aumento do tamanho do heap da JVM (`-Xmx2g` ou superior).  
- **Preocupações com Qualidade:** Ajuste as configurações de resolução em `ImageConvertOptions` se o DPI padrão não atender aos seus padrões de qualidade.  

## Aplicações Práticas
1. **Visualização Arquitetônica:** Exporte plantas baixas como TIFF para apresentações de alta resolução.  
2. **Documentação de Engenharia:** Gere imagens padronizadas para inclusão em manuais técnicos.  
3. **Relatórios Automatizados:** Incorpore TIFFs derivados de CAD em relatórios PDF ou HTML via pipeline de CI.  

## Considerações de Desempenho
- **Otimizar Uso de Memória:** Libere a instância `Converter` após a conversão (`converter.close()` se aplicável).  
- **Processamento em Lote:** Percorra uma lista de arquivos CAD e reutilize uma única configuração `Converter` para reduzir a sobrecarga.  
- **Mantenha-se Atualizado:** Atualize regularmente para a versão mais recente do GroupDocs Conversion Java para aproveitar melhorias de desempenho e correções de bugs.  

## Perguntas Frequentes

**Q:** Quais formatos de arquivo o GroupDocs Conversion suporta?  
**A:** Ele suporta mais de 110 formatos, incluindo arquivos CAD como DWG, DGN, DXF, além de tipos comuns de imagem, documento e arquivo.  

**Q:** Posso converter vários arquivos CAD de uma vez?  
**A:** Sim—implemente um loop simples que cria um novo `Converter` para cada arquivo ou reutilize a mesma instância com diferentes caminhos de origem.  

**Q:** Como lidar com arquivos de grande tamanho durante a conversão?  
**A:** Aumente o tamanho do heap da JVM, processe arquivos em lotes menores ou use opções de streaming fornecidas pela biblioteca.  

**Q:** E se a qualidade da imagem de saída não for satisfatória?  
**A:** Ajuste o DPI ou as configurações de dimensionamento em `ImageConvertOptions` para aumentar a resolução.  

**Q:** O suporte está disponível se eu encontrar problemas?  
**A:** O GroupDocs oferece documentação extensa, fóruns da comunidade e suporte direto para clientes licenciados.  

## Recursos
- [GroupDocs Documentation](https://docs.groupdocs.com/conversion/java/)
- [API Reference](https://reference.groupdocs.com/conversion/java/)
- [Download Latest Release](https://releases.groupdocs.com/conversion/java/)
- [Purchase Licenses](https://purchase.groupdocs.com/buy)
- [Free Trial Access](https://releases.groupdocs.com/conversion/java/)
- [Temporary License Request](https://purchase.groupdocs.com/temporary-license/)
- [Support Forum](https://forum.groupdocs.com/c/conversion/10)

---

**Última Atualização:** 2026-07-24  
**Testado com:** GroupDocs Conversion Java 25.2  
**Autor:** GroupDocs  

---

## Tutoriais Relacionados

- [convert cad pdf java – CAD Formats Conversion Tutorials for GroupDocs.Conversion Java](/conversion/java/cad-formats/)
- [convert pdf to jpg java using GroupDocs.Conversion – Guide](/conversion/java/document-operations/convert-pdf-to-jpg-groupdocs-java/)
- [How to Set License for GroupDocs.Conversion Java - Step‑By‑Step Guide](/conversion/java/getting-started/groupdocs-conversion-java-license-setup-file-path/)