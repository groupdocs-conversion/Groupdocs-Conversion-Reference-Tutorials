---
title: Konvertieren Sie CDR-Vektorgrafiken in PDF
linktitle: Konvertieren Sie CDR-Vektorgrafiken in PDF
second_title: GroupDocs.Conversion .NET-API
description: Konvertieren Sie CorelDRAW (CDR)-Vektorgrafikdateien mühelos in das PDF-Format mit GroupDocs.Conversion für .NET. Optimieren Sie Ihren Dokumentenkonvertierungsprozess.
weight: 12
url: /de/net/file-conversion-to-pdf/convert-cdr-to-pdf/
---
## Einführung
GroupDocs.Conversion für .NET ist eine leistungsstarke Dokumentkonvertierungsbibliothek, die es Entwicklern ermöglicht, verschiedene Dokumentformate nahtlos in PDF, Word, HTML und viele mehr zu konvertieren. In diesem Tutorial konzentrieren wir uns auf die Konvertierung von CorelDRAW (CDR)-Vektorgrafikdateien in das PDF-Format mit GroupDocs.Conversion für .NET. Am Ende dieses Leitfadens verfügen Sie über das nötige Wissen, um diese Konvertierung mühelos in Ihren .NET-Anwendungen durchzuführen.
## Voraussetzungen
Bevor wir mit dem Konvertierungsprozess beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen geschaffen haben:
### Installieren Sie GroupDocs.Conversion für .NET
 Um zu beginnen, müssen Sie GroupDocs.Conversion für .NET herunterladen und installieren. Sie können die Bibliothek unter herunterladen[Download-Seite](https://releases.groupdocs.com/conversion/net/).
### Besorgen Sie sich eine Lizenz
 Um das volle Potenzial von Gruppendokumente.Conversion für .NET nutzen zu können, benötigen Sie eine gültige Lizenz. Eine Lizenz erhalten Sie bei[GroupDocs](https://purchase.groupdocs.com/buy)oder fordern Sie zu Testzwecken eine temporäre Lizenz an[Hier](https://purchase.groupdocs.com/temporary-license/).

## Namespaces importieren
Stellen Sie sicher, dass Sie die erforderlichen Namespaces in Ihr .NET-Projekt importiert haben, um die GroupDocs.Conversion-Funktionen nutzen zu können. So können Sie es machen:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Schritt 1: Definieren Sie den Ausgabeordner und den Dateinamen
Geben Sie zunächst den Ausgabeordner an, in dem die konvertierte PDF-Datei gespeichert werden soll, sowie den gewünschten Dateinamen.
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "cdr-converted-to.pdf");
```
Unbedingt austauschen`"Your Document Directory"` mit dem Pfad zu Ihrem gewünschten Ausgabeordner.
## Schritt 2: Laden Sie die Quell-CDR-Datei
Laden Sie als Nächstes die CDR-Quelldatei, die Sie mit GroupDocs.Conversion in PDF konvertieren möchten.
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_CDR))
{
    // Hier kommt die Konvertierungslogik zum Einsatz
}
```
 Ersetzen`Constants.SAMPLE_CDR` mit dem Pfad zu Ihrer tatsächlichen CDR-Datei.
## Schritt 3: Konvertierungsoptionen angeben
Definieren Sie die Konvertierungsoptionen, z. B. die Angabe des Ausgabeformats (PDF) und etwaiger zusätzlicher Einstellungen.
```csharp
var options = new PdfConvertOptions();
```
Sie können die Konvertierungsoptionen entsprechend Ihren Anforderungen anpassen.
## Schritt 4: Führen Sie die Konvertierung durch
Führen Sie den Konvertierungsprozess mit den angegebenen Optionen aus.
```csharp
converter.Convert(outputFile, options);
```
Dieser Befehl konvertiert die CDR-Datei in PDF und speichert sie im angegebenen Ausgabeordner unter dem angegebenen Dateinamen.
## Schritt 5: Bestätigen Sie den Abschluss der Konvertierung
Abschließend wird eine Meldung angezeigt, die den erfolgreichen Abschluss des Konvertierungsvorgangs bestätigt.
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```
Diese Meldung informiert Sie über den Speicherort der konvertierten PDF-Datei.

## Abschluss
In diesem Tutorial haben wir gelernt, wie man CorelDRAW (CDR)-Vektorgrafikdateien mit GroupDocs.Conversion für .NET in das PDF-Format konvertiert. Wenn Sie die beschriebenen Schritte befolgen, können Sie Dokumentkonvertierungsfunktionen nahtlos in Ihre .NET-Anwendungen integrieren und so deren Funktionalität und Benutzerfreundlichkeit verbessern.
## FAQs
### Ist GroupDocs.Conversion für .NET mit allen Versionen von CorelDRAW-Dateien kompatibel?
GroupDocs.Conversion für .NET unterstützt eine Vielzahl von CorelDRAW-Versionen und gewährleistet so die Kompatibilität mit den meisten CDR-Dateien.
### Kann ich mit GroupDocs.Conversion für .NET mehrere CDR-Dateien gleichzeitig konvertieren?
Ja, Sie können mit GroupDocs.Conversion für .NET mehrere CDR-Dateien stapelweise in PDF oder andere Formate konvertieren und so die Effizienz und Produktivität verbessern.
### Benötigt GroupDocs.Conversion für .NET eine Internetverbindung für die Dokumentkonvertierung?
Nein, GroupDocs.Conversion für .NET führt die Dokumentkonvertierung lokal auf Ihrem Computer durch, sodass während des Konvertierungsvorgangs keine Internetverbindung erforderlich ist.
### Kann ich die Konvertierungseinstellungen an meine spezifischen Anforderungen anpassen?
Ja, GroupDocs.Conversion für .NET bietet umfangreiche Anpassungsoptionen, sodass Sie den Konvertierungsprozess genau an Ihre Bedürfnisse anpassen können.
### Ist technischer Support für GroupDocs.Conversion für .NET verfügbar?
 Ja, GroupDocs bietet umfassenden technischen Support für seine Produkte, einschließlich GroupDocs.Conversion für .NET. Sie können Hilfe bei der suchen[Hilfeforum](https://forum.groupdocs.com/c/conversion/11) für alle Fragen oder Probleme.