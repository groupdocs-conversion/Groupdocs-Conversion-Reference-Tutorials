---
date: '2026-09-25'
description: Apprenez comment convertir eml en pdf java avec GroupDocs.Conversion,
  en appliquant un timezone offset pour préserver les horodatages corrects. Guide
  étape par étape pour les développeurs Java.
keywords:
- convert eml to pdf java
- email to pdf conversion
- timezone offset java
lastmod: '2026-09-25'
og_description: Apprenez comment convertir eml en pdf java avec GroupDocs.Conversion,
  en appliquant un timezone offset pour préserver les horodatages corrects. Guide
  Java détaillé pour les développeurs.
og_image_alt: 'Java guide: convert eml to pdf with timezone offset using GroupDocs.Conversion'
og_title: Convertir eml en pdf java avec timezone offset en utilisant GroupDocs
schemas:
- author: GroupDocs
  dateModified: '2026-09-25'
  description: Learn how to convert eml to pdf java with GroupDocs.Conversion, applying
    a timezone offset to preserve correct timestamps. Step‑by‑step guide for Java
    developers.
  headline: How to convert eml to pdf java with timezone offset
  type: TechArticle
- description: Learn how to convert eml to pdf java with GroupDocs.Conversion, applying
    a timezone offset to preserve correct timestamps. Step‑by‑step guide for Java
    developers.
  name: How to convert eml to pdf java with timezone offset
  steps:
  - name: '**Libraries & dependencies**'
    text: '**Libraries & dependencies**'
  - name: '**Environment**'
    text: '**Environment**'
  - name: '**Knowledge**'
    text: '**Knowledge**'
  type: HowTo
- questions:
  - answer: It’s a powerful library that enables document conversion across dozens
      of formats, including email to PDF, with built‑in timezone handling.
    question: What is GroupDocs.Conversion for Java?
  - answer: Use `EmailLoadOptions.setTimeZoneOffset(milliseconds)` before initializing
      the `Converter`.
    question: How do I set the timezone offset for emails?
  - answer: Yes, the library supports `.eml`, `.msg`, and other common email file
      types.
    question: Can I convert multiple email formats with this setup?
  - answer: Missing dependencies, incorrect file paths, and providing the offset in
      the wrong unit (seconds vs. milliseconds).
    question: What are common pitfalls during conversion?
  - answer: Visit the [official documentation](https://docs.groupdocs.com/conversion/java/)
      for detailed guides and API references.
    question: Where can I find more resources on GroupDocs.Conversion?
  type: FAQPage
tags:
- convert eml
- GroupDocs.Conversion
- Java email conversion
- timezone offset
- PDF generation
title: Comment convertir eml en pdf java avec timezone offset
type: docs
url: /fr/java/email-formats/email-to-pdf-conversion-java-groupdocs/
weight: 1
---

# Comment convertir eml en pdf java avec décalage de fuseau horaire

Dans ce tutoriel, vous découvrirez comment **convert eml to pdf java** tout en ajustant correctement l'horodatage pour toute différence de fuseau horaire. En utilisant GroupDocs.Conversion for Java, vous verrez un flux de travail complet de bout en bout — de la configuration Maven, au chargement d'un e‑mail avec un décalage personnalisé, jusqu'à la diffusion des fichiers PDF résultants. Les étapes sont rédigées pour les développeurs Java 8+ qui ont besoin de PDF fiables, prêts pour l'archivage, affichant l'heure locale correcte.

## Réponses rapides
- **Quelle bibliothèque gère la conversion ?** GroupDocs.Conversion for Java.  
- **Quelle méthode principale définit le fuseau horaire ?** `EmailLoadOptions.setTimeZoneOffset`.  
- **Ai-je besoin d'une licence ?** Un essai gratuit suffit pour les tests ; une licence complète est requise en production.  
- **Puis-je traiter en lot de nombreux e‑mails ?** Oui — encapsulez la boucle de conversion dans une routine batch.  
- **Quelle version de Java est requise ?** JDK 8 ou ultérieure.  

## Qu'est-ce que convert eml to pdf java ?
L'expression « convert eml to pdf java » décrit le processus consistant à prendre un fichier e‑mail (généralement `.eml` ou `.msg`) et à générer un document PDF à l'aide de code Java. Cette conversion est essentielle pour l'archivage, la conformité légale et le partage multiplateforme, car les PDF conservent la mise en page et sont lisibles universellement.

## Pourquoi utiliser GroupDocs.Conversion for Java ?
GroupDocs.Conversion prend en charge **plus de 70** formats d'entrée et de sortie, y compris `.eml`, `.msg`, `.pdf`, `.docx` et les types d'images. Son `EmailLoadOptions` intégré vous permet de spécifier un décalage de fuseau horaire en millisecondes, garantissant que les horodatages du PDF correspondent à l'heure locale souhaitée. La bibliothèque traite les fichiers en flux, ce qui réduit l'utilisation de la mémoire jusqu'à **80 %** par rapport au chargement du document complet en RAM.

## Prérequis
Avant de commencer, assurez-vous d'avoir :

1. **Bibliothèques et dépendances**  
   - GroupDocs.Conversion for Java version **25.2** ou ultérieure.  

2. **Environnement**  
   - JDK 8+ installé et configuré sur votre machine.  
   - Maven comme outil d'automatisation de construction.  

3. **Connaissances**  
   - Programmation Java de base, notamment la gestion des fichiers I/O.  
   - Familiarité avec la structure `pom.xml` de Maven.  

## Configuration de GroupDocs.Conversion for Java

### Informations d'installation
Ajoutez le dépôt GroupDocs et la dépendance de conversion à votre `pom.xml` :

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

### Acquisition de licence
Vous pouvez commencer avec un essai gratuit ou demander une licence temporaire pour tester l'intégralité des fonctionnalités :

- **Essai gratuit** – Téléchargez la bibliothèque et explorez les fonctionnalités de base.  
- **Licence temporaire** – Demandez une licence temporaire [temporary license page](https://purchase.groupdocs.com/temporary-license/).  
- **Achat** – Pour une utilisation à long terme, envisagez d'acheter une licence sur le [official site](https://purchase.groupdocs.com/buy).  

### Initialisation de base
Voici le code minimal nécessaire pour créer une instance `Converter` et charger un e‑mail avec un décalage de fuseau horaire :

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.load.EmailLoadOptions;

// Initialize GroupDocs.Conversion with necessary load options for email files
EmailLoadOptions loadOptions = new EmailLoadOptions();
loadOptions.setTimeZoneOffset(7200000.0); // Set timezone offset in milliseconds (e.g., 2 hours)
```

## Comment définir le décalage de fuseau horaire ?
`EmailLoadOptions` est une classe de configuration qui contrôle la façon dont les fichiers e‑mail sont chargés pour la conversion. Chargez votre e‑mail avec un décalage personnalisé avant la conversion. La méthode `setTimeZoneOffset` accepte le décalage en **millisecondes**, ainsi un décalage de +2 heures correspond à `7200000`. Cet ajustement réécrit l'horodatage affiché dans le PDF généré. En fournissant le décalage, la bibliothèque recalcule les heures d'envoi et de réception affichées, garantissant que le PDF généré reflète le fuseau horaire local du destinataire. Ceci est particulièrement utile pour les équipes multinationales qui examinent des communications archivées.

```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
loadOptions.setTimeZoneOffset(7200000.0); // Set to 2 hours ahead (in milliseconds)
```

## Comment initialiser l'objet Converter ?
`Converter` est la classe principale qui effectue la conversion de documents en utilisant les options de chargement fournies. Créez un `Converter` en passant le chemin du fichier source et une lambda qui fournit les `loadOptions` définies précédemment. Cela lie le réglage du fuseau horaire au processus de conversion. Il lit l'e‑mail source, applique les paramètres `EmailLoadOptions` — y compris le décalage de fuseau horaire — et prépare le flux de sortie pour la génération du PDF. L'utilisation d'une lambda garantit que les options sont évaluées au moment de la conversion, ce qui est utile lors du traitement de plusieurs fichiers avec des paramètres différents.

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.convert.PdfConvertOptions;

String sourceFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.eml"; // Path to the email document.
String outputPattern = "YOUR_OUTPUT_DIRECTORY/ConvertEmailWithTimezoneOffset-%d.pdf";

List<OutputStream> streamPool = new ArrayList<>();
Converter converter = new Converter(sourceFilePath, () -> loadOptions);
PdfConvertOptions options = new PdfConvertOptions();
```

## Comment exécuter la conversion et diffuser les pages PDF ?
`PdfConvertOptions` spécifie les paramètres de sortie PDF tels que la taille de page, la compression et la qualité d'image. Appelez la méthode `convert`, en fournissant une instance `PdfConvertOptions` et un flux de sortie pour chaque page. Le bloc `try‑finally` garantit que tous les flux sont fermés, évitant les fuites de ressources. Après avoir configuré les options, la méthode `convert` parcourt chaque page de l'e‑mail, écrivant les données PDF dans des flux de sortie séparés. Cette approche vous permet de gérer efficacement les gros e‑mails, chaque page étant traitée et vidée individuellement, minimisant ainsi la consommation de mémoire.

```java
try {
    converter.convert((SaveDocumentStreamForFileType) t -> {
        try {
            OutputStream outputStream = Files.newOutputStream(Paths.get(String.format(outputPattern, streamPool.size())));
            streamPool.add(outputStream);
            return outputStream;
        } catch (IOException e) {
            throw new RuntimeException(e);
        }
    }, options);
} finally {
    for (OutputStream outputStream : streamPool) {
        if (outputStream != null) {
            outputStream.close();
        }
    }
}
```

## Applications pratiques
- **Archivage des e‑mails** – Conservez les PDF avec des horodatages précis à des fins légales ou d'audit.  
- **Collaboration inter‑fuseaux horaires** – Les équipes du monde entier voient la même heure locale dans les documents convertis.  
- **Rapports d'e‑mail** – Générez des rapports PDF qui conservent les heures d'envoi/réception originales pour la conformité.

Vous pouvez intégrer ce flux de travail dans des systèmes CRM, des plateformes de gestion de documents ou des tâches batch automatisées afin d'optimiser votre pipeline de documents.

## Considérations de performance
- **Gestion des ressources** – Fermez les flux rapidement (comme indiqué) pour libérer la mémoire.  
- **Traitement par lots** – Parcourez une collection de fichiers `.eml` et réutilisez une seule instance `Converter` lorsque cela est possible.  
- **Optimisation de la JVM** – Ajustez la taille du tas (`-Xmx`) pour les gros lots afin d'éviter `OutOfMemoryError`.  

## Problèmes courants et solutions

| Symptom | Cause probable | Solution |
|---------|----------------|----------|
| `NullPointerException` at `loadOptions` | Options de chargement non transmises correctement | Assurez‑vous que la lambda `() -> loadOptions` est utilisée lors de la création du `Converter`. |
| La sortie PDF est vide | Chemin du fichier d'entrée incorrect ou fichier manquant | Vérifiez que `sourceFilePath` pointe vers un fichier `.eml` existant. |
| Le fuseau horaire n'est pas reflété | Valeur de décalage incorrecte (par ex., secondes au lieu de millisecondes) | Fournissez le décalage en **millisecondes** (par ex., `7200000` pour +2 h). |

## Questions fréquemment posées
**Q : Qu'est‑ce que GroupDocs.Conversion for Java ?**  
R : C’est une bibliothèque puissante qui permet la conversion de documents parmi des dizaines de formats, y compris les e‑mails en PDF, avec une gestion intégrée du fuseau horaire.

**Q : Comment définir le décalage de fuseau horaire pour les e‑mails ?**  
R : Utilisez `EmailLoadOptions.setTimeZoneOffset(milliseconds)` avant d'initialiser le `Converter`.

**Q : Puis‑je convertir plusieurs formats d'e‑mail avec cette configuration ?**  
R : Oui, la bibliothèque prend en charge les fichiers `.eml`, `.msg` et d'autres types d'e‑mail courants.

**Q : Quels sont les pièges courants lors de la conversion ?**  
R : Dépendances manquantes, chemins de fichiers incorrects, et fournir le décalage dans la mauvaise unité (secondes vs. millisecondes).

**Q : Où puis‑je trouver plus de ressources sur GroupDocs.Conversion ?**  
R : Consultez la [official documentation](https://docs.groupdocs.com/conversion/java/) pour des guides détaillés et des références API.

## Ressources supplémentaires
- **Documentation** : Explorez davantage sur [GroupDocs Documentation](https://docs.groupdocs.com/conversion/java/)  
- **Référence API** : Référence détaillée disponible [API reference](https://reference.groupdocs.com/conversion/java/)  
- **Télécharger GroupDocs.Conversion** : Commencez avec la bibliothèque [GroupDocs.Conversion download page](https://releases.groupdocs.com/conversion/java/)  
- **Achat** : Pour une utilisation à long terme, achetez une licence sur [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy)  
- **Essai gratuit & licence** : Essayez gratuitement ou demandez une licence temporaire sur [GroupDocs Free Trial](https://releases.groupdocs.com/conversion/java/) et [Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Support** : Pour obtenir de l'aide, visitez le [GroupDocs Forum](https://forum.groupdocs.com/c/conversion/10)

Profitez de la puissance de GroupDocs.Conversion pour vos applications Java et bénéficiez dès aujourd'hui de conversions PDF précises et conscientes du fuseau horaire !

---

**Dernière mise à jour :** 2026-09-25  
**Testé avec :** GroupDocs.Conversion 25.2  
**Auteur :** GroupDocs

## Tutoriels associés

- [msg en pdf java – Conversion de formats d'e‑mail avec GroupDocs](/conversion/java/email-formats/)
- [eml en pdf java – Convertir un e‑mail en PDF avec GroupDocs](/conversion/java/pdf-conversion/convert-emails-to-pdfs-groupdocs-java/)
- [Convertir plusieurs types de fichiers avec GroupDocs.Conversion Java – Guide maître](/conversion/java/document-operations/groupdocs-conversion-java-master-document-conversion/)