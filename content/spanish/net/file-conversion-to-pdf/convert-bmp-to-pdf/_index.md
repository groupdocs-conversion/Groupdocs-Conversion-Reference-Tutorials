---
title: Convertir imágenes BMP a PDF
linktitle: Convertir imágenes BMP a PDF
second_title: API GroupDocs.Conversión .NET
description: Convierta imágenes BMP a PDF sin problemas utilizando GroupDocs.Conversion para .NET. Opciones personalizables para un resultado óptimo.
type: docs
weight: 11
url: /es/net/file-conversion-to-pdf/convert-bmp-to-pdf/
---
## Introducción
GroupDocs.Conversion para .NET proporciona una potente solución para convertir imágenes BMP a formato PDF sin problemas. Este tutorial lo guiará a través del proceso paso a paso.
### Requisitos previos
Antes de comenzar, asegúrese de tener lo siguiente:
1.  GroupDocs.Conversion para .NET: instale la biblioteca descargándola desde[enlace de descarga](https://releases.groupdocs.com/conversion/net/).
2. Archivo BMP de origen: prepare el archivo de imagen BMP que desea convertir.

## Importar espacios de nombres
Primero, importe los espacios de nombres necesarios para acceder a las clases y métodos requeridos:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Paso 1: configurar la carpeta de salida y el nombre del archivo
Defina la ruta de la carpeta de salida y el nombre del archivo PDF convertido:
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "bmp-converted-to.pdf");
```
## Paso 2: cargar el archivo BMP de origen
 Cargue el archivo BMP de origen utilizando el`Converter` clase:
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_BMP))
{
    // La lógica de conversión va aquí
}
```
## Paso 3: configurar las opciones de conversión
 Especifique las opciones de conversión. En este caso, usaremos`PdfConvertOptions` para convertir a formato PDF:
```csharp
var options = new PdfConvertOptions();
```
## Paso 4: Convertir BMP a PDF
Realice la conversión y guarde el archivo PDF convertido:
```csharp
converter.Convert(outputFile, options);
```
## Paso 5: verificar la conversión
Compruebe si la conversión se realizó correctamente y muestre la ruta de la carpeta de salida:
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
¡Felicidades! Ha convertido con éxito una imagen BMP a PDF usando GroupDocs.Conversion para .NET.

## Conclusión
En conclusión, GroupDocs.Conversion para .NET ofrece una solución sencilla pero potente para convertir imágenes BMP a formato PDF. Si sigue los pasos descritos en este tutorial, podrá integrar perfectamente esta funcionalidad en sus aplicaciones .NET.
## Preguntas frecuentes
### ¿GroupDocs.Conversion para .NET es compatible con todos los formatos de imagen BMP?
GroupDocs.Conversion para .NET admite una amplia gama de formatos de imágenes BMP, lo que garantiza la compatibilidad con la mayoría de los archivos BMP.
### ¿Puedo personalizar las opciones de conversión para tener más control sobre el PDF de salida?
Sí, puede personalizar varias opciones de conversión, como DPI, tamaño de página, orientación y más, para adaptar el PDF de salida según sus requisitos.
### ¿GroupDocs.Conversion para .NET requiere dependencias adicionales?
No, GroupDocs.Conversion para .NET es una biblioteca independiente que no requiere dependencias adicionales para las tareas de conversión básicas.
### ¿Existe una versión de prueba disponible para probar antes de comprar?
 Sí, puedes descargar una versión de prueba gratuita desde[página de lanzamientos](https://releases.groupdocs.com/) para evaluar las características de la biblioteca antes de realizar una compra.
### ¿Dónde puedo obtener soporte o asistencia si tengo algún problema?
 Puedes visitar el[Foro GroupDocs.Conversión](https://forum.groupdocs.com/c/conversion/11) para obtener ayuda de la comunidad o comuníquese con el soporte directamente para obtener ayuda personalizada.