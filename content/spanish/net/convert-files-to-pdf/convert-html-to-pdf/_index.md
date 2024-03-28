---
title: Convertir páginas web HTML a PDF
linktitle: Convertir páginas web HTML a PDF
second_title: API GroupDocs.Conversión .NET
description: Convierta fácilmente páginas web HTML a formato PDF utilizando GroupDocs.Conversion para .NET. Siga nuestra guía paso a paso para una conversión perfecta del formato de documentos.
type: docs
weight: 22
url: /es/net/convert-files-to-pdf/convert-html-to-pdf/
---
## Introducción
En la era digital actual, la capacidad de convertir sin problemas varios formatos de documentos es crucial tanto para las empresas como para los particulares. Ya sea que se trate de convertir páginas web HTML a PDF para compartirlas o archivarlas fácilmente, tener las herramientas adecuadas puede marcar la diferencia. En este tutorial, exploraremos cómo usar GroupDocs.Conversion para .NET para convertir de manera eficiente páginas web HTML a formato PDF.
## Requisitos previos
Antes de sumergirnos en el tutorial, asegúrese de cumplir con los siguientes requisitos previos:
1.  Instalación: asegúrese de tener GroupDocs.Conversion para .NET instalado en su entorno de desarrollo. Puede descargar los archivos necesarios desde el[enlace de descarga](https://releases.groupdocs.com/conversion/net/).
2. Archivo HTML de muestra: tenga listo un archivo HTML de muestra que desee convertir a PDF. Este servirá como nuestro archivo fuente para la conversión.
3. Entorno .NET: familiaridad básica con el desarrollo .NET y el uso de bibliotecas a través de paquetes NuGet.

## Importar espacios de nombres
Antes de comenzar el proceso de conversión, importemos los espacios de nombres necesarios:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```

## Paso 1: definir la carpeta de salida y la ruta del archivo
Primero, especifique la carpeta de salida donde desea guardar el archivo PDF convertido. Puede elegir cualquier directorio en su sistema.
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "html-converted-to.pdf");
```
## Paso 2: cargue el archivo HTML de origen
A continuación, cargue el archivo HTML de origen que desea convertir a PDF utilizando la clase Converter de GroupDocs.Conversion.
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_HTML))
```
## Paso 3: configurar las opciones de conversión
Configure las opciones de conversión según sus requisitos. En este caso, usaremos PdfConvertOptions para convertir HTML a PDF.
```csharp
var options = new PdfConvertOptions();
```
## Paso 4: realice la conversión
Ahora, realice la conversión real llamando al método Convert de la clase Converter y pasando la ruta del archivo de salida y las opciones de conversión.
```csharp
converter.Convert(outputFile, options);
```
## Paso 5: Mostrar mensaje de éxito
Finalmente, informe al usuario que el proceso de conversión se completó exitosamente y proporcione la ruta donde se guarda el archivo PDF convertido.
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```

## Conclusión
Con GroupDocs.Conversion para .NET, convertir páginas web HTML a formato PDF se vuelve muy sencillo. Si sigue los sencillos pasos descritos en este tutorial, podrá manejar de manera eficiente las conversiones de formato de documentos en sus aplicaciones .NET.
## Preguntas frecuentes
### ¿GroupDocs.Conversion para .NET es compatible con todas las versiones de .NET?
Sí, GroupDocs.Conversion para .NET es compatible con .NET Framework 4.6 y versiones posteriores.
### ¿Puedo convertir varios archivos HTML a PDF simultáneamente?
¡Absolutamente! Puede recorrer su lista de archivos HTML y realizar la conversión para cada archivo individualmente.
### ¿GroupDocs.Conversion admite la conversión a otros formatos además de PDF?
Sí, GroupDocs.Conversion admite una amplia gama de formatos de documentos para conversión, incluidos DOCX, XLSX, PPTX y más.
### ¿Existe una versión de prueba disponible para GroupDocs.Conversion para .NET?
 Sí, puedes descargar una versión de prueba gratuita desde[aquí](https://releases.groupdocs.com/).
### ¿Dónde puedo obtener soporte si encuentro algún problema durante la implementación?
 Puede buscar ayuda en el foro de la comunidad GroupDocs.Conversion[aquí](https://forum.groupdocs.com/c/conversion/11).