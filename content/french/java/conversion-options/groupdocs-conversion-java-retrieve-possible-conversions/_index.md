---
date: '2026-07-29'
description: Découvrez comment répertorier les formats et récupérer toutes les conversions
  possibles avec GroupDocs.Conversion for Java, idéal pour les flux de travail de
  conversion de fichiers cloud storage.
keywords:
- how to list formats
- cloud storage file conversion
- GroupDocs.Conversion Java
lastmod: '2026-07-29'
og_description: Apprenez à répertorier les formats et à récupérer toutes les conversions
  possibles avec GroupDocs.Conversion for Java. Idéal pour les pipelines de conversion
  de fichiers cloud storage.
og_image_alt: 'Guide: List formats and get conversion matrix with GroupDocs.Conversion
  Java'
og_title: Comment répertorier les formats avec GroupDocs.Conversion for Java
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
title: Comment répertorier les formats avec GroupDocs.Conversion for Java
type: docs
url: /fr/java/conversion-options/groupdocs-conversion-java-retrieve-possible-conversions/
weight: 1
---

# Comment répertorier les formats et récupérer toutes les conversions possibles avec GroupDocs.Conversion pour Java

Dans de nombreux projets de traitement de documents, la première étape consiste à connaître **comment répertorier les formats** que le moteur de conversion prend en charge. Ce tutoriel vous montre, étape par étape, comment interroger GroupDocs.Conversion pour Java, récupérer chaque paire source‑vers‑cible, et appliquer ces connaissances dans les pipelines de conversion de fichiers en stockage cloud. À la fin, vous disposerez d’une méthode réutilisable qui renvoie la matrice complète des conversions, ainsi que de conseils pratiques pour les performances et la gestion des erreurs.

## Réponses rapides
- **Que signifie “list formats” ?** Il renvoie chaque paire de conversion source‑vers‑cible que la bibliothèque peut gérer.  
- **Ai-je besoin d’une licence ?** Un essai gratuit fonctionne pour les tests ; une licence payante est requise pour la production.  
- **Cela peut-il aider à la conversion de fichiers en stockage cloud ?** Oui—connaître les formats pris en charge vous permet d’automatiser les conversions dans les pipelines de stockage cloud.  
- **Quelle version de Java est requise ?** JDK 8 ou supérieur.  
- **La fonctionnalité est‑elle thread‑safe ?** L’instance `Converter` peut être réutilisée entre les threads, mais libérez les ressources après utilisation.

## Qu’est‑ce que “how to list formats” dans GroupDocs.Conversion ?
L’opération **list formats** renvoie une collection qui décrit chaque format source ainsi que les formats cibles dans lesquels il peut être transformé. Cette matrice est générée à partir des règles de conversion internes de la bibliothèque et est essentielle pour créer des flux de travail dynamiques qui s’adaptent aux capacités réelles de GroupDocs.Conversion à l’exécution.

## Pourquoi utiliser GroupDocs.Conversion pour Java ?
GroupDocs.Conversion pour Java prend en charge **plus de 200 formats d’entrée** et **plus de 200 formats de sortie**, couvrant tout, des DOCX et PPTX aux PDF/A et types d’image. Il s’exécute entièrement sur le serveur, aucune installation de Microsoft Office ou de produits Adobe n’est requise. L’API est thread‑safe, peut traiter des documents de plusieurs centaines de pages sans charger le fichier complet en mémoire, et s’intègre parfaitement aux services de stockage cloud tels qu’AWS S3, Azure Blob et Google Cloud Storage.

## Prérequis
- **Java Development Kit (JDK) :** Version 8 ou supérieure.  
- **Maven :** Correctement configuré dans votre IDE (IntelliJ IDEA, Eclipse, NetBeans, etc.).  
- **GroupDocs.Conversion pour Java :** Ajouté en tant que dépendance Maven (voir ci‑dessous).  

## Configuration de GroupDocs.Conversion pour Java
Ajoutez le dépôt GroupDocs et la dépendance à votre `pom.xml` :

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
Commencez avec un essai gratuit pour explorer l’API. Pour les charges de travail en production, achetez une licence ou demandez une licence d’évaluation temporaire.

### Initialisation et configuration de base
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

## Comment répertorier les formats avec GroupDocs.Conversion pour Java
`Converter` est la classe principale qui effectue les conversions et fournit les informations de format. `getAllPossibleConversions()` renvoie une liste de toutes les paires de conversion source‑vers‑cible prises en charge. `ConversionInfo` représente une correspondance de conversion unique entre un format source et un format cible.  

Chargez le moteur `Converter`, appelez `getAllPossibleConversions()`, et vous recevrez une liste d’objets `ConversionInfo` décrivant chaque paire source‑vers‑cible autorisée. Cet appel unique suffit pour créer un menu déroulant d’options d’exportation, valider les fichiers entrants, ou concevoir des scripts de migration par lots.

### Initialiser et récupérer les conversions
La classe `Converter` est le moteur principal qui fournit les capacités de conversion et expose la méthode `getAllPossibleConversions()`.

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.contracts.PossibleConversions;

public class GetAllPossibleConversionsFeature {
    public static void run() {
        // Initialize the Converter object
        Converter converter = new Converter();
```

### Parcourir les conversions possibles
```java
// Retrieve all possible conversions supported by the library
for (PossibleConversions conversions : converter.getAllPossibleConversions()) {
    // Print source format description
    System.out.print(String.format("Source format: %s \n", conversions.getSource().getDescription()));
```

### Déterminer les types de conversion
```java
// Iterate through each target conversion available for the source format
for (TargetConversion conversion : conversions.getAll()) {
    // Determine if it's a primary or secondary conversion and print details
    System.out.print(String.format("\t...can be converted to %s format as %s conversion.\n",
            conversion.getFormat(),
            conversion.isPrimary() ? "primary" : "secondary"));
}
```

### Fonction complète
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

## Cas d’utilisation de conversion de fichiers en stockage cloud
Connaître la matrice complète des conversions est particulièrement utile lors de la création de services de **conversion de fichiers en stockage cloud** :

1. **Détection dynamique de format :** Lorsqu’un fichier arrive dans le stockage cloud, vous pouvez immédiatement vérifier si le format cible souhaité est pris en charge.  
2. **Migration par lots :** Déplacez de grandes bibliothèques de documents vers un format unifié (par ex., PDF/A) en parcourant les types source pris en charge.  
3. **Exportation guidée par l’utilisateur :** Proposez aux utilisateurs finaux un menu déroulant contenant uniquement les formats dans lesquels leur document actuel peut être exporté, réduisant les erreurs et améliorant l’expérience utilisateur.

## Considérations de performance
- **Gestion des ressources :** Libérez l’instance `Converter` ou utilisez try‑with‑resources si vous créez de nombreux convertisseurs à courte durée de vie.  
- **Traitement par lots :** Regroupez plusieurs fichiers en une seule tâche pour réduire la surcharge.  
- **Mise en cache :** Mettez en cache le résultat de `getAllPossibleConversions()` si vous l’interrogez fréquemment ; la matrice de conversion change rarement à l’exécution.

## Problèmes courants et solutions
| Symptôme | Cause probable | Solution |
|----------|----------------|----------|
| Aucun résultat n’apparaît | `Converter` non initialisé correctement | Assurez‑vous que le JAR de la bibliothèque est dans le classpath et que la licence est chargée. |
| La liste `TargetConversion` est vide | Utilisation d’une version de bibliothèque obsolète | Mettez à jour vers la dernière version de GroupDocs.Conversion. |
| Pics de mémoire sur de gros documents | Non libération des ressources du convertisseur | Appelez `converter.close()` ou utilisez try‑with‑resources. |

## Questions fréquentes

**Q : Qu’est‑ce que GroupDocs.Conversion pour Java ?**  
R : C’est une bibliothèque côté serveur qui prend en charge plus de 200 formats d’entrée et plus de 200 formats de sortie, permettant une conversion de documents rapide et sans licence, sans logiciel externe.

**Q : Comment démarrer avec GroupDocs.Conversion ?**  
R : Configurez votre projet Maven, ajoutez la dépendance présentée précédemment, chargez un fichier de licence et instanciez la classe `Converter` comme démontré dans la section d’initialisation.

**Q : Puis‑je convertir des types de fichiers personnalisés avec GroupDocs.Conversion ?**  
R : Oui—grâce aux points d’extensibilité de l’API, vous pouvez enregistrer des convertisseurs personnalisés ou brancher des gestionnaires tiers pour des formats propriétaires.

**Q : Quels sont les pièges courants lors de la mise en œuvre des conversions ?**  
R : Oublier de fermer le `Converter`, utiliser une ancienne version du JAR, ou négliger l’utilisation de la mémoire pour les PDF très volumineux. Suivez les conseils de gestion des ressources ci‑dessus.

**Q : Où puis‑je obtenir plus d’aide ?**  
R : Consultez la [documentation officielle](https://docs.groupdocs.com/conversion/java/) ou posez vos questions sur le forum communautaire de GroupDocs.

---

**Dernière mise à jour :** 2026-07-29  
**Testé avec :** GroupDocs.Conversion 25.2 pour Java  
**Auteur :** GroupDocs

## Tutoriels associés

- [Convertir Word en PDF et autres formats de fichier avec GroupDocs.Conversion pour Java](/conversion/java/)
- [Word vers PDF Java – Masquer les modifications suivies et options de conversion](/conversion/java/conversion-options/)
- [Comment suivre la progression de la conversion en Java avec GroupDocs - Guide complet](/conversion/java/conversion-events-logging/java-groupdocs-conversion-progress-listener/)