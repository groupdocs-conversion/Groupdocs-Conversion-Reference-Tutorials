---
title: Convertir OTG a PDF
linktitle: Convertir OTG a PDF
second_title: API GroupDocs.Conversión .NET
description: Aprenda cómo convertir archivos OTG a PDF usando GroupDocs.Conversion para .NET. Integración simple, eficiente y perfecta para sus proyectos.
type: docs
weight: 13
url: /es/net/pdf-conversion/convert-otg-to-pdf/
---
## Introducción
Convertir archivos OTG (OpenDocument Graphics) a formato PDF puede ser una tarea crucial, especialmente cuando se trata de sistemas de gestión de documentos o se comparten archivos entre diferentes plataformas. En este tutorial, lo guiaremos a través del proceso de conversión de archivos OTG a PDF usando la biblioteca GroupDocs.Conversion para .NET. ¡Vamos a sumergirnos!
## Requisitos previos
Antes de comenzar, asegúrese de tener los siguientes requisitos previos:
1. GroupDocs.Conversion para .NET: asegúrese de haber instalado la biblioteca GroupDocs.Conversion para .NET. Puedes descargarlo desde[aquí](https://releases.groupdocs.com/conversion/net/).
2. Archivo OTG: tenga listo el archivo OTG que desea convertir a PDF en su directorio de documentos.

## Importar espacios de nombres
Primero, necesita importar los espacios de nombres necesarios a su proyecto .NET. 
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Paso 1: configurar el directorio de salida y el nombre del archivo
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "otg-converted-to.pdf");
```
 En este paso, define el directorio de salida donde se guardará el archivo PDF convertido. Reemplazar`"Your Document Directory"` con la ruta al directorio de salida deseado.
## Paso 2: cargue el archivo OTG de origen y conviértalo a PDF
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_OTG))
{
    var options = new PdfConvertOptions();
    // Guardar archivo PDF convertido
    converter.Convert(outputFile, options);
}
```
 Aquí, creamos una instancia de un nuevo`Converter` objeto de la biblioteca GroupDocs.Conversion, pasando la ruta del archivo OTG de origen. Luego, creamos`PdfConvertOptions` para especificar opciones de conversión. Finalmente llamamos al`Convert` Método para convertir el archivo OTG a formato PDF.
## Paso 3: Verifique la finalización de la conversión
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
Este paso notifica al usuario que el proceso de conversión se completó exitosamente y proporciona la ruta donde se guarda el archivo PDF convertido.

## Conclusión
La conversión de archivos OTG a formato PDF se simplifica con la biblioteca GroupDocs.Conversion para .NET. Si sigue los pasos descritos en este tutorial, podrá integrar perfectamente esta funcionalidad en sus aplicaciones .NET, mejorando la interoperabilidad y accesibilidad de los documentos.
## Preguntas frecuentes
### ¿Puede GroupDocs.Conversion convertir otros formatos de archivo además de OTG a PDF?
Sí, GroupDocs.Conversion admite una amplia gama de formatos de archivo para conversión, incluidos DOCX, XLSX, PPTX, HTML y más.
### ¿GroupDocs.Conversion es adecuado para uso comercial?
¡Absolutamente! GroupDocs.Conversion ofrece licencias comerciales para empresas y organizaciones que buscan aprovechar sus poderosas capacidades de conversión de documentos.
### ¿GroupDocs.Conversion proporciona soporte técnico?
Sí, GroupDocs ofrece soporte técnico dedicado para ayudar a los usuarios con cualquier consulta o problema que puedan encontrar durante la implementación.
### ¿Puedo probar GroupDocs.Conversion antes de comprar una licencia?
Sí, puede aprovechar una prueba gratuita de GroupDocs.Conversion para explorar sus funciones y su compatibilidad con sus requisitos.
### ¿Cómo puedo obtener una licencia temporal para GroupDocs.Conversion?
Puede obtener una licencia temporal de GroupDocs para fines de evaluación o proyectos a corto plazo visitando la página temporal[licencia](https://purchase.groupdocs.com/temporary-license/).