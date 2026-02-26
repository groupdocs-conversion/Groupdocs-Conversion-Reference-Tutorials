---
date: '2026-02-26'
description: Apprenez à effectuer la conversion d’e-mails en PDF avec décalage horaire
  en Java en utilisant GroupDocs.Conversion, idéal pour l’archivage et la collaboration
  inter‑zones horaires.
keywords:
- Email to PDF Conversion
- Timezone Offset in Java
- GroupDocs.Conversion for Java
title: Conversion d'e-mails en PDF avec décalage de fuseau horaire en Java à l'aide
  de GroupDocs.Conversion
type: docs
url: /fr/java/email-formats/email-to-pdf-conversion-java-groupdocs/
weight: 1
---

.

# Comment convertir un e‑mail en PDF avec un décalage de fuseau horaire en Java en utilisant GroupDocs.Conversion

Convertir des documents e‑mail en PDF peut être difficile, surtout lorsqu'il est crucial de conserver des informations de fuseau horaire précises. Dans ce tutoriel, vous apprendrez **comment convertir un e‑mail en pdf** avec un décalage de fuseau horaire personnalisé en utilisant GroupDocs.Conversion pour Java. Ce guide vous accompagne à chaque étape — de la configuration du projet à la conversion finale — afin que vous puissiez mettre en œuvre rapidement et en toute confiance une solution fiable de **conversion d'e‑mail en pdf**.

## Réponses rapides
- **Quelle bibliothèque gère la conversion ?** GroupDocs.Conversion pour Java.  
- **Quelle méthode principale définit le fuseau horaire ?** `EmailLoadOptions.setTimeZoneOffset`.  
- **Ai‑je besoin d’une licence ?** Un essai gratuit fonctionne pour les tests ; une licence complète est requise pour la production.  
- **Puis‑je traiter un lot de nombreux e‑mails ?** Oui — encapsulez la boucle de conversion dans une routine de traitement par lots.  
- **Quelle version de Java est requise ?** JDK 8 ou supérieur.  

## Aperçu de la conversion d'e‑mail en PDF
Lorsque vous convertissez un e‑mail (`.eml`, `.msg`, etc.) en PDF, les horodatages originaux sont copiés à l’identique. Si l’e‑mail a été envoyé depuis un fuseau horaire différent, ces horodatages peuvent sembler trompeurs pour les lecteurs d’une autre région. En appliquant un **décalage de fuseau horaire**, vous garantissez que le PDF reflète l’heure locale correcte, préservant le contexte de la communication. C’est le cœur d’une **conversion d’e‑mail en pdf** efficace.

## Pourquoi utiliser GroupDocs.Conversion pour Java ?
- **Large prise en charge des formats** – Gère les fichiers `.eml`, `.msg` et de nombreux autres types d’e‑mail.  
- **Gestion intégrée du fuseau horaire** – `EmailLoadOptions` vous permet de définir les décalages en millisecondes.  
- **Haute performance** – La conversion basée sur le flux réduit l’empreinte mémoire.  
- **Licences prêtes pour l’entreprise** – Options d’essai et d’achat flexibles.  

## Prérequis
Avant de commencer, assurez‑vous d’avoir les éléments suivants :

1. **Bibliothèques et dépendances**  
   - GroupDocs.Conversion pour Java version 25.2 ou ultérieure.  

2. **Configuration de l’environnement**  
   - Java Development Kit (JDK 8+) installé.  
   - Maven comme outil de construction.  

3. **Connaissances**  
   - Programmation Java de base et I/O de fichiers.  
   - Familiarité avec la gestion des dépendances Maven.  

## Configuration de GroupDocs.Conversion pour Java

### Informations d’installation
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
Vous pouvez commencer avec un essai gratuit ou demander une licence temporaire pour tester l’ensemble des fonctionnalités :

- **Essai gratuit** – Téléchargez la bibliothèque et explorez les fonctionnalités de base.  
- **Licence temporaire** – Demandez une licence temporaire [ici](https://purchase.groupdocs.com/temporary-license/).  
- **Achat** – Pour une utilisation à long terme, envisagez d’acheter une licence sur le [site officiel](https://purchase.groupdocs.com/buy).

### Initialisation de base
Voici le code minimal nécessaire pour créer une instance `Converter` et charger un e‑mail avec un décalage de fuseau horaire :

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.load.EmailLoadOptions;

// Initialize GroupDocs.Conversion with necessary load options for email files
EmailLoadOptions loadOptions = new EmailLoadOptions();
loadOptions.setTimeZoneOffset(7200000.0); // Set timezone offset in milliseconds (e.g., 2 hours)
```

## Guide de mise en œuvre

### Options de chargement pour le document e‑mail
Définir le décalage de fuseau horaire garantit que le PDF reflète l’heure locale correcte.

#### Étape 1 – Définir le décalage de fuseau horaire
```java
EmailLoadOptions loadOptions = new EmailLoadOptions();
loadOptions.setTimeZoneOffset(7200000.0); // Set to 2 hours ahead (in milliseconds)
```

*Explication* : `setTimeZoneOffset` ajuste l’horodatage du document du nombre de millisecondes spécifié.

### Configuration et exécution de la conversion

#### Étape 2 – Initialiser l’objet Converter
```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.convert.PdfConvertOptions;

String sourceFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.eml"; // Path to the email document.
String outputPattern = "YOUR_OUTPUT_DIRECTORY/ConvertEmailWithTimezoneOffset-%d.pdf";

List<OutputStream> streamPool = new ArrayList<>();
Converter converter = new Converter(sourceFilePath, () -> loadOptions);
PdfConvertOptions options = new PdfConvertOptions();
```

*Explication* : Le `Converter` est créé avec le chemin du fichier source et une lambda qui fournit les `loadOptions` définies précédemment. Cela lie le réglage du fuseau horaire au processus de conversion.

#### Étape 3 – Exécuter la conversion
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

*Explication* : La méthode `convert` diffuse chaque page PDF vers un fichier nommé de façon unique. Le bloc `try‑finally` garantit que tous les flux sont fermés, évitant les fuites de ressources.

## Applications pratiques
- **Archivage des e‑mails** – Conservez les PDF avec des horodatages précis à des fins légales ou d’audit.  
- **Collaboration inter‑fuseaux horaires** – Les équipes du monde entier voient la même heure locale dans les documents convertis.  
- **Rapports d’e‑mail** – Générez des rapports PDF qui conservent les heures d’envoi/réception d’origine.

Vous pouvez intégrer ce flux de travail avec des systèmes CRM, des plateformes de gestion de documents ou des tâches par lots automatisées afin d’optimiser votre pipeline de documents.

## Considérations de performance
- **Gestion des ressources** – Fermez les flux rapidement (comme indiqué) pour libérer la mémoire.  
- **Traitement par lots** – Parcourez une collection de fichiers `.eml` et réutilisez une seule instance `Converter` lorsque cela est possible.  
- **Ajustement de la JVM** – Modifiez la taille du tas (`-Xmx`) pour les gros lots afin d’éviter `OutOfMemoryError`.

## Problèmes courants et solutions

| Symptôme | Cause probable | Solution |
|----------|----------------|----------|
| `NullPointerException` at `loadOptions` | Options de chargement non transmises correctement | Assurez‑vous que la lambda `() -> loadOptions` est utilisée lors de la création du `Converter`. |
| La sortie PDF est vide | Chemin du fichier d’entrée incorrect ou fichier manquant | Vérifiez que `sourceFilePath` pointe vers un fichier `.eml` existant. |
| Le fuseau horaire n’est pas reflété | Valeur de décalage incorrecte (p. ex. secondes au lieu de millisecondes) | Fournissez le décalage en **millisecondes** (p. ex. `7200000` pour +2 h). |

## Questions fréquemment posées
**Q : Qu’est‑ce que GroupDocs.Conversion pour Java ?**  
R : C’est une bibliothèque puissante qui permet la conversion de documents parmi des dizaines de formats, y compris la conversion d’e‑mail en PDF.

**Q : Comment définir le décalage de fuseau horaire pour les e‑mails ?**  
R : Utilisez `EmailLoadOptions.setTimeZoneOffset(milliseconds)` avant d’initialiser le `Converter`.

**Q : Puis‑je convertir plusieurs formats d’e‑mail avec cette configuration ?**  
R : Oui, la bibliothèque prend en charge les fichiers `.eml`, `.msg` et d’autres types d’e‑mail courants.

**Q : Quels sont les pièges courants lors de la conversion ?**  
R : Dépendances manquantes, chemins de fichiers incorrects, et fournir le décalage dans la mauvaise unité (secondes vs. millisecondes).

**Q : Où puis‑je trouver plus de ressources sur GroupDocs.Conversion ?**  
R : Consultez la [documentation officielle](https://docs.groupdocs.com/conversion/java/) pour des guides détaillés et des références API.

## Ressources
- **Documentation** : Explorez davantage sur [GroupDocs Documentation](https://docs.groupdocs.com/conversion/java/)  
- **Référence API** : Référence API détaillée disponible [ici](https://reference.groupdocs.com/conversion/java/)  
- **Télécharger GroupDocs.Conversion** : Commencez avec la bibliothèque [ici](https://releases.groupdocs.com/conversion/java/)  
- **Achat** : Pour une utilisation à long terme, achetez une licence sur la [page d’achat GroupDocs](https://purchase.groupdocs.com/buy)  
- **Essai gratuit & licence** : Essayez gratuitement ou demandez une licence temporaire sur [GroupDocs Free Trial](https://releases.groupdocs.com/conversion/java/) et [Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Support** : Pour obtenir de l’aide, visitez le [Forum GroupDocs](https://forum.groupdocs.com/c/conversion/10)

Profitez de la puissance de GroupDocs.Conversion pour vos applications Java et bénéficiez dès aujourd’hui de conversions PDF précises et conscientes du fuseau horaire !

---

**Dernière mise à jour :** 2026-02-26  
**Testé avec :** GroupDocs.Conversion 25.2  
**Auteur :** GroupDocs  

---