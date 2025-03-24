---
title: Convertir SVG en PDF
linktitle: Convertir SVG en PDF
second_title: API GroupDocs.Conversion .NET
description: Apprenez à convertir SVG en PDF à l'aide de GroupDocs.Conversion pour .NET sans effort. Rationalisez votre processus de gestion de documents.
weight: 15
url: /fr/net/file-format-conversion-convert-svg-to-pdf/
---

# Convertir SVG en PDF

## Introduction
Dans le monde de la programmation, convertir des fichiers d'un format à un autre est une tâche courante. Qu'il s'agisse d'images, de documents ou d'autres médias, il est crucial de pouvoir convertir de manière transparente entre les formats. Dans ce didacticiel, nous verrons comment convertir des fichiers SVG (Scalable Vector Graphics) en PDF (Portable Document Format) à l'aide de GroupDocs.Conversion pour .NET.
## Conditions préalables
Avant de vous lancer dans le processus de conversion, assurez-vous d'avoir configuré les conditions préalables suivantes :
### 1. Installez GroupDocs.Conversion pour .NET
Assurez-vous que GroupDocs.Conversion pour .NET est installé dans votre environnement de développement. Si ce n'est pas déjà fait, vous pouvez le télécharger depuis[site web](https://releases.groupdocs.com/conversion/net/).
### 2. Obtenez un exemple de fichier SVG
Vous aurez besoin d'un exemple de fichier SVG pour le convertir en PDF. Si vous n'en avez pas, vous pouvez facilement trouver des fichiers SVG en ligne ou en créer un à l'aide de divers outils de conception graphique.
### 3. Compréhension de base de C#
Familiarisez-vous avec les bases du langage de programmation C#, car nous l'utiliserons pour écrire le code de conversion.

## Importer des espaces de noms
Commençons par importer les espaces de noms nécessaires :
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
 Assurez-vous de remplacer`"Your Document Directory"` avec le chemin d’accès au répertoire de sortie souhaité.
## Étape 2 : Charger le fichier SVG source
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_SVG))
{
    // Le code de conversion va ici
}
```
 Remplacer`Constants.SAMPLE_SVG` avec le chemin d'accès à votre fichier SVG.
## Étape 3 : Définir les options de conversion
```csharp
var options = new PdfConvertOptions();
```
Ici, nous configurons des options de conversion spécifiquement pour la sortie PDF. Vous pouvez personnaliser ces options en fonction de vos besoins.
## Étape 4 : Effectuer la conversion
```csharp
converter.Convert(outputFile, options);
```
Cette ligne exécute le processus de conversion, en prenant le fichier SVG source et en le convertissant en PDF avec les options spécifiées.
## Étape 5 : Vérifier la fin de la conversion
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
Cette ligne génère un message confirmant la réussite du processus de conversion, ainsi que le répertoire où se trouve le fichier PDF converti.

## Conclusion
Dans ce didacticiel, nous avons appris à convertir des fichiers SVG en PDF à l'aide de GroupDocs.Conversion pour .NET. En suivant le guide étape par étape et en vous assurant que vous disposez des conditions préalables, vous pouvez intégrer de manière transparente des fonctionnalités de conversion de format de fichier dans vos applications .NET.
## FAQ
### GroupDocs.Conversion pour .NET est-il compatible avec tous les frameworks .NET ?
Oui, GroupDocs.Conversion pour .NET prend en charge plusieurs frameworks .NET, notamment .NET Core et .NET Framework.
### Puis-je personnaliser les options de conversion pour des formats de sortie spécifiques ?
Absolument! GroupDocs.Conversion pour .NET fournit des options de personnalisation étendues pour chaque format de sortie pris en charge.
### GroupDocs.Conversion pour .NET prend-il en charge la conversion par lots ?
Oui, vous pouvez convertir plusieurs fichiers simultanément à l'aide de GroupDocs.Conversion pour .NET.
### Existe-t-il une version d'essai disponible à des fins de test ?
 Oui, vous pouvez accéder à une version d'essai gratuite à partir de[ici](https://releases.groupdocs.com/).
### Où puis-je obtenir une assistance technique pour GroupDocs.Conversion pour .NET ?
Vous pouvez trouver un support technique et une assistance sur le forum GroupDocs[ici](https://forum.groupdocs.com/c/conversion/11).