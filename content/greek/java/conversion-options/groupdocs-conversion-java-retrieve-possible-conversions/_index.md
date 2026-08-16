---
date: '2026-07-29'
description: Ανακαλύψτε πώς να καταγράψετε τις μορφές και να ανακτήσετε όλες τις δυνατές
  μετατροπές χρησιμοποιώντας GroupDocs.Conversion for Java, ιδανικό για ροές εργασίας
  μετατροπής αρχείων σε αποθήκευση cloud.
keywords:
- how to list formats
- cloud storage file conversion
- GroupDocs.Conversion Java
lastmod: '2026-07-29'
og_description: Μάθετε πώς να καταγράψετε τις μορφές και να ανακτήσετε όλες τις δυνατές
  μετατροπές χρησιμοποιώντας GroupDocs.Conversion for Java. Ιδανικό για pipelines
  μετατροπής αρχείων σε αποθήκευση cloud.
og_image_alt: 'Guide: List formats and get conversion matrix with GroupDocs.Conversion
  Java'
og_title: Πώς να καταγράψετε τις μορφές με GroupDocs.Conversion for Java
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
title: Πώς να καταγράψετε τις μορφές με GroupDocs.Conversion for Java
type: docs
url: /el/java/conversion-options/groupdocs-conversion-java-retrieve-possible-conversions/
weight: 1
---

# Πώς να Λίστα Μορφές και Να Ανακτήσετε Όλες τις Πιθανές Μετατροπές με το GroupDocs.Conversion για Java

Σε πολλά έργα επεξεργασίας εγγράφων το πρώτο βήμα είναι να γνωρίζετε **πώς να λίστα μορφές** που υποστηρίζει η μηχανή μετατροπής. Αυτό το tutorial σας δείχνει, βήμα προς βήμα, πώς να ερωτήσετε το GroupDocs.Conversion για Java, να ανακτήσετε κάθε ζεύγος πηγή‑προς‑προορισμό και να εφαρμόσετε αυτή τη γνώση σε pipelines μετατροπής αρχείων σε cloud storage. Στο τέλος θα έχετε μια επαναχρησιμοποιήσιμη μέθοδο που επιστρέφει ολόκληρο τον πίνακα μετατροπών, καθώς και πρακτικές συμβουλές για απόδοση και διαχείριση σφαλμάτων.

## Γρήγορες Απαντήσεις
- **Τι σημαίνει “list formats”;** Επιστρέφει κάθε ζεύγος μετατροπής πηγή‑προς‑προορισμό που μπορεί να διαχειριστεί η βιβλιοθήκη.  
- **Χρειάζομαι άδεια;** Μια δωρεάν δοκιμή λειτουργεί για δοκιμές· απαιτείται πληρωμένη άδεια για παραγωγή.  
- **Μπορεί αυτό να βοηθήσει στη μετατροπή αρχείων σε αποθήκευση cloud;** Ναι—γνωρίζοντας τις υποστηριζόμενες μορφές μπορείτε να αυτοματοποιήσετε τις μετατροπές σε pipelines αποθήκευσης cloud.  
- **Ποια έκδοση της Java απαιτείται;** JDK 8 ή νεότερη.  
- **Είναι η δυνατότητα thread‑safe;** Η παρουσία `Converter` μπορεί να επαναχρησιμοποιηθεί μεταξύ νημάτων, αλλά πρέπει να απελευθερώνονται οι πόροι μετά τη χρήση.

## Τι είναι το “πώς να λίστα μορφές” στο GroupDocs.Conversion;
Η λειτουργία **list formats** επιστρέφει μια συλλογή που περιγράφει κάθε μορφή πηγής μαζί με τις μορφές προορισμού στις οποίες μπορεί να μετατραπεί. Αυτός ο πίνακας δημιουργείται από τους εσωτερικούς κανόνες μετατροπής της βιβλιοθήκης και είναι ουσιώδης για την κατασκευή δυναμικών ροών εργασίας που προσαρμόζονται στις πραγματικές δυνατότητες του GroupDocs.Conversion κατά το χρόνο εκτέλεσης.

## Γιατί να Χρησιμοποιήσετε το GroupDocs.Conversion για Java;
Το GroupDocs.Conversion για Java υποστηρίζει **200+ μορφές εισόδου** και **200+ μορφές εξόδου**, καλύπτοντας τα πάντα από DOCX και PPTX έως PDF/A και τύπους εικόνων. Εκτελείται πλήρως στον διακομιστή, έτσι δεν απαιτούνται προϊόντα Microsoft Office ή Adobe. Το API είναι thread‑safe, μπορεί να επεξεργαστεί έγγραφα με εκατοντάδες σελίδες χωρίς να φορτώνει ολόκληρο το αρχείο στη μνήμη, και ενσωματώνεται άψογα με υπηρεσίες αποθήκευσης cloud όπως AWS S3, Azure Blob και Google Cloud Storage.

## Προαπαιτούμενα
- **Java Development Kit (JDK):** Έκδοση 8 ή νεότερη.  
- **Maven:** Κανονικά ρυθμισμένο στο IDE σας (IntelliJ IDEA, Eclipse, NetBeans κ.λπ.).  
- **GroupDocs.Conversion for Java:** Προστέθηκε ως εξάρτηση Maven (δείτε παρακάτω).  

## Ρύθμιση του GroupDocs.Conversion για Java

Προσθέστε το αποθετήριο GroupDocs και την εξάρτηση στο `pom.xml` σας:

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

### Απόκτηση Άδειας
Ξεκινήστε με μια δωρεάν δοκιμή για να εξερευνήσετε το API. Για παραγωγικά φορτία εργασίας, αγοράστε άδεια ή ζητήστε προσωρινή άδεια αξιολόγησης.

### Βασική Αρχικοποίηση και Ρύθμιση

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

## Πώς να Λίστα Μορφές Χρησιμοποιώντας το GroupDocs.Conversion για Java
`Converter` είναι η κεντρική κλάση που εκτελεί μετατροπές και παρέχει πληροφορίες μορφών. Η μέθοδος `getAllPossibleConversions()` επιστρέφει μια λίστα με όλα τα υποστηριζόμενα ζεύγη μετατροπής πηγή‑προς‑προορισμό. Η `ConversionInfo` αντιπροσωπεύει μια μοναδική αντιστοίχηση μετατροπής μεταξύ μιας πηγής και μιας μορφής προορισμού.

Φορτώστε τη μηχανή `Converter`, καλέστε τη `getAllPossibleConversions()` και θα λάβετε μια λίστα αντικειμένων `ConversionInfo` που περιγράφουν κάθε επιτρεπτό ζεύγος πηγή‑προς‑προορισμό. Αυτή η ενιαία κλήση είναι ό,τι χρειάζεστε για να δημιουργήσετε ένα dropdown επιλογών εξαγωγής, να επικυρώσετε εισερχόμενα αρχεία ή να σχεδιάσετε σενάρια μαζικής μετεγκατάστασης.

### Αρχικοποίηση και Ανάκτηση Μετατροπών
Η κλάση `Converter` είναι η κεντρική μηχανή που παρέχει δυνατότητες μετατροπής και εκθέτει τη μέθοδο `getAllPossibleConversions()`.

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.contracts.PossibleConversions;

public class GetAllPossibleConversionsFeature {
    public static void run() {
        // Initialize the Converter object
        Converter converter = new Converter();
```

### Επανάληψη πάνω σε Πιθανές Μετατροπές

```java
// Retrieve all possible conversions supported by the library
for (PossibleConversions conversions : converter.getAllPossibleConversions()) {
    // Print source format description
    System.out.print(String.format("Source format: %s \n", conversions.getSource().getDescription()));
```

### Προσδιορισμός Τύπων Μετατροπής

```java
// Iterate through each target conversion available for the source format
for (TargetConversion conversion : conversions.getAll()) {
    // Determine if it's a primary or secondary conversion and print details
    System.out.print(String.format("\t...can be converted to %s format as %s conversion.\n",
            conversion.getFormat(),
            conversion.isPrimary() ? "primary" : "secondary"));
}
```

### Πλήρης Συνάρτηση

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

## Περιπτώσεις Χρήσης Μετατροπής Αρχείων σε Cloud Storage
Γνωρίζοντας τον πλήρη πίνακα μετατροπών είναι ιδιαίτερα πολύτιμο όταν δημιουργείτε **υπηρεσίες μετατροπής αρχείων σε cloud storage**:

1. **Δυναμική Ανίχνευση Μορφής:** Όταν ένα αρχείο προσγειώνεται σε cloud storage, μπορείτε άμεσα να ελέγξετε αν η επιθυμητή μορφή προορισμού υποστηρίζεται.  
2. **Μαζική Μεταφορά:** Μετακινήστε μεγάλες βιβλιοθήκες εγγράφων σε μια ενοποιημένη μορφή (π.χ., PDF/A) επαναλαμβάνοντας τους υποστηριζόμενους τύπους πηγής.  
3. **Εξαγωγή Κατά Προτίμηση Χρήστη:** Προσφέρετε στους τελικούς χρήστες ένα dropdown μόνο με τις μορφές στις οποίες το τρέχον έγγραφό τους μπορεί να εξαχθεί, μειώνοντας τα σφάλματα και βελτιώνοντας την εμπειρία χρήστη.

## Σκέψεις για την Απόδοση
- **Διαχείριση Πόρων:** Απελευθερώστε την παρουσία `Converter` ή χρησιμοποιήστε try‑with‑resources εάν δημιουργείτε πολλούς βραχύβιους converters.  
- **Επεξεργασία Μαζικής Επεξεργασίας:** Ομαδοποιήστε πολλά αρχεία σε μία εργασία για να μειώσετε το κόστος.  
- **Caching:** Αποθηκεύστε στην κρυφή μνήμη το αποτέλεσμα της `getAllPossibleConversions()` εάν το ερωτάτε συχνά· ο πίνακας μετατροπών σπάνια αλλάζει κατά το χρόνο εκτέλεσης.  

## Συχνά Προβλήματα και Λύσεις
| Συμπτωμα | Πιθανή Αιτία | Διόρθωση |
|---------|--------------|----------|
| Δεν εμφανίζεται έξοδος | `Converter` δεν έχει αρχικοποιηθεί σωστά | Βεβαιωθείτε ότι το JAR της βιβλιοθήκης βρίσκεται στο classpath και ότι η άδεια έχει φορτωθεί. |
| Η λίστα `TargetConversion` είναι κενή | Χρήση παλιάς έκδοσης βιβλιοθήκης | Αναβαθμίστε στην τελευταία έκδοση του GroupDocs.Conversion. |
| Αιχμές μνήμης σε μεγάλα έγγραφα | Μη απελευθέρωση πόρων του converter | Καλέστε `converter.close()` ή χρησιμοποιήστε try‑with‑resources. |

## Συχνές Ερωτήσεις

**Q: Τι είναι το GroupDocs.Conversion για Java;**  
A: Είναι μια βιβλιοθήκη διακομιστή που υποστηρίζει 200+ μορφές εισόδου και 200+ μορφές εξόδου, επιτρέποντας γρήγορη, χωρίς άδεια μετατροπή εγγράφων χωρίς εξωτερικό λογισμικό.

**Q: Πώς ξεκινάω με το GroupDocs.Conversion;**  
A: Ρυθμίστε το Maven project σας, προσθέστε την εξάρτηση που εμφανίστηκε νωρίτερα, φορτώστε ένα αρχείο άδειας και δημιουργήστε ένα αντικείμενο της κλάσης `Converter` όπως φαίνεται στην ενότητα αρχικοποίησης.

**Q: Μπορώ να μετατρέψω προσαρμοσμένους τύπους αρχείων χρησιμοποιώντας το GroupDocs.Conversion;**  
A: Ναι—μέσω των σημείων επεκτασιμότητας του API μπορείτε να καταχωρίσετε προσαρμοσμένους converters ή να ενσωματώσετε εξωτερικούς χειριστές τρίτων για ιδιόκτητες μορφές.

**Q: Ποια είναι τα κοινά προβλήματα κατά την υλοποίηση μετατροπών;**  
A: Η παράλειψη κλεισίματος του `Converter`, η χρήση παλιάς έκδοσης JAR ή η παραμέληση της χρήσης μνήμης για πολύ μεγάλα PDF. Ακολουθήστε τις παραπάνω συμβουλές διαχείρισης πόρων.

**Q: Πού μπορώ να βρω περισσότερη βοήθεια;**  
A: Επισκεφθείτε την επίσημη [τεκμηρίωση](https://docs.groupdocs.com/conversion/java/) ή θέστε ερωτήσεις στο φόρουμ κοινότητας GroupDocs.

---

**Τελευταία Ενημέρωση:** 2026-07-29  
**Δοκιμάστηκε Με:** GroupDocs.Conversion 25.2 for Java  
**Συγγραφέας:** GroupDocs

## Σχετικά Μαθήματα

- [Μετατροπή Word σε PDF και Άλλες Μορφές Αρχείων με το GroupDocs.Conversion για Java](/conversion/java/)
- [Word σε PDF Java – Απόκρυψη Παρακολουθούμενων Αλλαγών & Επιλογές Μετατροπής](/conversion/java/conversion-options/)
- [Πώς να Παρακολουθήσετε την Πρόοδο Μετατροπής σε Java με το GroupDocs - Ένας Πλήρης Οδηγός](/conversion/java/conversion-events-logging/java-groupdocs-conversion-progress-listener/)