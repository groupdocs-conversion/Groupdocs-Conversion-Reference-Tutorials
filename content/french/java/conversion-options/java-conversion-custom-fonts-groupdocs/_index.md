---
date: '2026-01-28'
description: Apprenez à convertir une présentation en PDF avec substitution de police
  personnalisée en utilisant GroupDocs.Conversion pour Java. Conservez les polices
  et assurez une apparence cohérente du document.
keywords:
- Java document conversion
- custom fonts in Java
- GroupDocs.Conversion for Java
title: Comment convertir une présentation en PDF avec des polices personnalisées en
  utilisant GroupDocs.Conversion pour Java
type: docs
url: /fr/java/conversion-options/java-conversion-custom-fonts-groupdocs/
weight: 1
---

# Comment convertir une présentation en PDF avec des polices personnalisées en utilisant GroupDocs.Conversion pour Java

Dans les flux de travail modernes, vous devez souvent **convertir une présentation en pdf** tout en conservant l'aspect et la convivialité d'origine. Que vous partagiez un deck client, archiviez du matériel de formation ou automatisiez la génération de rapports, les polices manquantes peuvent ruiner la qualité visuelle. Ce tutoriel vous montre exactement comment préserver les polices lors d'une conversion Java pptx en pdf en utilisant **GroupDocs.Conversion pour Java**.

## Réponses rapides
- **Quel est le principal avantage de la substitution de polices personnalisées ?** Elle garantit que le PDF ressemble exactement à la présentation source, même lorsque les polices d'origine ne sont pas installées sur la machine cible.  
- **Quelle bibliothèque gère la conversion ?** `GroupDocs.Conversion` pour Java.  
- **Ai-je besoin d'une licence ?** Un essai gratuit suffit pour le développement ; une licence commerciale est requise pour la production.  
- **Puis-je l'utiliser dans un projet Maven ?** Oui – il suffit d'ajouter le dépôt et la dépendance indiqués ci-dessous.  
- **Le processus est‑il thread‑safe ?** L'instance `Converter` est légère ; vous pouvez en créer une par thread de conversion.

## Qu'est‑ce que **convertir une présentation en pdf** ?
Cette expression décrit simplement l'action de transformer un fichier PowerPoint (.pptx) en document PDF. La conversion en PDF rend le fichier universellement visualisable, imprimable et plus facile à archiver, tout en préservant la mise en page, les images et le texte.

## Pourquoi utiliser la **substitution de polices personnalisées** ?
- **Cohérence de la marque :** Assurez-vous que les polices d'entreprise apparaissent correctement même sur les machines qui ne les possèdent pas.  
- **Fiabilité multiplateforme :** Les PDF s'affichent de la même manière sur Windows, macOS, Linux et les appareils mobiles.  
- **Réduction des tickets de support :** Plus de « mon PDF a l'air bizarre parce que la police manque ».

## Prérequis
1. **Java Development Kit (JDK)** – version 8 ou supérieure.  
2. **Maven** – pour la gestion des dépendances.  
3. **IDE** – IntelliJ IDEA, Eclipse ou tout éditeur compatible Java.  
4. **Connaissances de base en Java** – vous devez être à l'aise avec les classes et les méthodes.  

## Configuration de GroupDocs.Conversion pour Java

Intégrez la bibliothèque GroupDocs.Conversion dans votre projet Maven. L'extrait XML ci‑dessous ajoute le dépôt officiel et la dépendance requise.

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
- **Essai gratuit :** Téléchargez un essai depuis le site Web de GroupDocs.  
- **Licence temporaire :** Demandez une clé temporaire pour des tests prolongés.  
- **Achat :** Passez à une licence complète une fois que vous êtes satisfait.

Après que Maven ait résolu la dépendance, vous pouvez commencer à coder la logique de conversion.

## Guide d'implémentation

### Étape 1 : Définir les options de chargement de la présentation avec substitution de polices
La méthode suivante crée un objet `PresentationLoadOptions` et indique à GroupDocs comment remplacer les polices manquantes. C'est le cœur de **comment préserver les polices** pendant la conversion.

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.load.PresentationLoadOptions;
import com.groupdocs.conversion.contracts.FontSubstitute;
import java.util.ArrayList;
import java.util.List;

public PresentationLoadOptions definePresentationLoadOptionsWithFontSubstitution() {
    // Initialize PresentationLoadOptions
    PresentationLoadOptions loadOptions = new PresentationLoadOptions();
    
    // Create a list to hold font substitutes
    List<FontSubstitute> fontSubstitutes = new ArrayList<>();
    
    // Add font substitution mappings
    fontSubstitutes.add(FontSubstitute.create("Tahoma", "Arial"));
    fontSubstitutes.add(FontSubstitute.create("Times New Roman", "Arial"));
    
    // Set default font to be used if a specific font is not found
    loadOptions.setDefaultFont("YOUR_DOCUMENT_DIRECTORY/resources/fonts/Helvetica.ttf");
    
    // Apply the font substitutes to the load options
    loadOptions.setFontSubstitutes(fontSubstitutes);
    
    return loadOptions;
}
```

**Explication**  
- **Substitution de polices :** Associe « Tahoma » et « Times New Roman » à « Arial ».  
- **Police par défaut :** Fournit une police de secours (`Helvetica.ttf`) si aucune correspondance n'est trouvée.  

### Étape 2 : Convertir le document de présentation en PDF avec des options avancées
Nous utilisons maintenant les options de chargement de l'étape 1 pour effectuer réellement l'opération de **convertir une présentation en pdf**.

```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.convert.PdfConvertOptions;

public void defineConversionProcessWithAdvancedOptions(PresentationLoadOptions loadOptions) {
    // Specify the path for the converted PDF file
    String convertedFile = "YOUR_OUTPUT_DIRECTORY/ConvertedPresentation.pdf";
    
    // Initialize Converter with the presentation file and load options
    Converter converter = new Converter("YOUR_DOCUMENT_DIRECTORY/Presentation.pptx", () -> loadOptions);
    
    // Set up PDF conversion options (empty for default configuration)
    PdfConvertOptions options = new PdfConvertOptions();
    
    // Perform the conversion from presentation to PDF
    converter.convert(convertedFile, options);
}
```

**Explication**  
- **Initialisation du convertisseur :** Transmet le chemin du PPTX ainsi que les `loadOptions` personnalisées.  
- **Options de conversion PDF :** Vous pouvez ajuster davantage les paramètres (par ex., la qualité d'image) si nécessaire.  

## Applications pratiques
1. **Présentations professionnelles :** Conservez l'identité visuelle de l'entreprise lors du partage de PDF avec des partenaires externes.  
2. **Matériel éducatif :** Convertissez les présentations de cours en PDF pour une étude hors ligne sans vous soucier des polices manquantes.  
3. **Documents juridiques :** Préservez la mise en page exacte des diapositives probantes pour les dépôts judiciaires.  

## Considérations de performance
- **Gestion de la mémoire :** Allouez suffisamment d'espace heap pour les présentations volumineuses (`-Xmx2g` est un bon point de départ).  
- **Limiter les substitutions de polices :** Mappez uniquement les polices dont vous avez réellement besoin ; des mappages excessifs peuvent ralentir le traitement.  
- **Collecte des ordures :** Appelez `System.gc()` après de grandes conversions par lots si vous remarquez des pics de mémoire.  

## Problèmes courants et solutions

| Problème | Solution |
|----------|----------|
| **Fichier de police par défaut manquant** | Vérifiez que le chemin dans `setDefaultFont` pointe vers un fichier `.ttf` valide et que le fichier est lisible. |
| **La conversion se bloque sur un PPTX volumineux** | Augmentez la taille du heap JVM et envisagez de convertir les diapositives par lots. |
| **La police n'est pas substituée comme prévu** | Assurez-vous que le nom de la police source correspond exactement (sensible à la casse) au nom utilisé dans `FontSubstitute.create`. |
| **Le PDF de sortie est vide** | Confirmez que le PPTX source n'est pas corrompu et que le `Converter` pointe vers le bon chemin de fichier. |

## Questions fréquentes

**Q : Quel est le principal avantage d'utiliser des substitutions de polices personnalisées lors des conversions ?**  
R : La substitution de polices personnalisées garantit que le PDF conserve l'apparence prévue, même lorsque les polices d'origine ne sont pas disponibles sur le système cible.

**Q : Comment gérer les polices non prises en charge lors de la conversion ?**  
R : Utilisez la fonctionnalité `FontSubstitute` pour mapper les polices indisponibles à des alternatives, assurant une esthétique de document cohérente.

**Q : Puis-je utiliser GroupDocs.Conversion avec des solutions de stockage cloud ?**  
R : Oui, GroupDocs propose des intégrations permettant des conversions directement depuis des plateformes de stockage cloud telles qu'AWS S3 et Azure Blob Storage.

**Q : Que faire si mon processus de conversion est lent ?**  
R : Optimisez les ressources système, limitez les mappages de substitution de polices et augmentez la taille du heap JVM pour améliorer les performances.

**Q : Ce tutoriel fait-il partie d'une série plus large **document conversion tutorial java** ?**  
R : Absolument — ce guide se concentre sur les polices personnalisées, mais la série couvre également l'extraction d'images, le filigrane et le traitement par lots avec GroupDocs.Conversion pour Java.

## Conclusion
Vous disposez maintenant d'une approche complète et prête pour la production afin de **convertir une présentation en pdf** tout en préservant les polices grâce à **GroupDocs.Conversion pour Java**. En définissant des options de chargement avec des substituts de polices et en exploitant l'API puissante `Converter`, vous pouvez garantir la fidélité visuelle sur n'importe quelle plateforme.

**Étapes suivantes**  
- Expérimentez avec des `PdfConvertOptions` supplémentaires (par ex., définir la conformité PDF/A).  
- Intégrez la logique de conversion dans un service REST pour la génération de PDF à la demande.  
- Explorez d'autres modules GroupDocs tels que `GroupDocs.Annotation` pour ajouter des commentaires aux PDF générés.

---

**Dernière mise à jour :** 2026-01-28  
**Testé avec :** GroupDocs.Conversion 25.2 pour Java  
**Auteur :** GroupDocs  

---