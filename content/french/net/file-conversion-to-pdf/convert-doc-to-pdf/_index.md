---
title: Convertir des documents Word DOC en PDF
linktitle: Convertir des documents Word DOC en PDF
second_title: API GroupDocs.Conversion .NET
description: Convertissez sans effort des documents DOC Word en PDF à l'aide de GroupDocs.Conversion pour .NET. Suivez notre guide étape par étape pour une conversion transparente de documents.
weight: 23
url: /fr/net/file-conversion-to-pdf/convert-doc-to-pdf/
---

# Convertir des documents Word DOC en PDF

## Introduction
À l’ère numérique d’aujourd’hui, la capacité de convertir de manière transparente des documents d’un format à un autre est essentielle aussi bien pour les entreprises que pour les particuliers. Que vous traitiez de documents Word, de PDF ou d'autres types de fichiers, disposer des bons outils peut faire toute la différence. L'un de ces outils est GroupDocs.Conversion pour .NET, une bibliothèque puissante qui offre aux développeurs la possibilité de convertir facilement des documents.
## Conditions préalables
Avant de vous lancer dans le processus de conversion à l'aide de GroupDocs.Conversion pour .NET, assurez-vous que les conditions préalables suivantes sont remplies :
1.  Téléchargez et installez GroupDocs.Conversion pour .NET : accédez au[lien de téléchargement](https://releases.groupdocs.com/conversion/net/) et suivez les instructions d'installation fournies.
2. Obtenir une licence : vous aurez besoin d'une licence pour utiliser GroupDocs.Conversion pour .NET dans vos applications. Si vous débutez, vous pouvez bénéficier d'un[permis temporaire](https://purchase.groupdocs.com/temporary-license/) à des fins de test ou achetez une licence pour une utilisation en production.
3. Familiarité avec l'environnement .NET : Une connaissance de base du framework .NET et du langage de programmation C# est recommandée pour suivre les exemples.
4. Accès aux documents sources : assurez-vous de disposer des documents sources que vous avez l'intention de convertir. À des fins de démonstration, nous convertirons les documents DOC Word au format PDF.

## Importer des espaces de noms
Avant de commencer le processus de conversion, importons les espaces de noms nécessaires dans notre projet .NET :
```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```
## Étape 1 : Définir le dossier et le fichier de sortie
Tout d'abord, spécifiez le dossier de sortie dans lequel vous souhaitez que le fichier PDF converti soit enregistré, ainsi que le nom du fichier de sortie souhaité.
```csharp
string outputFolder = "Your Document Directory";
string outputFile = Path.Combine(outputFolder, "doc-converted-to.pdf");
```
## Étape 2 : Charger le fichier DOC source
Ensuite, chargez le fichier DOC source à l'aide de la classe GroupDocs.Conversion.Converter.
```csharp
using (var converter = new GroupDocs.Conversion.Converter(Constants.SAMPLE_DOC))
```
## Étape 3 : configurer les options de conversion
Configurez les options de conversion en fonction de vos besoins. Pour convertir DOC en PDF, nous utiliserons PdfConvertOptions.
```csharp
var options = new PdfConvertOptions();
```
## Étape 4 : Effectuer la conversion
Exécutez le processus de conversion en appelant la méthode Convert de l'objet convertisseur, en transmettant le chemin du fichier de sortie et les options de conversion.
```csharp
converter.Convert(outputFile, options);
```
## Étape 5 : Vérifier la fin de la conversion
Une fois la conversion terminée, affichez un message de réussite ainsi que l'emplacement du dossier de sortie.
```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```

## Conclusion
GroupDocs.Conversion pour .NET simplifie le processus de conversion de documents entre différents formats. En suivant les étapes décrites dans ce didacticiel, vous pouvez facilement convertir des documents DOC Word en PDF.
## FAQ
### GroupDocs.Conversion pour .NET est-il compatible avec toutes les versions de .NET ?
GroupDocs.Conversion pour .NET est compatible avec .NET Framework 2.0 et versions ultérieures, notamment .NET Core et .NET 5+.
### Puis-je convertir plusieurs documents simultanément à l’aide de GroupDocs.Conversion pour .NET ?
Oui, GroupDocs.Conversion pour .NET prend en charge la conversion par lots, vous permettant de convertir plusieurs documents en une seule fois.
### GroupDocs.Conversion pour .NET nécessite-t-il une connexion Internet ?
Non, GroupDocs.Conversion pour .NET fonctionne localement sur votre ordinateur et ne nécessite pas de connexion Internet pour la conversion.
### Puis-je personnaliser les options de conversion pour des besoins spécifiques ?
Oui, GroupDocs.Conversion pour .NET propose de nombreuses options pour personnaliser le processus de conversion en fonction de vos besoins spécifiques.
### Un support technique est-il disponible pour GroupDocs.Conversion pour .NET ?
 Oui, le support technique pour GroupDocs.Conversion pour .NET est disponible via le[forum](https://forum.groupdocs.com/c/conversion/11) où vous pouvez demander de l’aide et des conseils à la communauté et aux experts.