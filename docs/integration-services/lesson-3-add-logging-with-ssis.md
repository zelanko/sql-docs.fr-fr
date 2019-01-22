---
title: 'Leçon 3 : Ajouter la journalisation avec SSIS | Microsoft Docs'
ms.custom: ''
ms.date: 01/04/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 64cd24cc-ba8e-4bd7-b10b-6b80d8b04af6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 790738d3c66d4b973d2f6934e89caa77af6ffde0
ms.sourcegitcommit: dd794633466b1da8ead9889f5e633bdf4b3389cd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54142999"
---
# <a name="lesson-3-add-logging-with-ssis"></a>Leçon 3 : Ajouter la journalisation avec SSIS

[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] inclut des fonctions d'écriture dans un journal pour dépanner et contrôler l'exécution du package, lesquelles fournissent une trace des tâches et des événements de conteneur. Les fonctionnalités de journalisation sont flexibles. Vous pouvez activer la journalisation au niveau du package, ou sur des tâches ou des conteneurs spécifiques au sein du package. Vous sélectionnez les événements à enregistrer et créez plusieurs journaux pour un seul package.  
  
Les modules fournisseurs d’informations créent les journaux. Chaque module fournisseur d'informations peut écrire les informations de journalisation dans différents formats et types de destination. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] fournit les modules fournisseurs d'informations suivants :  
  
-   Fichier texte  
  
-   [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]  
  
-   Journal des événements Windows  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   Fichier XML  
  
Au cours de cette leçon, vous créez une copie du package que vous avez créé à la [Leçon 2: Ajouter un bouclage avec SSIS](../integration-services/lesson-2-adding-looping-with-ssis.md). Vous utiliser ce nouveau package et ajoutez et configurez le mode d’écriture dans un journal pour superviser des événements particuliers au cours de l’exécution du package. Si vous n’avez suivi aucune des leçons précédentes, vous pouvez également copier le package final de la leçon 2 inclus dans le tutoriel.  

> [!NOTE]
> Si ce n’est déjà fait, consultez les [prérequis de la leçon 1](../integration-services/lesson-1-create-a-project-and-basic-package-with-ssis.md#prerequisites).

## <a name="lesson-tasks"></a>Tâches de la leçon  
Cette leçon contient les tâches suivantes :  
  
-   [Étape 1 : Copier le package de la leçon 2](../integration-services/lesson-3-1-copying-the-lesson-2-package.md)  
  
-   [Étape 2 : Ajouter et configurer la journalisation](../integration-services/lesson-3-2-adding-and-configuring-logging.md)  
  
-   [Étape 3 : Tester le package de la leçon 3](../integration-services/lesson-3-3-testing-the-lesson-3-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Démarrer la leçon  
[Étape 1 : Copier le package de la leçon 2](../integration-services/lesson-3-1-copying-the-lesson-2-package.md)  
  
