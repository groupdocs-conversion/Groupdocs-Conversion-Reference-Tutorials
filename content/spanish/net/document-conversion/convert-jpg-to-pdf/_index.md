---
title: Convertir JPG a PDF
linktitle: Convertir JPG a PDF
second_title: API GroupDocs.Conversión .NET
description: Convierta JPG a PDF sin esfuerzo utilizando GroupDocs.Conversion para .NET. Siga este tutorial paso a paso para una conversión de documentos perfecta.
weight: 14
url: /es/net/document-conversion/convert-jpg-to-pdf/
---

# Convertir JPG a PDF

## Introducción

¿Está buscando convertir archivos JPG a PDF sin esfuerzo usando GroupDocs.Conversion para .NET? Este tutorial lo guiará a través del proceso paso a paso. GroupDocs.Conversion para .NET es una potente API que le permite convertir sin problemas varios formatos de documentos, incluidas imágenes, a PDF con facilidad. ¡Vamos a sumergirnos!

## Requisitos previos

Antes de comenzar, asegúrese de tener los siguientes requisitos previos:

1.  GroupDocs.Conversion para .NET: asegúrese de haber instalado GroupDocs.Conversion para .NET. Puedes descargarlo desde[aquí](https://releases.groupdocs.com/conversion/net/).
2. Entorno de desarrollo: tenga configurado un entorno de desarrollo, como Visual Studio, junto con .NET Framework o .NET Core.
3. Archivo JPG de muestra: prepare un archivo JPG de muestra que desee convertir a PDF.

## Importar espacios de nombres

Primero, importemos los espacios de nombres necesarios:

```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```

Ahora, dividamos el proceso de conversión en pasos simples:

## Paso 1: definir el directorio de salida y el nombre del archivo

```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "jpg-converted-to.pdf");
```

Asegúrese de especificar el directorio donde desea guardar el archivo PDF convertido y el nombre del archivo de salida deseado.

## Paso 2: cargue el archivo JPG de origen y conviértalo a PDF

```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_JPG))
{
    var options = new PdfConvertOptions();
    converter.Convert(outputFile, options);
}
```

 Inicializar el`Converter` objeto con la ruta a su archivo JPG de muestra. Luego, configure las opciones de conversión, como especificar opciones de conversión de PDF. Finalmente, llame al`Convert` método, pasando la ruta del archivo de salida y las opciones de conversión.

## Paso 3: mostrar el mensaje de finalización de la conversión

```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```

Una vez completada la conversión, muestre un mensaje que indique la conversión exitosa y la ubicación del archivo PDF convertido.

## Conclusión

Convertir archivos JPG a PDF usando GroupDocs.Conversion para .NET es sencillo con solo unas pocas líneas de código. Si sigue este tutorial, podrá integrar perfectamente las capacidades de conversión de documentos en sus aplicaciones .NET.

## Preguntas frecuentes

### P: ¿Puedo convertir varios archivos JPG a PDF simultáneamente?

R: Sí, puedes convertir varios archivos JPG a PDF iterando sobre cada archivo y realizando el proceso de conversión descrito en el tutorial.

### P: ¿GroupDocs.Conversion admite otros formatos de imagen además de JPG?

R: Sí, GroupDocs.Conversion admite varios formatos de imagen como PNG, TIFF, BMP y GIF, entre otros.

### P: ¿Puedo personalizar el archivo PDF de salida usando las opciones de conversión?

R: ¡Absolutamente! GroupDocs.Conversion proporciona una amplia gama de opciones de conversión que le permiten personalizar el PDF de salida según sus requisitos.

### P: ¿Existe una versión de prueba disponible para GroupDocs.Conversion para .NET?

R: Sí, puede acceder a una versión de prueba gratuita de GroupDocs.Conversion para .NET desde[aquí](https://releases.groupdocs.com/).

### P: ¿Dónde puedo buscar ayuda si encuentro algún problema durante el proceso de conversión?

 R: Si encuentra algún problema o tiene preguntas sobre GroupDocs.Conversion para .NET, no dude en visitar el[Foro GroupDocs.Conversión](https://forum.groupdocs.com/c/conversion/11) para asistencia.