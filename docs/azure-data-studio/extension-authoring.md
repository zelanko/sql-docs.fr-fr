---
title: Créer des extensions
description: Vous pouvez ajouter des fonctionnalités à Azure Data Studio à l’aide d’une extension. Découvrez comment en créer une et comment la publier dans la galerie d’extensions.
ms.prod: azure-data-studio
ms.technology: ''
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: alayu, maghan, sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 0473ac567f26748999e5718fe5f81660b0bfb7ba
ms.sourcegitcommit: 620a868e623134ad6ced6728ce9d03d7d0038fe0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87411125"
---
# <a name="extend-the-functionality-by-creating-azure-data-studio-extensions"></a>Étendre les fonctionnalités en créant des extensions Azure Data Studio

Les extensions dans Azure Data Studio offrent un moyen simple d’ajouter des fonctionnalités à l'installation d’Azure Data Studio de base.

Les extensions sont fournies par l’équipe Azure Data Studio (Microsoft), ainsi que par la communauté tierce (vous !).


## <a name="author-an-extension"></a>Créer une extension

Si vous souhaitez étendre Azure Data Studio, vous pouvez créer votre propre extension et la publier dans la galerie d’extensions.

**Écriture d’une extension**

***Composants requis***

Pour développer une extension, [Node.js](https://nodejs.org/) doit être installé et disponible dans votre `$PATH`. Node.js comprend npm, le gestionnaire de package Node.js, qui sera utilisé pour installer le générateur d’extensions.

Pour créer votre nouvelle extension, vous pouvez utiliser le générateur d’extensions Azure Data Studio. Le [générateur d’extensions](https://www.npmjs.com/package/generator-azuredatastudio) Yeoman est un bon point de départ pour les projets d’extension. Pour lancer le générateur, tapez la commande suivante à une invite de commandes :

```
npm install -g yo generator-azuredatastudio # Install the generator
yo azuredatastudio
```

Pour obtenir un guide détaillé expliquant comment bien démarrer avec votre modèle d’extension, consultez l’article [Création d’une extension](https://docs.microsoft.com/sql/azure-data-studio/tutorial-create-extension?view=sql-server-ver15), qui vous guide tout au long de la création d’une extension de mappage de touches.

**Références d’extensibilité**

Pour en savoir plus sur l’extensibilité d’Azure Data Studio, consultez [Vue d’ensemble de l’extensibilité](extensibility.md). Vous pouvez également voir des exemples d’utilisation de l’API dans des [exemples](https://github.com/Microsoft/azuredatastudio/tree/main/samples) existants.


## <a name="debug-an-extension"></a>Déboguer une extension

Vous pouvez déboguer votre nouvelle extension à l’aide de l’extension Visual Studio Code [Azure Data Studio Debug](https://github.com/kevcunnane/sqlops-debug).

Étapes
1. Ouvrez votre extension avec [Visual Studio Code](https://code.visualstudio.com/).
1. Installez l’extension Azure Data Studio Debug.
1. Appuyez sur **F5** ou cliquez sur l’icône de débogage, puis cliquez sur **Démarrer**.
1. Une nouvelle instance d’Azure Data Studio démarre en mode spécial (hôte de développement d’extension) et cette nouvelle instance est désormais consciente de votre extension.


## <a name="create-an-extension-package"></a>Créer un package d’extension

Après avoir écrit votre extension, vous devez créer un package VSIX pour pouvoir l’installer dans Azure Data Studio. Vous pouvez utiliser [vsce](https://github.com/Microsoft/vscode-vsce) (Extensions Visual Studio Code) pour créer le package VSIX. 

```
npm install -g vsce
cd myExtensionName
vsce package
# The myExtensionName.vsix file has now been generated
```

Avec un package VSIX, vous pouvez partager votre extension localement et en privé en partageant le fichier `.vsix` et en utilisant la commande **Extensions : Installer à partir d’un VSIX** dans la palette de commandes pour installer l’extension dans Azure Data Studio.


## <a name="publish-an-extension"></a>Publier une extension

Pour publier votre nouvelle extension sur Azure Data Studio :

1. Ajoutez votre extension à https://github.com/Microsoft/azuredatastudio/blob/release/extensions/extensionsGallery.json
2. Nous n’avons actuellement pas de prise en charge pour l’hébergement d’extensions tierces. Par conséquent, au lieu de télécharger l’extension, Azure Data Studio propose l’option d’accéder à une page de téléchargement. Pour définir une page de téléchargement pour votre extension, définissez la valeur de la ressource « Microsoft.AzureDataStudio.DownloadPage ».
3. Créez une demande de tirage (pull request) sur une branche release/extensions.
4. Envoyez une demande de révision à l’équipe.

Votre extension sera examinée et ajoutée à la galerie d’extensions.

**Publication de mises à jour d’extension**

Le processus de publication de mises à jour est similaire à la publication de l’extension. Vérifiez que la version est mise à jour dans package.json.
