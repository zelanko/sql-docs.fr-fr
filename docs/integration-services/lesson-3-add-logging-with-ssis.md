---
title: "Le&#231;on 3 : Ajouter la journalisation avec SSIS | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 64cd24cc-ba8e-4bd7-b10b-6b80d8b04af6
caps.latest.revision: 25
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 25
---
# Le&#231;on 3 : Ajouter la journalisation avec SSIS
[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] inclut des fonctions d'écriture dans un journal pour dépanner et contrôler l'exécution du package, lesquelles fournissent une trace des tâches et des événements de conteneur. Les fonctions d'écriture dans un journal sont d'une utilisation souple et peuvent être activées au niveau du package ou de tâches et de conteneurs spécifiques au sein du package. Vous pouvez sélectionner les événements à enregistrer et créer plusieurs journaux pour un seul package.  
  
La fonction d'écriture dans un journal est fournie par un module fournisseur d'informations. Chaque module fournisseur d'informations peut écrire les informations de journalisation dans différents formats et types de destination. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] fournit les modules fournisseurs d'informations suivants :  
  
-   Fichier texte  
  
-   [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]  
  
-   Journal des événements Windows  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   Fichier XML  
  
Au cours de cette leçon, vous allez créer une copie du package que vous avez créé à la [Leçon 2 : Ajout d’un bouclage avec SSIS](../integration-services/lesson-2-adding-looping-with-ssis.md). Vous allez utiliser ce nouveau package et ajouter et configurer le mode d'écriture dans un journal pour contrôler des événements particuliers au cours de l'exécution du package. Si vous n'avez effectué aucune des leçons précédentes, vous pouvez également copier le package final de la leçon 2 inclus dans le didacticiel.  
  
> [!IMPORTANT]  
> Pour suivre ce didacticiel, vous devez disposer de l'exemple de base de données **AdventureWorksDW2012** . Pour plus d’informations sur l’installation et le déploiement **d’AdventureWorksDW2012**, consultez [Reporting Services Product Samples sur CodePlex](http://go.microsoft.com/fwlink/p/?LinkID=526910).  
  
## Tâches de la leçon  
Cette leçon contient les tâches suivantes :  
  
-   [Étape 1 : Copie du package de la leçon 2](../integration-services/step-1-copying-the-lesson-2-package.md)  
  
-   [Étape 2 : Ajout et configuration de la journalisation](../integration-services/step-2-adding-and-configuring-logging.md)  
  
-   [Étape 3 : Test de la leçon 3 du package du didacticiel](../integration-services/step-3-testing-the-lesson-3-tutorial-package.md)  
  
## Démarrer la leçon  
[Étape 1 : Copie du package de la leçon 2](../integration-services/step-1-copying-the-lesson-2-package.md)  
  
  
  
