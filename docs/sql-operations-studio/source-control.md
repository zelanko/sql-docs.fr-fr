---
title: "Source de contrôle dans les opérations de SQL Studio (version préliminaire) | Documents Microsoft"
description: "Découvrez comment configurer le contrôle de code source dans les opérations de SQL Studio (version préliminaire)."
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: 
ms.topic: article
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4f28199262b087ad5362da0ddf56827216aec748
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
#  <a name="using-source-control-in-includename-sosincludesname-sos-shortmd"></a>À l’aide du contrôle de code source[!INCLUDE[name-sos](../includes/name-sos-short.md)]

[!INCLUDE[name-sos](../includes/name-sos-short.md)]prend en charge Git pour le contrôle de version/source.


## <a name="git-support-in-includename-sosincludesname-sos-shortmd"></a>Prise en charge GIT dans[!INCLUDE[name-sos](../includes/name-sos-short.md)]

[!INCLUDE[name-sos](../includes/name-sos-short.md)]est fourni avec un gestionnaire de contrôle de code source Git (SCM), mais vous devez toujours [installer Git (version 2.0.0 ou version ultérieure)](https://git-scm.com/download) avant que ces fonctionnalités soient disponibles. 



## <a name="open-an-existing-git-repository"></a>Ouvrir un référentiel Git existant

1. Sous le **fichier** menu, sélectionnez **ouvrir le dossier...**
2. Accédez au dossier qui contient vos fichiers de suivi git, puis cliquez sur **sélectionner le dossier**. Les sous-dossiers dans votre référentiel local sont OK sélectionner ici.


## <a name="initialize-a-new-git-repository"></a>Initialiser un nouveau référentiel git

1. Sélectionnez **contrôle de code Source**, puis sélectionnez l’icône git.

   ![Icône du contrôle de code source git](media/source-control/source-control.png)

1. Entrez le chemin d’accès au dossier que vous souhaitez initialiser un référentiel Git, puis appuyez sur **entrée**.

   ![initialiser le référentiel Git](media/source-control/initialize-git-repository.png)

## <a name="working-with-git-repositories"></a>Utilisation des référentiels Git

[!INCLUDE[name-sos](../includes/name-sos-short.md)]hérite de son implémentation Git à partir de Code de Visual Studio, mais ne prend pas en charge des fournisseurs supplémentaires SCM. Pour plus d’informations sur l’utilisation de Git après avoir ouvert ou initialiser un référentiel, consultez [prise en charge de Git dans VS Code](https://code.visualstudio.com/docs/editor/versioncontrol#_git-support).


## <a name="additional-resources"></a>Ressources supplémentaires
- [Documentation de GIT](https://git-scm.com/documentation)
