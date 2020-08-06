---
title: Contrôle de code source
description: Azure Data Studio prend en charge Git pour la gestion du contrôle de code source. Découvrez comment ouvrir un référentiel Git et comment en initialiser un nouveau.
ms.prod: azure-data-studio
ms.technology: ''
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: alayu, sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: c8b3ad59ac518eebefa9fbb073544fdb7791a419
ms.sourcegitcommit: 7035d9471876c70b99c58bf9b46af5cce6e9c66c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87522503"
---
# <a name="source-control-in-azure-data-studio"></a>Contrôle de code source dans Azure Data Studio

Azure Data Studio prend en charge Git pour le contrôle de version/code source.

## <a name="git-support-in-azure-data-studio"></a>Prise en charge de git dans Azure Data Studio

Azure Data Studio est fourni avec un gestionnaire de contrôle de code source Git, mais vous devez toujours [installer Git (version 2.0.0 ou ultérieure)](https://git-scm.com/download) pour que ces fonctionnalités soient disponibles. 

## <a name="open-an-existing-git-repository"></a>Ouvrir un référentiel git existant

1. Dans le menu **Fichier**, sélectionnez **Ouvrir le dossier...**
2. Accédez au dossier qui contient vos fichiers suivis par git, puis cliquez sur **Sélectionner un dossier**. Les sous-dossiers de votre référentiel local peuvent être sélectionnés ici.

## <a name="initialize-a-new-git-repository"></a>Initialiser un nouveau référentiel git

1. Sélectionnez **Contrôle de code source**, puis sélectionnez l’icône git.

   ![Icône git de contrôle de code source](media/source-control/source-control.png)

1. Entrez le chemin d’accès au dossier que vous souhaitez initialiser en tant que référentiel git, puis appuyez sur **Entrée**.

   ![Initialiser le référentiel Git](media/source-control/initialize-git-repository.png)

## <a name="working-with-git-repositories"></a>Utilisation des référentiels Git

Azure Data Studio hérite son implémentation Git de VS Code, mais ne prend pas en charge des fournisseurs SCM supplémentaires actuellement. Pour plus d’informations sur l’utilisation de Git après avoir ouvert ou initialisé un référentiel, consultez [Prise en charge de Git dans VS Code.](https://code.visualstudio.com/docs/editor/versioncontrol#_git-support)

## <a name="additional-resources"></a>Ressources supplémentaires

- [Documentation de Git](https://git-scm.com/documentation)
