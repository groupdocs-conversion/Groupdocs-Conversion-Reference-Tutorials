---
"description": "Convertissez facilement des images BMP en PDF grâce à GroupDocs.Conversion pour .NET. Options personnalisables pour un rendu optimal."
"linktitle": "Convertir des images BMP en PDF"
"second_title": "API .NET GroupDocs.Conversion"
"title": "Convertir des images BMP en PDF"
"url": "/fr/net/file-conversion-to-pdf/convert-bmp-to-pdf/"
"weight": 11
type: docs
---
# Convertir des images BMP en PDF

## Introduction
GroupDocs.Conversion pour .NET offre une solution puissante pour convertir facilement des images BMP au format PDF. Ce tutoriel vous guidera pas à pas.
### Prérequis
Avant de commencer, assurez-vous d’avoir les éléments suivants :
1. GroupDocs.Conversion pour .NET : installez la bibliothèque en la téléchargeant à partir du [lien de téléchargement](https://releases.groupdocs.com/conversion/net/).
2. Fichier BMP source : préparez le fichier image BMP que vous souhaitez convertir.

## Importer des espaces de noms
Tout d’abord, importez les espaces de noms nécessaires pour accéder aux classes et méthodes requises :
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Étape 1 : définir le dossier de sortie et le nom du fichier
Définissez le chemin du dossier de sortie et le nom du fichier PDF converti :
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "bmp-converted-to.pdf");
```
## Étape 2 : Charger le fichier BMP source
Chargez le fichier BMP source à l'aide de la `Converter` classe:
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_BMP))
{
    // La logique de conversion va ici
}
```
## Étape 3 : Configurer les options de conversion
Spécifiez les options de conversion. Dans ce cas, nous utiliserons `PdfConvertOptions` pour la conversion au format PDF :
```csharp
var options = new PdfConvertOptions();
```
## Étape 4 : Convertir un fichier BMP en PDF
Effectuez la conversion et enregistrez le fichier PDF converti :
```csharp
converter.Convert(outputFile, options);
```
## Étape 5 : Vérifier la conversion
Vérifiez si la conversion est réussie et affichez le chemin du dossier de sortie :
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
Félicitations ! Vous avez réussi à convertir une image BMP en PDF avec GroupDocs.Conversion pour .NET.

## Conclusion
En conclusion, GroupDocs.Conversion pour .NET offre une solution simple et performante pour convertir des images BMP au format PDF. En suivant les étapes décrites dans ce tutoriel, vous pourrez intégrer facilement cette fonctionnalité à vos applications .NET.
## FAQ
### GroupDocs.Conversion pour .NET est-il compatible avec tous les formats d'image BMP ?
GroupDocs.Conversion pour .NET prend en charge une large gamme de formats d'image BMP, garantissant la compatibilité avec la plupart des fichiers BMP.
### Puis-je personnaliser les options de conversion pour plus de contrôle sur le PDF de sortie ?
Oui, vous pouvez personnaliser diverses options de conversion telles que le DPI, la taille de la page, l'orientation, etc. pour adapter le PDF de sortie en fonction de vos besoins.
### GroupDocs.Conversion pour .NET nécessite-t-il des dépendances supplémentaires ?
Non, GroupDocs.Conversion pour .NET est une bibliothèque autonome qui ne nécessite aucune dépendance supplémentaire pour les tâches de conversion de base.
### Existe-t-il une version d'essai disponible pour tester avant d'acheter ?
Oui, vous pouvez télécharger une version d'essai gratuite à partir du [page des communiqués](https://releases.groupdocs.com/) pour évaluer les fonctionnalités de la bibliothèque avant de procéder à un achat.
### Où puis-je obtenir de l’aide ou de l’assistance si je rencontre des problèmes ?
Vous pouvez visiter le [Forum GroupDocs.Conversion](https://forum.groupdocs.com/c/conversion/11) pour obtenir de l'aide auprès de la communauté ou contactez directement le support pour une aide personnalisée.