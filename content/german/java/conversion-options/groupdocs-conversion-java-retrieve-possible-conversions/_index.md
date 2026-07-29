---
date: '2026-07-29'
description: Entdecken Sie, wie Sie Formate auflisten und alle möglichen Konvertierungen
  mit GroupDocs.Conversion for Java abrufen, ideal für cloud storage file conversion
  workflows.
keywords:
- how to list formats
- cloud storage file conversion
- GroupDocs.Conversion Java
lastmod: '2026-07-29'
og_description: Erfahren Sie, wie Sie Formate auflisten und alle möglichen Konvertierungen
  mit GroupDocs.Conversion for Java abrufen. Ideal für cloud storage file conversion
  pipelines.
og_image_alt: 'Guide: List formats and get conversion matrix with GroupDocs.Conversion
  Java'
og_title: Wie man Formate mit GroupDocs.Conversion for Java auflistet
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
title: Wie man Formate mit GroupDocs.Conversion for Java auflistet
type: docs
url: /de/java/conversion-options/groupdocs-conversion-java-retrieve-possible-conversions/
weight: 1
---

# Wie man Formate auflistet und alle möglichen Konvertierungen mit GroupDocs.Conversion für Java abruft

In vielen Dokumenten‑Verarbeitungsprojekten ist der erste Schritt zu wissen, **wie man Formate auflistet**, die die Konvertierungs‑Engine unterstützt. Dieses Tutorial zeigt Ihnen Schritt für Schritt, wie Sie GroupDocs.Conversion für Java abfragen, jedes Quell‑zu‑Ziel‑Paar abrufen und dieses Wissen in Cloud‑Speicher‑Dateikonvertierungs‑Pipelines anwenden. Am Ende haben Sie eine wiederverwendbare Methode, die die vollständige Konvertierungsmatrix zurückgibt, plus praktische Tipps für Leistung und Fehlerbehandlung.

## Schnelle Antworten
- **Was bedeutet „list formats“?** Sie gibt jedes Quell‑zu‑Ziel‑Konvertierungspaar zurück, das die Bibliothek verarbeiten kann.  
- **Brauche ich eine Lizenz?** Eine kostenlose Testversion funktioniert zum Testen; für die Produktion ist eine kostenpflichtige Lizenz erforderlich.  
- **Kann das bei der Cloud‑Speicher‑Dateikonvertierung helfen?** Ja – das Wissen über unterstützte Formate ermöglicht die Automatisierung von Konvertierungen in Cloud‑Speicher‑Pipelines.  
- **Welche Java‑Version wird benötigt?** JDK 8 oder neuer.  
- **Ist die Funktion thread‑sicher?** Die `Converter`‑Instanz kann über Threads hinweg wiederverwendet werden, aber Ressourcen nach Gebrauch freigeben.

## Was bedeutet „how to list formats“ in GroupDocs.Conversion?
Der **list formats**‑Vorgang gibt eine Sammlung zurück, die jedes Quellformat zusammen mit den Zielformaten beschreibt, in die es umgewandelt werden kann. Diese Matrix wird aus den internen Konvertierungsregeln der Bibliothek generiert und ist entscheidend für den Aufbau dynamischer Workflows, die sich zur Laufzeit an die tatsächlichen Fähigkeiten von GroupDocs.Conversion anpassen.

## Warum GroupDocs.Conversion für Java verwenden?
GroupDocs.Conversion für Java unterstützt **200+ Eingabeformate** und **200+ Ausgabeformate**, von DOCX und PPTX bis hin zu PDF/A und Bildtypen. Es läuft vollständig auf dem Server, sodass keine Microsoft‑Office‑ oder Adobe‑Produkte erforderlich sind. Die API ist thread‑sicher, kann Dokumente mit mehreren hundert Seiten verarbeiten, ohne die gesamte Datei in den Speicher zu laden, und lässt sich nahtlos in Cloud‑Speicherdienste wie AWS S3, Azure Blob und Google Cloud Storage integrieren.

## Voraussetzungen
- **Java Development Kit (JDK):** Version 8 oder neuer.  
- **Maven:** Richtig in Ihrer IDE (IntelliJ IDEA, Eclipse, NetBeans usw.) konfiguriert.  
- **GroupDocs.Conversion für Java:** Als Maven‑Abhängigkeit hinzugefügt (siehe unten).  

## Einrichtung von GroupDocs.Conversion für Java

Add the GroupDocs repository and dependency to your `pom.xml`:

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

### Lizenzbeschaffung
Beginnen Sie mit einer kostenlosen Testversion, um die API zu erkunden. Für Produktionsumgebungen erwerben Sie eine Lizenz oder fordern Sie eine temporäre Evaluierungslizenz an.

### Grundlegende Initialisierung und Einrichtung

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

## Wie man Formate mit GroupDocs.Conversion für Java auflistet
`Converter` ist die Kernklasse, die Konvertierungen durchführt und Formatinformationen bereitstellt. `getAllPossibleConversions()` gibt eine Liste aller unterstützten Quell‑zu‑Ziel‑Konvertierungspaare zurück. `ConversionInfo` repräsentiert eine einzelne Konvertierungszuordnung zwischen einem Quell‑ und einem Zielformat.

Laden Sie die `Converter`‑Engine, rufen Sie `getAllPossibleConversions()` auf, und Sie erhalten eine Liste von `ConversionInfo`‑Objekten, die jedes zulässige Quell‑zu‑Ziel‑Paar beschreiben. Dieser einzelne Aufruf reicht aus, um ein Dropdown mit Exportoptionen zu erstellen, eingehende Dateien zu validieren oder Batch‑Migrations‑Skripte zu entwerfen.

### Initialisieren und Konvertierungen abrufen

The `Converter` class is the core engine that provides conversion capabilities and exposes the `getAllPossibleConversions()` method.  

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.contracts.PossibleConversions;

public class GetAllPossibleConversionsFeature {
    public static void run() {
        // Initialize the Converter object
        Converter converter = new Converter();
```

### Durch mögliche Konvertierungen iterieren

```java
// Retrieve all possible conversions supported by the library
for (PossibleConversions conversions : converter.getAllPossibleConversions()) {
    // Print source format description
    System.out.print(String.format("Source format: %s \n", conversions.getSource().getDescription()));
```

### Konvertierungstypen bestimmen

```java
// Iterate through each target conversion available for the source format
for (TargetConversion conversion : conversions.getAll()) {
    // Determine if it's a primary or secondary conversion and print details
    System.out.print(String.format("\t...can be converted to %s format as %s conversion.\n",
            conversion.getFormat(),
            conversion.isPrimary() ? "primary" : "secondary"));
}
```

### Vollständige Funktion

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

## Anwendungsfälle für Cloud‑Speicher‑Dateikonvertierung
Das Wissen über die vollständige Konvertierungsmatrix ist besonders wertvoll beim Aufbau von **Cloud‑Speicher‑Dateikonvertierungs**‑Diensten:

1. **Dynamische Format-Erkennung:** Wenn eine Datei im Cloud‑Speicher landet, können Sie sofort abfragen, ob das gewünschte Zielformat unterstützt wird.  
2. **Batch‑Migration:** Große Dokumentenbibliotheken in ein einheitliches Format (z. B. PDF/A) verschieben, indem Sie über unterstützte Quelltypen iterieren.  
3. **Benutzer‑gesteuerter Export:** Endbenutzern ein Dropdown nur der Formate anbieten, in die ihr aktuelles Dokument exportiert werden kann, wodurch Fehler reduziert und die Benutzererfahrung verbessert wird.

## Leistungsüberlegungen
- **Ressourcenverwaltung:** Die `Converter`‑Instanz freigeben oder try‑with‑resources verwenden, wenn Sie viele kurzlebige Converter erstellen.  
- **Batch‑Verarbeitung:** Mehrere Dateien zu einem einzigen Job zusammenfassen, um Overhead zu reduzieren.  
- **Caching:** Das Ergebnis von `getAllPossibleConversions()` zwischenspeichern, wenn Sie es häufig abfragen; die Konvertierungsmatrix ändert sich zur Laufzeit selten.  

## Häufige Probleme und Lösungen
| Symptom | Wahrscheinliche Ursache | Lösung |
|---------|--------------------------|--------|
| Keine Ausgabe erscheint | `Converter` nicht korrekt initialisiert | Stellen Sie sicher, dass die Bibliotheks‑JAR im Klassenpfad ist und die Lizenz geladen wurde. |
| `TargetConversion`‑Liste ist leer | Verwendung einer veralteten Bibliotheksversion | Auf die neueste GroupDocs.Conversion‑Version aktualisieren. |
| Speicherspitzen bei großen Dokumenten | Converter‑Ressourcen werden nicht freigegeben | `converter.close()` aufrufen oder try‑with‑resources verwenden. |

## Häufig gestellte Fragen

**Q: Was ist GroupDocs.Conversion für Java?**  
A: Es ist eine serverseitige Bibliothek, die 200+ Eingabe‑ und 200+ Ausgabeformate unterstützt und schnelle, lizenzfreie Dokumentkonvertierung ohne externe Software ermöglicht.

**Q: Wie beginne ich mit GroupDocs.Conversion?**  
A: Richten Sie Ihr Maven‑Projekt ein, fügen Sie die zuvor gezeigte Abhängigkeit hinzu, laden Sie eine Lizenzdatei und instanziieren Sie die `Converter`‑Klasse wie im Abschnitt zur Initialisierung gezeigt.

**Q: Kann ich benutzerdefinierte Dateitypen mit GroupDocs.Conversion konvertieren?**  
A: Ja – über die Erweiterungspunkte der API können Sie benutzerdefinierte Converter registrieren oder Drittanbieter‑Handler für proprietäre Formate einbinden.

**Q: Was sind häufige Stolperfallen bei der Implementierung von Konvertierungen?**  
A: Das Vergessen, den `Converter` zu schließen, die Verwendung einer alten JAR‑Version oder das Übersehen des Speicherverbrauchs bei sehr großen PDFs. Befolgen Sie die oben genannten Tipps zur Ressourcenverwaltung.

**Q: Wo kann ich weitere Hilfe erhalten?**  
A: Besuchen Sie die offizielle [Dokumentation](https://docs.groupdocs.com/conversion/java/) oder stellen Sie Fragen im GroupDocs‑Community‑Forum.

---  
**Zuletzt aktualisiert:** 2026-07-29  
**Getestet mit:** GroupDocs.Conversion 25.2 für Java  
**Autor:** GroupDocs

## Verwandte Tutorials

- [Word in PDF und andere Dateiformate mit GroupDocs.Conversion für Java konvertieren](/conversion/java/)
- [Word zu PDF Java – Änderungen nachverfolgen ausblenden & Konvertierungsoptionen](/conversion/java/conversion-options/)
- [Wie man den Konvertierungsfortschritt in Java mit GroupDocs verfolgt – Ein vollständiger Leitfaden](/conversion/java/conversion-events-logging/java-groupdocs-conversion-progress-listener/)