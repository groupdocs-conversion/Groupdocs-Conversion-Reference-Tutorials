---
"description": "Erfahren Sie, wie Sie PowerPoint-Präsentationen (PPTX) mit GroupDocs.Conversion für .NET in das PDF-Format konvertieren. Einfacher und effizienter Konvertierungsprozess."
"linktitle": "Konvertieren Sie PPTX in PDF"
"second_title": "GroupDocs.Conversion .NET API"
"title": "Konvertieren Sie PPTX in PDF"
"url": "/de/net/pdf-conversion/convert-pptx-to-pdf/"
"weight": 29
---

# Konvertieren Sie PPTX in PDF

## Einführung
In diesem Tutorial erfahren Sie, wie Sie eine PowerPoint-Präsentation (PPTX) mithilfe der GroupDocs.Conversion-Bibliothek für .NET in ein Portable Document Format (PDF) konvertieren. Folgen Sie dazu den unten stehenden Schritten.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:
1. GroupDocs.Conversion für .NET-Bibliothek: Stellen Sie sicher, dass Sie die GroupDocs.Conversion für .NET-Bibliothek installiert haben. Sie können sie herunterladen von [Hier](https://releases.groupdocs.com/conversion/net/).
2. Entwicklungsumgebung: Richten Sie eine Entwicklungsumgebung mit den erforderlichen Tools wie Visual Studio oder einer anderen .NET-IDE ein.

## Namespaces importieren
Fügen Sie die erforderlichen Namespaces in Ihr Projekt ein, um auf die GroupDocs.Conversion-Funktionen zuzugreifen.
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Schritt 1: Ausgabeordner und Dateinamen festlegen
Definieren Sie zunächst den Ausgabeordner, in dem die konvertierte PDF-Datei gespeichert wird, und geben Sie den Namen der PDF-Ausgabedatei an.
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "pptx-converted-to.pdf");
```
## Schritt 2: Laden Sie die Quell-PPTX-Datei
Laden Sie die Quelldatei der PowerPoint-Präsentation (PPTX) mithilfe der Bibliothek GroupDocs.Conversion.
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PPTX))
{
    // Die Konvertierungslogik wird hier platziert
}
```
## Schritt 3: Konvertierungsoptionen festlegen
Definieren Sie die Konvertierungsoptionen. In diesem Fall konvertieren wir in das PDF-Format. Erstellen Sie daher eine Instanz von `PdfConvertOptions`.
```csharp
var options = new PdfConvertOptions();
```
## Schritt 4: Führen Sie die Konvertierung durch
Führen Sie den Konvertierungsvorgang mit dem `Convert` Methode und übergeben Sie den Ausgabedateipfad zusammen mit den Konvertierungsoptionen.
```csharp
converter.Convert(outputFile, options);
```
## Schritt 5: Ausgabe prüfen
Nachdem die Konvertierung erfolgreich abgeschlossen wurde, wird eine Meldung angezeigt, die den Abschluss und den Speicherort der Ausgabedatei angibt.
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```

## Abschluss
In diesem Tutorial haben wir gelernt, wie man eine PowerPoint-Präsentation (PPTX) mithilfe der Bibliothek GroupDocs.Conversion für .NET in ein Portable Document Format (PDF) konvertiert. Mit den oben beschriebenen Schritten können Sie diese Konvertierung problemlos in Ihren .NET-Anwendungen durchführen.
## Häufig gestellte Fragen
### F: Ist GroupDocs.Conversion mit allen Versionen von .NET kompatibel?
A: Ja, GroupDocs.Conversion unterstützt .NET Framework 2.0 und höher, einschließlich .NET Core und .NET Standard.
### F: Kann ich Dateien in andere Formate als PDF konvertieren?
A: Ja, GroupDocs.Conversion unterstützt eine breite Palette von Dokumentformaten für die Konvertierung, darunter Word, Excel, HTML und mehr.
### F: Bietet GroupDocs.Conversion eine kostenlose Testversion an?
A: Ja, Sie können auf eine kostenlose Testversion von GroupDocs.Conversion zugreifen von [Hier](https://releases.groupdocs.com/).
### F: Wie erhalte ich Support für GroupDocs.Conversion?
A: Sie erhalten Unterstützung im GroupDocs-Community-Forum [Hier](https://forum.groupdocs.com/c/conversion/11).
### F: Ist für GroupDocs.Conversion eine temporäre Lizenz verfügbar?
A: Ja, Sie können eine temporäre Lizenz für GroupDocs.Conversion erhalten von [Hier](https://purchase.groupdocs.com/temporary-license/).