---
title: Convertir imágenes DNG a PDF
linktitle: Convertir imágenes DNG a PDF
second_title: API GroupDocs.Conversión .NET
description: Aprenda cómo convertir imágenes DNG a PDF sin esfuerzo usando GroupDocs.Conversion para .NET. Siga nuestra guía paso a paso para una conversión perfecta.
weight: 21
url: /es/net/file-conversion-to-pdf/convert-dng-to-pdf/
---
## Introducción
En este tutorial, lo guiaremos a través del proceso de conversión de imágenes DNG a PDF usando GroupDocs.Conversion para .NET. DNG (Digital Negative) es un formato de archivo utilizado para fotografía digital. Al convertir imágenes DNG a PDF, puede compartirlas o almacenarlas fácilmente en un formato más aceptado universalmente.
## Requisitos previos
Antes de comenzar, asegúrese de tener lo siguiente:
1.  GroupDocs.Conversion para .NET: descargue e instale la biblioteca GroupDocs.Conversion para .NET desde[aquí](https://releases.groupdocs.com/conversion/net/).
2. Archivo DNG de origen: necesita un archivo de imagen DNG que desee convertir a PDF.
3. Entorno de desarrollo: asegúrese de tener configurado un entorno de desarrollo .NET.

## Importar espacios de nombres
En primer lugar, debe importar los espacios de nombres necesarios a su proyecto. Agregue las siguientes directivas de uso a su archivo de código:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Paso 1: cargue el archivo DNG de origen
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "dng-converted-to.pdf");
// Cargue el archivo DNG de origen
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_DNG))
{
    // Continuar con el proceso de conversión
}
```
 En este paso, define la carpeta de salida donde se guardará el archivo PDF convertido. Asegúrese de reemplazar`"Your Document Directory"` con la ruta al directorio deseado. Luego, especifica el nombre y la ruta del archivo PDF de salida.
## Paso 2: convertir DNG a PDF
```csharp
var options = new PdfConvertOptions();
// Guardar archivo PDF convertido
converter.Convert(outputFile, options);
```
 Aquí, creas una instancia de`PdfConvertOptions` para configurar opciones específicas para la conversión de PDF, si es necesario. Entonces llamas al`Convert` método de la`converter`objeto, pasando la ruta del archivo de salida y las opciones de conversión.
## Paso 3: gestionar la finalización de la conversión
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
Una vez completado el proceso de conversión, mostrará un mensaje de éxito junto con el directorio donde se encuentra el archivo PDF convertido.

## Conclusión
En conclusión, la conversión de imágenes DNG a PDF se puede realizar fácilmente utilizando GroupDocs.Conversion para .NET. Si sigue los sencillos pasos descritos en este tutorial, puede convertir de manera eficiente sus archivos DNG a formato PDF, haciéndolos más accesibles y compartibles.
## Preguntas frecuentes
### ¿GroupDocs.Conversion para .NET es compatible con todas las versiones de .NET?
Sí, GroupDocs.Conversion para .NET es compatible con .NET Framework 4.6.1 y superior, así como con .NET Core 2.0 y superior.
### ¿Puedo convertir varios archivos DNG a PDF simultáneamente?
Sí, puede convertir varios archivos DNG a PDF recorriendo cada archivo y realizando el proceso de conversión para cada uno.
### ¿Existe alguna limitación en el tamaño de los archivos DNG que se pueden convertir?
GroupDocs.Conversion para .NET no tiene limitaciones específicas en cuanto al tamaño de los archivos DNG que se pueden convertir. Sin embargo, el rendimiento puede variar según el tamaño y la complejidad de los archivos de entrada.
### ¿Puedo personalizar las opciones de conversión para la salida de PDF?
 Sí, puedes personalizar varias opciones como tamaño de página, orientación, compresión y más usando el`PdfConvertOptions`clase proporcionada por GroupDocs.Conversion para .NET.
### ¿Hay soporte técnico disponible para GroupDocs.Conversion para .NET?
 Sí, el soporte técnico está disponible a través del foro de GroupDocs.[aquí](https://forum.groupdocs.com/c/conversion/11), donde puede hacer preguntas y obtener asistencia de expertos.