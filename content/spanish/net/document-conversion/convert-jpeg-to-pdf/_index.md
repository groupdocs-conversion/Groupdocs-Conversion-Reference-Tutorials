---
title: Convertir JPEG a PDF
linktitle: Convertir JPEG a PDF
second_title: API GroupDocs.Conversión .NET
description: Convierta JPEG a PDF sin problemas utilizando GroupDocs.Conversion para .NET. Siga nuestra guía paso a paso para una transformación eficiente del formato de archivo.
weight: 12
url: /es/net/document-conversion/convert-jpeg-to-pdf/
---

# Convertir JPEG a PDF

## Introducción
En el mundo del desarrollo de software, convertir archivos de un formato a otro es una tarea común. Ya sea que se trate de convertir imágenes a PDF, documentos a imágenes o cualquier otra transformación de formato de archivo, tener una herramienta confiable para realizar esta tarea de manera eficiente es crucial. Una de esas herramientas es GroupDocs.Conversion para .NET, una poderosa biblioteca que brinda a los desarrolladores la capacidad de convertir varios formatos de archivos sin problemas.
## Requisitos previos
Antes de sumergirse en el proceso de conversión utilizando GroupDocs.Conversion para .NET, existen algunos requisitos previos que debe cumplir:
### 1. Instale GroupDocs.Conversion para .NET
 En primer lugar, debe instalar la biblioteca GroupDocs.Conversion para .NET. Puedes descargar la biblioteca desde[pagina de descarga](https://releases.groupdocs.com/conversion/net/) y siga las instrucciones de instalación proporcionadas.
### 2. Comprensión básica de C#
Debe tener un conocimiento básico del lenguaje de programación C#, ya que lo usaremos para escribir fragmentos de código para el proceso de conversión.
### 3. Entorno de desarrollo integrado (IDE)
Necesitará un IDE como Visual Studio o JetBrains Rider para escribir, compilar y ejecutar los ejemplos de código.
### 4. Archivo(s) fuente para convertir
Asegúrese de tener los archivos de origen listos en el formato desde el que desea convertir. Por ejemplo, si está convirtiendo de JPEG a PDF, tenga disponibles los archivos JPEG.

## Importar espacios de nombres
Antes de profundizar en el proceso paso a paso de convertir JPEG a PDF usando GroupDocs.Conversion para .NET, importemos los espacios de nombres necesarios:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```

## Paso 1: definir la carpeta de salida y el nombre del archivo
Primero, defina la carpeta de salida donde se guardará el archivo PDF convertido y especifique el nombre del archivo de salida:
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "jpeg-converted-to.pdf");
```
## Paso 2: cargue el archivo JPEG de origen
 A continuación, cargue el archivo JPEG de origen utilizando el`Converter` clase proporcionada por GroupDocs.Conversion:
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_JPEG))
{
    // El código de conversión irá aquí
}
```
## Paso 3: configurar las opciones de conversión
Configure las opciones de conversión según sus requisitos. En este caso, dado que estamos convirtiendo JPEG a PDF, usaremos`PdfConvertOptions`:
```csharp
var options = new PdfConvertOptions();
```
## Paso 4: realice la conversión
 Realice la conversión real llamando al`Convert` método y pasando la ruta del archivo de salida junto con las opciones de conversión:
```csharp
converter.Convert(outputFile, options);
```
## Paso 5: Mostrar mensaje de finalización
Finalmente, mostrará un mensaje indicando que el proceso de conversión se completó exitosamente:
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```

## Conclusión
En este tutorial, aprendimos cómo convertir JPEG a PDF usando GroupDocs.Conversion para .NET. Si sigue la guía paso a paso y comprende los requisitos previos, podrá integrar perfectamente las capacidades de conversión de formatos de archivos en sus aplicaciones .NET.
## Preguntas frecuentes
### ¿GroupDocs.Conversion para .NET es compatible con todos los marcos .NET?
Sí, GroupDocs.Conversion para .NET es compatible con varios marcos .NET, incluidos .NET Core y .NET Framework.
### ¿Puedo convertir varios archivos simultáneamente usando GroupDocs.Conversion para .NET?
Sí, puedes convertir varios archivos simultáneamente implementando técnicas de procesamiento paralelo en tu código.
### ¿GroupDocs.Conversion para .NET admite la conversión entre todos los formatos de archivo?
GroupDocs.Conversion para .NET admite una amplia gama de formatos de archivo, incluidos, entre otros, imágenes, documentos, hojas de cálculo, presentaciones y más.
### ¿Existe una versión de prueba disponible para GroupDocs.Conversion para .NET?
 Sí, puede aprovechar una versión de prueba gratuita desde[sitio web](https://releases.groupdocs.com/).
### ¿Dónde puedo buscar ayuda o soporte con respecto a GroupDocs.Conversion para .NET?
 Puedes visitar el[Foro GroupDocs.Conversión](https://forum.groupdocs.com/c/conversion/11) para recibir ayuda y apoyo de la comunidad.