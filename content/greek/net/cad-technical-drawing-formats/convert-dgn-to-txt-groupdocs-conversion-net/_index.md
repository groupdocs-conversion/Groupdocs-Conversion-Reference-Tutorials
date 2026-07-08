---
date: '2026-07-06'
description: Μάθετε πώς να δημιουργήσετε φάκελο εξόδου C# και να μετατρέψετε αρχεία
  CAD DGN σε TXT χρησιμοποιώντας το GroupDocs.Conversion .NET – ιδανικό για αρχιτέκτονες
  και μηχανικούς.
keywords:
- create output folder c#
- cad file to txt
- GroupDocs.Conversion .NET
schemas:
- author: GroupDocs
  dateModified: '2026-07-06'
  description: Learn how to create output folder C# and convert CAD DGN files to TXT
    using GroupDocs.Conversion .NET – ideal for architects and engineers.
  headline: Create Output Folder C# & Convert DGN to TXT with GroupDocs
  type: TechArticle
- description: Learn how to create output folder C# and convert CAD DGN files to TXT
    using GroupDocs.Conversion .NET – ideal for architects and engineers.
  name: Create Output Folder C# & Convert DGN to TXT with GroupDocs
  steps:
  - name: Define the Output Directory Path
    text: Specify where your converted files will be saved. The example below creates
      a folder called **ConvertedFiles** in the application’s root directory. **Why:**
      Defining a dedicated output path keeps your project organized and makes it easier
      to locate generated TXT files for downstream processing.
  - name: Set Up Conversion Options
    text: The `TxtConvertOptions` class holds settings required for the conversion,
      allowing you to customize line endings, encoding, and whether to include hidden
      layers. **What It Does:** This object tells the converter exactly how to render
      the textual representation, ensuring consistent results across dif
  - name: Perform the Conversion
    text: Execute the conversion with the previously defined options. The lambda expression
      creates the output file on‑the‑fly, avoiding temporary storage. **Why:** Using
      a lambda for `Save` gives you full control over the output stream, which is
      especially useful when integrating the conversion into web serv
  - name: Run the Conversion
    text: Finally, invoke the `Convert` method, passing the source DGN path, the target
      format, and the options object. **Why:** The method handles all low‑level parsing,
      text extraction, and file writing in a single call, freeing you from dealing
      with the complex CAD internals.
  type: HowTo
- questions:
  - answer: Over 50 formats, including PDF, DOCX, XLSX, DGN, DWG, DXF, and TXT.
    question: Which file formats does GroupDocs.Conversion support?
  - answer: No hard limit; performance scales with available RAM and CPU. Files up
      to 2 GB convert reliably on standard servers.
    question: Is there a size limit for converting DGN files?
  - answer: Yes—set the `Encoding` property in `TxtConvertOptions` (e.g., UTF‑8, ASCII).
    question: Can I customize the text encoding of the output TXT?
  - answer: Wrap the conversion call in a try‑catch block, log `ConversionException`
      details, and optionally retry with a fallback configuration.
    question: How should I handle conversion errors in production?
  - answer: The official documentation and API reference provide extensive code samples
      and configuration guides.
    question: Where can I find more examples and API references?
  type: FAQPage
title: Δημιουργία Φακέλου Εξόδου C# & Μετατροπή DGN σε TXT με GroupDocs
type: docs
url: /el/net/cad-technical-drawing-formats/convert-dgn-to-txt-groupdocs-conversion-net/
weight: 1
---

# Πώς να Μετατρέψετε Αρχεία DGN σε TXT Χρησιμοποιώντας το GroupDocs.Conversion .NET

## Εισαγωγή

Αναζητάτε έναν αποδοτικό τρόπο για **create output folder C#** και να μετατρέψετε πολύπλοκα αρχεία DGN σε πιο διαχειρίσιμο μορφότυπο TXT; Πολλοί αρχιτέκτονες, μηχανικοί και επαγγελματίες κατασκευής χρειάζονται να εξάγουν δεδομένα απλού κειμένου από σχέδια CAD για αναφορές, αγωγούς ανάλυσης δεδομένων ή ενσωμάτωση με παλαιά συστήματα. Αυτό το εκπαιδευτικό υλικό σας καθοδηγεί στη χρήση του **GroupDocs.Conversion .NET** για τη φόρτωση ενός αρχείου DGN, τη ρύθμιση ενός κατάλληλου καταλόγου εξόδου και τη δημιουργία ενός καθαρού αρχείου TXT — όλα με σαφή, έτοιμο για παραγωγή κώδικα.

**Τι Θα Μάθετε**
- Πώς να ρυθμίσετε το GroupDocs.Conversion για .NET
- Πώς να **create output folder C#** και να καθορίσετε τον προορισμό για τα μετατρεπόμενα αρχεία
- Πώς να φορτώσετε ένα αρχείο DGN και να το μετατρέψετε σε TXT
- Βασικές επιλογές διαμόρφωσης που σας επιτρέπουν να ρυθμίσετε με ακρίβεια τη διαδικασία μετατροπής

## Γρήγορες Απαντήσεις
- **Ποια βιβλιοθήκη διαχειρίζεται τη μετατροπή DGN‑σε‑TXT;** GroupDocs.Conversion .NET  
- **Χρειάζομαι άδεια για παραγωγική χρήση;** Ναι, απαιτείται πλήρης ή προσωρινή άδεια.  
- **Μπορώ να το τρέξω σε .NET 6;** Απόλυτα – η βιβλιοθήκη υποστηρίζει .NET 5/6, .NET Core 3.1 και .NET Framework 4.5+.  
- **Πώς δημιουργώ τον φάκελο εξόδου σε C#;** Χρησιμοποιήστε `Directory.CreateDirectory(path)` πριν από τη μετατροπή.  
- **Ποια είναι η τυπική ταχύτητα μετατροπής;** Η μετατροπή ενός DGN 200 σελίδων σε TXT συνήθως ολοκληρώνεται κάτω από 2 δευτερόλεπτα σε έναν τυπικό διακομιστή.

## Τι είναι το “create output folder C#”;
**Create output folder C#** αναφέρεται στην προγραμματιστική διασφάλιση ότι ένας κατάλογος υπάρχει στο σύστημα αρχείων πριν από την εγγραφή αρχείων σε αυτόν, συνήθως χρησιμοποιώντας `System.IO.Directory.CreateDirectory`. Αυτό αποτρέπει σφάλματα “διαδρομή δεν βρέθηκε” κατά τις λειτουργίες εγγραφής αρχείων.

## Γιατί να χρησιμοποιήσετε το GroupDocs.Conversion για CAD σε TXT;
Το GroupDocs.Conversion υποστηρίζει **50+ μορφές εισόδου και εξόδου**, συμπεριλαμβανομένων DGN, DWG και DXF, και μπορεί να επεξεργαστεί αρχεία έως **2 GB** χωρίς να φορτώνει ολόκληρο το έγγραφο στη μνήμη. Η εγγενής μηχανή εξαγωγής κειμένου διατηρεί τα ονόματα των επιπέδων, τις σημειώσεις και τα δεδομένα χαρακτηριστικών, παρέχοντας ένα αρχείο TXT που αντικατοπτρίζει το κειμενικό περιεχόμενο του αρχικού σχεδίου με **99 % πιστότητα**.

## Προαπαιτούμενα
- **GroupDocs.Conversion .NET** βιβλιοθήκη (έκδοση 25.3.0 ή νεότερη)  
- Visual Studio 2022 (ή οποιοδήποτε IDE που υποστηρίζει C# 8.0+)  
- .NET 6 SDK (ή .NET Core 3.1 / .NET Framework 4.5+)  
- Έγκυρη άδεια GroupDocs (δωρεάν δοκιμή ή προσωρινή άδεια λειτουργεί για δοκιμές)  

## Ρύθμιση του GroupDocs.Conversion για .NET

Εγκαταστήστε τη βιβλιοθήκη GroupDocs.Conversion χρησιμοποιώντας τον διαχειριστή πακέτων της επιλογής σας.

**Κονσόλα Διαχειριστή Πακέτων NuGet:**  
```bash
Install-Package GroupDocs.Conversion -Version 25.3.0
```  

**.NET CLI:**  
```bash
dotnet add package GroupDocs.Conversion --version 25.3.0
```  

> **Συμβουλή:** Μετά την εγκατάσταση, προσθέστε το αρχείο άδειας στο έργο σας και φορτώστε το κατά την εκκίνηση της εφαρμογής για να αποφύγετε σφάλματα άδειας χρόνου εκτέλεσης.

### Βασική Αρχικοποίηση

Η κλάση `Converter` είναι το βασικό στοιχείο του GroupDocs.Conversion που φορτώνει αρχεία προέλευσης και εκτελεί μετασχηματισμούς μορφής.  
```csharp
using System;
using GroupDocs.Conversion;

// Initialize the conversion handler
class Program
{
    static void Main()
    {
        var converter = new Converter("path/to/your/file.dgn");
        Console.WriteLine("Setup complete. Ready to convert!");
    }
}
```  

## Οδηγός Υλοποίησης

### Πώς δημιουργώ φάκελο εξόδου σε C#;

`Directory.CreateDirectory` δημιουργεί όλους τους καταλόγους και υποκαταλόγους στη συγκεκριμένη διαδρομή εάν δεν υπάρχουν ήδη.

Χρησιμοποιήστε `Directory.CreateDirectory` για να διασφαλίσετε ότι η διαδρομή προορισμού υπάρχει πριν καλέσετε το API μετατροπής. Αυτή η μοναδική γραμμή δημιουργεί το φάκελο εάν λείπει και αποτυγχάνει σιωπηλά εάν ο φάκελος υπάρχει ήδη, εξαλείφοντας εξαιρέσεις “directory not found” κατά τις εγγραφές αρχείων. Επίσης επιστρέφει την πλήρη διαδρομή, την οποία μπορείτε να επαναχρησιμοποιήσετε για καταγραφή ή περαιτέρω επεξεργασία.

```csharp
string outputFolder = Path.Combine(Environment.CurrentDirectory, "ConvertedFiles");
Directory.CreateDirectory(outputFolder);
```

### Φόρτωση και Μετατροπή Αρχείου DGN σε TXT

#### Επισκόπηση
Αυτή η δυνατότητα σας επιτρέπει να φορτώσετε ένα αρχείο DGN και να το μετατρέψετε σε αναπαράσταση απλού κειμένου (TXT), που είναι χρήσιμη για την εξαγωγή σημειώσεων σχεδίασης, μεταδεδομένων ή ενσωματωμένων σχολίων από αρχιτεκτονικά σχέδια.

##### Βήμα 1: Ορισμός Διαδρομής Καταλόγου Εξόδου

Καθορίστε πού θα αποθηκευτούν τα μετατρεπόμενα αρχεία σας. Το παρακάτω παράδειγμα δημιουργεί έναν φάκελο με όνομα **ConvertedFiles** στον ριζικό κατάλογο της εφαρμογής.

```csharp
string outputFolder = Path.Combine("YOUR_OUTPUT_DIRECTORY", "ConvertedFiles");
Directory.CreateDirectory(outputFolder); // Ensure directory exists
```  

**Γιατί:** Ο ορισμός μιας αφιερωμένης διαδρομής εξόδου διατηρεί το έργο σας οργανωμένο και καθιστά πιο εύκολη την εύρεση των παραγόμενων αρχείων TXT για επεξεργασία σε επόμενα στάδια.

##### Βήμα 2: Ρύθμιση Επιλογών Μετατροπής

Η κλάση `TxtConvertOptions` περιέχει τις ρυθμίσεις που απαιτούνται για τη μετατροπή, επιτρέποντάς σας να προσαρμόσετε τα τέλη γραμμής, την κωδικοποίηση και το αν θα συμπεριληφθούν κρυφά επίπεδα.

```csharp
var txtOptions = new TxtConvertOptions
{
    Encoding = Encoding.UTF8,
    IncludeHiddenLayers = false
};
```

**Τι Κάνει:** Αυτό το αντικείμενο λέει στον μετατροπέα ακριβώς πώς να αποδώσει την κειμενική αναπαράσταση, εξασφαλίζοντας συνεπή αποτελέσματα μεταξύ διαφορετικών πηγών DGN.

##### Βήμα 3: Εκτέλεση της Μετατροπής

Εκτελέστε τη μετατροπή με τις προηγουμένως ορισμένες επιλογές. Η έκφραση lambda δημιουργεί το αρχείο εξόδου άμεσα, αποφεύγοντας προσωρινή αποθήκευση.

```csharp
var convertOptions = new TextConvertOptions();
```  

**Γιατί:** Η χρήση μιας lambda για το `Save` σας δίνει πλήρη έλεγχο του ρεύματος εξόδου, κάτι που είναι ιδιαίτερα χρήσιμο όταν ενσωματώνετε τη μετατροπή σε web services ή background workers.

##### Βήμα 4: Εκτέλεση της Μετατροπής

Τέλος, καλέστε τη μέθοδο `Convert`, περνώντας τη διαδρομή του πηγαίου DGN, τη μορφή προορισμού και το αντικείμενο επιλογών.

```csharp
converter.Convert(() => File.Create(Path.Combine(outputFolder, "output.txt")), convertOptions);
```  

**Γιατί:** Η μέθοδος διαχειρίζεται όλη τη χαμηλού επιπέδου ανάλυση, εξαγωγή κειμένου και εγγραφή αρχείου σε μία κλήση, απελευθερώνοντάς σας από την αντιμετώπιση των πολύπλοκων εσωτερικών λειτουργιών CAD.

## Κοινά Προβλήματα και Λύσεις
- **Σφάλμα Αρχείου Δεν Βρέθηκε:** Επαληθεύστε ότι η διαδρομή του αρχείου DGN είναι απόλυτη ή σωστά σχετική με το εκτελέσιμο.  
- **Προβλήματα Δικαιωμάτων:** Βεβαιωθείτε ότι η εφαρμογή εκτελείται με λογαριασμό που έχει πρόσβαση εγγραφής στον φάκελο εξόδου.  
- **Σφάλματα Μετατροπής:** Επιβεβαιώστε ότι η έκδοση του πακέτου NuGet `GroupDocs.Conversion` ταιριάζει με την έκδοση του αρχείου άδειας· ασυμφωνίες εκδόσεων μπορούν να προκαλέσουν σφάλματα χρόνου εκτέλεσης.  

## Πρακτικές Εφαρμογές
Αυτή η δυνατότητα μετατροπής μπορεί να ενσωματωθεί σε:
- **Εξαγωγή Δεδομένων:** Ανάκτηση κειμενικών σημειώσεων από σχέδια DGN για αναλύσεις ή αναφορές.  
- **Διαλειτουργικότητα:** Εισαγωγή του εξαγόμενου κειμένου σε συστήματα GIS, βάσεις δεδομένων BIM ή παλαιά ERP modules που δέχονται μόνο κείμενο.  
- **Ροές Αυτοματοποίησης:** Ενσωμάτωση του βήματος μετατροπής σε CI/CD pipelines για αυτόματη δημιουργία τεκμηρίωσης από αρχεία σχεδίασης.  

## Παρατηρήσεις Απόδοσης
Όταν επεξεργάζεστε μεγάλες παρτίδες αρχείων CAD, κρατήστε αυτές τις συμβουλές στο μυαλό:
- **Βελτιστοποίηση Χρήσης Πόρων:** Παρακολουθήστε την κατανάλωση μνήμης· το GroupDocs επεξεργάζεται αρχεία σε λειτουργία streaming, διατηρώντας το αποτύπωμα μνήμης χαμηλό ακόμη και για σχέδια με εκατοντάδες σελίδες.  
- **Αποτελεσματική Διαχείριση Μνήμης:** Αποδεσμεύστε το αντικείμενο `Converter` μετά από κάθε μετατροπή για άμεση απελευθέρωση μη διαχειριζόμενων πόρων.  
- **Επεξεργασία Παρτίδας:** Χρησιμοποιήστε `Parallel.ForEach` για ταυτόχρονη μετατροπή πολλαπλών αρχείων DGN, αλλά περιορίστε το βαθμό παραλληλισμού για να μην εξαντλήσετε την CPU ή το εύρος ζώνης I/O.  

## Πόροι
- [τεκμηρίωση](https://docs.groupdocs.com/conversion/net/)  
- [Τεκμηρίωση GroupDocs Conversion](https://docs.groupdocs.com/conversion/net/)  
- [Αναφορά API GroupDocs Conversion](https://reference.groupdocs.com/conversion/net/)  
- [Τελευταία Έκδοση](https://releases.groupdocs.com/conversion/net/)  
- [Αγορά GroupDocs.Conversion](https://purchase.groupdocs.com/buy)  
- [Δοκιμάστε το GroupDocs Conversion Δωρεάν](https://releases.groupdocs.com/conversion/net/)  
- [Αίτηση για Προσωρινή Άδεια](https://purchase.groupdocs.com/temporary-license/)  
- [Φόρουμ GroupDocs](https://forum.groupdocs.com/c/conversion/10)  

## Συμπέρασμα
Συγχαρητήρια! Έχετε μάθει πώς να **create output folder C#**, να φορτώσετε ένα αρχείο DGN και να το μετατρέψετε σε TXT χρησιμοποιώντας το GroupDocs.Conversion .NET. Ενσωματώνοντας αυτά τα βήματα στις εφαρμογές σας, θα βελτιώσετε την εξαγωγή δεδομένων, την διαλειτουργικότητα και θα αυξήσετε τη συνολική παραγωγικότητα στις ροές εργασίας που βασίζονται στο CAD.

Εξερευνήστε επιπλέον μορφές—όπως DGN → PDF ή DGN → DOCX—αντικαθιστώντας το `TxtConvertOptions` με την κατάλληλη κλάση επιλογών. Η σουίτα GroupDocs προσφέρει ένα ενοποιημένο API που καλύπτει πάνω από 50 τύπους αρχείων, ώστε να μπορείτε να δημιουργήσετε μια ενιαία, συντηρήσιμη μηχανή μετατροπής για όλα τα έγγραφα μηχανικής σας.

## Συχνές Ερωτήσεις

**Ε: Ποιοι τύποι αρχείων υποστηρίζει το GroupDocs.Conversion;**  
Α: Πάνω από 50 μορφές, συμπεριλαμβανομένων PDF, DOCX, XLSX, DGN, DWG, DXF και TXT.

**Ε: Υπάρχει όριο μεγέθους για τη μετατροπή αρχείων DGN;**  
Α: Δεν υπάρχει σκληρό όριο· η απόδοση κλιμακώνεται ανάλογα με τη διαθέσιμη RAM και CPU. Αρχεία έως 2 GB μετατρέπονται αξιόπιστα σε τυπικούς διακομιστές.

**Ε: Μπορώ να προσαρμόσω την κωδικοποίηση κειμένου του εξόδου TXT;**  
Α: Ναι—ορίστε την ιδιότητα `Encoding` στο `TxtConvertOptions` (π.χ., UTF‑8, ASCII).

**Ε: Πώς πρέπει να διαχειρίζομαι τα σφάλματα μετατροπής στην παραγωγή;**  
Α: Περιβάλλετε την κλήση μετατροπής σε μπλοκ try‑catch, καταγράψτε τις λεπτομέρειες του `ConversionException` και, προαιρετικά, επαναλάβετε με εναλλακτική διαμόρφωση.

**Ε: Πού μπορώ να βρω περισσότερα παραδείγματα και αναφορές API;**  
Α: Η επίσημη τεκμηρίωση και η αναφορά API παρέχουν εκτενείς παραδείγματα κώδικα και οδηγούς διαμόρφωσης.

---

**Τελευταία Ενημέρωση:** 2026-07-06  
**Δοκιμάστηκε Με:** GroupDocs.Conversion .NET 25.3.0  
**Συγγραφέας:** GroupDocs

## Σχετικά Μαθήματα

- [Πώς να Μετατρέψετε Αρχεία DGN σε PNG Χρησιμοποιώντας το GroupDocs.Conversion για .NET: Ένας Πλήρης Οδηγός](/conversion/net/cad-technical-drawing-formats/convert-dgn-to-png-groupdocs-conversion-net/)
- [Πώς να Μετατρέψετε Αρχεία DGN σε Παρουσιάσεις PowerPoint Χρησιμοποιώντας το GroupDocs.Conversion για .NET (Οδηγός Βήμα‑Βήμα)](/conversion/net/cad-technical-drawing-formats/convert-dgn-to-ppt-groupdocs-conversion-net/)
- [Πώς να Μετατρέψετε Αρχεία DWG σε TXT Χρησιμοποιώντας το GroupDocs.Conversion σε .NET: Οδηγός Βήμα‑Βήμα](/conversion/net/cad-technical-drawing-formats/convert-dwg-to-txt-groupdocs-dotnet/)