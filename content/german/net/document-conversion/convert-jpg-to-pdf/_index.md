---
"description": "Konvertieren Sie JPG mühelos in PDF mit GroupDocs.Conversion für .NET. Folgen Sie dieser Schritt-für-Schritt-Anleitung für eine reibungslose Dokumentkonvertierung."
"linktitle": "Konvertieren Sie JPG in PDF"
"second_title": "GroupDocs.Conversion .NET API"
"title": "Konvertieren Sie JPG in PDF"
"url": "/de/net/document-conversion/convert-jpg-to-pdf/"
"weight": 14
type: docs
---
# Konvertieren Sie JPG in PDF

## Einführung

Möchten Sie JPG-Dateien mit GroupDocs.Conversion für .NET mühelos in PDF konvertieren? Dieses Tutorial führt Sie Schritt für Schritt durch den Prozess. GroupDocs.Conversion für .NET ist eine leistungsstarke API, mit der Sie verschiedene Dokumentformate, einschließlich Bilder, problemlos in PDF konvertieren können. Los geht‘s!

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:

1. GroupDocs.Conversion für .NET: Stellen Sie sicher, dass Sie GroupDocs.Conversion für .NET installiert haben. Sie können es herunterladen von [Hier](https://releases.groupdocs.com/conversion/net/).
2. Entwicklungsumgebung: Richten Sie eine Entwicklungsumgebung wie Visual Studio zusammen mit .NET Framework oder .NET Core ein.
3. Beispiel-JPG-Datei: Bereiten Sie eine Beispiel-JPG-Datei vor, die Sie in PDF konvertieren möchten.

## Namespaces importieren

Lassen Sie uns zunächst die erforderlichen Namespaces importieren:

```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```

Lassen Sie uns nun den Konvertierungsprozess in einfache Schritte unterteilen:

## Schritt 1: Ausgabeverzeichnis und Dateinamen festlegen

```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "jpg-converted-to.pdf");
```

Geben Sie unbedingt das Verzeichnis an, in dem Sie die konvertierte PDF-Datei speichern möchten, sowie den gewünschten Ausgabedateinamen.

## Schritt 2: Laden Sie die JPG-Quelldatei und konvertieren Sie sie in PDF

```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_JPG))
{
    var options = new PdfConvertOptions();
    converter.Convert(outputFile, options);
}
```

Initialisieren Sie den `Converter` Objekt mit dem Pfad zu Ihrer JPG-Beispieldatei. Konfigurieren Sie anschließend die Konvertierungsoptionen, z. B. die Angabe von PDF-Konvertierungsoptionen. Rufen Sie abschließend die `Convert` -Methode, wobei der Ausgabedateipfad und die Konvertierungsoptionen übergeben werden.

## Schritt 3: Anzeige der Konvertierungsabschlussmeldung

```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```

Nachdem die Konvertierung abgeschlossen ist, wird eine Meldung angezeigt, die die erfolgreiche Konvertierung und den Speicherort der konvertierten PDF-Datei angibt.

## Abschluss

Die Konvertierung von JPG-Dateien in PDF mit GroupDocs.Conversion für .NET ist mit nur wenigen Codezeilen ganz einfach. Mit diesem Tutorial können Sie Dokumentkonvertierungsfunktionen nahtlos in Ihre .NET-Anwendungen integrieren.

## Häufig gestellte Fragen

### F: Kann ich mehrere JPG-Dateien gleichzeitig in PDF konvertieren?

A: Ja, Sie können mehrere JPG-Dateien in PDF konvertieren, indem Sie jede Datei durchlaufen und den im Lernprogramm beschriebenen Konvertierungsprozess durchführen.

### F: Unterstützt GroupDocs.Conversion neben JPG auch andere Bildformate?

A: Ja, GroupDocs.Conversion unterstützt verschiedene Bildformate wie unter anderem PNG, TIFF, BMP und GIF.

### F: Kann ich die PDF-Ausgabedatei mithilfe von Konvertierungsoptionen anpassen?

A: Absolut! GroupDocs.Conversion bietet eine breite Palette an Konvertierungsoptionen, mit denen Sie das Ausgabe-PDF Ihren Anforderungen entsprechend anpassen können.

### F: Gibt es eine Testversion von GroupDocs.Conversion für .NET?

A: Ja, Sie können auf eine kostenlose Testversion von GroupDocs.Conversion für .NET zugreifen von [Hier](https://releases.groupdocs.com/).

### F: Wo kann ich Hilfe suchen, wenn während des Konvertierungsvorgangs Probleme auftreten?

A: Wenn Sie auf Probleme stoßen oder Fragen zu GroupDocs.Conversion für .NET haben, besuchen Sie bitte die [GroupDocs.Conversion-Forum](https://forum.groupdocs.com/c/conversion/11) um Hilfe.