---
title: Créer des extensions
titleSuffix: Azure Data Studio
description: En savoir plus sur la création et l’ajout d’extensions à Azure Data Studio
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: d0c43df8b24a33f3763dc5ff3a80e989b9b85038
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "67959607"
---
# <a name="extend-the-functionality-by-creating-azure-data-studio-extensions"></a>Étendre les fonctionnalités en créant des extensions Azure Data Studio

Les extensions dans [!INCLUDE[name-sos](../includes/name-sos-short.md)] offrent un moyen simple d’ajouter des fonctionnalités à l'installation [!INCLUDE[name-sos](../includes/name-sos-short.md)] de base.

Les extensions sont fournies par l’équipe Azure Data Studio (Microsoft), ainsi que par la communauté tierce (vous !).


## <a name="author-an-extension"></a>Créer une extension

Si vous souhaitez étendre Azure Data Studio, vous pouvez créer votre propre extension et la publier dans la galerie d’extensions.

**Écriture d’une extension**

***Prérequis***

Pour développer une extension, Node.js doit être installé et disponible dans votre $PATH. Node.js comprend npm, le gestionnaire de package Node.js, qui sera utilisé pour installer le générateur d’extensions.

Pour démarrer votre nouvelle extension, vous pouvez utiliser le générateur d’extensions Azure Data Studio. Le [générateur d’extensions](https://www.npmjs.com/package/generator-azuredatastudio) Yeoman facilite la création de projets d’extension simples. Pour lancer le générateur, saisissez la commande suivante dans une invite de commandes :

`npm install -g yo generator-azuredatastudio`

`yo azuredatastudio`


**Références d’extensibilité**

Pour en savoir plus sur l’extensibilité d’Azure Data Studio, consultez [Vue d’ensemble de l’extensibilité](extensibility.md). Vous pouvez également voir des exemples d’utilisation de l’API dans des [exemples](https://github.com/Microsoft/azuredatastudio/tree/master/samples) existants.


## <a name="debug-an-extension"></a>Déboguer une extension

Vous pouvez déboguer votre nouvelle extension à l’aide de l’extension Visual Studio Code [Azure Data Studio Debug](https://github.com/kevcunnane/sqlops-debug).

Étapes
- Ouvrez votre extension avec [Visual Studio Code](https://code.visualstudio.com/)
- Installer l’extension Azure Data Studio Debug
- Appuyez sur **F5** ou cliquez sur l’icône de débogage, puis cliquez sur **Démarrer**.
- Une nouvelle instance d’Azure Data Studio démarre en mode spécial (hôte de développement d’extension) et cette nouvelle instance est désormais consciente de votre extension.


## <a name="create-an-extension-package"></a>Créer un package d’extension

Après avoir écrit votre extension, vous devez créer un package VSIX pour pouvoir l’installer dans Azure Data Studio. Vous pouvez utiliser [vsce](https://github.com/Microsoft/vscode-vsce) pour créer le package VSIX.

`npm install -g vsce`

`vsce package`


## <a name="publish-an-extension"></a>Publier une extension

Pour publier votre nouvelle extension sur Azure Data Studio :

1. Ajoutez votre extension à https://github.com/Microsoft/azuredatastudio/blob/release/extensions/extensionsGallery.json
2. Nous n’avons actuellement pas de prise en charge pour l’hébergement d’extensions tierces. Par conséquent, au lieu de télécharger l’extension, Azure Data Studio propose l’option d’accéder à une page de téléchargement. Pour définir une page de téléchargement pour votre extension, définissez la valeur de la ressource « Microsoft.AzureDataStudio.DownloadPage ».
3. Créez une demande de tirage (pull request) sur une branche release/extensions.
4. Envoyez une demande de révision à l’équipe.

Votre extension sera examinée et ajoutée à la galerie d’extensions.

**Publication de mises à jour d’extension** Le processus de publication de mises à jour est similaire à la publication de l’extension. Vérifiez que la version est mise à jour dans package.json
