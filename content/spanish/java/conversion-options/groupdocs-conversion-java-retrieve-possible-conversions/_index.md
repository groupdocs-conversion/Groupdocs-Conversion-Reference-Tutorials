---
date: '2026-07-29'
description: Descubra cómo listar formatos y obtener todas las conversiones posibles
  usando GroupDocs.Conversion for Java, ideal para flujos de trabajo de conversión
  de archivos en almacenamiento en la nube.
keywords:
- how to list formats
- cloud storage file conversion
- GroupDocs.Conversion Java
lastmod: '2026-07-29'
og_description: Aprenda cómo listar formatos y obtener todas las conversiones posibles
  usando GroupDocs.Conversion for Java. Ideal para pipelines de conversión de archivos
  en almacenamiento en la nube.
og_image_alt: 'Guide: List formats and get conversion matrix with GroupDocs.Conversion
  Java'
og_title: Cómo listar formatos con GroupDocs.Conversion for Java
schemas:
- author: GroupDocs
  dateModified: '2026-07-29'
  description: Discover how to list formats and retrieve all possible conversions
    using GroupDocs.Conversion for Java, ideal for cloud storage file conversion workflows.
  headline: How to List Formats with GroupDocs.Conversion for Java
  type: TechArticle
- description: Discover how to list formats and retrieve all possible conversions
    using GroupDocs.Conversion for Java, ideal for cloud storage file conversion workflows.
  name: How to List Formats with GroupDocs.Conversion for Java
  steps:
  - name: '**Dynamic Format Detection:** When a file lands in cloud storage, you can
      instantly query whether the desired target format is supported.'
    text: '**Dynamic Format Detection:** When a file lands in cloud storage, you can
      instantly query whether the desired target format is supported.'
  - name: '**Batch Migration:** Move large document libraries to a unified format
      (e.g., PDF/A) by iterating over supported source types.'
    text: '**Batch Migration:** Move large document libraries to a unified format
      (e.g., PDF/A) by iterating over supported source types.'
  - name: '**User‑Driven Export:** Offer end‑users a dropdown of only the formats
      their current document can be exported to, reducing errors and improving UX.'
    text: '**User‑Driven Export:** Offer end‑users a dropdown of only the formats
      their current document can be exported to, reducing errors and improving UX.'
  type: HowTo
- questions:
  - answer: It is a server‑side library that supports 200+ input and 200+ output formats,
      enabling fast, license‑free document conversion without external software.
    question: What is GroupDocs.Conversion for Java?
  - answer: Set up your Maven project, add the dependency shown earlier, load a license
      file, and instantiate the `Converter` class as demonstrated in the initialization
      section.
    question: How do I start with GroupDocs.Conversion?
  - answer: Yes—through the API’s extensibility points you can register custom converters
      or plug‑in third‑party handlers for proprietary formats.
    question: Can I convert custom file types using GroupDocs.Conversion?
  - answer: Forgetting to close the `Converter`, using an old JAR version, or overlooking
      memory usage for very large PDFs. Follow the resource‑management tips above.
    question: What are common pitfalls when implementing conversions?
  - answer: Visit the official [documentation](https://docs.groupdocs.com/conversion/java/)
      or ask questions in the GroupDocs community forum.
    question: Where can I get more help?
  type: FAQPage
tags:
- convert formats
- GroupDocs.Conversion
- Java document conversion
- cloud storage conversion
title: Cómo listar formatos con GroupDocs.Conversion for Java
type: docs
url: /es/java/conversion-options/groupdocs-conversion-java-retrieve-possible-conversions/
weight: 1
---

# Cómo listar formatos y recuperar todas las conversiones posibles con GroupDocs.Conversion para Java

En muchos proyectos de procesamiento de documentos, el primer paso es saber **cómo listar formatos** que admite el motor de conversión. Este tutorial le muestra, paso a paso, cómo consultar GroupDocs.Conversion para Java, recuperar cada par origen‑destino y aplicar ese conocimiento en canalizaciones de conversión de archivos en almacenamiento en la nube. Al final tendrá un método reutilizable que devuelve la matriz completa de conversiones, además de consejos prácticos para el rendimiento y el manejo de errores.

## Respuestas rápidas
- **¿Qué significa “list formats”?** Devuelve cada par de conversión origen‑destino que la biblioteca puede manejar.  
- **¿Necesito una licencia?** Una prueba gratuita funciona para pruebas; se requiere una licencia de pago para producción.  
- **¿Puede esto ayudar en la conversión de archivos en almacenamiento en la nube?** Sí—conocer los formatos compatibles le permite automatizar conversiones en canalizaciones de almacenamiento en la nube.  
- **¿Qué versión de Java se requiere?** JDK 8 o posterior.  
- **¿Es la característica segura para subprocesos?** La instancia `Converter` puede reutilizarse entre hilos, pero libere los recursos después de su uso.

## ¿Qué es “cómo listar formatos” en GroupDocs.Conversion?
La operación **list formats** devuelve una colección que describe cada formato de origen junto con los formatos de destino a los que puede transformarse. Esta matriz se genera a partir de las reglas internas de conversión de la biblioteca y es esencial para crear flujos de trabajo dinámicos que se adapten a las capacidades reales de GroupDocs.Conversion en tiempo de ejecución.

## ¿Por qué usar GroupDocs.Conversion para Java?
GroupDocs.Conversion para Java admite **más de 200 formatos de entrada** y **más de 200 formatos de salida**, cubriendo todo desde DOCX y PPTX hasta PDF/A y tipos de imagen. Se ejecuta completamente en el servidor, por lo que no se requieren productos de Microsoft Office o Adobe. La API es segura para subprocesos, puede procesar documentos de cientos de páginas sin cargar todo el archivo en memoria, e integra sin problemas con servicios de almacenamiento en la nube como AWS S3, Azure Blob y Google Cloud Storage.

## Requisitos previos
- **Java Development Kit (JDK):** Versión 8 o posterior.  
- **Maven:** Configurado correctamente en su IDE (IntelliJ IDEA, Eclipse, NetBeans, etc.).  
- **GroupDocs.Conversion para Java:** Añadido como dependencia Maven (ver más abajo).  

## Configuración de GroupDocs.Conversion para Java

Agregue el repositorio de GroupDocs y la dependencia a su `pom.xml`:

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

### Obtención de licencia
Comience con una prueba gratuita para explorar la API. Para cargas de trabajo en producción, adquiera una licencia o solicite una licencia de evaluación temporal.

### Inicialización y configuración básicas

```java
import com.groupdocs.conversion.Converter;

public class ConversionSetup {
    public static void main(String[] args) {
        // Initialize the Converter object
        Converter converter = new Converter();
        
        System.out.println("GroupDocs.Conversion for Java has been initialized successfully.");
    }
}
```

## Cómo listar formatos usando GroupDocs.Conversion para Java
`Converter` es la clase central que realiza conversiones y proporciona información de formatos. `getAllPossibleConversions()` devuelve una lista de todos los pares de conversión origen‑destino compatibles. `ConversionInfo` representa un mapeo de conversión único entre un formato de origen y uno de destino.  

Cargue el motor `Converter`, llame a `getAllPossibleConversions()` y recibirá una lista de objetos `ConversionInfo` que describen cada par origen‑destino permitido. Esta única llamada es todo lo que necesita para crear un menú desplegable de opciones de exportación, validar archivos entrantes o diseñar scripts de migración por lotes.

### Inicializar y obtener conversiones
La clase `Converter` es el motor central que brinda capacidades de conversión y expone el método `getAllPossibleConversions()`.

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.contracts.PossibleConversions;

public class GetAllPossibleConversionsFeature {
    public static void run() {
        // Initialize the Converter object
        Converter converter = new Converter();
```

### Iterar sobre conversiones posibles

```java
// Retrieve all possible conversions supported by the library
for (PossibleConversions conversions : converter.getAllPossibleConversions()) {
    // Print source format description
    System.out.print(String.format("Source format: %s \n", conversions.getSource().getDescription()));
```

### Determinar tipos de conversión

```java
// Iterate through each target conversion available for the source format
for (TargetConversion conversion : conversions.getAll()) {
    // Determine if it's a primary or secondary conversion and print details
    System.out.print(String.format("\t...can be converted to %s format as %s conversion.\n",
            conversion.getFormat(),
            conversion.isPrimary() ? "primary" : "secondary"));
}
```

### Función completa

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.contracts.PossibleConversions;
import com.groupdocs.conversion.contracts.TargetConversion;

public class GetAllPossibleConversionsFeature {
    public static void run() {
        // Initialize the Converter object
        Converter converter = new Converter();

        // Retrieve all possible conversions supported by the library
        for (PossibleConversions conversions : converter.getAllPossibleConversions()) {
            // Print source format description
            System.out.print(String.format("Source format: %s \n", conversions.getSource().getDescription()));

            // Iterate through each target conversion available for the source format
            for (TargetConversion conversion : conversions.getAll()) {
                // Determine if it's a primary or secondary conversion and print details
                System.out.print(String.format("\t...can be converted to %s format as %s conversion.\n",
                        conversion.getFormat(),
                        conversion.isPrimary() ? "primary" : "secondary"));
            }
        }
    }
}
```

## Casos de uso de conversión de archivos en almacenamiento en la nube
Conocer la matriz completa de conversiones es especialmente valioso al crear servicios de **conversión de archivos en almacenamiento en la nube**:

1. **Detección dinámica de formatos:** Cuando un archivo llega al almacenamiento en la nube, puede consultar instantáneamente si el formato de destino deseado es compatible.  
2. **Migración por lotes:** Mueva grandes bibliotecas de documentos a un formato unificado (p.ej., PDF/A) iterando sobre los tipos de origen compatibles.  
3. **Exportación guiada por el usuario:** Ofrezca a los usuarios finales un menú desplegable solo con los formatos a los que su documento actual puede exportarse, reduciendo errores y mejorando la experiencia de usuario.

## Consideraciones de rendimiento
- **Gestión de recursos:** Libere la instancia `Converter` o use try‑with‑resources si crea muchos convertidores de corta duración.  
- **Procesamiento por lotes:** Agrupe varios archivos en un solo trabajo para reducir la sobrecarga.  
- **Caché:** Almacene en caché el resultado de `getAllPossibleConversions()` si lo consulta con frecuencia; la matriz de conversiones rara vez cambia en tiempo de ejecución.  

## Problemas comunes y soluciones
| Síntoma | Causa probable | Solución |
|---------|----------------|----------|
| No aparece salida | `Converter` no inicializado correctamente | Asegúrese de que el JAR de la biblioteca esté en el classpath y la licencia esté cargada. |
| La lista `TargetConversion` está vacía | Uso de una versión de biblioteca obsoleta | Actualice a la última versión de GroupDocs.Conversion. |
| Picos de memoria en documentos grandes | No liberar los recursos del convertidor | Llame a `converter.close()` o use try‑with‑resources. |

## Preguntas frecuentes

**P: ¿Qué es GroupDocs.Conversion para Java?**  
R: Es una biblioteca del lado del servidor que admite más de 200 formatos de entrada y más de 200 formatos de salida, permitiendo una conversión de documentos rápida y sin licencia sin software externo.

**P: ¿Cómo comienzo con GroupDocs.Conversion?**  
R: Configure su proyecto Maven, añada la dependencia mostrada anteriormente, cargue un archivo de licencia e instancie la clase `Converter` como se muestra en la sección de inicialización.

**P: ¿Puedo convertir tipos de archivo personalizados usando GroupDocs.Conversion?**  
R: Sí—a través de los puntos de extensibilidad de la API puede registrar convertidores personalizados o integrar manejadores de terceros para formatos propietarios.

**P: ¿Cuáles son los errores comunes al implementar conversiones?**  
R: Olvidar cerrar el `Converter`, usar una versión antigua del JAR o pasar por alto el uso de memoria para PDFs muy grandes. Siga los consejos de gestión de recursos anteriores.

**P: ¿Dónde puedo obtener más ayuda?**  
R: Visite la [documentación](https://docs.groupdocs.com/conversion/java/) oficial o haga preguntas en el foro de la comunidad de GroupDocs.

---

**Última actualización:** 2026-07-29  
**Probado con:** GroupDocs.Conversion 25.2 para Java  
**Autor:** GroupDocs

## Tutoriales relacionados

- [Convertir Word a PDF y otros formatos de archivo con GroupDocs.Conversion para Java](/conversion/java/)
- [Word a PDF Java – Ocultar cambios rastreados y opciones de conversión](/conversion/java/conversion-options/)
- [Cómo rastrear el progreso de la conversión en Java con GroupDocs - Guía completa](/conversion/java/conversion-events-logging/java-groupdocs-conversion-progress-listener/)