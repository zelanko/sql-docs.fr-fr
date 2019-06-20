---
title: 'Leçon 3 : Ajout de la journalisation | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 64cd24cc-ba8e-4bd7-b10b-6b80d8b04af6
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e716b808d5d9ada8aeaf50d92006cc6453c6e47d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "67046763"
---
# <a name="lesson-3-adding-logging"></a>Leçon 3 : Ajout du mode d’écriture dans un journal
  [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] inclut des fonctions d'écriture dans un journal pour dépanner et contrôler l'exécution du package, lesquelles fournissent une trace des tâches et des événements de conteneur. Les fonctions d'écriture dans un journal sont d'une utilisation souple et peuvent être activées au niveau du package ou de tâches et de conteneurs spécifiques au sein du package. Vous pouvez sélectionner les événements à enregistrer et créer plusieurs journaux pour un seul package.  
  
 La fonction d'écriture dans un journal est fournie par un module fournisseur d'informations. Chaque module fournisseur d'informations peut écrire les informations de journalisation dans différents formats et types de destination. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] fournit les modules fournisseurs d'informations suivants :  
  
-   Fichier texte  
  
-   [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]  
  
-   Journal des événements Windows  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   Fichier XML  
  
 Dans cette leçon, vous allez créer une copie du package que vous avez créé dans [leçon 2 : Ajout d’un bouclage](lesson-2-adding-looping-with-ssis.md). Vous allez utiliser ce nouveau package et ajouter et configurer le mode d'écriture dans un journal pour contrôler des événements particuliers au cours de l'exécution du package. Si vous n'avez effectué aucune des leçons précédentes, vous pouvez également copier le package final de la leçon 2 inclus dans le didacticiel.  
  
> [!IMPORTANT]  
>  Pour suivre ce didacticiel, vous devez disposer de l'exemple de base de données **AdventureWorksDW2012** . Pour plus d’informations sur comment installer et déployer **AdventureWorksDW2012**, [Reporting Services Product Samples sur GitHub](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).  
  
## <a name="lesson-tasks"></a>Tâches de la leçon  
 Cette leçon contient les tâches suivantes :  
  
-   [Étape 1 : Copie du Package de la leçon 2](lesson-3-1-copying-the-lesson-2-package.md)  
  
-   [Étape 2 : Ajout et configuration de journalisation](lesson-3-2-adding-and-configuring-logging.md)  
  
-   [Étape 3 : Test de la leçon 3 du Package du didacticiel](../integration-services/lesson-3-3-testing-the-lesson-3-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Démarrer la leçon  
 [Étape 1 : Copie du Package de la leçon 2](lesson-3-1-copying-the-lesson-2-package.md)  
  
  
