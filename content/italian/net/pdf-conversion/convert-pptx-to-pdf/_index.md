---
title: Converti PPTX in PDF
linktitle: Converti PPTX in PDF
second_title: API GroupDocs.Conversion .NET
description: Scopri come convertire presentazioni PowerPoint (PPTX) in formato PDF utilizzando GroupDocs.Conversion per .NET. Processo di conversione semplice ed efficiente.
weight: 29
url: /it/net/pdf-conversion/convert-pptx-to-pdf/
---

# Converti PPTX in PDF

## introduzione
In questo tutorial, esamineremo il processo di conversione di un file di presentazione PowerPoint (PPTX) in un formato PDF (Portable Document Format) utilizzando la libreria GroupDocs.Conversion per .NET. Seguire i passaggi seguenti per ottenere questa conversione.
## Prerequisiti
Prima di iniziare, assicurati di possedere i seguenti prerequisiti:
1.  GroupDocs.Conversion per la libreria .NET: assicurati di aver installato la libreria GroupDocs.Conversion per .NET. Puoi scaricarlo da[Qui](https://releases.groupdocs.com/conversion/net/).
2. Ambiente di sviluppo: configura un ambiente di sviluppo con gli strumenti necessari come Visual Studio o qualsiasi altro IDE .NET.

## Importa spazi dei nomi
Includi gli spazi dei nomi necessari nel tuo progetto per accedere alle funzionalità GroupDocs.Conversion.
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Passaggio 1: imposta la cartella di output e il nome del file
Innanzitutto, definisci la cartella di output in cui verrà salvato il file PDF convertito e specifica il nome del file PDF di output.
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "pptx-converted-to.pdf");
```
## Passaggio 2: caricare il file PPTX di origine
Caricare il file di presentazione PowerPoint (PPTX) di origine utilizzando la libreria GroupDocs.Conversion.
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PPTX))
{
    // La logica di conversione verrà posizionata qui
}
```
## Passaggio 3: specificare le opzioni di conversione
Definire le opzioni di conversione. In questo caso, stiamo convertendo in formato PDF, quindi crea un'istanza di`PdfConvertOptions`.
```csharp
var options = new PdfConvertOptions();
```
## Passaggio 4: eseguire la conversione
 Esegui il processo di conversione utilizzando il file`Convert` metodo e passare il percorso del file di output insieme alle opzioni di conversione.
```csharp
converter.Convert(outputFile, options);
```
## Passaggio 5: controllare l'output
Una volta completata con successo la conversione, viene visualizzato un messaggio che indica il completamento e la posizione del file di output.
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```

## Conclusione
In questo tutorial, abbiamo imparato come convertire un file di presentazione PowerPoint (PPTX) in un formato PDF (Portable Document Format) utilizzando la libreria GroupDocs.Conversion per .NET. Seguendo i passaggi sopra descritti, puoi facilmente eseguire questa conversione nelle tue applicazioni .NET.
## Domande frequenti
### D: GroupDocs.Conversion è compatibile con tutte le versioni di .NET?
R: Sì, GroupDocs.Conversion supporta .NET Framework 2.0 e versioni successive, inclusi .NET Core e .NET Standard.
### D: Posso convertire file in formati diversi dal PDF?
R: Sì, GroupDocs.Conversion supporta un'ampia gamma di formati di documenti per la conversione, inclusi Word, Excel, HTML e altri.
### D: GroupDocs.Conversion offre una prova gratuita?
 R: Sì, puoi accedere a una prova gratuita di GroupDocs.Conversion da[Qui](https://releases.groupdocs.com/).
### D: Come posso ottenere supporto per GroupDocs.Conversion?
 R: Puoi ottenere supporto dal forum della community di GroupDocs[Qui](https://forum.groupdocs.com/c/conversion/11).
### D: È disponibile una licenza temporanea per GroupDocs.Conversion?
 R: Sì, puoi ottenere una licenza temporanea per GroupDocs.Conversion da[Qui](https://purchase.groupdocs.com/temporary-license/).