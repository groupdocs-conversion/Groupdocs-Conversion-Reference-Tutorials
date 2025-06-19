---
"description": "Apprenez à convertir facilement des fichiers SVG en PDF avec GroupDocs.Conversion pour .NET. Simplifiez votre gestion documentaire."
"linktitle": "Convertir SVG en PDF"
"second_title": "API .NET GroupDocs.Conversion"
"title": "Convertir SVG en PDF"
"url": "/fr/net/file-format-conversion-tutorials/convert-svg-to-pdf/"
"weight": 15
---

# Convertir SVG en PDF

## Introduction
Dans le monde de la programmation, la conversion de fichiers d'un format à un autre est une tâche courante. Qu'il s'agisse d'images, de documents ou d'autres supports, il est crucial de pouvoir convertir facilement d'un format à l'autre. Dans ce tutoriel, nous allons découvrir comment convertir des fichiers SVG (Scalable Vector Graphics) en PDF (Portable Document Format) avec GroupDocs.Conversion pour .NET.
## Prérequis
Avant de vous lancer dans le processus de conversion, assurez-vous d’avoir configuré les conditions préalables suivantes :
### 1. Installer GroupDocs.Conversion pour .NET
Assurez-vous que GroupDocs.Conversion pour .NET est installé dans votre environnement de développement. Si ce n'est pas déjà fait, vous pouvez le télécharger depuis le [site web](https://releases.groupdocs.com/conversion/net/).
### 2. Obtenir un exemple de fichier SVG
Vous aurez besoin d'un fichier SVG d'exemple pour convertir en PDF. Si vous n'en avez pas, vous pouvez facilement trouver des fichiers SVG en ligne ou en créer un à l'aide de divers outils de conception graphique.
### 3. Compréhension de base de C#
Familiarisez-vous avec les bases du langage de programmation C#, car nous l'utiliserons pour écrire le code de conversion.

## Importer des espaces de noms
Tout d’abord, importons les espaces de noms nécessaires :
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Étape 1 : Définir le dossier et le fichier de sortie
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "svg-converted-to.pdf");
```
Assurez-vous de remplacer `"Your Document Directory"` avec le chemin vers votre répertoire de sortie souhaité.
## Étape 2 : charger le fichier SVG source
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_SVG))
{
    // Le code de conversion va ici
}
```
Remplacer `Constants.SAMPLE_SVG` avec le chemin vers votre fichier SVG.
## Étape 3 : Définir les options de conversion
```csharp
var options = new PdfConvertOptions();
```
Ici, nous configurons des options de conversion spécifiques à la sortie PDF. Vous pouvez personnaliser ces options selon vos besoins.
## Étape 4 : Effectuer la conversion
```csharp
converter.Convert(outputFile, options);
```
Cette ligne exécute le processus de conversion, en prenant le fichier SVG source et en le convertissant en PDF avec les options spécifiées.
## Étape 5 : Vérifier la fin de la conversion
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
Cette ligne génère un message confirmant la réussite du processus de conversion, ainsi que le répertoire dans lequel se trouve le fichier PDF converti.

## Conclusion
Dans ce tutoriel, nous avons appris à convertir des fichiers SVG en PDF avec GroupDocs.Conversion pour .NET. En suivant le guide étape par étape et en vous assurant de disposer des prérequis, vous pourrez intégrer facilement les fonctionnalités de conversion de format de fichier à vos applications .NET.
## FAQ
### GroupDocs.Conversion pour .NET est-il compatible avec tous les frameworks .NET ?
Oui, GroupDocs.Conversion pour .NET prend en charge plusieurs frameworks .NET, notamment .NET Core et .NET Framework.
### Puis-je personnaliser les options de conversion pour des formats de sortie spécifiques ?
Absolument ! GroupDocs.Conversion pour .NET offre de nombreuses options de personnalisation pour chaque format de sortie pris en charge.
### GroupDocs.Conversion pour .NET prend-il en charge la conversion par lots ?
Oui, vous pouvez convertir plusieurs fichiers simultanément à l’aide de GroupDocs.Conversion pour .NET.
### Existe-t-il une version d'essai disponible à des fins de test ?
Oui, vous pouvez accéder à une version d'essai gratuite à partir de [ici](https://releases.groupdocs.com/).
### Où puis-je obtenir une assistance technique pour GroupDocs.Conversion pour .NET ?
Vous pouvez trouver du support technique et de l'assistance sur le forum GroupDocs [ici](https://forum.groupdocs.com/c/conversion/11).