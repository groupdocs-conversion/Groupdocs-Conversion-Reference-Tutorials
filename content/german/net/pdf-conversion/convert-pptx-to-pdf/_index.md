---
title: Konvertieren Sie PPTX in PDF
linktitle: Konvertieren Sie PPTX in PDF
second_title: GroupDocs.Conversion .NET-API
description: Erfahren Sie, wie Sie PowerPoint-Präsentationen (PPTX) mit GroupDocs.Conversion für .NET in das PDF-Format konvertieren. Einfacher und effizienter Konvertierungsprozess.
weight: 29
url: /de/net/pdf-conversion/convert-pptx-to-pdf/
---

# Konvertieren Sie PPTX in PDF

## Einführung
In diesem Tutorial führen wir den Prozess der Konvertierung einer PowerPoint-Präsentationsdatei (PPTX) in ein Portable Document Format (PDF) mithilfe der GroupDocs.Conversion-Bibliothek für .NET durch. Führen Sie die folgenden Schritte aus, um diese Konvertierung durchzuführen.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:
1.  GroupDocs.Conversion für .NET-Bibliothek: Stellen Sie sicher, dass Sie die GroupDocs.Conversion für .NET-Bibliothek installiert haben. Sie können es herunterladen unter[Hier](https://releases.groupdocs.com/conversion/net/).
2. Entwicklungsumgebung: Richten Sie eine Entwicklungsumgebung mit den erforderlichen Tools wie Visual Studio oder einer anderen .NET-IDE ein.

## Namespaces importieren
Fügen Sie die erforderlichen Namespaces in Ihr Projekt ein, um auf die GroupDocs.Conversion-Funktionen zuzugreifen.
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Schritt 1: Legen Sie den Ausgabeordner und den Dateinamen fest
Definieren Sie zunächst den Ausgabeordner, in dem die konvertierte PDF-Datei gespeichert wird, und geben Sie den Namen der Ausgabe-PDF-Datei an.
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "pptx-converted-to.pdf");
```
## Schritt 2: Laden Sie die Quell-PPTX-Datei
Laden Sie die Quelldatei der PowerPoint-Präsentation (PPTX) mithilfe der GroupDocs.Conversion-Bibliothek.
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PPTX))
{
    // Hier wird die Konvertierungslogik platziert
}
```
## Schritt 3: Konvertierungsoptionen angeben
Definieren Sie die Konvertierungsoptionen. In diesem Fall konvertieren wir in das PDF-Format. Erstellen Sie also eine Instanz von`PdfConvertOptions`.
```csharp
var options = new PdfConvertOptions();
```
## Schritt 4: Führen Sie die Konvertierung durch
 Führen Sie den Konvertierungsvorgang mit dem aus`Convert` -Methode und übergeben Sie den Pfad der Ausgabedatei zusammen mit den Konvertierungsoptionen.
```csharp
converter.Convert(outputFile, options);
```
## Schritt 5: Überprüfen Sie die Ausgabe
Nachdem die Konvertierung erfolgreich abgeschlossen wurde, wird eine Meldung angezeigt, die den Abschluss und den Speicherort der Ausgabedatei angibt.
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```

## Abschluss
In diesem Tutorial haben wir gelernt, wie man eine PowerPoint-Präsentationsdatei (PPTX) mithilfe der GroupDocs.Conversion-Bibliothek für .NET in ein Portable Document Format (PDF) konvertiert. Wenn Sie die oben beschriebenen Schritte befolgen, können Sie diese Konvertierung problemlos in Ihren .NET-Anwendungen durchführen.
## FAQs
### F: Ist GroupDocs.Conversion mit allen Versionen von .NET kompatibel?
A: Ja, GroupDocs.Conversion unterstützt .NET Framework 2.0 und höher, einschließlich .NET Core und .NET Standard.
### F: Kann ich Dateien in andere Formate als PDF konvertieren?
A: Ja, GroupDocs.Conversion unterstützt eine Vielzahl von Dokumentformaten für die Konvertierung, darunter Word, Excel, HTML und mehr.
### F: Bietet GroupDocs.Conversion eine kostenlose Testversion an?
 A: Ja, Sie können auf eine kostenlose Testversion von GroupDocs.Conversion zugreifen[Hier](https://releases.groupdocs.com/).
### F: Wie kann ich Unterstützung für GroupDocs.Conversion erhalten?
 A: Sie können Unterstützung vom GroupDocs-Community-Forum erhalten[Hier](https://forum.groupdocs.com/c/conversion/11).
### F: Gibt es eine temporäre Lizenz für GroupDocs.Conversion?
 A: Ja, Sie können eine temporäre Lizenz für GroupDocs.Conversion erhalten von[Hier](https://purchase.groupdocs.com/temporary-license/).