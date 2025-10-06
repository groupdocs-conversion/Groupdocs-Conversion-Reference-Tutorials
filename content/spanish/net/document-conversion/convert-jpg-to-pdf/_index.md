---
"description": "Convierte JPG a PDF fácilmente con GroupDocs.Conversion para .NET. Sigue este tutorial paso a paso para una conversión de documentos fluida."
"linktitle": "Convertir JPG a PDF"
"second_title": "API .NET de GroupDocs.Conversion"
"title": "Convertir JPG a PDF"
"url": "/es/net/document-conversion/convert-jpg-to-pdf/"
"weight": 14
type: docs
---
# Convertir JPG a PDF

## Introducción

¿Quieres convertir archivos JPG a PDF fácilmente con GroupDocs.Conversion para .NET? Este tutorial te guiará paso a paso. GroupDocs.Conversion para .NET es una potente API que te permite convertir fácilmente varios formatos de documentos, incluyendo imágenes, a PDF. ¡Comencemos!

## Prerrequisitos

Antes de comenzar, asegúrese de tener los siguientes requisitos previos:

1. GroupDocs.Conversion para .NET: Asegúrese de tener instalado GroupDocs.Conversion para .NET. Puede descargarlo desde [aquí](https://releases.groupdocs.com/conversion/net/).
2. Entorno de desarrollo: tenga configurado un entorno de desarrollo, como Visual Studio, junto con .NET Framework o .NET Core.
3. Archivo JPG de muestra: prepare un archivo JPG de muestra que desee convertir a PDF.

## Importar espacios de nombres

Primero, importemos los espacios de nombres necesarios:

```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```

Ahora, desglosemos el proceso de conversión en pasos simples:

## Paso 1: Definir el directorio de salida y el nombre del archivo

```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "jpg-converted-to.pdf");
```

Asegúrese de especificar el directorio donde desea guardar el archivo PDF convertido y el nombre del archivo de salida deseado.

## Paso 2: Cargue el archivo JPG de origen y conviértalo a PDF

```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_JPG))
{
    var options = new PdfConvertOptions();
    converter.Convert(outputFile, options);
}
```

Inicializar el `Converter` objeto con la ruta a su archivo JPG de muestra. Luego, configure las opciones de conversión, como especificar las opciones de conversión a PDF. Finalmente, llame al `Convert` método, pasando la ruta del archivo de salida y las opciones de conversión.

## Paso 3: Mostrar mensaje de finalización de conversión

```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```

Una vez completada la conversión, se mostrará un mensaje indicando la conversión exitosa y la ubicación del archivo PDF convertido.

## Conclusión

Convertir archivos JPG a PDF con GroupDocs.Conversion para .NET es muy sencillo, solo requiere unas pocas líneas de código. Siguiendo este tutorial, podrá integrar fácilmente las funciones de conversión de documentos en sus aplicaciones .NET.

## Preguntas frecuentes

### P: ¿Puedo convertir varios archivos JPG a PDF simultáneamente?

R: Sí, puedes convertir varios archivos JPG a PDF iterando sobre cada archivo y realizando el proceso de conversión descrito en el tutorial.

### P: ¿GroupDocs.Conversion admite otros formatos de imagen además de JPG?

R: Sí, GroupDocs.Conversion admite varios formatos de imagen como PNG, TIFF, BMP y GIF, entre otros.

### P: ¿Puedo personalizar el archivo PDF de salida utilizando las opciones de conversión?

R: ¡Por supuesto! GroupDocs.Conversion ofrece una amplia gama de opciones de conversión que le permiten personalizar el PDF resultante según sus necesidades.

### P: ¿Hay una versión de prueba disponible de GroupDocs.Conversion para .NET?

R: Sí, puede acceder a una versión de prueba gratuita de GroupDocs.Conversion para .NET desde [aquí](https://releases.groupdocs.com/).

### P: ¿Dónde puedo buscar ayuda si encuentro algún problema durante el proceso de conversión?

A: Si tiene algún problema o tiene preguntas sobre GroupDocs.Conversion para .NET, no dude en visitar el sitio [Foro de GroupDocs.Conversion](https://forum.groupdocs.com/c/conversion/11) para obtener ayuda.