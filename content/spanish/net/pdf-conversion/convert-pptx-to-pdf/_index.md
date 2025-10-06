---
"description": "Aprenda a convertir presentaciones de PowerPoint (PPTX) a formato PDF con GroupDocs.Conversion para .NET. Un proceso de conversión sencillo y eficiente."
"linktitle": "Convertir PPTX a PDF"
"second_title": "API .NET de GroupDocs.Conversion"
"title": "Convertir PPTX a PDF"
"url": "/es/net/pdf-conversion/convert-pptx-to-pdf/"
"weight": 29
type: docs
---
# Convertir PPTX a PDF

## Introducción
En este tutorial, explicaremos el proceso de conversión de una presentación de PowerPoint (PPTX) a un formato de documento portátil (PDF) mediante la biblioteca GroupDocs.Conversion para .NET. Siga los pasos a continuación para lograr esta conversión.
## Prerrequisitos
Antes de comenzar, asegúrese de tener los siguientes requisitos previos:
1. Biblioteca GroupDocs.Conversion para .NET: Asegúrese de tener instalada la biblioteca GroupDocs.Conversion para .NET. Puede descargarla desde [aquí](https://releases.groupdocs.com/conversion/net/).
2. Entorno de desarrollo: configure un entorno de desarrollo con las herramientas necesarias como Visual Studio o cualquier otro IDE .NET.

## Importar espacios de nombres
Incluya los espacios de nombres necesarios en su proyecto para acceder a las funcionalidades de GroupDocs.Conversion.
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Paso 1: Establecer la carpeta de salida y el nombre del archivo
Primero, defina la carpeta de salida donde se guardará el archivo PDF convertido y especifique el nombre del archivo PDF de salida.
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "pptx-converted-to.pdf");
```
## Paso 2: Cargue el archivo PPTX de origen
Cargue el archivo de presentación de PowerPoint (PPTX) de origen utilizando la biblioteca GroupDocs.Conversion.
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PPTX))
{
    // La lógica de conversión se colocará aquí
}
```
## Paso 3: Especificar las opciones de conversión
Defina las opciones de conversión. En este caso, convertiremos a formato PDF, así que cree una instancia de `PdfConvertOptions`.
```csharp
var options = new PdfConvertOptions();
```
## Paso 4: Realizar la conversión
Ejecute el proceso de conversión utilizando el `Convert` método y pase la ruta del archivo de salida junto con las opciones de conversión.
```csharp
converter.Convert(outputFile, options);
```
## Paso 5: Verificar la salida
Una vez completada exitosamente la conversión, se mostrará un mensaje indicando la finalización y la ubicación del archivo de salida.
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```

## Conclusión
En este tutorial, aprendimos a convertir una presentación de PowerPoint (PPTX) a un formato de documento portátil (PDF) utilizando la biblioteca GroupDocs.Conversion para .NET. Siguiendo los pasos descritos anteriormente, podrá realizar esta conversión fácilmente en sus aplicaciones .NET.
## Preguntas frecuentes
### P: ¿GroupDocs.Conversion es compatible con todas las versiones de .NET?
R: Sí, GroupDocs.Conversion es compatible con .NET Framework 2.0 y versiones superiores, incluidos .NET Core y .NET Standard.
### P: ¿Puedo convertir archivos a otros formatos que no sean PDF?
R: Sí, GroupDocs.Conversion admite una amplia gama de formatos de documentos para la conversión, incluidos Word, Excel, HTML y más.
### P: ¿GroupDocs.Conversion ofrece alguna prueba gratuita?
R: Sí, puede acceder a una prueba gratuita de GroupDocs.Conversion desde [aquí](https://releases.groupdocs.com/).
### P: ¿Cómo puedo obtener soporte para GroupDocs.Conversion?
R: Puede obtener ayuda en el foro de la comunidad de GroupDocs [aquí](https://forum.groupdocs.com/c/conversion/11).
### P: ¿Hay una licencia temporal disponible para GroupDocs.Conversion?
R: Sí, puede obtener una licencia temporal para GroupDocs.Conversion desde [aquí](https://purchase.groupdocs.com/temporary-license/).