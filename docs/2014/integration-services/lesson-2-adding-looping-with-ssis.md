---
title: 'Leçon 2 : Ajout d’un bouclage | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 01f2ed61-1e5a-4ec6-b6a6-2bd070c64077
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: a542b2828a2ea6803a6b4174396e57c7e9d3af4e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62767551"
---
# <a name="lesson-2-adding-looping"></a>Leçon 2 : Ajout d’un bouclage
  Dans [Leçon 1 : Création du projet et le Package de base](lesson-1-create-a-project-and-basic-package-with-ssis.md), que vous avez créé un package qui extrait des données d’une source de fichier plat unique, transformé les données à l’aide de transformations de recherche et enfin de charger les données dans le **FactCurrency** table de faits de la **AdventureWorksDW2012** base de données exemple.  
  
 Toutefois, il est rare qu'un processus d'extraction, de transformation et de chargement (ETL, extract, transform, and load) utilise un seul fichier plat. Un processus ETL classique extrait généralement les données de plusieurs sources de fichiers plats. L'extraction des données à partir de plusieurs sources nécessite un flux de contrôle répétitif. L'une des fonctions les plus appréciées de [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] est la facilité avec laquelle vous pouvez ajouter une itération ou un bouclage aux packages.  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] fournit deux types de conteneurs pour effectuer des boucles dans des packages : le conteneur de boucles Foreach et le conteneur de boucles For. Le conteneur de boucles Foreach utilise un énumérateur pour effectuer le bouclage, tandis que le conteneur de boucles For utilise généralement une expression variable. Cette leçon est basée sur le conteneur de boucles Foreach.  
  
 Le conteneur de boucles Foreach permet à un package de répéter le flux de contrôle pour chaque membre d'un énumérateur spécifié. Avec le conteneur de boucles Foreach, vous pouvez énumérer :  
  
-   Lignes du recordset ADO  
  
-   Informations du schéma ADO.NET  
  
-   des structures de fichiers et de répertoires ;  
  
-   des variables système, package et utilisateur ;  
  
-   Objets énumérables contenus dans une variable  
  
-   Éléments d'une collection  
  
-   Nœuds dans une expression de langage XML Path (XPath)  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Objects (SMO)  
  
 Au cours de cette leçon, vous allez modifier le package ETL simple que vous avez créé au cours de la leçon 1 pour tirer parti du conteneur de boucles Foreach. Vous allez également définir des variables de package définies par l'utilisateur pour faire en sorte que le package du didacticiel effectue une itération sur tous les fichiers plats du dossier. Si vous n'avez pas effectué la leçon précédente, vous pouvez également copier le package final de la leçon 1 inclus dans le didacticiel.  
  
 Au cours de cette leçon, vous n'allez pas modifier le flux de données mais uniquement le flux de contrôle.  
  
> [!IMPORTANT]  
>  Pour suivre ce didacticiel, vous devez disposer de l'exemple de base de données **AdventureWorksDW2012** . Pour plus d'informations sur l'installation et le déploiement d' **AdventureWorksDW2012**, consultez [Reporting Services Product Samples sur CodePlex](https://go.microsoft.com/fwlink/p/?LinkID=526910).  
  
## <a name="lesson-tasks"></a>Tâches de la leçon  
 Cette leçon contient les tâches suivantes :  
  
-   [Étape 1 : Copie du Package de la leçon 1](lesson-2-1-copying-the-lesson-1-package.md)  
  
-   [Étape 2 : Ajout et configuration du conteneur de boucles Foreach](lesson-2-2-adding-and-configuring-the-foreach-loop-container.md)  
  
-   [Étape 3 : Modification du Gestionnaire de connexions de fichiers plats](lesson-2-3-modifying-the-flat-file-connection-manager.md)  
  
-   [Étape 4 : Test de la leçon 2 du Package du didacticiel](lesson-2-4-testing-the-lesson-2-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Démarrer la leçon  
 [Étape 1 : Copie du Package de la leçon 1](lesson-2-1-copying-the-lesson-1-package.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Conteneur de boucles For](control-flow/for-loop-container.md)  
  
  
