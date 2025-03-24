---
title: Convertir OTG en PDF
linktitle: Convertir OTG en PDF
second_title: API GroupDocs.Conversion .NET
description: Découvrez comment convertir des fichiers OTG en PDF à l'aide de GroupDocs.Conversion pour .NET. Intégration simple, efficace et transparente pour vos projets.
weight: 13
url: /fr/net/pdf-conversion/convert-otg-to-pdf/
---

# Convertir OTG en PDF

## Introduction
La conversion de fichiers OTG (OpenDocument Graphics) au format PDF peut être une tâche cruciale, en particulier lorsqu'il s'agit de systèmes de gestion de documents ou de partage de fichiers sur différentes plates-formes. Dans ce didacticiel, nous vous guiderons tout au long du processus de conversion de fichiers OTG en PDF à l'aide de la bibliothèque GroupDocs.Conversion pour .NET. Allons-y !
## Conditions préalables
Avant de commencer, assurez-vous de disposer des prérequis suivants :
1. GroupDocs.Conversion pour .NET : assurez-vous d'avoir installé la bibliothèque GroupDocs.Conversion pour .NET. Vous pouvez le télécharger depuis[ici](https://releases.groupdocs.com/conversion/net/).
2. Fichier OTG : préparez le fichier OTG que vous souhaitez convertir en PDF dans votre répertoire de documents.

## Importer des espaces de noms
Tout d’abord, vous devez importer les espaces de noms nécessaires dans votre projet .NET. 
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Étape 1 : Définir le répertoire de sortie et le nom du fichier
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "otg-converted-to.pdf");
```
 Dans cette étape, vous définissez le répertoire de sortie dans lequel le fichier PDF converti sera enregistré. Remplacer`"Your Document Directory"` avec le chemin d’accès au répertoire de sortie souhaité.
## Étape 2 : Chargez le fichier OTG source et convertissez-le en PDF
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_OTG))
{
    var options = new PdfConvertOptions();
    // Enregistrer le fichier PDF converti
    converter.Convert(outputFile, options);
}
```
 Ici, nous instancions un nouveau`Converter` objet de la bibliothèque GroupDocs.Conversion, en passant le chemin du fichier OTG source. Ensuite, nous créons`PdfConvertOptions` pour spécifier les options de conversion. Enfin, nous appelons le`Convert` méthode pour convertir le fichier OTG au format PDF.
## Étape 3 : Vérifier la fin de la conversion
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```
Cette étape informe l'utilisateur que le processus de conversion est terminé avec succès et fournit le chemin où le fichier PDF converti est enregistré.

## Conclusion
La conversion de fichiers OTG au format PDF est simplifiée grâce à la bibliothèque GroupDocs.Conversion pour .NET. En suivant les étapes décrites dans ce didacticiel, vous pouvez intégrer de manière transparente cette fonctionnalité dans vos applications .NET, améliorant ainsi l'interopérabilité et l'accessibilité des documents.
## FAQ
### GroupDocs.Conversion peut-il convertir d'autres formats de fichiers que OTG en PDF ?
Oui, GroupDocs.Conversion prend en charge un large éventail de formats de fichiers pour la conversion, notamment DOCX, XLSX, PPTX, HTML, etc.
### GroupDocs.Conversion est-il adapté à un usage commercial ?
Absolument! GroupDocs.Conversion propose des licences commerciales pour les entreprises et les organisations cherchant à tirer parti de ses puissantes capacités de conversion de documents.
### GroupDocs.Conversion fournit-il une assistance technique ?
Oui, GroupDocs propose un support technique dédié pour aider les utilisateurs pour toute question ou problème qu'ils pourraient rencontrer lors de la mise en œuvre.
### Puis-je essayer GroupDocs.Conversion avant d’acheter une licence ?
Oui, vous pouvez bénéficier d'un essai gratuit de GroupDocs.Conversion pour explorer ses fonctionnalités et sa compatibilité avec vos besoins.
### Comment puis-je obtenir une licence temporaire pour GroupDocs.Conversion ?
Vous pouvez obtenir une licence temporaire auprès de GroupDocs à des fins d'évaluation ou pour des projets à court terme en visitant le site temporaire.[Licence](https://purchase.groupdocs.com/temporary-license/).