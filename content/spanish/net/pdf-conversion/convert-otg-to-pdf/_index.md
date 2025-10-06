---
"description": "Aprenda a convertir archivos OTG a PDF con GroupDocs.Conversion para .NET. Integración sencilla, eficiente y fluida para sus proyectos."
"linktitle": "Convertir OTG a PDF"
"second_title": "API .NET de GroupDocs.Conversion"
"title": "Convertir OTG a PDF"
"url": "/es/net/pdf-conversion/convert-otg-to-pdf/"
"weight": 13
type: docs
---
# Convertir OTG a PDF

## Introducción
Convertir archivos OTG (OpenDocument Graphics) a formato PDF puede ser crucial, especialmente al trabajar con sistemas de gestión documental o compartir archivos entre diferentes plataformas. En este tutorial, te guiaremos en el proceso de conversión de archivos OTG a PDF con la biblioteca GroupDocs.Conversion para .NET. ¡Comencemos!
## Prerrequisitos
Antes de comenzar, asegúrese de tener los siguientes requisitos previos:
1. GroupDocs.Conversion para .NET: Asegúrese de tener instalada la biblioteca GroupDocs.Conversion para .NET. Puede descargarla desde [aquí](https://releases.groupdocs.com/conversion/net/).
2. Archivo OTG: Tenga listo en su directorio de documentos el archivo OTG que desea convertir a PDF.

## Importar espacios de nombres
Primero, debes importar los espacios de nombres necesarios a tu proyecto .NET. 
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Paso 1: Establecer el directorio de salida y el nombre del archivo
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "otg-converted-to.pdf");
```
En este paso, define el directorio de salida donde se guardará el archivo PDF convertido. Reemplazar `"Your Document Directory"` con la ruta al directorio de salida deseado.
## Paso 2: Cargue el archivo OTG de origen y conviértalo a PDF
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_OTG))
{
    var options = new PdfConvertOptions();
    // Guardar archivo PDF convertido
    converter.Convert(outputFile, options);
}
```
Aquí, instanciamos una nueva `Converter` Objeto de la biblioteca GroupDocs.Conversion, pasando la ruta del archivo OTG de origen. Luego, creamos `PdfConvertOptions` para especificar las opciones de conversión. Finalmente, llamamos a `Convert` Método para convertir el archivo OTG al formato PDF.
## Paso 3: Verificar la finalización de la conversión
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
Este paso notifica al usuario que el proceso de conversión se completó exitosamente y proporciona la ruta donde se guarda el archivo PDF convertido.

## Conclusión
Convertir archivos OTG a formato PDF es muy sencillo con la biblioteca GroupDocs.Conversion para .NET. Siguiendo los pasos de este tutorial, podrá integrar esta funcionalidad sin problemas en sus aplicaciones .NET, mejorando así la interoperabilidad y la accesibilidad de los documentos.
## Preguntas frecuentes
### ¿Puede GroupDocs.Conversion convertir otros formatos de archivos además de OTG a PDF?
Sí, GroupDocs.Conversion admite una amplia gama de formatos de archivos para la conversión, incluidos DOCX, XLSX, PPTX, HTML y más.
### ¿GroupDocs.Conversion es adecuado para uso comercial?
¡Por supuesto! GroupDocs.Conversion ofrece licencias comerciales para empresas y organizaciones que buscan aprovechar sus potentes capacidades de conversión de documentos.
### ¿GroupDocs.Conversion proporciona soporte técnico?
Sí, GroupDocs ofrece soporte técnico dedicado para ayudar a los usuarios con cualquier consulta o problema que puedan encontrar durante la implementación.
### ¿Puedo probar GroupDocs.Conversion antes de comprar una licencia?
Sí, puede aprovechar una prueba gratuita de GroupDocs.Conversion para explorar sus características y compatibilidad con sus requisitos.
### ¿Cómo puedo obtener una licencia temporal para GroupDocs.Conversion?
Puede obtener una licencia temporal de GroupDocs para fines de evaluación o proyectos a corto plazo visitando el sitio web temporal [licencia](https://purchase.groupdocs.com/temporary-license/).