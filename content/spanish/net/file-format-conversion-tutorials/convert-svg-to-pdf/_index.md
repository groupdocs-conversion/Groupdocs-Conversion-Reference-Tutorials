---
title: Convertir SVG a PDF
linktitle: Convertir SVG a PDF
second_title: API GroupDocs.Conversión .NET
description: Aprenda cómo convertir SVG a PDF usando GroupDocs.Conversion para .NET sin esfuerzo. Agilice su proceso de gestión de documentos.
type: docs
weight: 15
url: /es/net/file-format-conversion-tutorials/convert-svg-to-pdf/
---
## Introducción
En el mundo de la programación convertir archivos de un formato a otro es una tarea habitual. Ya sea que se trate de imágenes, documentos u otros medios, es fundamental poder convertir sin problemas entre formatos. En este tutorial, profundizaremos en cómo convertir archivos SVG (gráficos vectoriales escalables) a PDF (formato de documento portátil) usando GroupDocs.Conversion para .NET.
## Requisitos previos
Antes de sumergirse en el proceso de conversión, asegúrese de tener configurados los siguientes requisitos previos:
### 1. Instale GroupDocs.Conversion para .NET
Asegúrese de tener GroupDocs.Conversion para .NET instalado en su entorno de desarrollo. Si aún no lo has hecho, puedes descargarlo desde[sitio web](https://releases.groupdocs.com/conversion/net/).
### 2. Obtenga un archivo SVG de muestra
Necesitará un archivo SVG de muestra para convertirlo a PDF. Si no tiene uno, puede encontrar fácilmente archivos SVG en línea o crear uno usando varias herramientas de diseño gráfico.
### 3. Comprensión básica de C#
Familiarícese con los conceptos básicos del lenguaje de programación C#, ya que lo usaremos para escribir el código de conversión.

## Importar espacios de nombres
Primero, importemos los espacios de nombres necesarios:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Paso 1: definir la carpeta y el archivo de salida
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "svg-converted-to.pdf");
```
 Asegúrese de reemplazar`"Your Document Directory"` con la ruta al directorio de salida deseado.
## Paso 2: cargue el archivo SVG de origen
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_SVG))
{
    // El código de conversión va aquí
}
```
 Reemplazar`Constants.SAMPLE_SVG` con la ruta a su archivo SVG.
## Paso 3: configurar las opciones de conversión
```csharp
var options = new PdfConvertOptions();
```
Aquí, estamos configurando opciones de conversión específicamente para la salida de PDF. Puede personalizar estas opciones según sus requisitos.
## Paso 4: realice la conversión
```csharp
converter.Convert(outputFile, options);
```
Esta línea ejecuta el proceso de conversión, tomando el archivo SVG de origen y convirtiéndolo a PDF con las opciones especificadas.
## Paso 5: Verifique la finalización de la conversión
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
Esta línea genera un mensaje que confirma la finalización exitosa del proceso de conversión, junto con el directorio donde se encuentra el archivo PDF convertido.

## Conclusión
En este tutorial, aprendimos cómo convertir archivos SVG a PDF usando GroupDocs.Conversion para .NET. Si sigue la guía paso a paso y se asegura de contar con los requisitos previos, podrá incorporar sin problemas capacidades de conversión de formatos de archivos en sus aplicaciones .NET.
## Preguntas frecuentes
### ¿GroupDocs.Conversion para .NET es compatible con todos los marcos .NET?
Sí, GroupDocs.Conversion para .NET admite múltiples marcos .NET, incluidos .NET Core y .NET Framework.
### ¿Puedo personalizar las opciones de conversión para formatos de salida específicos?
¡Absolutamente! GroupDocs.Conversion para .NET proporciona amplias opciones de personalización para cada formato de salida admitido.
### ¿GroupDocs.Conversion para .NET admite la conversión por lotes?
Sí, puede convertir varios archivos simultáneamente utilizando GroupDocs.Conversion para .NET.
### ¿Existe una versión de prueba disponible para fines de prueba?
 Sí, puedes acceder a una versión de prueba gratuita desde[aquí](https://releases.groupdocs.com/).
### ¿Dónde puedo obtener soporte técnico para GroupDocs.Conversion para .NET?
Puede encontrar soporte técnico y asistencia en el foro de GroupDocs.[aquí](https://forum.groupdocs.com/c/conversion/11).