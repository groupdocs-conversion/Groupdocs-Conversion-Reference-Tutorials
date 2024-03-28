---
title: Konvertieren Sie SVG in PDF
linktitle: Konvertieren Sie SVG in PDF
second_title: GroupDocs.Conversion .NET-API
description: Erfahren Sie, wie Sie SVG mit GroupDocs.Conversion für .NET mühelos in PDF konvertieren. Optimieren Sie Ihren Dokumentenverwaltungsprozess.
type: docs
weight: 15
url: /de/net/file-format-conversion-tutorials/convert-svg-to-pdf/
---
## Einführung
In der Welt der Programmierung ist das Konvertieren von Dateien von einem Format in ein anderes eine häufige Aufgabe. Unabhängig davon, ob Sie mit Bildern, Dokumenten oder anderen Medien arbeiten, ist die nahtlose Konvertierung zwischen Formaten von entscheidender Bedeutung. In diesem Tutorial erfahren Sie, wie Sie SVG-Dateien (Scalable Vector Graphics) mit GroupDocs.Conversion für .NET in PDF (Portable Document Format) konvertieren.
## Voraussetzungen
Bevor Sie mit dem Konvertierungsprozess beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:
### 1. Installieren Sie GroupDocs.Conversion für .NET
Stellen Sie sicher, dass GroupDocs.Conversion für .NET in Ihrer Entwicklungsumgebung installiert ist. Wenn Sie es noch nicht getan haben, können Sie es hier herunterladen[Webseite](https://releases.groupdocs.com/conversion/net/).
### 2. Besorgen Sie sich eine Beispiel-SVG-Datei
Für die Konvertierung in PDF benötigen Sie eine Beispiel-SVG-Datei. Wenn Sie noch keine haben, können Sie SVG-Dateien ganz einfach online finden oder mit verschiedenen Grafikdesign-Tools eine erstellen.
### 3. Grundlegendes Verständnis von C#
Machen Sie sich mit den Grundlagen der Programmiersprache C# vertraut, da wir sie zum Schreiben des Konvertierungscodes verwenden werden.

## Namespaces importieren
Importieren wir zunächst die notwendigen Namespaces:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Schritt 1: Ausgabeordner und -datei definieren
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "svg-converted-to.pdf");
```
 Stellen Sie sicher, dass Sie es ersetzen`"Your Document Directory"` mit dem Pfad zu Ihrem gewünschten Ausgabeverzeichnis.
## Schritt 2: Laden Sie die Quell-SVG-Datei
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_SVG))
{
    // Der Konvertierungscode kommt hierher
}
```
 Ersetzen`Constants.SAMPLE_SVG` mit dem Pfad zu Ihrer SVG-Datei.
## Schritt 3: Konvertierungsoptionen festlegen
```csharp
var options = new PdfConvertOptions();
```
Hier richten wir Konvertierungsoptionen speziell für die PDF-Ausgabe ein. Sie können diese Optionen entsprechend Ihren Anforderungen anpassen.
## Schritt 4: Führen Sie die Konvertierung durch
```csharp
converter.Convert(outputFile, options);
```
Diese Zeile führt den Konvertierungsprozess aus, indem sie die SVG-Quelldatei mit den angegebenen Optionen in PDF konvertiert.
## Schritt 5: Überprüfen Sie den Abschluss der Konvertierung
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
Diese Zeile gibt eine Meldung aus, die den erfolgreichen Abschluss des Konvertierungsvorgangs bestätigt, zusammen mit dem Verzeichnis, in dem sich die konvertierte PDF-Datei befindet.

## Abschluss
In diesem Tutorial haben wir gelernt, wie man SVG-Dateien mit GroupDocs.Conversion für .NET in PDF konvertiert. Indem Sie die Schritt-für-Schritt-Anleitung befolgen und sicherstellen, dass Sie über die Voraussetzungen verfügen, können Sie Funktionen zur Dateiformatkonvertierung nahtlos in Ihre .NET-Anwendungen integrieren.
## FAQs
### Ist GroupDocs.Conversion für .NET mit allen .NET-Frameworks kompatibel?
Ja, GroupDocs.Conversion für .NET unterstützt mehrere .NET Frameworks, einschließlich .NET Core und .NET Framework.
### Kann ich die Konvertierungsoptionen für bestimmte Ausgabeformate anpassen?
Absolut! GroupDocs.Conversion für .NET bietet umfangreiche Anpassungsoptionen für jedes unterstützte Ausgabeformat.
### Unterstützt GroupDocs.Conversion für .NET die Stapelkonvertierung?
Ja, Sie können mit GroupDocs.Conversion für .NET mehrere Dateien gleichzeitig konvertieren.
### Gibt es zu Testzwecken eine Testversion?
 Ja, Sie können auf eine kostenlose Testversion zugreifen[Hier](https://releases.groupdocs.com/).
### Wo erhalte ich technischen Support für GroupDocs.Conversion für .NET?
Technischen Support und Hilfe finden Sie im GroupDocs-Forum[Hier](https://forum.groupdocs.com/c/conversion/11).