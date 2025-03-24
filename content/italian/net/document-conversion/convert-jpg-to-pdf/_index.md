---
title: Converti JPG in PDF
linktitle: Converti JPG in PDF
second_title: API GroupDocs.Conversion .NET
description: Converti JPG in PDF senza sforzo utilizzando GroupDocs.Conversion per .NET. Segui questo tutorial passo passo per convertire i documenti senza problemi.
weight: 14
url: /it/net/document-conversion/convert-jpg-to-pdf/
---

# Converti JPG in PDF

## introduzione

Stai cercando di convertire file JPG in PDF senza sforzo utilizzando GroupDocs.Conversion per .NET? Questo tutorial ti guiderà attraverso il processo passo dopo passo. GroupDocs.Conversion per .NET è una potente API che ti consente di convertire facilmente vari formati di documenti, comprese le immagini, in PDF. Immergiamoci!

## Prerequisiti

Prima di iniziare, assicurati di possedere i seguenti prerequisiti:

1.  GroupDocs.Conversion per .NET: assicurati di aver installato GroupDocs.Conversion per .NET. Puoi scaricarlo da[Qui](https://releases.groupdocs.com/conversion/net/).
2. Ambiente di sviluppo: disporre di un ambiente di sviluppo configurato, ad esempio Visual Studio, insieme a .NET Framework o .NET Core.
3. File JPG di esempio: prepara un file JPG di esempio che desideri convertire in PDF.

## Importa spazi dei nomi

Innanzitutto, importiamo gli spazi dei nomi necessari:

```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```

Ora suddividiamo il processo di conversione in semplici passaggi:

## Passaggio 1: definire la directory di output e il nome del file

```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "jpg-converted-to.pdf");
```

Assicurati di specificare la directory in cui desideri salvare il file PDF convertito e il nome del file di output desiderato.

## Passaggio 2: carica il file JPG di origine e converti in PDF

```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_JPG))
{
    var options = new PdfConvertOptions();
    converter.Convert(outputFile, options);
}
```

 Inizializza il`Converter` oggetto con il percorso del file JPG di esempio. Quindi, configura le opzioni di conversione, ad esempio specificando le opzioni di conversione PDF. Infine, chiama il`Convert` metodo, passando il percorso del file di output e le opzioni di conversione.

## Passaggio 3: visualizza il messaggio di completamento della conversione

```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```

Una volta completata la conversione, viene visualizzato un messaggio che indica l'avvenuta conversione e la posizione del file PDF convertito.

## Conclusione

Convertire file JPG in PDF utilizzando GroupDocs.Conversion per .NET è semplice con solo poche righe di codice. Seguendo questo tutorial, puoi integrare perfettamente le funzionalità di conversione dei documenti nelle tue applicazioni .NET.

## Domande frequenti

### D: Posso convertire più file JPG in PDF contemporaneamente?

R: Sì, puoi convertire più file JPG in PDF eseguendo l'iterazione su ciascun file ed eseguendo il processo di conversione descritto nel tutorial.

### D: GroupDocs.Conversion supporta altri formati di immagine oltre a JPG?

R: Sì, GroupDocs.Conversion supporta vari formati di immagine come PNG, TIFF, BMP e GIF, tra gli altri.

### D: Posso personalizzare il file PDF di output utilizzando le opzioni di conversione?

R: Assolutamente! GroupDocs.Conversion fornisce un'ampia gamma di opzioni di conversione che ti consentono di personalizzare il PDF di output in base alle tue esigenze.

### D: È disponibile una versione di prova di GroupDocs.Conversion per .NET?

R: Sì, puoi accedere a una versione di prova gratuita di GroupDocs.Conversion per .NET da[Qui](https://releases.groupdocs.com/).

### D: Dove posso chiedere aiuto se riscontro problemi durante il processo di conversione?

 R: Se riscontri problemi o hai domande riguardanti GroupDocs.Conversion per .NET, non esitare a visitare il[Forum GroupDocs.Conversion](https://forum.groupdocs.com/c/conversion/11) per assistenza.