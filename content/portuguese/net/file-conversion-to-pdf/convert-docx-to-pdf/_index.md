---
title: Converter documentos DOCX do Word em PDF
linktitle: Converter documentos DOCX do Word em PDF
second_title: API GroupDocs.Conversion .NET
description: Aprenda como converter facilmente documentos DOCX Word em PDF usando GroupDocs.Conversion for .NET. Aprimore seus recursos de gerenciamento de documentos.
type: docs
weight: 24
url: /pt/net/file-conversion-to-pdf/convert-docx-to-pdf/
---
## Introdução
No domínio do gerenciamento de documentos, a conversão de arquivos de um formato para outro costuma ser uma necessidade. Seja por motivos de compatibilidade, fins de arquivamento ou simplesmente preferência, ser capaz de converter facilmente entre formatos é crucial. Neste tutorial, nos aprofundaremos em como converter documentos DOCX Word em PDF sem esforço usando a biblioteca GroupDocs.Conversion para .NET. Seguindo estas instruções passo a passo, você estará preparado para lidar com essas conversões com facilidade.
## Pré-requisitos
Antes de mergulhar no processo de conversão, certifique-se de ter os seguintes pré-requisitos em vigor:
1.  GroupDocs.Conversion for .NET: certifique-se de ter a biblioteca instalada em seu ambiente de desenvolvimento. Caso contrário, você pode baixá-lo em[aqui](https://releases.groupdocs.com/conversion/net/).
2. .NET Framework: certifique-se de ter um conhecimento prático de desenvolvimento .NET e de ter o ambiente necessário configurado.

## Importar namespaces
Para começar, vamos importar os namespaces necessários em seu código C#:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Etapa 1: definir pasta e arquivo de saída
Em primeiro lugar, especifique a pasta de saída onde deseja que o arquivo PDF convertido seja salvo e defina o nome do arquivo de saída:
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "docx-converted-to.pdf");
```
 Substituir`"Your Document Directory"` com o caminho do diretório onde deseja salvar o arquivo PDF convertido.
## Etapa 2: Carregar arquivo DOCX de origem
Em seguida, carregue o arquivo DOCX de origem usando a biblioteca GroupDocs.Conversion:
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_DOCX))
{
    // O código de conversão irá aqui
}
```
 Substituir`Constants.SAMPLE_DOCX` com o caminho para o arquivo DOCX de origem.
## Etapa 3: especifique as opções de conversão
Defina as opções de conversão. Neste caso, usaremos PdfConvertOptions já que estamos convertendo para PDF:
```csharp
var options = new PdfConvertOptions();
```
## Etapa 4: realizar a conversão
Execute a conversão real e salve o arquivo PDF convertido:
```csharp
converter.Convert(outputFile, options);
```
## Etapa 5: exibir mensagem de sucesso
Por fim, notifique o usuário de que o processo de conversão foi concluído com sucesso:
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```

## Conclusão
Concluindo, converter documentos DOCX Word para o formato PDF é uma tarefa simples com a biblioteca GroupDocs.Conversion para .NET. Seguindo as etapas descritas neste tutorial, você pode realizar essas conversões perfeitamente em seus aplicativos .NET, aprimorando os recursos de gerenciamento de documentos.
## Perguntas frequentes
### O GroupDocs.Conversion é compatível com todas as versões do .NET?
Sim, GroupDocs.Conversion é compatível com diversas versões do .NET, garantindo flexibilidade aos desenvolvedores.
### Posso converter outros formatos de arquivo além de DOCX para PDF usando GroupDocs.Conversion?
Absolutamente! GroupDocs.Conversion oferece suporte a uma ampla variedade de formatos de arquivo para conversão, incluindo DOCX, XLSX, PPTX e muito mais.
### Existe uma versão de teste disponível para GroupDocs.Conversion?
 Sim, você pode aproveitar um teste gratuito em[aqui](https://releases.groupdocs.com/).
### Como posso obter suporte para consultas relacionadas ao GroupDocs.Conversion?
 Você pode buscar ajuda no fórum da comunidade GroupDocs[aqui](https://forum.groupdocs.com/c/conversion/11).
### Onde posso obter uma licença temporária para GroupDocs.Conversion?
 Você pode adquirir uma licença temporária em[aqui](https://purchase.groupdocs.com/temporary-license/).