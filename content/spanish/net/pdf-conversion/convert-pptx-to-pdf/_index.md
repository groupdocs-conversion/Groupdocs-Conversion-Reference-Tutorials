---
title: Convertir PPTX a PDF
linktitle: Convertir PPTX a PDF
second_title: API GroupDocs.Conversión .NET
description: Aprenda a convertir presentaciones de PowerPoint (PPTX) a formato PDF usando GroupDocs.Conversion para .NET. Proceso de conversión fácil y eficiente.
weight: 29
url: /es/net/pdf-conversion/convert-pptx-to-pdf/
---

# Convertir PPTX a PDF

## Introducción
En este tutorial, recorreremos el proceso de conversión de un archivo de presentación de PowerPoint (PPTX) a un formato de documento portátil (PDF) utilizando la biblioteca GroupDocs.Conversion para .NET. Siga los pasos a continuación para lograr esta conversión.
## Requisitos previos
Antes de comenzar, asegúrese de tener los siguientes requisitos previos:
1.  Biblioteca GroupDocs.Conversion para .NET: asegúrese de haber instalado la biblioteca GroupDocs.Conversion para .NET. Puedes descargarlo desde[aquí](https://releases.groupdocs.com/conversion/net/).
2. Entorno de desarrollo: configure un entorno de desarrollo con las herramientas necesarias como Visual Studio o cualquier otro .NET IDE.

## Importar espacios de nombres
Incluya los espacios de nombres necesarios en su proyecto para acceder a las funcionalidades de GroupDocs.Conversion.
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Paso 1: configurar la carpeta de salida y el nombre del archivo
Primero, defina la carpeta de salida donde se guardará el archivo PDF convertido y especifique el nombre del archivo PDF de salida.
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "pptx-converted-to.pdf");
```
## Paso 2: cargue el archivo PPTX de origen
Cargue el archivo de presentación de PowerPoint (PPTX) de origen utilizando la biblioteca GroupDocs.Conversion.
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PPTX))
{
    // La lógica de conversión se colocará aquí.
}
```
## Paso 3: especifique las opciones de conversión
Defina las opciones de conversión. En este caso, estamos convirtiendo al formato PDF, así que cree una instancia de`PdfConvertOptions`.
```csharp
var options = new PdfConvertOptions();
```
## Paso 4: realice la conversión
 Ejecute el proceso de conversión utilizando el`Convert` método y pase la ruta del archivo de salida junto con las opciones de conversión.
```csharp
converter.Convert(outputFile, options);
```
## Paso 5: verificar la salida
Una vez que la conversión se haya completado con éxito, muestre un mensaje que indique la finalización y la ubicación del archivo de salida.
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```

## Conclusión
En este tutorial, aprendimos cómo convertir un archivo de presentación de PowerPoint (PPTX) a un formato de documento portátil (PDF) usando la biblioteca GroupDocs.Conversion para .NET. Si sigue los pasos descritos anteriormente, podrá realizar fácilmente esta conversión en sus aplicaciones .NET.
## Preguntas frecuentes
### P: ¿GroupDocs.Conversion es compatible con todas las versiones de .NET?
R: Sí, GroupDocs.Conversion es compatible con .NET Framework 2.0 y superiores, incluidos .NET Core y .NET Standard.
### P: ¿Puedo convertir archivos a formatos distintos de PDF?
R: Sí, GroupDocs.Conversion admite una amplia gama de formatos de documentos para conversión, incluidos Word, Excel, HTML y más.
### P: ¿GroupDocs.Conversion ofrece alguna prueba gratuita?
 R: Sí, puede acceder a una prueba gratuita de GroupDocs.Conversion desde[aquí](https://releases.groupdocs.com/).
### P: ¿Cómo puedo obtener soporte para GroupDocs.Conversion?
 R: Puede obtener asistencia en el foro de la comunidad GroupDocs.[aquí](https://forum.groupdocs.com/c/conversion/11).
### P: ¿Existe una licencia temporal disponible para GroupDocs.Conversion?
 R: Sí, puede obtener una licencia temporal para GroupDocs.Conversion desde[aquí](https://purchase.groupdocs.com/temporary-license/).