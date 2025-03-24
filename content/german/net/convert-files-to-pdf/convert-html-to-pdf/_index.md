---
title: Konvertieren Sie HTML-Webseiten in PDF
linktitle: Konvertieren Sie HTML-Webseiten in PDF
second_title: GroupDocs.Conversion .NET-API
description: Konvertieren Sie HTML-Webseiten mühelos in das PDF-Format mit GroupDocs.Conversion für .NET. Befolgen Sie unsere Schritt-für-Schritt-Anleitung für eine nahtlose Konvertierung des Dokumentformats.
weight: 22
url: /de/net/convert-files-to-pdf/convert-html-to-pdf/
---
## Einführung
Im heutigen digitalen Zeitalter ist die Fähigkeit, verschiedene Dokumentformate nahtlos zu konvertieren, für Unternehmen und Privatpersonen gleichermaßen von entscheidender Bedeutung. Ganz gleich, ob es darum geht, HTML-Webseiten zur einfachen Weitergabe oder Archivierung in PDFs zu konvertieren, die richtigen Tools können den entscheidenden Unterschied machen. In diesem Tutorial erfahren Sie, wie Sie GroupDocs.Conversion für .NET verwenden, um HTML-Webseiten effizient in das PDF-Format zu konvertieren.
## Voraussetzungen
Bevor wir uns mit dem Tutorial befassen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:
1.  Installation: Stellen Sie sicher, dass GroupDocs.Conversion für .NET in Ihrer Entwicklungsumgebung installiert ist. Die benötigten Dateien können Sie hier herunterladen[Download-Link](https://releases.groupdocs.com/conversion/net/).
2. Beispiel-HTML-Datei: Halten Sie eine Beispiel-HTML-Datei bereit, die Sie in PDF konvertieren möchten. Dies dient uns als Quelldatei für die Konvertierung.
3. .NET-Umgebung: Grundlegende Vertrautheit mit der .NET-Entwicklung und der Verwendung von Bibliotheken über NuGet-Pakete.

## Namespaces importieren
Bevor wir mit dem Konvertierungsprozess beginnen, importieren wir die erforderlichen Namespaces:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```

## Schritt 1: Definieren Sie den Ausgabeordner und den Dateipfad
Geben Sie zunächst den Ausgabeordner an, in dem Sie die konvertierte PDF-Datei speichern möchten. Sie können ein beliebiges Verzeichnis auf Ihrem System auswählen.
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "html-converted-to.pdf");
```
## Schritt 2: Laden Sie die Quell-HTML-Datei
Laden Sie als Nächstes die HTML-Quelldatei, die Sie mit der Converter-Klasse von GroupDocs.Conversion in PDF konvertieren möchten.
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_HTML))
```
## Schritt 3: Konvertierungsoptionen konfigurieren
Konfigurieren Sie die Konvertierungsoptionen entsprechend Ihren Anforderungen. In diesem Fall verwenden wir PdfConvertOptions zum Konvertieren von HTML in PDF.
```csharp
var options = new PdfConvertOptions();
```
## Schritt 4: Führen Sie die Konvertierung durch
Führen Sie nun die eigentliche Konvertierung durch, indem Sie die Convert-Methode der Converter-Klasse aufrufen und den Ausgabedateipfad und die Konvertierungsoptionen übergeben.
```csharp
converter.Convert(outputFile, options);
```
## Schritt 5: Erfolgsmeldung anzeigen
Teilen Sie dem Benutzer abschließend mit, dass der Konvertierungsvorgang erfolgreich abgeschlossen wurde, und geben Sie den Pfad an, in dem die konvertierte PDF-Datei gespeichert wird.
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```

## Abschluss
Mit GroupDocs.Conversion für .NET wird die Konvertierung von HTML-Webseiten in das PDF-Format zum Kinderspiel. Indem Sie die in diesem Tutorial beschriebenen einfachen Schritte befolgen, können Sie Dokumentformatkonvertierungen in Ihren .NET-Anwendungen effizient durchführen.
## FAQs
### Ist GroupDocs.Conversion für .NET mit allen Versionen von .NET kompatibel?
Ja, GroupDocs.Conversion für .NET ist mit .NET Framework 4.6 und späteren Versionen kompatibel.
### Kann ich mehrere HTML-Dateien gleichzeitig in PDF konvertieren?
Absolut! Sie können Ihre Liste der HTML-Dateien durchlaufen und die Konvertierung für jede Datei einzeln durchführen.
### Unterstützt GroupDocs.Conversion die Konvertierung in andere Formate außer PDF?
Ja, GroupDocs.Conversion unterstützt eine Vielzahl von Dokumentformaten für die Konvertierung, darunter DOCX, XLSX, PPTX und mehr.
### Gibt es eine Testversion für GroupDocs.Conversion für .NET?
 Ja, Sie können eine kostenlose Testversion herunterladen von[Hier](https://releases.groupdocs.com/).
### Wo bekomme ich Unterstützung, wenn bei der Implementierung Probleme auftreten?
 Sie können Hilfe im Community-Forum GroupDocs.Conversion suchen[Hier](https://forum.groupdocs.com/c/conversion/11).