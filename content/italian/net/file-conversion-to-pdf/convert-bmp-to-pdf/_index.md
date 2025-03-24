---
title: Converti immagini BMP in PDF
linktitle: Converti immagini BMP in PDF
second_title: API GroupDocs.Conversion .NET
description: Converti immagini BMP in PDF senza problemi utilizzando GroupDocs.Conversion per .NET. Opzioni personalizzabili per un output ottimale.
weight: 11
url: /it/net/file-conversion-to-pdf/convert-bmp-to-pdf/
---

# Converti immagini BMP in PDF

## introduzione
GroupDocs.Conversion per .NET fornisce una potente soluzione per convertire senza problemi le immagini BMP in formato PDF. Questo tutorial ti guiderà attraverso il processo passo dopo passo.
### Prerequisiti
Prima di iniziare, assicurati di avere quanto segue:
1.  GroupDocs.Conversion per .NET: installa la libreria scaricandola dal file[Link per scaricare](https://releases.groupdocs.com/conversion/net/).
2. File BMP di origine: prepara il file immagine BMP che desideri convertire.

## Importa spazi dei nomi
Innanzitutto, importa gli spazi dei nomi necessari per accedere alle classi e ai metodi richiesti:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Passaggio 1: imposta la cartella di output e il nome del file
Definire il percorso della cartella di output e il nome del file PDF convertito:
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "bmp-converted-to.pdf");
```
## Passaggio 2: caricare il file BMP di origine
 Caricare il file BMP di origine utilizzando il file`Converter` classe:
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_BMP))
{
    // La logica di conversione va qui
}
```
## Passaggio 3: configura le opzioni di conversione
 Specificare le opzioni di conversione. In questo caso, useremo`PdfConvertOptions` per la conversione in formato PDF:
```csharp
var options = new PdfConvertOptions();
```
## Passaggio 4: converti BMP in PDF
Esegui la conversione e salva il file PDF convertito:
```csharp
converter.Convert(outputFile, options);
```
## Passaggio 5: verifica la conversione
Controlla se la conversione ha avuto esito positivo e visualizza il percorso della cartella di output:
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
Congratulazioni! Hai convertito con successo un'immagine BMP in PDF utilizzando GroupDocs.Conversion per .NET.

## Conclusione
In conclusione, GroupDocs.Conversion per .NET offre una soluzione semplice ma potente per convertire immagini BMP in formato PDF. Seguendo i passaggi descritti in questo tutorial, puoi integrare perfettamente questa funzionalità nelle tue applicazioni .NET.
## Domande frequenti
### GroupDocs.Conversion per .NET è compatibile con tutti i formati di immagine BMP?
GroupDocs.Conversion per .NET supporta un'ampia gamma di formati di immagine BMP, garantendo la compatibilità con la maggior parte dei file BMP.
### Posso personalizzare le opzioni di conversione per un maggiore controllo sul PDF di output?
Sì, puoi personalizzare varie opzioni di conversione come DPI, dimensioni della pagina, orientamento e altro per personalizzare il PDF di output in base alle tue esigenze.
### GroupDocs.Conversion per .NET richiede dipendenze aggiuntive?
No, GroupDocs.Conversion per .NET è una libreria autonoma che non richiede dipendenze aggiuntive per le attività di conversione di base.
### È disponibile una versione di prova da provare prima dell'acquisto?
 Sì, puoi scaricare una versione di prova gratuita da[pagina delle uscite](https://releases.groupdocs.com/) per valutare le caratteristiche della libreria prima di effettuare un acquisto.
### Dove posso ottenere supporto o assistenza in caso di problemi?
 Puoi visitare il[Forum GroupDocs.Conversion](https://forum.groupdocs.com/c/conversion/11) per ricevere assistenza dalla community o contattare direttamente il supporto per un aiuto personalizzato.