---
date: '2025-12-20'
description: Apprenez à convertir une présentation en PDF en utilisant GroupDocs.Conversion
  pour Java, y compris la substitution de polices personnalisées et la prise en charge
  de la conversion pptx vers PDF en Java.
keywords:
- Java document conversion
- custom fonts in Java
- GroupDocs.Conversion for Java
title: 'Java : convertir une présentation en PDF avec GroupDocs.Conversion'
type: docs
url: /fr/java/conversion-options/java-conversion-custom-fonts-groupdocs/
weight: 1
---

# Java : Convertir une présentation en PDF avec GroupDocs.Conversion

Dans l'environnement numérique actuel, rapide, **convertir une présentation en PDF** de manière fiable tout en préservant l'aspect original est une capacité indispensable. Que vous partagiez un diaporama destiné à un client, archiviez du matériel de formation ou automatisiez la génération de rapports, les polices manquantes peuvent ruiner l'expérience visuelle. Ce tutoriel vous guide à travers l'utilisation de GroupDocs.Conversion pour Java afin de **convertir une présentation en PDF** avec substitution de polices personnalisées, de sorte que votre sortie ressemble exactement à ce qui était prévu sur n'importe quel appareil.

## Réponses rapides
- **Que signifie “convert presentation to PDF” ?** Il transforme les fichiers PowerPoint (par ex. .pptx) en documents PDF tout en conservant la mise en page, les graphiques et le texte.  
- **Quelle bibliothèque gère la conversion ?** GroupDocs.Conversion for Java.  
- **Ai‑je besoin d’une dépendance Maven ?** Oui – ajoutez la **groupdocs maven dependency** ci‑dessous.  
- **Puis‑je remplacer les polices manquantes ?** Absolument, utilisez `FontSubstitute` pour associer les polices indisponibles à des alternatives.  
- **Une licence est‑elle requise pour la production ?** Oui, une licence GroupDocs valide est nécessaire pour un usage commercial.

## Qu’est‑ce que “convert presentation to PDF” en Java ?
Convertir une présentation en PDF signifie prendre un fichier PowerPoint (généralement .pptx) et générer une version PDF qui reflète les diapositives originales. Le processus implique l'analyse du contenu des diapositives, le rendu des graphiques et l'intégration des polices afin que le PDF s'affiche de manière cohérente sur toutes les plateformes.

## Pourquoi utiliser GroupDocs.Conversion pour cette tâche ?
- **Haute fidélité** – maintient la mise en page exacte, les animations (en images statiques) et les graphiques vectoriels.  
- **Support de polices personnalisées** – vous permet de définir des polices de secours, éliminant les avertissements de “police manquante”.  
- **Compatible Maven** – intégration simple de la **groupdocs maven dependency**.  
- **Multi‑plateforme** – fonctionne sous Windows, Linux et macOS sans binaires natifs supplémentaires.

## Prérequis
1. **Java Development Kit (JDK) 8+** installé.  
2. **Maven** pour la gestion des dépendances (ou Gradle si vous préférez).  
3. Connaissances de base en Java et en structure de projet Maven.  
4. Accès à une licence **GroupDocs.Conversion** (essai ou payante).

## Configuration de GroupDocs.Conversion pour Java

### Configuration Maven (groupdocs maven dependency)

Ajoutez le référentiel et la dépendance à votre `pom.xml` :

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

> **Astuce :** Gardez le numéro de version à jour en vérifiant régulièrement le référentiel Maven de GroupDocs.

### Acquisition de licence
- **Free Trial :** Téléchargez une version d'essai depuis le site Web de GroupDocs.  
- **Temporary License :** Demandez une clé temporaire pour des tests prolongés.  
- **Full License :** Achetez une licence de production une fois que vous êtes satisfait.

## Guide d’implémentation

### Comment convertir une présentation en PDF avec substitution de polices personnalisées

#### Étape 1 : Définir les options de chargement de la présentation avec substitution de polices

Créez une méthode d'assistance qui prépare `PresentationLoadOptions` et associe les polices manquantes aux polices disponibles.

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

**Explication :**  
- **Font Substitution** associe les polices indisponibles (par ex. Tahoma) à une alternative fiable (Arial).  
- **Default Font** fournit une police de secours finale, garantissant que chaque élément de texte possède un glyphe.

#### Étape 2 : Convertir la présentation en PDF en utilisant les options de chargement

Utilisez maintenant la classe `Converter` avec `PdfConvertOptions` pour effectuer la conversion réelle.

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

**Explication :**  
- **Converter Initialization** lie le fichier source `.pptx` aux `loadOptions` personnalisées.  
- **PdfConvertOptions** peut être étendu (par ex. réglage de la qualité d'image) mais les valeurs par défaut fonctionnent pour la plupart des scénarios.

### Cas d’utilisation pratiques

| Scénario | Pourquoi les polices personnalisées sont importantes |
|----------|-------------------------------------------------------|
| **Identité d’entreprise** | Garantit des polices cohérentes avec la marque même sur des machines dépourvues de la police d’entreprise. |
| **Supports d’e‑learning** | Les étudiants reçoivent des PDF qui ressemblent exactement aux diapositives originales, quel que soit le système d’exploitation. |
| **Dépôts juridiques** | Les tribunaux exigent souvent des PDF ; la substitution de polices évite le texte illisible. |

## Considérations de performance
- **Memory Management :** Les présentations volumineuses peuvent consommer beaucoup d'espace du tas. Augmentez le paramètre JVM `-Xmx` si vous rencontrez `OutOfMemoryError`.  
- **Limit Substitutions :** Mappez uniquement les polices dont vous avez réellement besoin ; les mappages inutiles ajoutent une surcharge de traitement.  
- **Reuse Load Options :** Si vous convertissez de nombreux fichiers en lot, créez une fois le `PresentationLoadOptions` et réutilisez‑le.

## Pièges courants et dépannage
1. **Missing Font Files :** Assurez‑vous que le fichier de police de secours (`Helvetica.ttf` dans l’exemple) existe et que le chemin est correct.  
2. **Incorrect Maven Version :** Utiliser une version obsolète de GroupDocs peut ne pas inclure l’API `FontSubstitute`. Mettez à jour vers la dernière version.  
3. **File Path Issues :** Utilisez des chemins absolus ou configurez les ressources Maven pour éviter `FileNotFoundException`.

## Questions fréquentes

**Q : Quel est le principal avantage d’utiliser la substitution de polices personnalisées lors de la conversion d’une présentation en PDF ?**  
A : Elle garantit que la mise en page visuelle reste inchangée même si l’environnement cible ne possède pas les polices originales.

**Q : En quoi “pptx to pdf java” diffère‑t‑il d’une simple copie de fichier ?**  
A : La conversion rend chaque diapositive, intègre les polices et aplatit les graphiques dans un PDF, ce qu’une opération de copie ne peut pas réaliser.

**Q : Puis‑je intégrer cette conversion dans un pipeline CI/CD ?**  
A : Oui — encapsulez le code Java dans un plugin Maven ou un conteneur Docker et invoquez‑le pendant les étapes de construction.

**Q : GroupDocs.Conversion prend‑il en charge les entrées depuis le stockage cloud ?**  
A : Absolument. Vous pouvez transmettre des flux depuis AWS S3, Azure Blob ou Google Cloud Storage directement au `Converter`.

**Q : Ma conversion est lente pour un diaporama de 200 diapositives—des conseils ?**  
A : Augmentez la taille du tas, limitez les substitutions de polices aux essentielles, et envisagez de convertir en lots parallèles si le CPU le permet.

## Conclusion

Vous disposez désormais d’une solution complète, prête pour la production, pour **convertir une présentation en PDF** avec gestion personnalisée des polices en utilisant GroupDocs.Conversion pour Java. En ajoutant la dépendance Maven, en définissant les substituts de polices et en invoquant le convertisseur, vous garantissez que vos PDF ressemblent exactement aux diapositives sources sur n’importe quel appareil.

**Prochaines étapes :**  
- Expérimentez avec des `PdfConvertOptions` supplémentaires comme la compression d’image.  
- Combinez cette logique avec un service de surveillance de fichiers pour automatiser les conversions par lots.  
- Explorez les autres capacités de conversion de GroupDocs (par ex. DOCX → PDF, HTML → PDF).

---

**Dernière mise à jour :** 2025-12-20  
**Testé avec :** GroupDocs.Conversion 25.2  
**Auteur :** GroupDocs