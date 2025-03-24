---
title: Converti la grafica vettoriale CDR in PDF
linktitle: Converti la grafica vettoriale CDR in PDF
second_title: API GroupDocs.Conversion .NET
description: Converti senza sforzo file di grafica vettoriale CorelDRAW (CDR) in formato PDF utilizzando GroupDocs.Conversion per .NET. Semplifica il processo di conversione dei documenti.
weight: 12
url: /it/net/file-conversion-to-pdf/convert-cdr-to-pdf/
---

# Converti la grafica vettoriale CDR in PDF

## introduzione
GroupDocs.Conversion per .NET è una potente libreria di conversione di documenti che consente agli sviluppatori di convertire senza problemi vari formati di documenti in PDF, Word, HTML e molti altri. In questo tutorial, ci concentreremo sulla conversione dei file di grafica vettoriale CorelDRAW (CDR) in formato PDF utilizzando GroupDocs.Conversion per .NET. Al termine di questa guida avrai le conoscenze necessarie per eseguire facilmente questa conversione nelle tue applicazioni .NET.
## Prerequisiti
Prima di immergerci nel processo di conversione, assicurati di aver impostato i seguenti prerequisiti:
### Installa GroupDocs.Conversion per .NET
 Per iniziare, devi scaricare e installare GroupDocs.Conversion per .NET. È possibile scaricare la libreria da[pagina di download](https://releases.groupdocs.com/conversion/net/).
### Ottieni una licenza
 Per sfruttare tutto il potenziale di GroupDocs.Conversion per .NET, avrai bisogno di una licenza valida. È possibile ottenere una licenza da[GroupDocs](https://purchase.groupdocs.com/buy) richiedere una licenza temporanea a scopo di test[Qui](https://purchase.groupdocs.com/temporary-license/).

## Importa spazi dei nomi
Assicurati di aver importato gli spazi dei nomi necessari nel tuo progetto .NET per utilizzare le funzionalità GroupDocs.Conversion. Ecco come puoi farlo:
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Passaggio 1: definire la cartella di output e il nome del file
Innanzitutto, specifica la cartella di output in cui verrà salvato il file PDF convertito, insieme al nome del file desiderato.
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "cdr-converted-to.pdf");
```
Assicurati di sostituire`"Your Document Directory"` con il percorso della cartella di output desiderata.
## Passaggio 2: caricare il file CDR di origine
Successivamente, carica il file CDR di origine che desideri convertire in PDF utilizzando GroupDocs.Conversion.
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_CDR))
{
    // La logica di conversione andrà qui
}
```
 Sostituire`Constants.SAMPLE_CDR` con il percorso del tuo file CDR effettivo.
## Passaggio 3: specificare le opzioni di conversione
Definire le opzioni di conversione, come specificare il formato di output (PDF) ed eventuali impostazioni aggiuntive.
```csharp
var options = new PdfConvertOptions();
```
Puoi personalizzare le opzioni di conversione in base alle tue esigenze.
## Passaggio 4: eseguire la conversione
Esegui il processo di conversione con le opzioni specificate.
```csharp
converter.Convert(outputFile, options);
```
Questo comando convertirà il file CDR in PDF e lo salverà nella cartella di output specificata con il nome file fornito.
## Passaggio 5: conferma il completamento della conversione
Infine, visualizza un messaggio che conferma il corretto completamento del processo di conversione.
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```
Questo messaggio ti informerà sulla posizione in cui viene salvato il file PDF convertito.

## Conclusione
In questo tutorial, abbiamo imparato come convertire file di grafica vettoriale CorelDRAW (CDR) in formato PDF utilizzando GroupDocs.Conversion per .NET. Seguendo i passaggi descritti, puoi integrare perfettamente le funzionalità di conversione dei documenti nelle tue applicazioni .NET, migliorandone la funzionalità e l'usabilità.
## Domande frequenti
### GroupDocs.Conversion for .NET è compatibile con tutte le versioni dei file CorelDRAW?
GroupDocs.Conversion per .NET supporta un'ampia gamma di versioni di CorelDRAW, garantendo la compatibilità con la maggior parte dei file CDR.
### Posso convertire più file CDR contemporaneamente utilizzando GroupDocs.Conversion per .NET?
Sì, puoi convertire in batch più file CDR in PDF o altri formati utilizzando GroupDocs.Conversion per .NET, migliorando l'efficienza e la produttività.
### GroupDocs.Conversion per .NET richiede una connessione Internet per la conversione dei documenti?
No, GroupDocs.Conversion for .NET esegue la conversione dei documenti localmente sul tuo computer, eliminando la necessità di una connessione Internet durante il processo di conversione.
### Posso personalizzare le impostazioni di conversione in base alle mie esigenze specifiche?
Sì, GroupDocs.Conversion per .NET fornisce ampie opzioni di personalizzazione, consentendoti di personalizzare il processo di conversione per soddisfare le tue precise esigenze.
### È disponibile il supporto tecnico per GroupDocs.Conversion per .NET?
 Sì, GroupDocs offre supporto tecnico completo per i suoi prodotti, incluso GroupDocs.Conversion per .NET. Puoi chiedere assistenza a[Forum di assistenza](https://forum.groupdocs.com/c/conversion/11) per qualsiasi domanda o problema.