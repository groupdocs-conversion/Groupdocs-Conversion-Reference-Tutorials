---
"description": "Convertissez facilement des fichiers JPG en PDF grâce à GroupDocs.Conversion pour .NET. Suivez ce tutoriel étape par étape pour une conversion fluide de vos documents."
"linktitle": "Convertir JPG en PDF"
"second_title": "API .NET GroupDocs.Conversion"
"title": "Convertir JPG en PDF"
"url": "/fr/net/document-conversion/convert-jpg-to-pdf/"
"weight": 14
---

# Convertir JPG en PDF

## Introduction

Vous souhaitez convertir facilement des fichiers JPG en PDF avec GroupDocs.Conversion pour .NET ? Ce tutoriel vous guidera pas à pas. GroupDocs.Conversion pour .NET est une API puissante qui vous permet de convertir facilement et en toute simplicité divers formats de documents, y compris des images, au format PDF. C'est parti !

## Prérequis

Avant de commencer, assurez-vous de disposer des prérequis suivants :

1. GroupDocs.Conversion pour .NET : Assurez-vous d'avoir installé GroupDocs.Conversion pour .NET. Vous pouvez le télécharger depuis [ici](https://releases.groupdocs.com/conversion/net/).
2. Environnement de développement : disposez d’un environnement de développement configuré, tel que Visual Studio, ainsi que .NET Framework ou .NET Core.
3. Exemple de fichier JPG : préparez un exemple de fichier JPG que vous souhaitez convertir en PDF.

## Importer des espaces de noms

Tout d’abord, importons les espaces de noms nécessaires :

```csharp
using System;
using System.IO;
using GroupDocs.Conversion.Options.Convert;
```

Décomposons maintenant le processus de conversion en étapes simples :

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

Initialiser le `Converter` avec le chemin d'accès à votre fichier JPG d'exemple. Configurez ensuite les options de conversion, comme la spécification des options de conversion PDF. Enfin, appelez l' `Convert` méthode, en passant le chemin du fichier de sortie et les options de conversion.

## Étape 3 : Afficher le message de fin de conversion

```csharp
Console.WriteLine("\nConversion to pdf completed successfully. \nCheck output in {0}", outputFolder);
```

Une fois la conversion terminée, affichez un message indiquant la conversion réussie et l'emplacement du fichier PDF converti.

## Conclusion

Convertir des fichiers JPG en PDF avec GroupDocs.Conversion pour .NET est simple et ne nécessite que quelques lignes de code. En suivant ce tutoriel, vous pourrez intégrer facilement des fonctionnalités de conversion de documents à vos applications .NET.

## FAQ

### Q : Puis-je convertir plusieurs fichiers JPG en PDF simultanément ?

: Oui, vous pouvez convertir plusieurs fichiers JPG en PDF en parcourant chaque fichier et en exécutant le processus de conversion décrit dans le didacticiel.

### Q : GroupDocs.Conversion prend-il en charge d’autres formats d’image en plus du JPG ?

R : Oui, GroupDocs.Conversion prend en charge divers formats d’image tels que PNG, TIFF, BMP et GIF, entre autres.

### Q : Puis-je personnaliser le fichier PDF de sortie à l’aide des options de conversion ?

R : Absolument ! GroupDocs.Conversion propose une large gamme d'options de conversion vous permettant de personnaliser le PDF de sortie selon vos besoins.

### Q : Existe-t-il une version d’essai disponible pour GroupDocs.Conversion pour .NET ?

R : Oui, vous pouvez accéder à une version d'essai gratuite de GroupDocs.Conversion pour .NET à partir de [ici](https://releases.groupdocs.com/).

### Q : Où puis-je demander de l’aide si je rencontre des problèmes pendant le processus de conversion ?

R : Si vous rencontrez des problèmes ou avez des questions concernant GroupDocs.Conversion pour .NET, n'hésitez pas à visiter le [Forum GroupDocs.Conversion](https://forum.groupdocs.com/c/conversion/11) pour obtenir de l'aide.