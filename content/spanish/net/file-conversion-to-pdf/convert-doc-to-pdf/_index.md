---
"description": "Convierte fácilmente documentos DOC de Word a PDF con GroupDocs.Conversion para .NET. Sigue nuestra guía paso a paso para una conversión fluida."
"linktitle": "Convertir documentos DOC de Word a PDF"
"second_title": "API .NET de GroupDocs.Conversion"
"title": "Convertir documentos DOC de Word a PDF"
"url": "/es/net/file-conversion-to-pdf/convert-doc-to-pdf/"
"weight": 23
---

# Convertir documentos DOC de Word a PDF

## Introducción
En la era digital actual, la capacidad de convertir documentos de un formato a otro sin problemas es esencial tanto para empresas como para particulares. Ya sea que trabaje con documentos de Word, PDF u otros tipos de archivos, contar con las herramientas adecuadas puede marcar la diferencia. Una de estas herramientas es GroupDocs.Conversion para .NET, una potente biblioteca que permite a los desarrolladores convertir documentos fácilmente.
## Prerrequisitos
Antes de sumergirse en el proceso de conversión utilizando GroupDocs.Conversion para .NET, asegúrese de tener los siguientes requisitos previos:
1. Descargue e instale GroupDocs.Conversion para .NET: navegue hasta el [enlace de descarga](https://releases.groupdocs.com/conversion/net/) y siga las instrucciones de instalación proporcionadas.
2. Obtenga una licencia: Necesitará una licencia para usar GroupDocs.Conversion para .NET en sus aplicaciones. Si recién está comenzando, puede obtener una. [licencia temporal](https://purchase.groupdocs.com/temporary-license/) para fines de prueba o comprar una licencia para uso en producción.
3. Familiaridad con el entorno .NET: Se recomienda tener conocimientos básicos del marco .NET y del lenguaje de programación C# para seguir los ejemplos.
4. Acceso a los documentos fuente: Asegúrese de tener los documentos fuente que desea convertir. A modo de demostración, convertiremos documentos DOC de Word a formato PDF.

## Importar espacios de nombres
Antes de comenzar el proceso de conversión, importemos los espacios de nombres necesarios en nuestro proyecto .NET:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Paso 1: Definir la carpeta y el archivo de salida
Primero, especifique la carpeta de salida donde desea que se guarde el archivo PDF convertido, junto con el nombre del archivo de salida deseado.
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "doc-converted-to.pdf");
```
## Paso 2: Cargar el archivo DOC de origen
A continuación, cargue el archivo DOC de origen utilizando la clase GroupDocs.Conversion.Converter.
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_DOC))
```
## Paso 3: Configurar las opciones de conversión
Configure las opciones de conversión según sus necesidades. Para convertir de DOC a PDF, usaremos PdfConvertOptions.
```csharp
var options = new PdfConvertOptions();
```
## Paso 4: Realizar la conversión
Ejecute el proceso de conversión llamando al método Convert del objeto convertidor, pasando la ruta del archivo de salida y las opciones de conversión.
```csharp
converter.Convert(outputFile, options);
```
## Paso 5: Verificar la finalización de la conversión
Una vez completada la conversión, se mostrará un mensaje de éxito junto con la ubicación de la carpeta de salida.
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```

## Conclusión
GroupDocs.Conversion para .NET simplifica la conversión de documentos entre varios formatos. Siguiendo los pasos de este tutorial, podrá convertir documentos DOC de Word a PDF fácilmente.
## Preguntas frecuentes
### ¿GroupDocs.Conversion para .NET es compatible con todas las versiones de .NET?
GroupDocs.Conversion para .NET es compatible con .NET Framework 2.0 y versiones posteriores, incluidos .NET Core y .NET 5+.
### ¿Puedo convertir varios documentos simultáneamente usando GroupDocs.Conversion para .NET?
Sí, GroupDocs.Conversion para .NET admite la conversión por lotes, lo que le permite convertir varios documentos de una sola vez.
### ¿GroupDocs.Conversion para .NET requiere una conexión a Internet?
No, GroupDocs.Conversion para .NET funciona localmente en su máquina y no requiere una conexión a Internet para la conversión.
### ¿Puedo personalizar las opciones de conversión para requisitos específicos?
Sí, GroupDocs.Conversion para .NET ofrece amplias opciones para personalizar el proceso de conversión para adaptarlo a sus necesidades específicas.
### ¿Hay soporte técnico disponible para GroupDocs.Conversion para .NET?
Sí, el soporte técnico para GroupDocs.Conversion para .NET está disponible a través de [foro](https://forum.groupdocs.com/c/conversion/11) donde puede buscar ayuda y orientación de la comunidad y de expertos.