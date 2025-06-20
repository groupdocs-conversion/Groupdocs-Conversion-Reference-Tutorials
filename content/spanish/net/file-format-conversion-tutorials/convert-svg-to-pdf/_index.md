---
"description": "Aprenda a convertir SVG a PDF fácilmente con GroupDocs.Conversion para .NET. Optimice su gestión documental."
"linktitle": "Convertir SVG a PDF"
"second_title": "API .NET de GroupDocs.Conversion"
"title": "Convertir SVG a PDF"
"url": "/es/net/file-format-conversion-tutorials/convert-svg-to-pdf/"
"weight": 15
---

# Convertir SVG a PDF

## Introducción
En el mundo de la programación, convertir archivos de un formato a otro es una tarea común. Ya sea que trabajes con imágenes, documentos u otros medios, poder convertir entre formatos sin problemas es crucial. En este tutorial, profundizaremos en cómo convertir archivos SVG (Gráficos Vectoriales Escalables) a PDF (Formato de Documento Portátil) usando GroupDocs.Conversion para .NET.
## Prerrequisitos
Antes de sumergirse en el proceso de conversión, asegúrese de tener configurados los siguientes requisitos previos:
### 1. Instalar GroupDocs.Conversion para .NET
Asegúrese de tener GroupDocs.Conversion para .NET instalado en su entorno de desarrollo. Si aún no lo tiene, puede descargarlo desde [sitio web](https://releases.groupdocs.com/conversion/net/).
### 2. Obtenga un archivo SVG de muestra
Necesitará un archivo SVG de muestra para convertirlo a PDF. Si no lo tiene, puede encontrarlo fácilmente en línea o crear uno con diversas herramientas de diseño gráfico.
### 3. Comprensión básica de C#
Familiarícese con los conceptos básicos del lenguaje de programación C#, ya que lo usaremos para escribir el código de conversión.

## Importar espacios de nombres
Primero, importemos los espacios de nombres necesarios:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Paso 1: Definir la carpeta y el archivo de salida
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "svg-converted-to.pdf");
```
Asegúrese de reemplazar `"Your Document Directory"` con la ruta al directorio de salida deseado.
## Paso 2: Cargue el archivo SVG de origen
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_SVG))
{
    // El código de conversión va aquí
}
```
Reemplazar `Constants.SAMPLE_SVG` con la ruta a su archivo SVG.
## Paso 3: Establecer las opciones de conversión
```csharp
var options = new PdfConvertOptions();
```
Aquí configuramos opciones de conversión específicas para la salida a PDF. Puede personalizar estas opciones según sus necesidades.
## Paso 4: Realizar la conversión
```csharp
converter.Convert(outputFile, options);
```
Esta línea ejecuta el proceso de conversión, tomando el archivo SVG de origen y convirtiéndolo a PDF con las opciones especificadas.
## Paso 5: Verificar la finalización de la conversión
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
Esta línea genera un mensaje que confirma la finalización exitosa del proceso de conversión, junto con el directorio donde se encuentra el archivo PDF convertido.

## Conclusión
En este tutorial, aprendimos a convertir archivos SVG a PDF con GroupDocs.Conversion para .NET. Siguiendo la guía paso a paso y asegurándote de cumplir con los requisitos previos, podrás integrar fácilmente las funciones de conversión de formatos de archivo en tus aplicaciones .NET.
## Preguntas frecuentes
### ¿GroupDocs.Conversion para .NET es compatible con todos los marcos .NET?
Sí, GroupDocs.Conversion para .NET es compatible con varios marcos .NET, incluidos .NET Core y .NET Framework.
### ¿Puedo personalizar las opciones de conversión para formatos de salida específicos?
¡Por supuesto! GroupDocs.Conversion para .NET ofrece amplias opciones de personalización para cada formato de salida compatible.
### ¿GroupDocs.Conversion para .NET admite la conversión por lotes?
Sí, puedes convertir varios archivos simultáneamente usando GroupDocs.Conversion para .NET.
### ¿Existe una versión de prueba disponible para fines de prueba?
Sí, puedes acceder a una versión de prueba gratuita desde [aquí](https://releases.groupdocs.com/).
### ¿Dónde puedo obtener soporte técnico para GroupDocs.Conversion para .NET?
Puede encontrar soporte técnico y asistencia en el foro de GroupDocs [aquí](https://forum.groupdocs.com/c/conversion/11).