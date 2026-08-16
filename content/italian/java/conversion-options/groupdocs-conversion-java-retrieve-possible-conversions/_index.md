---
date: '2026-07-29'
description: Scopri come elencare i formati e recuperare tutte le conversioni possibili
  usando GroupDocs.Conversion for Java, ideale per i flussi di lavoro di conversione
  di file su cloud storage.
keywords:
- how to list formats
- cloud storage file conversion
- GroupDocs.Conversion Java
lastmod: '2026-07-29'
og_description: Impara come elencare i formati e recuperare tutte le conversioni possibili
  usando GroupDocs.Conversion for Java. Ideale per pipeline di conversione di file
  su cloud storage.
og_image_alt: 'Guide: List formats and get conversion matrix with GroupDocs.Conversion
  Java'
og_title: Come elencare i formati con GroupDocs.Conversion for Java
schemas:
- author: GroupDocs
  dateModified: '2026-07-29'
  description: Discover how to list formats and retrieve all possible conversions
    using GroupDocs.Conversion for Java, ideal for cloud storage file conversion workflows.
  headline: How to List Formats with GroupDocs.Conversion for Java
  type: TechArticle
- description: Discover how to list formats and retrieve all possible conversions
    using GroupDocs.Conversion for Java, ideal for cloud storage file conversion workflows.
  name: How to List Formats with GroupDocs.Conversion for Java
  steps:
  - name: '**Dynamic Format Detection:** When a file lands in cloud storage, you can
      instantly query whether the desired target format is supported.'
    text: '**Dynamic Format Detection:** When a file lands in cloud storage, you can
      instantly query whether the desired target format is supported.'
  - name: '**Batch Migration:** Move large document libraries to a unified format
      (e.g., PDF/A) by iterating over supported source types.'
    text: '**Batch Migration:** Move large document libraries to a unified format
      (e.g., PDF/A) by iterating over supported source types.'
  - name: '**User‑Driven Export:** Offer end‑users a dropdown of only the formats
      their current document can be exported to, reducing errors and improving UX.'
    text: '**User‑Driven Export:** Offer end‑users a dropdown of only the formats
      their current document can be exported to, reducing errors and improving UX.'
  type: HowTo
- questions:
  - answer: It is a server‑side library that supports 200+ input and 200+ output formats,
      enabling fast, license‑free document conversion without external software.
    question: What is GroupDocs.Conversion for Java?
  - answer: Set up your Maven project, add the dependency shown earlier, load a license
      file, and instantiate the `Converter` class as demonstrated in the initialization
      section.
    question: How do I start with GroupDocs.Conversion?
  - answer: Yes—through the API’s extensibility points you can register custom converters
      or plug‑in third‑party handlers for proprietary formats.
    question: Can I convert custom file types using GroupDocs.Conversion?
  - answer: Forgetting to close the `Converter`, using an old JAR version, or overlooking
      memory usage for very large PDFs. Follow the resource‑management tips above.
    question: What are common pitfalls when implementing conversions?
  - answer: Visit the official [documentation](https://docs.groupdocs.com/conversion/java/)
      or ask questions in the GroupDocs community forum.
    question: Where can I get more help?
  type: FAQPage
tags:
- convert formats
- GroupDocs.Conversion
- Java document conversion
- cloud storage conversion
title: Come elencare i formati con GroupDocs.Conversion for Java
type: docs
url: /it/java/conversion-options/groupdocs-conversion-java-retrieve-possible-conversions/
weight: 1
---

# Come elencare i formati e recuperare tutte le possibili conversioni con GroupDocs.Conversion per Java

In molti progetti di elaborazione documenti il primo passo è sapere **come elencare i formati** supportati dal motore di conversione. Questo tutorial ti mostra, passo dopo passo, come interrogare GroupDocs.Conversion per Java, recuperare ogni coppia sorgente‑destinazione e applicare queste informazioni nei flussi di conversione di file in cloud storage. Alla fine avrai un metodo riutilizzabile che restituisce la matrice completa delle conversioni, più consigli pratici su performance e gestione degli errori.

## Risposte rapide
- **Cosa significa “elencare i formati”?** Restituisce ogni coppia di conversione sorgente‑destinazione che la libreria può gestire.  
- **È necessaria una licenza?** Una prova gratuita è sufficiente per i test; è richiesta una licenza a pagamento per la produzione.  
- **Può aiutare nella conversione di file in cloud storage?** Sì—conoscere i formati supportati consente di automatizzare le conversioni nei pipeline di cloud storage.  
- **Quale versione di Java è richiesta?** JDK 8 o successiva.  
- **La funzionalità è thread‑safe?** L'istanza `Converter` può essere riutilizzata tra thread, ma è necessario rilasciare le risorse dopo l'uso.

## Cos'è “elencare i formati” in GroupDocs.Conversion?
L'operazione **list formats** restituisce una collezione che descrive ogni formato sorgente insieme ai formati di destinazione in cui può essere trasformato. Questa matrice è generata dalle regole di conversione interne della libreria ed è essenziale per costruire workflow dinamici che si adattano alle reali capacità di GroupDocs.Conversion a runtime.

## Perché usare GroupDocs.Conversion per Java?
GroupDocs.Conversion per Java supporta **oltre 200 formati di input** e **oltre 200 formati di output**, coprendo tutto, da DOCX e PPTX a PDF/A e tipi di immagine. Funziona interamente sul server, quindi non sono richiesti Microsoft Office o prodotti Adobe. L'API è thread‑safe, può elaborare documenti di centinaia di pagine senza caricare l'intero file in memoria e si integra perfettamente con servizi di cloud storage come AWS S3, Azure Blob e Google Cloud Storage.

## Prerequisiti
- **Java Development Kit (JDK):** Versione 8 o più recente.  
- **Maven:** Configurato correttamente nel tuo IDE (IntelliJ IDEA, Eclipse, NetBeans, ecc.).  
- **GroupDocs.Conversion per Java:** Aggiunto come dipendenza Maven (vedi sotto).  

## Configurazione di GroupDocs.Conversion per Java

Aggiungi il repository GroupDocs e la dipendenza al tuo `pom.xml`:

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/conversion/java/</url>
   </repository>
</repositories>
<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-conversion</artifactId>
      <version>25.2</version>
   </dependency>
</dependencies>
```

### Acquisizione della licenza
Inizia con una prova gratuita per esplorare l'API. Per carichi di lavoro di produzione, acquista una licenza o richiedi una licenza di valutazione temporanea.

### Inizializzazione e configurazione di base

```java
import com.groupdocs.conversion.Converter;

public class ConversionSetup {
    public static void main(String[] args) {
        // Initialize the Converter object
        Converter converter = new Converter();
        
        System.out.println("GroupDocs.Conversion for Java has been initialized successfully.");
    }
}
```

## Come elencare i formati usando GroupDocs.Conversion per Java
`Converter` è la classe principale che esegue le conversioni e fornisce informazioni sui formati. `getAllPossibleConversions()` restituisce un elenco di tutte le coppie di conversione sorgente‑destinazione supportate. `ConversionInfo` rappresenta una singola mappatura di conversione tra un formato sorgente e uno di destinazione.  

Carica il motore `Converter`, chiama `getAllPossibleConversions()` e riceverai un elenco di oggetti `ConversionInfo` che descrivono ogni coppia sorgente‑destinazione ammissibile. Questa singola chiamata è tutto ciò di cui hai bisogno per costruire un menu a tendina di opzioni di esportazione, convalidare i file in ingresso o progettare script di migrazione batch.

### Inizializzare e recuperare le conversioni

La classe `Converter` è il motore centrale che fornisce le capacità di conversione ed espone il metodo `getAllPossibleConversions()`.  

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.contracts.PossibleConversions;

public class GetAllPossibleConversionsFeature {
    public static void run() {
        // Initialize the Converter object
        Converter converter = new Converter();
```

### Iterare sulle possibili conversioni

```java
// Retrieve all possible conversions supported by the library
for (PossibleConversions conversions : converter.getAllPossibleConversions()) {
    // Print source format description
    System.out.print(String.format("Source format: %s \n", conversions.getSource().getDescription()));
```

### Determinare i tipi di conversione

```java
// Iterate through each target conversion available for the source format
for (TargetConversion conversion : conversions.getAll()) {
    // Determine if it's a primary or secondary conversion and print details
    System.out.print(String.format("\t...can be converted to %s format as %s conversion.\n",
            conversion.getFormat(),
            conversion.isPrimary() ? "primary" : "secondary"));
}
```

### Funzione completa

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.contracts.PossibleConversions;
import com.groupdocs.conversion.contracts.TargetConversion;

public class GetAllPossibleConversionsFeature {
    public static void run() {
        // Initialize the Converter object
        Converter converter = new Converter();

        // Retrieve all possible conversions supported by the library
        for (PossibleConversions conversions : converter.getAllPossibleConversions()) {
            // Print source format description
            System.out.print(String.format("Source format: %s \n", conversions.getSource().getDescription()));

            // Iterate through each target conversion available for the source format
            for (TargetConversion conversion : conversions.getAll()) {
                // Determine if it's a primary or secondary conversion and print details
                System.out.print(String.format("\t...can be converted to %s format as %s conversion.\n",
                        conversion.getFormat(),
                        conversion.isPrimary() ? "primary" : "secondary"));
            }
        }
    }
}
```

## Casi d'uso per la conversione di file in cloud storage
Conoscere la matrice completa delle conversioni è particolarmente utile quando si costruiscono servizi di **conversione di file in cloud storage**:

1. **Rilevamento dinamico del formato:** Quando un file arriva in cloud storage, puoi interrogare immediatamente se il formato di destinazione desiderato è supportato.  
2. **Migrazione batch:** Sposta grandi librerie di documenti verso un formato unificato (ad esempio, PDF/A) iterando sui tipi sorgente supportati.  
3. **Esportazione guidata dall'utente:** Offri agli utenti finali un menu a tendina contenente solo i formati in cui il loro documento corrente può essere esportato, riducendo errori e migliorando l'esperienza utente.

## Considerazioni sulle prestazioni
- **Gestione delle risorse:** Rilascia l'istanza `Converter` o utilizza try‑with‑resources se crei molti converter a breve durata.  
- **Elaborazione batch:** Raggruppa più file in un unico job per ridurre l'overhead.  
- **Caching:** Memorizza nella cache il risultato di `getAllPossibleConversions()` se lo interroghi frequentemente; la matrice di conversione raramente cambia a runtime.  

## Problemi comuni e soluzioni
| Sintomo | Probabile causa | Soluzione |
|---------|----------------|-----------|
| Nessun output appare | `Converter` non inizializzato correttamente | Assicurati che il JAR della libreria sia nel classpath e che la licenza sia caricata. |
| `TargetConversion` list è vuota | Utilizzo di una versione della libreria obsoleta | Aggiorna all'ultima versione di GroupDocs.Conversion. |
| Picchi di memoria su documenti di grandi dimensioni | Mancata chiusura delle risorse del converter | Chiama `converter.close()` o usa try‑with‑resources. |

## Domande frequenti

**Q: Cos'è GroupDocs.Conversion per Java?**  
A: È una libreria server‑side che supporta oltre 200 formati di input e oltre 200 formati di output, consentendo conversioni rapide di documenti senza software esterno e senza licenza aggiuntiva.

**Q: Come iniziare con GroupDocs.Conversion?**  
A: Configura il tuo progetto Maven, aggiungi la dipendenza mostrata in precedenza, carica un file di licenza e istanzia la classe `Converter` come illustrato nella sezione di inizializzazione.

**Q: Posso convertire tipi di file personalizzati con GroupDocs.Conversion?**  
A: Sì—tramite i punti di estensibilità dell'API è possibile registrare converter personalizzati o integrare gestori di terze parti per formati proprietari.

**Q: Quali sono le insidie più comuni nell'implementare le conversioni?**  
A: Dimenticare di chiudere il `Converter`, utilizzare una versione JAR obsoleta o trascurare l'uso della memoria per PDF molto grandi. Segui i consigli di gestione delle risorse sopra indicati.

**Q: Dove posso trovare ulteriore supporto?**  
A: Visita la [documentazione](https://docs.groupdocs.com/conversion/java/) ufficiale o poni domande nel forum della community di GroupDocs.

---

**Last Updated:** 2026-07-29  
**Tested With:** GroupDocs.Conversion 25.2 for Java  
**Author:** GroupDocs

## Tutorial correlati

- [Converti Word in PDF e altri formati di file con GroupDocs.Conversion per Java](/conversion/java/)
- [Word in PDF Java – Nascondi le modifiche tracciate e opzioni di conversione](/conversion/java/conversion-options/)
- [Come monitorare l'avanzamento della conversione in Java con GroupDocs - Guida completa](/conversion/java/conversion-events-logging/java-groupdocs-conversion-progress-listener/)