---
title: Azure Data Studio utilisateur et les paramètres de l’espace de travail | Microsoft Docs
description: Comment modifier les utilisateurs de Studio de données Azure et les paramètres de l’espace de travail.
ms.custom: tools|sos
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: e446d117bd56cb0c3607eeaf40522800d82e8a7e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "48038474"
---
# <a name="user-and-workspace-settings"></a>Paramètres des utilisateurs et espace de travail

Il est facile de configurer [!INCLUDE[name-sos](../includes/name-sos-short.md)] à votre guise via les paramètres. Presque toutes les parties de [!INCLUDE[name-sos](../includes/name-sos-short.md)]d’éditeur, l’interface utilisateur et comportement fonctionnel comporte des options que vous pouvez modifier.

[!INCLUDE[name-sos](../includes/name-sos-short.md)] fournit deux portées différentes pour les paramètres :

* **Utilisateur** ces paramètres s’appliquent globalement à n’importe quelle instance de [!INCLUDE[name-sos](../includes/name-sos-short.md)] vous ouvrir.
* **Espace de travail** paramètres de l’espace de travail sont des paramètres spécifiques à un dossier sur votre ordinateur et sont disponibles uniquement lorsque le dossier est ouvert dans la barre latérale de l’Explorateur. Paramètres définis dans cette étendue de remplacent l’étendue de l’utilisateur.

## <a name="creating-user-and-workspace-settings"></a>Création d’utilisateur et les paramètres de l’espace de travail

La commande de menu **fichier** > **préférences** > **paramètres** (**Code**  >  **Préférences** > **paramètres** sur Mac) fournit le point d’entrée pour configurer les paramètres utilisateur et l’espace de travail. Vous sont fournis avec une liste de paramètres par défaut. Copier les paramètres que vous souhaitez modifier appropriés `settings.json` fichier. Les onglets à droite vous permettent de basculer rapidement entre les fichiers de paramètres utilisateur et l’espace de travail.

Vous pouvez également ouvrir les paramètres utilisateur et l’espace de travail à partir de la **Palette de commandes** (**Ctrl + Maj + P**) avec **préférences : ouvrir les paramètres utilisateur** et  **Préférences : Ouvrir les espace de travail paramètres** ou utilisez le raccourci clavier (**Ctrl +,**).

L’exemple suivant désactive les numéros de ligne dans l’éditeur et configure les lignes de code pour être mises en retrait automatiquement.

![Exemples de paramètres](media/settings/sample-settings.png)

Modifications apportées aux paramètres sont rechargées par [!INCLUDE[name-sos](../includes/name-sos-short.md)] après avoir modifié `settings.json` est enregistré.

>**Remarque :** paramètres de l’espace de travail sont utiles pour le partage des paramètres spécifiques au projet dans une équipe.

## <a name="settings-file-locations"></a>Emplacements des fichiers de paramètres

Selon votre plateforme, le fichier de paramètres utilisateur se trouve ici :

* **Windows** `%APPDATA%\sqlops\User\settings.json`
* **Mac** `$HOME/Library/Application Support/sqlops/User/settings.json`
* **Linux** `$HOME/.config/sqlops/User/settings.json`

Le fichier de paramètre d’espace de travail se trouve sous le `.[!INCLUDE[name-sos](../includes/name-sos-short.md)]` dossier dans votre projet.

## <a name="hot-exit"></a>Sortie à chaud

Azure Data Studio mémorise les changements apportés aux fichiers lorsque vous quittez par défaut. Cela est identique à la fonctionnalité de sortie actif dans Visual Studio Code.

Par défaut, la sortie à chaud est désactivée. Activer la sortie à chaud en modifiant le `files.hotExit` paramètre. Pour plus d’informations, consultez [à chaud de sortie (dans la documentation de Visual Studio Code)](https://code.visualstudio.com/docs/editor/codebasics#_hot-exit).


## <a name="tab-color"></a>Couleur d’onglet

Pour simplifier l’identifiant les connexions que vous travaillez avec, les onglets ouverts dans l’éditeur peuvent avoir leurs couleurs redéfinis pour correspondre à la couleur du groupe de serveurs auquel appartient la connexion. Par défaut, les couleurs d’onglet sont désactivées par défaut. Activer les couleurs d’onglet en modifiant le `sql.tabColorMode` paramètre.

## <a name="additional-resources"></a>Ressources supplémentaires

Étant donné que [!INCLUDE[name-sos](../includes/name-sos-short.md)] hérite ses paramètres utilisateur et l’espace de travail à partir de Visual Studio Code, des informations détaillées sur les paramètres de la fonctionnalité est dans le [paramètres pour Visual Studio Code](https://code.visualstudio.com/docs/getstarted/settings) article.
