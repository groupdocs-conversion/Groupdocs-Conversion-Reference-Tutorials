---
title: Converti immagini DNG in PDF
linktitle: Converti immagini DNG in PDF
second_title: API GroupDocs.Conversion .NET
description: Scopri come convertire immagini DNG in PDF senza sforzo utilizzando GroupDocs.Conversion per .NET. Segui la nostra guida passo passo per una conversione senza problemi.
weight: 21
url: /it/net/file-conversion-to-pdf/convert-dng-to-pdf/
---

# Converti immagini DNG in PDF

## introduzione
In questo tutorial ti guideremo attraverso il processo di conversione delle immagini DNG in PDF utilizzando GroupDocs.Conversion per .NET. DNG (Digital Negative) è un formato file utilizzato per la fotografia digitale. Convertendo le immagini DNG in PDF, puoi condividerle o archiviarle facilmente in un formato più universalmente accettato.
## Prerequisiti
Prima di iniziare, assicurati di avere quanto segue:
1.  GroupDocs.Conversion per .NET: scarica e installa la libreria GroupDocs.Conversion per .NET da[Qui](https://releases.groupdocs.com/conversion/net/).
2. File DNG di origine: è necessario un file immagine DNG che desideri convertire in PDF.
3. Ambiente di sviluppo: assicurati di avere un ambiente di sviluppo .NET configurato.

## Importa spazi dei nomi
Innanzitutto, devi importare gli spazi dei nomi necessari nel tuo progetto. Aggiungi le seguenti direttive using al tuo file di codice:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Passaggio 1: carica il file DNG di origine
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "dng-converted-to.pdf");
// Carica il file DNG di origine
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_DNG))
{
    // Continuare con il processo di conversione
}
```
 In questo passaggio definisci la cartella di output in cui verrà salvato il file PDF convertito. Assicurarsi di sostituire`"Your Document Directory"` con il percorso della directory desiderata. Quindi, specifichi il nome e il percorso del file PDF di output.
## Passaggio 2: converti DNG in PDF
```csharp
var options = new PdfConvertOptions();
// Salva il file PDF convertito
converter.Convert(outputFile, options);
```
 Qui crei un'istanza di`PdfConvertOptions` per impostare eventuali opzioni specifiche per la conversione PDF, se richiesto. Quindi chiami il`Convert` metodo del`converter`oggetto, passando il percorso del file di output e le opzioni di conversione.
## Passaggio 3: gestire il completamento della conversione
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
Una volta completato il processo di conversione, verrà visualizzato un messaggio di successo insieme alla directory in cui si trova il file PDF convertito.

## Conclusione
In conclusione, la conversione di immagini DNG in PDF può essere facilmente eseguita utilizzando GroupDocs.Conversion per .NET. Seguendo i semplici passaggi descritti in questo tutorial, puoi convertire in modo efficiente i tuoi file DNG in formato PDF, rendendoli più accessibili e condivisibili.
## Domande frequenti
### GroupDocs.Conversion per .NET è compatibile con tutte le versioni di .NET?
Sì, GroupDocs.Conversion per .NET è compatibile con .NET Framework 4.6.1 e versioni successive, nonché con .NET Core 2.0 e versioni successive.
### Posso convertire più file DNG in PDF contemporaneamente?
Sì, puoi convertire più file DNG in PDF eseguendo l'iterazione di ciascun file ed eseguendo il processo di conversione per ciascuno di essi.
### Esistono limitazioni sulla dimensione dei file DNG che possono essere convertiti?
GroupDocs.Conversion per .NET non presenta limitazioni specifiche sulla dimensione dei file DNG che possono essere convertiti. Tuttavia, le prestazioni possono variare in base alle dimensioni e alla complessità dei file di input.
### Posso personalizzare le opzioni di conversione per l'output PDF?
 Sì, puoi personalizzare varie opzioni come dimensioni della pagina, orientamento, compressione e altro utilizzando il file`PdfConvertOptions`classe fornita da GroupDocs.Conversion per .NET.
### È disponibile il supporto tecnico per GroupDocs.Conversion per .NET?
 Sì, il supporto tecnico è disponibile tramite il forum GroupDocs[Qui](https://forum.groupdocs.com/c/conversion/11), dove puoi porre domande e ottenere assistenza da esperti.