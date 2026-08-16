---
date: '2026-07-24'
description: 'Conversion d''images Java simplifiée : apprenez comment convertir des
  fichiers CAD en TIFF avec des dimensions personnalisées en utilisant GroupDocs Conversion
  Java. Guide étape par étape pour les développeurs.'
keywords:
- java image conversion
- custom width height
- set image dimensions java
lastmod: '2026-07-24'
og_description: Conversion d'images Java simplifiée. Convertissez des fichiers CAD
  en images TIFF de haute qualité avec une largeur et une hauteur personnalisées en
  utilisant GroupDocs Conversion Java. Suivez notre guide détaillé.
og_image_alt: 'Guide: Convert CAD to TIFF with custom dimensions using GroupDocs Conversion
  Java'
og_title: 'Conversion d''images Java : CAD vers TIFF avec dimensions personnalisées'
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
title: 'Conversion d''images Java : CAD vers TIFF avec dimensions personnalisées'
type: docs
url: /fr/java/cad-formats/cad-conversion-tiff-custom-dimensions-groupdocs-java/
weight: 1
---

# Conversion d'images Java : CAD en TIFF avec dimensions personnalisées

Si vous devez transformer des dessins CAD en images TIFF haute résolution tout en contrôlant la largeur et la hauteur exactes en pixels, **java image conversion** est la solution. En utilisant GroupDocs Conversion Java, vous pouvez rasteriser n'importe quel format CAD pris en charge (DWG, DGN, DXF, etc.) en un fichier TIFF qui s'intègre parfaitement aux rapports, aux portails web ou aux mises en page imprimées. Ce guide vous accompagne à chaque étape — de la configuration du projet à la conversion finale — afin que vous puissiez intégrer le processus dans n'importe quel flux de travail basé sur Java.

## Réponses rapides
- **Quelle bibliothèque devrais-je utiliser pour la conversion d'images Java ?** GroupDocs Conversion Java, une bibliothèque robuste de conversion d'images Java.  
- **Comment définir des dimensions personnalisées pour un fichier CAD ?** Utilisez `CadLoadOptions` et spécifiez `setWidth()` et `setHeight()`.  
- **Puis-je convertir DWG en TIFF en une seule étape ?** Oui — chargez le CAD, définissez les dimensions, puis convertissez avec `ImageConvertOptions`.  
- **Ai-je besoin d'une licence ?** Un essai gratuit suffit pour l'évaluation ; une licence complète débloque toutes les fonctionnalités.  
- **Quelle version de Java est requise ?** Toute version Java 8+ est prise en charge.

## Qu'est-ce que GroupDocs Conversion Java ?
La bibliothèque `GroupDocs Conversion Java` est une solution de **java image conversion** qui prend en charge plus de 110 formats d'entrée et de sortie, y compris tous les principaux types CAD et images raster.  
La classe `Converter` est le composant central qui initie les opérations de conversion de fichiers.  
Elle offre le rendu côté serveur, le redimensionnement et des options spécifiques aux formats, permettant aux développeurs de convertir des fichiers sans installer de visionneuses tierces.

## Pourquoi convertir CAD en TIFF avec des dimensions personnalisées ?
Définir une largeur et une hauteur explicites garantit que le TIFF résultant respecte exactement les contraintes de mise en page des systèmes en aval. En définissant les dimensions en pixels avant la rasterisation, vous évitez les artefacts de mise à l'échelle en aval, maintenez la cohérence des épaisseurs de ligne et assurez que l'image s'intègre parfaitement aux PDF, aux pages web ou aux supports imprimés sans traitement supplémentaire. Cette approche simplifie également les pipelines automatisés où chaque image doit se conformer à une spécification de taille prédéfinie.

- **Préserve la fidélité visuelle :** Rasteriser à 1920 × 1080 px (ou toute taille de votre choix) conserve la netteté des traits et des hachures.  
- **Assure des mises en page cohérentes :** Les images s'intègrent proprement dans les PDF, les pages HTML ou les modèles d'impression sans redimensionnement supplémentaire.  
- **Améliore la compatibilité :** Le format TIFF est universellement accepté sur Windows, macOS, Linux et la plupart des outils de conception, réduisant les problèmes de conversion de format.

## Prérequis
Avant de commencer, assurez-vous d'avoir :

1. **GroupDocs Conversion Java** version 25.2 ou ultérieure (la dernière version est recommandée).  
2. Un IDE Java tel qu'IntelliJ IDEA ou Eclipse.  
3. Maven installé pour la gestion des dépendances.  
4. Connaissances de base en programmation Java et familiarité avec le `pom.xml` de Maven.  

## Configuration de GroupDocs Conversion Java
Ajoutez la dépendance Maven de GroupDocs à votre `pom.xml` :

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-conversion</artifactId>
    <version>25.2</version>
</dependency>
```

**Acquisition de licence :** Vous pouvez obtenir un essai gratuit, demander une licence temporaire pour la pleine fonctionnalité, ou acheter une licence permanente pour débloquer entièrement les fonctionnalités de GroupDocs Conversion.

Une fois votre projet Java correctement lié à ces dépendances, vous êtes prêt à commencer à convertir des fichiers CAD !

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

## Comment convertir CAD en TIFF avec des dimensions personnalisées ?
Convertir des fichiers CAD en TIFF avec des dimensions précises implique de charger le dessin source, de configurer les options de rendu et d'appeler l'API de conversion. En suivant une séquence linéaire — définir la largeur et la hauteur, choisir TIFF comme format de sortie et exécuter la conversion — vous vous assurez que l'image générée correspond exactement aux exigences de taille de vos applications en aval, tout en préservant les détails et la qualité du dessin original.  

1. **Importer les classes requises** (voir étape par étape ci‑dessous).  
2. **Créer une instance de `CadLoadOptions`** et définir `width` et `height` à vos dimensions cibles.  
3. **Instancier `ImageConvertOptions`**, en spécifiant `ImageFileType.Tiff`.  
4. **Appeler la méthode `convert`** sur un objet `Converter`, en passant le chemin source, les options de chargement et les options de conversion.

### Chargement de documents CAD avec dimensions personnalisées (Comment définir les dimensions)

La classe `CadLoadOptions` indique à GroupDocs comment rasteriser le dessin avant la conversion.

`CadLoadOptions` est l'objet de configuration qui définit les paramètres de rendu tels que la largeur, la hauteur et le DPI pour les fichiers CAD.

#### Étape 1 : Importer les bibliothèques nécessaires
```java
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.filetypes.ImageFileType;
import com.groupdocs.conversion.options.convert.ImageConvertOptions;
import com.groupdocs.conversion.options.load.CadLoadOptions;
```

#### Étape 2 : Configurer les options de chargement avec des dimensions personnalisées
```java
String sourceDocumentPath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DWG_WITH_LAYOUTS_AND_LAYERS";
CadLoadOptions loadOptions = new CadLoadOptions();
loadOptions.setWidth(1920); // Specify the desired width in pixels
loadOptions.setHeight(1080); // Specify the desired height in pixels
Converter converter = new Converter(sourceDocumentPath, () -> loadOptions);
```
*Explication :* En configurant `CadLoadOptions`, vous indiquez à **GroupDocs Conversion Java** de rasteriser le dessin CAD à 1920 × 1080 pixels avant tout traitement ultérieur.

### Conversion d'une image CAD en TIFF (Convertir CAD en TIFF)

`ImageConvertOptions` indique à la bibliothèque de produire un fichier TIFF avec les paramètres que vous spécifiez.

`ImageConvertOptions` encapsule tous les paramètres de conversion spécifiques aux images, y compris le format de sortie, la résolution et le niveau de compression.

#### Étape 3 : Configurer les options de conversion
```java
String convertedFilePath = "YOUR_OUTPUT_DIRECTORY/ConvertCadAndSpecifyWidthAndHeight.tiff";
ImageConvertOptions options = new ImageConvertOptions();
options.setFormat(ImageFileType.Tiff); // Set the conversion target to TIFF format
```

#### Étape 4 : Effectuer la conversion
```java
converter.convert(convertedFilePath, options);
```
*Explication :* Définir `ImageFileType.Tiff` indique à **GroupDocs Conversion Java** de produire un fichier TIFF de haute qualité qui respecte la largeur et la hauteur que vous avez définies précédemment.

## Conseils de dépannage et pièges courants
- **Problèmes de chemin de fichier :** Vérifiez que les chemins source et destination sont corrects et que l'application dispose des permissions de lecture/écriture.  
- **Formats non pris en charge :** Assurez-vous que le fichier CAD est l'un des formats supportés (DWG, DGN, DXF, etc.).  
- **Contraintes de mémoire :** Les grands dessins peuvent nécessiter d'augmenter la taille du tas JVM (`-Xmx2g` ou plus).  
- **Problèmes de qualité :** Ajustez les paramètres de résolution de `ImageConvertOptions` si le DPI par défaut ne répond pas à vos exigences de qualité.  

## Applications pratiques
1. **Visualisation architecturale :** Exporter les plans d'étage en TIFF pour des présentations haute résolution.  
2. **Documentation d'ingénierie :** Générer des images standardisées pour inclusion dans les manuels techniques.  
3. **Rapports automatisés :** Intégrer des TIFF dérivés de CAD dans des rapports PDF ou HTML via un pipeline CI.  

## Considérations de performance
- **Optimiser l'utilisation de la mémoire :** Libérez l'instance `Converter` après la conversion (`converter.close()` si applicable).  
- **Traitement par lots :** Parcourez une liste de fichiers CAD et réutilisez une seule configuration `Converter` pour réduire la surcharge.  
- **Restez à jour :** Mettez régulièrement à jour vers la dernière version de GroupDocs Conversion Java pour bénéficier des améliorations de performance et des corrections de bugs.  

## Questions fréquemment posées

**Q :** Quels formats de fichiers GroupDocs Conversion prend‑il en charge ?  
**R :** Il prend en charge plus de 110 formats, y compris les fichiers CAD tels que DWG, DGN, DXF, ainsi que les types d'images, de documents et d'archives courants.  

**Q :** Puis‑je convertir plusieurs fichiers CAD en même temps ?  
**R :** Oui — implémentez une boucle simple qui crée un nouveau `Converter` pour chaque fichier ou réutilisez la même instance avec différents chemins source.  

**Q :** Comment gérer les gros fichiers lors de la conversion ?  
**R :** Augmentez la taille du tas JVM, traitez les fichiers par lots plus petits, ou utilisez les options de streaming fournies par la bibliothèque.  

**Q :** Que faire si la qualité de l'image de sortie n'est pas satisfaisante ?  
**R :** Ajustez le DPI ou les paramètres de mise à l'échelle dans `ImageConvertOptions` pour augmenter la résolution.  

**Q :** Le support est‑il disponible en cas de problème ?  
**R :** GroupDocs propose une documentation exhaustive, des forums communautaires et un support direct pour les clients sous licence.  

## Ressources
- [Documentation GroupDocs](https://docs.groupdocs.com/conversion/java/)
- [Référence API](https://reference.groupdocs.com/conversion/java/)
- [Télécharger la dernière version](https://releases.groupdocs.com/conversion/java/)
- [Acheter des licences](https://purchase.groupdocs.com/buy)
- [Accès à l'essai gratuit](https://releases.groupdocs.com/conversion/java/)
- [Demande de licence temporaire](https://purchase.groupdocs.com/temporary-license/)
- [Forum de support](https://forum.groupdocs.com/c/conversion/10)

---

**Dernière mise à jour :** 2026-07-24  
**Testé avec :** GroupDocs Conversion Java 25.2  
**Auteur :** GroupDocs  

---

## Tutoriels associés

- [convert cad pdf java – Tutoriels de conversion de formats CAD pour GroupDocs.Conversion Java](/conversion/java/cad-formats/)
- [convert pdf to jpg java using GroupDocs.Conversion – Guide](/conversion/java/document-operations/convert-pdf-to-jpg-groupdocs-java/)
- [Comment configurer la licence pour GroupDocs.Conversion Java - Guide étape par étape](/conversion/java/getting-started/groupdocs-conversion-java-license-setup-file-path/)