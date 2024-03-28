---
title: Convertir documentos DOC de Word a PDF
linktitle: Convertir documentos DOC de Word a PDF
second_title: API GroupDocs.Conversión .NET
description: Convierta sin esfuerzo documentos DOC Word a PDF utilizando GroupDocs.Conversion para .NET. Siga nuestra guía paso a paso para una conversión de documentos perfecta.
type: docs
weight: 23
url: /es/net/file-conversion-to-pdf/convert-doc-to-pdf/
---
## Introducción
En la era digital actual, la capacidad de convertir documentos sin problemas de un formato a otro es esencial tanto para las empresas como para los particulares. Ya sea que trabaje con documentos de Word, PDF u otros tipos de archivos, tener las herramientas adecuadas puede marcar la diferencia. Una de esas herramientas es GroupDocs.Conversion para .NET, una poderosa biblioteca que brinda a los desarrolladores la capacidad de convertir documentos con facilidad.
## Requisitos previos
Antes de sumergirse en el proceso de conversión utilizando GroupDocs.Conversion para .NET, asegúrese de tener implementados los siguientes requisitos previos:
1.  Descargue e instale GroupDocs.Conversion para .NET: navegue hasta la[enlace de descarga](https://releases.groupdocs.com/conversion/net/) y siga las instrucciones de instalación proporcionadas.
2. Obtenga una licencia: necesitará una licencia para utilizar GroupDocs.Conversion para .NET en sus aplicaciones. Si recién estás comenzando, puedes aprovechar una[licencia temporal](https://purchase.groupdocs.com/temporary-license/) con fines de prueba o comprar una licencia para uso en producción.
3. Familiaridad con el entorno .NET: se recomienda seguir conocimientos básicos del marco .NET y el lenguaje de programación C# junto con los ejemplos.
4. Acceso a los documentos fuente: asegúrese de tener los documentos fuente que desea convertir. Para fines de demostración, convertiremos documentos DOC Word a formato PDF.

## Importar espacios de nombres
Antes de comenzar el proceso de conversión, importemos los espacios de nombres necesarios a nuestro proyecto .NET:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Paso 1: definir la carpeta y el archivo de salida
Primero, especifique la carpeta de salida donde desea guardar el archivo PDF convertido, junto con el nombre del archivo de salida deseado.
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "doc-converted-to.pdf");
```
## Paso 2: cargar el archivo DOC de origen
A continuación, cargue el archivo DOC de origen utilizando la clase GroupDocs.Conversion.Converter.
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_DOC))
```
## Paso 3: configurar las opciones de conversión
Configure las opciones de conversión según sus requisitos. Para convertir DOC a PDF, usaremos PdfConvertOptions.
```csharp
var options = new PdfConvertOptions();
```
## Paso 4: realizar la conversión
Ejecute el proceso de conversión llamando al método Convert del objeto convertidor, pasando la ruta del archivo de salida y las opciones de conversión.
```csharp
converter.Convert(outputFile, options);
```
## Paso 5: verificar la finalización de la conversión
Una vez que se complete la conversión, muestre un mensaje de éxito junto con la ubicación de la carpeta de salida.
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```

## Conclusión
GroupDocs.Conversion para .NET simplifica el proceso de conversión de documentos entre varios formatos. Si sigue los pasos descritos en este tutorial, podrá convertir fácilmente documentos DOC Word a PDF.
## Preguntas frecuentes
### ¿GroupDocs.Conversion para .NET es compatible con todas las versiones de .NET?
GroupDocs.Conversion para .NET es compatible con .NET Framework 2.0 y versiones posteriores, incluidos .NET Core y .NET 5+.
### ¿Puedo convertir varios documentos simultáneamente usando GroupDocs.Conversion para .NET?
Sí, GroupDocs.Conversion para .NET admite la conversión por lotes, lo que le permite convertir varios documentos de una sola vez.
### ¿GroupDocs.Conversion para .NET requiere una conexión a Internet?
No, GroupDocs.Conversion para .NET funciona localmente en su máquina y no requiere una conexión a Internet para la conversión.
### ¿Puedo personalizar las opciones de conversión para requisitos específicos?
Sí, GroupDocs.Conversion para .NET ofrece amplias opciones para personalizar el proceso de conversión para satisfacer sus necesidades específicas.
### ¿Hay soporte técnico disponible para GroupDocs.Conversion para .NET?
 Sí, el soporte técnico para GroupDocs.Conversion para .NET está disponible a través de[foro](https://forum.groupdocs.com/c/conversion/11) donde puede buscar asistencia y orientación de la comunidad y expertos.