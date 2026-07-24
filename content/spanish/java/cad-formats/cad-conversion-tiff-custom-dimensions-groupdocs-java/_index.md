---
date: '2026-07-24'
description: 'Conversión de imágenes Java simplificada: aprenda cómo convertir archivos
  CAD a TIFF con dimensiones personalizadas usando GroupDocs Conversion Java. Guía
  paso a paso para desarrolladores.'
keywords:
- java image conversion
- custom width height
- set image dimensions java
lastmod: '2026-07-24'
og_description: Conversión de imágenes Java simplificada. Convierta archivos CAD a
  imágenes TIFF de alta calidad con ancho y alto personalizados usando GroupDocs Conversion
  Java. Siga nuestra guía detallada.
og_image_alt: 'Guide: Convert CAD to TIFF with custom dimensions using GroupDocs Conversion
  Java'
og_title: 'Conversión de imágenes Java: CAD a TIFF con dimensiones personalizadas'
schemas:
- author: GroupDocs
  dateModified: '2026-07-24'
  description: 'Java image conversion made easy: learn how to convert CAD files to
    TIFF with custom dimensions using GroupDocs Conversion Java. Step‑by‑step guide
    for developers.'
  headline: 'Java Image Conversion: CAD to TIFF with Custom Dimensions'
  type: TechArticle
- questions:
  - answer: GroupDocs Conversion Java, a robust Java image conversion library.
    question: What library should I use for Java image conversion?
  - answer: Use `CadLoadOptions` and specify `setWidth()` and `setHeight()`.
    question: How do I set custom dimensions for a CAD file?
  - answer: Yes—load the CAD, set dimensions, then convert with `ImageConvertOptions`.
    question: Can I convert DWG to TIFF in one step?
  - answer: A free trial works for evaluation; a full license unlocks all features.
    question: Do I need a license?
  - answer: Any Java 8+ runtime is supported.
    question: What Java version is required?
  type: FAQPage
tags:
- convert CAD
- GroupDocs Conversion
- Java image conversion
- TIFF
- CAD processing
title: 'Conversión de imágenes Java: CAD a TIFF con dimensiones personalizadas'
type: docs
url: /es/java/cad-formats/cad-conversion-tiff-custom-dimensions-groupdocs-java/
weight: 1
---

# Conversión de Imágenes Java: CAD a TIFF con Dimensiones Personalizadas

Si necesita convertir dibujos CAD en imágenes TIFF de alta resolución mientras controla el ancho y alto exactos en píxeles, **java image conversion** es la clave. Usando GroupDocs Conversion Java, puede rasterizar cualquier formato CAD compatible (DWG, DGN, DXF, etc.) en un archivo TIFF que encaje perfectamente en informes, portales web o diseños de impresión. Esta guía lo lleva paso a paso—desde la configuración del proyecto hasta la conversión final—para que pueda integrar el proceso en cualquier flujo de trabajo basado en Java.

## Respuestas rápidas
- **¿Qué biblioteca debo usar para la conversión de imágenes Java?** GroupDocs Conversion Java, una biblioteca robusta de conversión de imágenes Java.  
- **¿Cómo establezco dimensiones personalizadas para un archivo CAD?** Use `CadLoadOptions` y especifique `setWidth()` y `setHeight()`.  
- **¿Puedo convertir DWG a TIFF en un solo paso?** Sí—cargue el CAD, establezca dimensiones y luego convierta con `ImageConvertOptions`.  
- **¿Necesito una licencia?** Una prueba gratuita sirve para evaluación; una licencia completa desbloquea todas las funciones.  
- **¿Qué versión de Java se requiere?** Cualquier runtime Java 8+ es compatible.

## ¿Qué es GroupDocs Conversion Java?
La biblioteca `GroupDocs Conversion Java` es una solución de **java image conversion** que soporta más de 110 formatos de entrada y salida, incluidos todos los principales tipos de CAD y de imágenes raster.  
La clase `Converter` es el componente central que inicia las operaciones de conversión de archivos.  
Proporciona renderizado del lado del servidor, escalado y opciones específicas de formato, permitiendo a los desarrolladores convertir archivos sin instalar visores de terceros.

## ¿Por qué convertir CAD a TIFF con dimensiones personalizadas?
Establecer ancho y alto explícitos garantiza que el TIFF resultante cumpla con las restricciones de diseño exactas de los sistemas posteriores. Al definir las dimensiones en píxeles antes de la rasterización, evita artefactos de escalado posteriores, mantiene la consistencia del grosor de línea y asegura que la imagen se integre sin problemas en PDFs, páginas web o material impreso sin procesamiento adicional. Este enfoque también simplifica las canalizaciones automatizadas donde cada imagen debe ajustarse a una especificación de tamaño predefinida.  

- **Preserva la fidelidad visual:** Rasterizar a 1920 × 1080 px (o cualquier tamaño que elija) mantiene los trazos y sombreados nítidos.  
- **Garantiza diseños consistentes:** Las imágenes se incrustan limpiamente en PDFs, páginas HTML o plantillas de impresión sin redimensionamiento adicional.  
- **Mejora la compatibilidad:** TIFF es universalmente aceptado en Windows, macOS, Linux y la mayoría de las herramientas de diseño, reduciendo los problemas de conversión de formatos.

## Requisitos previos
1. **GroupDocs Conversion Java** versión 25.2 o posterior (se recomienda la última versión).  
2. Un IDE Java como IntelliJ IDEA o Eclipse.  
3. Maven instalado para la gestión de dependencias.  
4. Conocimientos básicos de programación Java y familiaridad con el `pom.xml` de Maven.  

## Configuración de GroupDocs Conversion Java

Agregue la dependencia de GroupDocs Maven a su `pom.xml`:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-conversion</artifactId>
    <version>25.2</version>
</dependency>
```

**Adquisición de licencia:** Puede obtener una prueba gratuita, solicitar una licencia temporal para funcionalidad completa, o comprar una licencia permanente para desbloquear totalmente las funciones de GroupDocs Conversion.

Una vez que su proyecto Java esté vinculado correctamente con estas dependencias, ¡está listo para comenzar a convertir archivos CAD!

```xml
<repositories>
    <repository>
        <id>repository.groupdocs.com</id>
        <name>GroupDocs Repository</name>
        <url>https://releases.groupdocs.com/conversion/java/</url>
    </repository>
</repositories>
<dependencies>
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-conversion</artifactId>
        <version>25.2</version>
    </dependency>
</dependencies>
```

## Cómo convertir CAD a TIFF con dimensiones personalizadas?

Convertir archivos CAD a TIFF con dimensiones precisas implica cargar el dibujo fuente, configurar opciones de renderizado e invocar la API de conversión. Siguiendo una secuencia lineal—estableciendo ancho y alto, eligiendo TIFF como formato de salida y ejecutando la conversión—se asegura que la imagen generada cumpla con los requisitos exactos de tamaño de sus aplicaciones posteriores, mientras preserva el detalle y la calidad del dibujo original.  

1. **Importe las clases requeridas** (ver paso a paso a continuación).  
2. **Cree una instancia de `CadLoadOptions`** y establezca `width` y `height` a sus dimensiones objetivo.  
3. **Instancie `ImageConvertOptions`**, especificando `ImageFileType.Tiff`.  
4. **Llame al método `convert`** en un objeto `Converter`, pasando la ruta de origen, las opciones de carga y las opciones de conversión.

### Carga de documentos CAD con dimensiones personalizadas (Cómo establecer dimensiones)

La clase `CadLoadOptions` indica a GroupDocs cómo rasterizar el dibujo antes de la conversión.

`CadLoadOptions` es el objeto de configuración que define parámetros de renderizado como ancho, alto y DPI para archivos CAD.

#### Paso 1: Importar bibliotecas necesarias
```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.filetypes.ImageFileType;
import com.groupdocs.conversion.options.convert.ImageConvertOptions;
import com.groupdocs.conversion.options.load.CadLoadOptions;
```

#### Paso 2: Configurar opciones de carga con dimensiones personalizadas
```java
String sourceDocumentPath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DWG_WITH_LAYOUTS_AND_LAYERS";
CadLoadOptions loadOptions = new CadLoadOptions();
loadOptions.setWidth(1920); // Specify the desired width in pixels
loadOptions.setHeight(1080); // Specify the desired height in pixels
Converter converter = new Converter(sourceDocumentPath, () -> loadOptions);
```
*Explicación:* Al configurar `CadLoadOptions`, le indica a **GroupDocs Conversion Java** que rasterice el dibujo CAD a 1920 × 1080 píxeles antes de cualquier procesamiento adicional.

### Conversión de CAD a imagen TIFF (Convertir CAD a TIFF)

`ImageConvertOptions` dirige la biblioteca para producir un archivo TIFF con los ajustes que especifique.

`ImageConvertOptions` encapsula todos los parámetros de conversión específicos de imagen, incluido el formato de salida, la resolución y el nivel de compresión.

#### Paso 3: Configurar opciones de conversión
```java
String convertedFilePath = "YOUR_OUTPUT_DIRECTORY/ConvertCadAndSpecifyWidthAndHeight.tiff";
ImageConvertOptions options = new ImageConvertOptions();
options.setFormat(ImageFileType.Tiff); // Set the conversion target to TIFF format
```

#### Paso 4: Realizar la conversión
```java
converter.convert(convertedFilePath, options);
```
*Explicación:* Establecer `ImageFileType.Tiff` indica a **GroupDocs Conversion Java** que genere un archivo TIFF de alta calidad que respete el ancho y alto que definió anteriormente.

## Consejos de solución de problemas y errores comunes
- **Problemas con la ruta del archivo:** Verifique que tanto las rutas de origen como de destino sean correctas y que la aplicación tenga permisos de lectura/escritura.  
- **Formatos no compatibles:** Asegúrese de que el archivo CAD sea uno de los formatos compatibles (DWG, DGN, DXF, etc.).  
- **Restricciones de memoria:** Los dibujos grandes pueden requerir aumentar el tamaño del heap de JVM (`-Xmx2g` o superior).  
- **Problemas de calidad:** Ajuste la configuración de resolución de `ImageConvertOptions` si el DPI predeterminado no cumple con sus estándares de calidad.  

## Aplicaciones prácticas
1. **Visualización arquitectónica:** Exportar planos de planta como TIFF para presentaciones de alta resolución.  
2. **Documentación de ingeniería:** Generar imágenes estandarizadas para incluir en manuales técnicos.  
3. **Informes automatizados:** Incrustar TIFF derivados de CAD en informes PDF o HTML mediante una canalización CI.  

## Consideraciones de rendimiento
- **Optimizar el uso de memoria:** Libere la instancia `Converter` después de la conversión (`converter.close()` si corresponde).  
- **Procesamiento por lotes:** Recorrer una lista de archivos CAD y reutilizar una única configuración `Converter` para reducir la sobrecarga.  
- **Manténgase actualizado:** Actualice regularmente a la última versión de GroupDocs Conversion Java para beneficiarse de mejoras de rendimiento y correcciones de errores.  

## Preguntas frecuentes

**Q:** ¿Qué formatos de archivo admite GroupDocs Conversion?  
**A:** Soporta más de 110 formatos, incluidos archivos CAD como DWG, DGN, DXF, así como tipos comunes de imágenes, documentos y archivos.

**Q:** ¿Puedo convertir varios archivos CAD a la vez?  
**A:** Sí—implemente un bucle simple que cree un nuevo `Converter` para cada archivo o reutilice la misma instancia con diferentes rutas de origen.

**Q:** ¿Cómo manejo archivos de gran tamaño durante la conversión?  
**A:** Aumente el tamaño del heap de JVM, procese los archivos en lotes más pequeños o use opciones de transmisión proporcionadas por la biblioteca.

**Q:** ¿Qué pasa si la calidad de la imagen de salida no es satisfactoria?  
**A:** Ajuste el DPI o la configuración de escalado en `ImageConvertOptions` para aumentar la resolución.

**Q:** ¿Está disponible el soporte si encuentro problemas?  
**A:** GroupDocs ofrece documentación extensa, foros de la comunidad y soporte directo para clientes con licencia.

## Recursos
- [Documentación de GroupDocs](https://docs.groupdocs.com/conversion/java/)
- [Referencia de API](https://reference.groupdocs.com/conversion/java/)
- [Descargar la última versión](https://releases.groupdocs.com/conversion/java/)
- [Comprar licencias](https://purchase.groupdocs.com/buy)
- [Acceso a prueba gratuita](https://releases.groupdocs.com/conversion/java/)
- [Solicitud de licencia temporal](https://purchase.groupdocs.com/temporary-license/)
- [Foro de soporte](https://forum.groupdocs.com/c/conversion/10)

---

**Última actualización:** 2026-07-24  
**Probado con:** GroupDocs Conversion Java 25.2  
**Autor:** GroupDocs  

---

## Tutoriales relacionados

- [convert cad pdf java – Tutoriales de conversión de formatos CAD para GroupDocs.Conversion Java](/conversion/java/cad-formats/)
- [convert pdf to jpg java usando GroupDocs.Conversion – Guía](/conversion/java/document-operations/convert-pdf-to-jpg-groupdocs-java/)
- [Cómo configurar la licencia para GroupDocs.Conversion Java - Guía paso a paso](/conversion/java/getting-started/groupdocs-conversion-java-license-setup-file-path/)