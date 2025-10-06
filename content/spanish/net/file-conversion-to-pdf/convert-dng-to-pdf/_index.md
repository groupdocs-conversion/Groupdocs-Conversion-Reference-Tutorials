---
"description": "Aprenda a convertir imágenes DNG a PDF fácilmente con GroupDocs.Conversion para .NET. Siga nuestra guía paso a paso para una conversión fluida."
"linktitle": "Convertir imágenes DNG a PDF"
"second_title": "API .NET de GroupDocs.Conversion"
"title": "Convertir imágenes DNG a PDF"
"url": "/es/net/file-conversion-to-pdf/convert-dng-to-pdf/"
"weight": 21
type: docs
---
# Convertir imágenes DNG a PDF

## Introducción
En este tutorial, le guiaremos a través del proceso de conversión de imágenes DNG a PDF con GroupDocs.Conversion para .NET. DNG (Digital Negative) es un formato de archivo utilizado para fotografía digital. Al convertir imágenes DNG a PDF, podrá compartirlas o almacenarlas fácilmente en un formato más universal.
## Prerrequisitos
Antes de comenzar, asegúrese de tener lo siguiente:
1. GroupDocs.Conversion para .NET: Descargue e instale la biblioteca GroupDocs.Conversion para .NET desde [aquí](https://releases.groupdocs.com/conversion/net/).
2. Archivo DNG de origen: necesita un archivo de imagen DNG que desee convertir a PDF.
3. Entorno de desarrollo: asegúrese de tener configurado un entorno de desarrollo .NET.

## Importar espacios de nombres
Primero, debe importar los espacios de nombres necesarios a su proyecto. Agregue las siguientes directivas using a su archivo de código:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Paso 1: Cargue el archivo DNG de origen
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "dng-converted-to.pdf");
// Cargar el archivo DNG de origen
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_DNG))
{
    // Continuar con el proceso de conversión
}
```
En este paso, define la carpeta de salida donde se guardará el archivo PDF convertido. Asegúrate de reemplazar `"Your Document Directory"` Con la ruta al directorio deseado. Luego, especifique el nombre y la ruta del archivo PDF de salida.
## Paso 2: Convertir DNG a PDF
```csharp
var options = new PdfConvertOptions();
// Guardar archivo PDF convertido
converter.Convert(outputFile, options);
```
Aquí, crea una instancia de `PdfConvertOptions` Para configurar opciones específicas para la conversión a PDF, si es necesario. Luego, llama al `Convert` método de la `converter` objeto, pasando la ruta del archivo de salida y las opciones de conversión.
## Paso 3: Gestionar la finalización de la conversión
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
Una vez completado el proceso de conversión, aparecerá un mensaje de éxito junto con el directorio donde se encuentra el archivo PDF convertido.

## Conclusión
En conclusión, convertir imágenes DNG a PDF es fácil con GroupDocs.Conversion para .NET. Siguiendo los sencillos pasos de este tutorial, podrá convertir sus archivos DNG a formato PDF de forma eficiente, haciéndolos más accesibles y fáciles de compartir.
## Preguntas frecuentes
### ¿GroupDocs.Conversion para .NET es compatible con todas las versiones de .NET?
Sí, GroupDocs.Conversion para .NET es compatible con .NET Framework 4.6.1 y superior, así como con .NET Core 2.0 y superior.
### ¿Puedo convertir varios archivos DNG a PDF simultáneamente?
Sí, puedes convertir varios archivos DNG a PDF iterando sobre cada archivo y realizando el proceso de conversión para cada uno.
### ¿Existe alguna limitación en el tamaño de los archivos DNG que se pueden convertir?
GroupDocs.Conversion para .NET no tiene límites específicos en cuanto al tamaño de los archivos DNG que se pueden convertir. Sin embargo, el rendimiento puede variar según el tamaño y la complejidad de los archivos de entrada.
### ¿Puedo personalizar las opciones de conversión para la salida PDF?
Sí, puedes personalizar varias opciones como el tamaño de la página, la orientación, la compresión y más usando el `PdfConvertOptions` clase proporcionada por GroupDocs.Conversion para .NET.
### ¿Hay soporte técnico disponible para GroupDocs.Conversion para .NET?
Sí, el soporte técnico está disponible a través del foro GroupDocs [aquí](https://forum.groupdocs.com/c/conversion/11), donde podrás hacer preguntas y obtener ayuda de expertos.