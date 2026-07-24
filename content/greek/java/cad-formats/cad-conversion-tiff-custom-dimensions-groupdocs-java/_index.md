---
date: '2026-07-24'
description: 'Η μετατροπή εικόνας Java γίνεται εύκολη: μάθετε πώς να μετατρέπετε αρχεία
  CAD σε TIFF με προσαρμοσμένες διαστάσεις χρησιμοποιώντας το GroupDocs Conversion
  Java. Οδηγός βήμα‑βήμα για προγραμματιστές.'
keywords:
- java image conversion
- custom width height
- set image dimensions java
lastmod: '2026-07-24'
og_description: Η μετατροπή εικόνας Java γίνεται εύκολη. Μετατρέψτε αρχεία CAD σε
  εικόνες TIFF υψηλής ποιότητας με προσαρμοσμένο πλάτος και ύψος χρησιμοποιώντας το
  GroupDocs Conversion Java. Ακολουθήστε τον λεπτομερή μας οδηγό.
og_image_alt: 'Guide: Convert CAD to TIFF with custom dimensions using GroupDocs Conversion
  Java'
og_title: 'Μετατροπή εικόνας Java: CAD σε TIFF με προσαρμοσμένες διαστάσεις'
schemas:
- author: GroupDocs
  dateModified: '2026-07-24'
  description: 'Java image conversion made easy: learn how to convert CAD files to
    TIFF with custom dimensions using GroupDocs Conversion Java. Step‑by‑step guide
    for developers.'
  headline: 'Java Image Conversion: CAD to TIFF with Custom Dimensions'
  type: TechArticle
- questions:
  - answer: GroupDocs Conversion Java, a robust Java image conversion library.
    question: What library should I use for Java image conversion?
  - answer: Use `CadLoadOptions` and specify `setWidth()` and `setHeight()`.
    question: How do I set custom dimensions for a CAD file?
  - answer: Yes—load the CAD, set dimensions, then convert with `ImageConvertOptions`.
    question: Can I convert DWG to TIFF in one step?
  - answer: A free trial works for evaluation; a full license unlocks all features.
    question: Do I need a license?
  - answer: Any Java 8+ runtime is supported.
    question: What Java version is required?
  type: FAQPage
tags:
- convert CAD
- GroupDocs Conversion
- Java image conversion
- TIFF
- CAD processing
title: 'Μετατροπή εικόνας Java: CAD σε TIFF με προσαρμοσμένες διαστάσεις'
type: docs
url: /el/java/cad-formats/cad-conversion-tiff-custom-dimensions-groupdocs-java/
weight: 1
---

# Μετατροπή Εικόνας Java: CAD σε TIFF με Προσαρμοσμένες Διαστάσεις

Αν χρειάζεστε να μετατρέψετε σχέδια CAD σε εικόνες TIFF υψηλής ανάλυσης ενώ ελέγχετε το ακριβές πλάτος και ύψος σε εικονοστοιχεία, η **java image conversion** είναι το κλειδί. Χρησιμοποιώντας το GroupDocs Conversion Java, μπορείτε να ραστεροποιήσετε οποιαδήποτε υποστηριζόμενη μορφή CAD (DWG, DGN, DXF, κ.λπ.) σε αρχείο TIFF που ταιριάζει τέλεια σε αναφορές, διαδικτυακές πύλες ή εκτυπώσεις. Αυτός ο οδηγός σας καθοδηγεί βήμα‑βήμα—από τη ρύθμιση του έργου μέχρι την τελική μετατροπή—ώστε να ενσωματώσετε τη διαδικασία σε οποιαδήποτε ροή εργασίας βασισμένη σε Java.

## Σύντομες Απαντήσεις
- **Ποια βιβλιοθήκη πρέπει να χρησιμοποιήσω για τη μετατροπή εικόνας Java;** GroupDocs Conversion Java, a robust Java image conversion library.  
- **Πώς ορίζω προσαρμοσμένες διαστάσεις για ένα αρχείο CAD;** Use `CadLoadOptions` and specify `setWidth()` and `setHeight()`.  
- **Μπορώ να μετατρέψω DWG σε TIFF σε ένα βήμα;** Yes—load the CAD, set dimensions, then convert with `ImageConvertOptions`.  
- **Χρειάζομαι άδεια;** A free trial works for evaluation; a full license unlocks all features.  
- **Ποια έκδοση της Java απαιτείται;** Any Java 8+ runtime is supported.

## Τι είναι το GroupDocs Conversion Java;
Η βιβλιοθήκη `GroupDocs Conversion Java` είναι μια λύση **java image conversion** που υποστηρίζει πάνω από 110 μορφές εισόδου και εξόδου, συμπεριλαμβανομένων όλων των κύριων τύπων CAD και ραστερ εικόνων.  
Η κλάση `Converter` είναι το κύριο στοιχείο που ξεκινά τις λειτουργίες μετατροπής αρχείων.  
Παρέχει απόδοση στην πλευρά του διακομιστή, κλιμάκωση και επιλογές ειδικές για μορφές, επιτρέποντας στους προγραμματιστές να μετατρέπουν αρχεία χωρίς την εγκατάσταση προγραμμάτων προβολής τρίτων.

## Γιατί να Μετατρέψετε CAD σε TIFF με Προσαρμοσμένες Διαστάσεις;
Ο καθορισμός σαφούς πλάτους και ύψους εγγυάται ότι το παραγόμενο TIFF ταιριάζει ακριβώς με τις απαιτήσεις διάταξης των επόμενων συστημάτων. Ορίζοντας τις διαστάσεις σε εικονοστοιχεία πριν από τη ραστεροποίηση, αποφεύγετε τα τεχνάσματα κλιμάκωσης, διατηρείτε τη συνέπεια του πάχους των γραμμών και εξασφαλίζετε ότι η εικόνα ενσωματώνεται άψογα σε PDF, ιστοσελίδες ή έντυπο υλικό χωρίς πρόσθετη επεξεργασία. Αυτή η προσέγγιση απλοποιεί επίσης τις αυτοματοποιημένες γραμμές παραγωγής όπου κάθε εικόνα πρέπει να συμμορφώνεται με μια προκαθορισμένη προδιαγραφή μεγέθους.  

- **Διατηρεί την Οπτική Πιστότητα:** Η ραστεροποίηση σε 1920 × 1080 px (ή οποιοδήποτε μέγεθος επιλέξετε) διατηρεί τις γραμμές και τις γραμμώσεις καθαρές.  
- **Εξασφαλίζει Συνεπείς Διατάξεις:** Οι εικόνες ενσωματώνονται καθαρά σε PDF, σελίδες HTML ή πρότυπα εκτύπωσης χωρίς πρόσθετη αλλαγή μεγέθους.  
- **Αυξάνει τη Συμβατότητα:** Το TIFF είναι καθολικά αποδεκτό σε Windows, macOS, Linux και τα περισσότερα εργαλεία σχεδίασης, μειώνοντας τα προβλήματα μετατροπής μορφών.

## Προαπαιτούμενα
Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

1. **GroupDocs Conversion Java** έκδοση 25.2 ή νεότερη (συνιστάται η πιο πρόσφατη έκδοση).  
2. Ένα IDE Java όπως IntelliJ IDEA ή Eclipse.  
3. Maven εγκατεστημένο για διαχείριση εξαρτήσεων.  
4. Βασικές γνώσεις προγραμματισμού Java και εξοικείωση με το `pom.xml` του Maven.  

## Ρύθμιση του GroupDocs Conversion Java

Προσθέστε την εξάρτηση Maven του GroupDocs στο `pom.xml` σας:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-conversion</artifactId>
    <version>25.2</version>
</dependency>
```

**Απόκτηση Άδειας:** Μπορείτε να αποκτήσετε δωρεάν δοκιμή, να ζητήσετε προσωρινή άδεια για πλήρη λειτουργικότητα ή να αγοράσετε μόνιμη άδεια ώστε να ξεκλειδώσετε πλήρως τις δυνατότητες του GroupDocs Conversion.

Μόλις το έργο Java σας συνδεθεί σωστά με αυτές τις εξαρτήσεις, είστε έτοιμοι να ξεκινήσετε τη μετατροπή αρχείων CAD!

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

## Πώς να Μετατρέψετε CAD σε TIFF με Προσαρμοσμένες Διαστάσεις;

Η μετατροπή αρχείων CAD σε TIFF με ακριβείς διαστάσεις περιλαμβάνει τη φόρτωση του αρχικού σχεδίου, τη διαμόρφωση των επιλογών απόδοσης και την κλήση του API μετατροπής. Ακολουθώντας μια γραμμική ακολουθία—ορίζοντας πλάτος και ύψος, επιλέγοντας TIFF ως μορφή εξόδου και εκτελώντας τη μετατροπή—εξασφαλίζετε ότι η παραγόμενη εικόνα ταιριάζει ακριβώς με τις απαιτήσεις μεγέθους των επόμενων εφαρμογών σας, διατηρώντας ταυτόχρονα τις λεπτομέρειες και την ποιότητα του αρχικού σχεδίου.

1. **Εισάγετε τις απαιτούμενες κλάσεις** (δείτε βήμα‑βήμα παρακάτω).  
2. **Δημιουργήστε ένα αντικείμενο `CadLoadOptions`** και ορίστε `width` και `height` στις επιθυμητές διαστάσεις.  
3. **Δημιουργήστε ένα αντικείμενο `ImageConvertOptions`**, καθορίζοντας `ImageFileType.Tiff`.  
4. **Καλέστε τη μέθοδο `convert`** σε ένα αντικείμενο `Converter`, περνώντας τη διαδρομή προέλευσης, τις επιλογές φόρτωσης και τις επιλογές μετατροπής.  

### Φόρτωση Εγγράφων CAD με Προσαρμοσμένες Διαστάσεις (Πώς να Ορίσετε Διαστάσεις)

Η κλάση `CadLoadOptions` ενημερώνει το GroupDocs πώς να ραστεροποιήσει το σχέδιο πριν από τη μετατροπή.

`CadLoadOptions` είναι το αντικείμενο διαμόρφωσης που ορίζει παραμέτρους απόδοσης όπως πλάτος, ύψος και DPI για αρχεία CAD.

#### Βήμα 1: Εισαγωγή Απαραίτητων Βιβλιοθηκών
```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.filetypes.ImageFileType;
import com.groupdocs.conversion.options.convert.ImageConvertOptions;
import com.groupdocs.conversion.options.load.CadLoadOptions;
```

#### Βήμα 2: Ρύθμιση Επιλογών Φόρτωσης με Προσαρμοσμένες Διαστάσεις
```java
String sourceDocumentPath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DWG_WITH_LAYOUTS_AND_LAYERS";
CadLoadOptions loadOptions = new CadLoadOptions();
loadOptions.setWidth(1920); // Specify the desired width in pixels
loadOptions.setHeight(1080); // Specify the desired height in pixels
Converter converter = new Converter(sourceDocumentPath, () -> loadOptions);
```
*Επεξήγηση:* Με τη διαμόρφωση του `CadLoadOptions`, ενημερώνετε το **GroupDocs Conversion Java** να ραστεροποιήσει το σχέδιο CAD σε 1920 × 1080 εικονοστοιχεία πριν από οποιαδήποτε περαιτέρω επεξεργασία.

### Μετατροπή CAD σε Εικόνα TIFF (Convert CAD to TIFF)

`ImageConvertOptions` καθοδηγεί τη βιβλιοθήκη να παράγει ένα αρχείο TIFF με τις ρυθμίσεις που ορίζετε.

`ImageConvertOptions` περιλαμβάνει όλες τις παραμέτρους μετατροπής ειδικές για εικόνες, συμπεριλαμβανομένης της μορφής εξόδου, της ανάλυσης και του επιπέδου συμπίεσης.

#### Βήμα 3: Διαμόρφωση Επιλογών Μετατροπής
```java
String convertedFilePath = "YOUR_OUTPUT_DIRECTORY/ConvertCadAndSpecifyWidthAndHeight.tiff";
ImageConvertOptions options = new ImageConvertOptions();
options.setFormat(ImageFileType.Tiff); // Set the conversion target to TIFF format
```

#### Βήμα 4: Εκτέλεση της Μετατροπής
```java
converter.convert(convertedFilePath, options);
```
*Επεξήγηση:* Ορίζοντας `ImageFileType.Tiff` καθοδηγεί το **GroupDocs Conversion Java** να δημιουργήσει ένα αρχείο TIFF υψηλής ποιότητας που σέβεται το πλάτος και το ύψος που ορίσατε προηγουμένως.

## Συμβουλές Επίλυσης Προβλημάτων & Συνηθισμένα Πιθανά Σφάλματα
- **Προβλήματα Διαδρομής Αρχείου:** Επαληθεύστε ότι οι διαδρομές προέλευσης και προορισμού είναι σωστές και ότι η εφαρμογή έχει δικαιώματα ανάγνωσης/εγγραφής.  
- **Μη Υποστηριζόμενες Μορφές:** Βεβαιωθείτε ότι το αρχείο CAD είναι μία από τις υποστηριζόμενες μορφές (DWG, DGN, DXF, κ.λπ.).  
- **Περιορισμοί Μνήμης:** Μεγάλα σχέδια μπορεί να απαιτούν αύξηση του μεγέθους heap της JVM (`-Xmx2g` ή μεγαλύτερο).  
- **Ανησυχίες Ποιότητας:** Ρυθμίστε τις ρυθμίσεις ανάλυσης του `ImageConvertOptions` εάν το προεπιλεγμένο DPI δεν ανταποκρίνεται στα πρότυπα ποιότητας.  

## Πρακτικές Εφαρμογές
1. **Αρχιτεκτονική Οπτικοποίηση:** Εξαγωγή σχεδίων ορόφων ως TIFF για παρουσιάσεις υψηλής ανάλυσης.  
2. **Τεχνική Τεκμηρίωση:** Δημιουργία τυποποιημένων εικόνων για ενσωμάτωση σε τεχνικά εγχειρίδια.  
3. **Αυτοματοποιημένες Αναφορές:** Ενσωμάτωση TIFF προερχόμενων από CAD σε αναφορές PDF ή HTML μέσω CI pipeline.  

## Σκέψεις Απόδοσης
- **Βελτιστοποίηση Χρήσης Μνήμης:** Αποδεσμεύστε το αντικείμενο `Converter` μετά τη μετατροπή (`converter.close()` αν είναι εφαρμόσιμο).  
- **Επεξεργασία σε Παρτίδες:** Επανάληψη σε λίστα αρχείων CAD και επαναχρησιμοποίηση μιας ενιαίας διαμόρφωσης `Converter` για μείωση του φόρτου.  
- **Παραμείνετε Ενημερωμένοι:** Αναβαθμίστε τακτικά στην πιο πρόσφατη έκδοση του GroupDocs Conversion Java για να επωφεληθείτε από βελτιώσεις απόδοσης και διορθώσεις σφαλμάτων.  

## Συχνές Ερωτήσεις

**Q:** Ποιες μορφές αρχείων υποστηρίζει το GroupDocs Conversion;  
**A:** Υποστηρίζει πάνω από 110 μορφές, συμπεριλαμβανομένων αρχείων CAD όπως DWG, DGN, DXF, καθώς και κοινών τύπων εικόνας, εγγράφων και αρχείων συμπίεσης.

**Q:** Μπορώ να μετατρέψω πολλαπλά αρχεία CAD ταυτόχρονα;  
**A:** Ναι—εφαρμόστε έναν απλό βρόχο που δημιουργεί ένα νέο `Converter` για κάθε αρχείο ή επαναχρησιμοποιήστε το ίδιο αντικείμενο με διαφορετικές διαδρομές προέλευσης.

**Q:** Πώς να διαχειριστώ μεγάλα μεγέθη αρχείων κατά τη μετατροπή;  
**A:** Αυξήστε το μέγεθος heap της JVM, επεξεργαστείτε τα αρχεία σε μικρότερες παρτίδες ή χρησιμοποιήστε τις επιλογές streaming που παρέχει η βιβλιοθήκη.

**Q:** Τι κάνω αν η ποιότητα της εξόδου εικόνας δεν είναι ικανοποιητική;  
**A:** Ρυθμίστε το DPI ή τις ρυθμίσεις κλιμάκωσης στο `ImageConvertOptions` για αύξηση της ανάλυσης.

**Q:** Υπάρχει υποστήριξη αν αντιμετωπίσω προβλήματα;  
**A:** Το GroupDocs προσφέρει εκτενή τεκμηρίωση, φόρουμ κοινότητας και άμεση υποστήριξη για πελάτες με άδεια.

## Πόροι
- [Τεκμηρίωση GroupDocs](https://docs.groupdocs.com/conversion/java/)
- [Αναφορά API](https://reference.groupdocs.com/conversion/java/)
- [Λήψη Τελευταίας Έκδοσης](https://releases.groupdocs.com/conversion/java/)
- [Αγορά Αδειών](https://purchase.groupdocs.com/buy)
- [Πρόσβαση Δωρεάν Δοκιμής](https://releases.groupdocs.com/conversion/java/)
- [Αίτηση Προσωρινής Άδειας](https://purchase.groupdocs.com/temporary-license/)
- [Φόρουμ Υποστήριξης](https://forum.groupdocs.com/c/conversion/10)

---

**Τελευταία Ενημέρωση:** 2026-07-24  
**Δοκιμή Με:** GroupDocs Conversion Java 25.2  
**Συγγραφέας:** GroupDocs  

## Σχετικές Εκπαιδεύσεις

- [convert cad pdf java – Εκπαιδεύσεις Μετατροπής CAD Μορφών για GroupDocs.Conversion Java](/conversion/java/cad-formats/)
- [convert pdf to jpg java using GroupDocs.Conversion – Οδηγός](/conversion/java/document-operations/convert-pdf-to-jpg-groupdocs-java/)
- [Πώς να Ορίσετε Άδεια για GroupDocs.Conversion Java - Οδηγός Βήμα‑Βήμα](/conversion/java/getting-started/groupdocs-conversion-java-license-setup-file-path/)