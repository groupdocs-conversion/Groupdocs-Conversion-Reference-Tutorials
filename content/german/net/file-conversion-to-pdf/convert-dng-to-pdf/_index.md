---
"description": "Erfahren Sie, wie Sie DNG-Bilder mit GroupDocs.Conversion für .NET mühelos in PDF konvertieren. Folgen Sie unserer Schritt-für-Schritt-Anleitung für eine reibungslose Konvertierung."
"linktitle": "Konvertieren Sie DNG-Bilder in PDF"
"second_title": "GroupDocs.Conversion .NET API"
"title": "Konvertieren Sie DNG-Bilder in PDF"
"url": "/de/net/file-conversion-to-pdf/convert-dng-to-pdf/"
"weight": 21
---

# Konvertieren Sie DNG-Bilder in PDF

## Einführung
In diesem Tutorial führen wir Sie durch die Konvertierung von DNG-Bildern in PDF mit GroupDocs.Conversion für .NET. DNG (Digital Negative) ist ein Dateiformat für die digitale Fotografie. Durch die Konvertierung von DNG-Bildern in PDF können Sie diese einfach in einem allgemein akzeptierten Format teilen oder speichern.
## Voraussetzungen
Bevor Sie beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:
1. GroupDocs.Conversion für .NET: Laden Sie die GroupDocs.Conversion-Bibliothek für .NET herunter und installieren Sie sie von [Hier](https://releases.groupdocs.com/conversion/net/).
2. Quell-DNG-Datei: Sie benötigen eine DNG-Bilddatei, die Sie in PDF konvertieren möchten.
3. Entwicklungsumgebung: Stellen Sie sicher, dass Sie eine .NET-Entwicklungsumgebung eingerichtet haben.

## Namespaces importieren
Zunächst müssen Sie die erforderlichen Namespaces in Ihr Projekt importieren. Fügen Sie Ihrer Codedatei die folgenden using-Direktiven hinzu:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Schritt 1: Laden Sie die Quell-DNG-Datei
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "dng-converted-to.pdf");
// Laden Sie die Quell-DNG-Datei
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_DNG))
{
    // Fahren Sie mit dem Konvertierungsprozess fort
}
```
In diesem Schritt definieren Sie den Ausgabeordner, in dem die konvertierte PDF-Datei gespeichert wird. Ersetzen Sie `"Your Document Directory"` mit dem Pfad zu Ihrem gewünschten Verzeichnis. Anschließend geben Sie den Namen und Pfad der Ausgabe-PDF-Datei an.
## Schritt 2: DNG in PDF konvertieren
```csharp
var options = new PdfConvertOptions();
// Konvertierte PDF-Datei speichern
converter.Convert(outputFile, options);
```
Hier erstellen Sie eine Instanz von `PdfConvertOptions` um bei Bedarf spezielle Optionen für die PDF-Konvertierung festzulegen. Anschließend rufen Sie die `Convert` Methode der `converter` Objekt, wobei der Ausgabedateipfad und die Konvertierungsoptionen übergeben werden.
## Schritt 3: Abschluss der Konvertierung
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
Nach Abschluss des Konvertierungsvorgangs wird Ihnen eine Erfolgsmeldung zusammen mit dem Verzeichnis angezeigt, in dem sich die konvertierte PDF-Datei befindet.

## Abschluss
Zusammenfassend lässt sich sagen, dass die Konvertierung von DNG-Bildern in PDF mit GroupDocs.Conversion für .NET problemlos möglich ist. Mit den einfachen Schritten in diesem Tutorial können Sie Ihre DNG-Dateien effizient ins PDF-Format konvertieren und so leichter zugänglich und gemeinsam nutzbar machen.
## Häufig gestellte Fragen
### Ist GroupDocs.Conversion für .NET mit allen Versionen von .NET kompatibel?
Ja, GroupDocs.Conversion für .NET ist mit .NET Framework 4.6.1 und höher sowie .NET Core 2.0 und höher kompatibel.
### Kann ich mehrere DNG-Dateien gleichzeitig in PDF konvertieren?
Ja, Sie können mehrere DNG-Dateien in PDF konvertieren, indem Sie jede Datei durchlaufen und den Konvertierungsprozess für jede einzelne durchführen.
### Gibt es Einschränkungen hinsichtlich der Größe der DNG-Dateien, die konvertiert werden können?
GroupDocs.Conversion für .NET unterliegt keinen spezifischen Größenbeschränkungen für konvertierbare DNG-Dateien. Die Leistung kann jedoch je nach Größe und Komplexität der Eingabedateien variieren.
### Kann ich die Konvertierungsoptionen für die PDF-Ausgabe anpassen?
Ja, Sie können verschiedene Optionen wie Seitengröße, Ausrichtung, Komprimierung und mehr anpassen, indem Sie `PdfConvertOptions` Klasse bereitgestellt von GroupDocs.Conversion für .NET.
### Gibt es technischen Support für GroupDocs.Conversion für .NET?
Ja, technischer Support ist über das GroupDocs-Forum verfügbar [Hier](https://forum.groupdocs.com/c/conversion/11), wo Sie Fragen stellen und Hilfe von Experten erhalten können.