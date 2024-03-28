---
title: Convertir PPTX en PDF
linktitle: Convertir PPTX en PDF
second_title: API GroupDocs.Conversion .NET
description: Découvrez comment convertir des présentations PowerPoint (PPTX) au format PDF à l'aide de GroupDocs.Conversion pour .NET. Processus de conversion simple et efficace.
type: docs
weight: 29
url: /fr/net/pdf-conversion/convert-pptx-to-pdf/
---
## Introduction
Dans ce didacticiel, nous allons parcourir le processus de conversion d'un fichier de présentation PowerPoint (PPTX) en format de document portable (PDF) à l'aide de la bibliothèque GroupDocs.Conversion pour .NET. Suivez les étapes ci-dessous pour réaliser cette conversion.
## Conditions préalables
Avant de commencer, assurez-vous de disposer des prérequis suivants :
1.  Bibliothèque GroupDocs.Conversion pour .NET : assurez-vous d'avoir installé la bibliothèque GroupDocs.Conversion pour .NET. Vous pouvez le télécharger depuis[ici](https://releases.groupdocs.com/conversion/net/).
2. Environnement de développement : configurez un environnement de développement avec les outils nécessaires comme Visual Studio ou tout autre IDE .NET.

## Importer des espaces de noms
Incluez les espaces de noms nécessaires dans votre projet pour accéder aux fonctionnalités GroupDocs.Conversion.
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Étape 1 : Définir le dossier de sortie et le nom du fichier
Tout d'abord, définissez le dossier de sortie dans lequel le fichier PDF converti sera enregistré et spécifiez le nom du fichier PDF de sortie.
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "pptx-converted-to.pdf");
```
## Étape 2 : Charger le fichier PPTX source
Chargez le fichier de présentation PowerPoint source (PPTX) à l'aide de la bibliothèque GroupDocs.Conversion.
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_PPTX))
{
    // La logique de conversion sera placée ici
}
```
## Étape 3 : Spécifiez les options de conversion
Définissez les options de conversion. Dans ce cas, nous convertissons au format PDF, créez donc une instance de`PdfConvertOptions`.
```csharp
var options = new PdfConvertOptions();
```
## Étape 4 : Effectuer la conversion
 Exécutez le processus de conversion à l'aide du`Convert` et transmettez le chemin du fichier de sortie ainsi que les options de conversion.
```csharp
converter.Convert(outputFile, options);
```
## Étape 5 : Vérifier la sortie
Une fois la conversion terminée avec succès, affichez un message indiquant l'achèvement et l'emplacement du fichier de sortie.
```csharp
Console.WriteLine("\nConversion to PDF completed successfully. \nCheck output in {0}", outputFolder);
```

## Conclusion
Dans ce didacticiel, nous avons appris à convertir un fichier de présentation PowerPoint (PPTX) en format de document portable (PDF) à l'aide de la bibliothèque GroupDocs.Conversion pour .NET. En suivant les étapes décrites ci-dessus, vous pouvez facilement effectuer cette conversion dans vos applications .NET.
## FAQ
### Q : GroupDocs.Conversion est-il compatible avec toutes les versions de .NET ?
R : Oui, GroupDocs.Conversion prend en charge .NET Framework 2.0 et versions ultérieures, notamment .NET Core et .NET Standard.
### Q : Puis-je convertir des fichiers dans des formats autres que PDF ?
R : Oui, GroupDocs.Conversion prend en charge un large éventail de formats de documents pour la conversion, notamment Word, Excel, HTML, etc.
### Q : GroupDocs.Conversion propose-t-il un essai gratuit ?
 R : Oui, vous pouvez accéder à un essai gratuit de GroupDocs.Conversion à partir de[ici](https://releases.groupdocs.com/).
### Q : Comment puis-je obtenir de l'aide pour GroupDocs.Conversion ?
 R : Vous pouvez obtenir de l'aide sur le forum de la communauté GroupDocs.[ici](https://forum.groupdocs.com/c/conversion/11).
### Q : Existe-t-il une licence temporaire disponible pour GroupDocs.Conversion ?
 R : Oui, vous pouvez obtenir une licence temporaire pour GroupDocs.Conversion auprès de[ici](https://purchase.groupdocs.com/temporary-license/).