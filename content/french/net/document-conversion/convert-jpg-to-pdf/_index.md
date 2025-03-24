---
title: Convertir JPG en PDF
linktitle: Convertir JPG en PDF
second_title: API GroupDocs.Conversion .NET
description: Convertissez facilement des JPG en PDF à l'aide de GroupDocs.Conversion pour .NET. Suivez ce didacticiel étape par étape pour une conversion transparente de documents.
weight: 14
url: /fr/net/document-conversion/convert-jpg-to-pdf/
---

# Convertir JPG en PDF

## Introduction

Cherchez-vous à convertir des fichiers JPG en PDF sans effort à l'aide de GroupDocs.Conversion pour .NET ? Ce tutoriel vous guidera étape par étape tout au long du processus. GroupDocs.Conversion pour .NET est une API puissante qui vous permet de convertir facilement et en toute transparence divers formats de documents, y compris les images, au format PDF. Allons-y !

## Conditions préalables

Avant de commencer, assurez-vous de disposer des prérequis suivants :

1.  GroupDocs.Conversion pour .NET : assurez-vous d'avoir installé GroupDocs.Conversion pour .NET. Vous pouvez le télécharger depuis[ici](https://releases.groupdocs.com/conversion/net/).
2. Environnement de développement : disposez d'un environnement de développement, tel que Visual Studio, avec .NET Framework ou .NET Core.
3. Exemple de fichier JPG : préparez un exemple de fichier JPG que vous souhaitez convertir en PDF.

## Importer des espaces de noms

Commençons par importer les espaces de noms nécessaires :

```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```

Maintenant, décomposons le processus de conversion en étapes simples :

## Étape 1 : Définir le répertoire de sortie et le nom du fichier

```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "jpg-converted-to.pdf");
```

Assurez-vous de spécifier le répertoire dans lequel vous souhaitez enregistrer le fichier PDF converti et le nom du fichier de sortie souhaité.

## Étape 2 : Chargez le fichier JPG source et convertissez-le en PDF

```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_JPG))
{
    var options = new PdfConvertOptions();
    converter.Convert(outputFile, options);
}
```

 Initialisez le`Converter` objet avec le chemin d’accès à votre exemple de fichier JPG. Ensuite, configurez les options de conversion, telles que la spécification des options de conversion PDF. Enfin, appelez le`Convert` méthode, en transmettant le chemin du fichier de sortie et les options de conversion.

## Étape 3 : Afficher le message de fin de conversion

```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```

Une fois la conversion terminée, affichez un message indiquant la conversion réussie et l'emplacement du fichier PDF converti.

## Conclusion

La conversion de fichiers JPG en PDF à l'aide de GroupDocs.Conversion pour .NET est simple avec seulement quelques lignes de code. En suivant ce didacticiel, vous pouvez intégrer de manière transparente les fonctionnalités de conversion de documents dans vos applications .NET.

## FAQ

### Q : Puis-je convertir plusieurs fichiers JPG en PDF simultanément ?

R : Oui, vous pouvez convertir plusieurs fichiers JPG en PDF en parcourant chaque fichier et en effectuant le processus de conversion décrit dans le didacticiel.

### Q : GroupDocs.Conversion prend-il en charge d'autres formats d'image que JPG ?

R : Oui, GroupDocs.Conversion prend en charge divers formats d'image tels que PNG, TIFF, BMP et GIF, entre autres.

### Q : Puis-je personnaliser le fichier PDF de sortie à l'aide des options de conversion ?

R : Absolument ! GroupDocs.Conversion offre une large gamme d'options de conversion vous permettant de personnaliser le PDF de sortie en fonction de vos besoins.

### Q : Existe-t-il une version d'essai disponible pour GroupDocs.Conversion pour .NET ?

 : Oui, vous pouvez accéder à une version d'essai gratuite de GroupDocs.Conversion pour .NET à partir de[ici](https://releases.groupdocs.com/).

### Q : Où puis-je demander de l'aide si je rencontre des problèmes pendant le processus de conversion ?

 R : Si vous rencontrez des problèmes ou avez des questions concernant GroupDocs.Conversion pour .NET, n'hésitez pas à visiter le[Forum GroupDocs.Conversion](https://forum.groupdocs.com/c/conversion/11) à l'aide.