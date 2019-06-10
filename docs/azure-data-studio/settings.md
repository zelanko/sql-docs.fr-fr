---
title: Paramètres des utilisateurs et espace de travail
titleSuffix: Azure Data Studio
description: Comment personnaliser un Studio de données Azure en modifiant les paramètres des utilisateurs et espace de travail.
ms.custom: seodec18
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: jroth
ms.openlocfilehash: 883c0c98531311d77754fcbcdd86615283aecdc7
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66798070"
---
# <a name="modify-user-and-workspace-settings"></a>Modifier les paramètres des utilisateurs et espace de travail

Il est facile de configurer [!INCLUDE[name-sos](../includes/name-sos-short.md)] à votre guise via les paramètres. Presque toutes les parties de [!INCLUDE[name-sos](../includes/name-sos-short.md)]d’éditeur, l’interface utilisateur et comportement fonctionnel comporte des options que vous pouvez modifier.

[!INCLUDE[name-sos](../includes/name-sos-short.md)] fournit deux portées différentes pour les paramètres :

* **Utilisateur** ces paramètres s’appliquent globalement à n’importe quelle instance de [!INCLUDE[name-sos](../includes/name-sos-short.md)] vous ouvrir.
* **Espace de travail** paramètres de l’espace de travail sont des paramètres spécifiques à un dossier sur votre ordinateur et sont disponibles uniquement lorsque le dossier est ouvert dans la barre latérale de l’Explorateur. Paramètres définis dans cette étendue de remplacent l’étendue de l’utilisateur.

## <a name="creating-user-and-workspace-settings"></a>Création d’utilisateur et les paramètres de l’espace de travail

La commande de menu **fichier** > **préférences** > **paramètres** (**Code**  >  **Préférences** > **paramètres** sur Mac) fournit le point d’entrée pour configurer les paramètres utilisateur et l’espace de travail. Vous sont fournis avec une liste de paramètres par défaut. Copier les paramètres que vous souhaitez modifier appropriés `settings.json` fichier. Les onglets à droite vous permettent de basculer rapidement entre les fichiers de paramètres utilisateur et l’espace de travail.

Vous pouvez également ouvrir les paramètres utilisateur et l’espace de travail à partir de la **Palette de commandes** (**Ctrl + Maj + P**) avec **préférences : Ouvrez les paramètres utilisateur** et **préférences : Ouvrir les paramètres de l’espace de travail** ou utilisez le raccourci clavier (**Ctrl +,** ).

L’exemple suivant désactive les numéros de ligne dans l’éditeur et configure les lignes de code pour être mises en retrait automatiquement.

![Exemples de paramètres](media/settings/sample-settings.png)

Modifications apportées aux paramètres sont rechargées par [!INCLUDE[name-sos](../includes/name-sos-short.md)] après avoir modifié `settings.json` est enregistré.

>**Remarque :** Paramètres de l’espace de travail sont utiles pour le partage des paramètres spécifiques au projet dans une équipe.

## <a name="settings-file-locations"></a>Emplacements des fichiers de paramètres

Selon votre plateforme, le fichier de paramètres utilisateur se trouve ici :

* **Windows** `%APPDATA%\azuredatastudio\User\settings.json`
* **Mac** `$HOME/Library/Application Support/azuredatastudio/User/settings.json`
* **Linux** `$HOME/.config/azuredatastudio/User/settings.json`

Le fichier de paramètre d’espace de travail se trouve sous le `.[!INCLUDE[name-sos](../includes/name-sos-short.md)]` dossier dans votre projet.

## <a name="hot-exit"></a>Sortie à chaud

Azure Data Studio mémorise les changements apportés aux fichiers lorsque vous quittez par défaut. Cela est identique à la fonctionnalité de sortie actif dans Visual Studio Code.

Par défaut, la sortie à chaud est désactivée. Activer la sortie à chaud en modifiant le `files.hotExit` paramètre. Pour plus d’informations, consultez [à chaud de sortie (dans la documentation de Visual Studio Code)](https://code.visualstudio.com/docs/editor/codebasics#_hot-exit).


## <a name="tab-color"></a>Couleur d’onglet

Pour simplifier l’identifiant les connexions que vous travaillez avec, les onglets ouverts dans l’éditeur peuvent avoir leurs couleurs redéfinis pour correspondre à la couleur du groupe de serveurs auquel appartient la connexion. Par défaut, les couleurs d’onglet sont désactivées par défaut. Activer les couleurs d’onglet en modifiant le `sql.tabColorMode` paramètre.

## <a name="additional-resources"></a>Ressources supplémentaires

Étant donné que [!INCLUDE[name-sos](../includes/name-sos-short.md)] hérite ses paramètres utilisateur et l’espace de travail à partir de Visual Studio Code, des informations détaillées sur les paramètres de la fonctionnalité est dans le [paramètres pour Visual Studio Code](https://code.visualstudio.com/docs/getstarted/settings) article.
