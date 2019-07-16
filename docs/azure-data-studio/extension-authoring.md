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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67959607"
---
# <a name="extend-the-functionality-by-creating-azure-data-studio-extensions"></a>Étendre les fonctionnalités en créant des extensions d’Azure Data Studio

Extensions dans [!INCLUDE[name-sos](../includes/name-sos-short.md)] fournissent un moyen simple d’ajouter des fonctionnalités à la base de [!INCLUDE[name-sos](../includes/name-sos-short.md)] installation.

Extensions sont fournies par l’équipe Azure Data Studio (Microsoft), ainsi que de la Communauté tiers 3e (vous !).


## <a name="author-an-extension"></a>Créer une extension

Si vous souhaitez étendre Azure Data Studio, vous pouvez créer votre propre extension et publiez-le dans la galerie d’extensions.

**Écriture d’une Extension**

***Conditions préalables***

Pour développer une extension, vous devez Node.js installé et disponible dans votre $PATH. Node.js inclut npm, le Gestionnaire de Package Node.js, qui sera utilisé pour installer le Générateur d’extension.

Pour démarrer votre nouvelle extension, vous pouvez utiliser le Générateur d’Extension de Studio de données Azure. Le Yeoman [Générateur d’extension](https://www.npmjs.com/package/generator-azuredatastudio) rend très facile de créer des projets d’extension simple. Pour lancer le générateur, tapez la commande suivante dans une invite de commandes :

`npm install -g yo generator-azuredatastudio`

`yo azuredatastudio`


**Références d’extensibilité**

Pour en savoir plus sur, consultez Azure données Studio extensibilité [vue d’ensemble de l’extensibilité](extensibility.md). Vous pouvez également voir des exemples montrant comment utiliser l’API existant [exemples](https://github.com/Microsoft/azuredatastudio/tree/master/samples).


## <a name="debug-an-extension"></a>Une extension de débogage

Vous pouvez déboguer votre nouvelle extension à l’aide d’extension Visual Studio Code [Azure données Studio déboguer](https://github.com/kevcunnane/sqlops-debug).

Étapes
- Ouvrez votre extension avec [Visual Studio Code](https://code.visualstudio.com/)
- Installer l’extension de débogage de Studio de données Azure
- Appuyez sur **F5** ou cliquez sur l’icône de débogage, cliquez sur **Démarrer**.
- Une nouvelle instance d’Azure Data Studio démarre en mode spécial (hôte de développement d’Extension) et cette nouvelle instance est désormais prenant en charge de votre extension.


## <a name="create-an-extension-package"></a>Créer un package d’extension

Après l’écriture de votre extension, vous devez créer un package VSIX pour pouvoir l’installer dans Azure Data Studio. Vous pouvez utiliser [vsce](https://github.com/Microsoft/vscode-vsce) pour créer le package VSIX.

`npm install -g vsce`

`vsce package`


## <a name="publish-an-extension"></a>Publier une extension

Pour publier votre nouvelle extension à Azure Data Studio :

1. Ajouter votre extension https://github.com/Microsoft/azuredatastudio/blob/release/extensions/extensionsGallery.json
2. Nous ne disposons actuellement pas prise en charge de l’hôte les extensions tierces, par conséquent, au lieu de télécharger l’extension, Azure Data Studio a l’option pour accéder à une page de téléchargement. Pour définir une page de téléchargement pour votre extension, définissez la valeur de ressource « Microsoft.AzureDataStudio.DownloadPage ».
3. Créer une demande de tirage par rapport à la branche de version/extensions.
4. Envoyer une demande de révision à l’équipe.

Votre extension est passé en revue et ajoutée à la galerie d’extensions.

**Publication des mises à jour de l’Extension** le processus de publication des mises à jour est similaire à la publication de l’extension. Vérifiez que la version est mis à jour dans le fichier package.json
