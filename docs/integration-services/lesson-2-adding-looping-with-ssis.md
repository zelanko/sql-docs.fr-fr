---
title: 'Leçon 2 : Ajouter un bouclage avec SSIS | Microsoft Docs'
ms.custom: ''
ms.date: 01/03/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 01f2ed61-1e5a-4ec6-b6a6-2bd070c64077
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ccd3be3203aae382cda239ed6d7bdc2fa224923b
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "71296056"
---
# <a name="lesson-2-add-looping-with-ssis"></a>Leçon 2 : Ajouter un bouclage avec SSIS

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



Dans [Leçon 1 : Créer un projet et un package de base avec SSIS](../integration-services/lesson-1-create-a-project-and-basic-package-with-ssis.md), vous avez créé un package qui extrait des données d’une source de fichier plat unique. Les données sont ensuite transformées par des transformations de recherche. Enfin, le package charge les données dans une copie de la table de faits **FactCurrencyRate** de l’exemple de base de données **AdventureWorksDW2012**.  
  
Un processus ETL (extraction, transformation et chargement) permet généralement d’extraire des données de plusieurs sources de fichiers plats. L'extraction des données à partir de plusieurs sources nécessite un flux de contrôle répétitif. [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] permet d’ajouter facilement une itération ou un bouclage à des packages.  
  
[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] fournit deux types de conteneurs pour effectuer des boucles dans des packages : le conteneur de boucles Foreach et le conteneur de boucles For. Le conteneur de boucles Foreach utilise un énumérateur pour le bouclage, tandis que le conteneur de boucles For utilise généralement une expression variable. Cette leçon est basée sur le conteneur de boucles Foreach.  
  
Le conteneur de boucles Foreach permet à un package de répéter le flux de contrôle pour chaque membre d'un énumérateur spécifié. Avec le conteneur de boucles Foreach, vous pouvez énumérer :  
  
-   Lignes du recordset ADO  
  
-   Informations du schéma ADO.NET  
  
-   des structures de fichiers et de répertoires ;  
  
-   Des variables système, package et utilisateur  
  
-   Des objets énumérables dans une variable  
  
-   Éléments d'une collection  
  
-   Nœuds dans une expression de langage XML Path (XPath)  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Objects (SMO)  
  
Au cours de cette leçon, vous modifiez l’exemple de package ETL de la leçon 1 pour utiliser un conteneur de boucles Foreach et vous définissez une variable de package définie par l’utilisateur pour le package. Cette variable est ensuite utilisée pour itérer au sein des fichiers correspondants dans l’exemple de dossier.   
  
Au cours de cette leçon, vous n’allez pas modifier le flux de données mais uniquement le flux de contrôle.  
  
> [!NOTE]  
> Si ce n’est déjà fait, consultez les [prérequis de la leçon 1](../integration-services/lesson-1-create-a-project-and-basic-package-with-ssis.md#prerequisites).

## <a name="lesson-tasks"></a>Tâches de la leçon  
Cette leçon contient les tâches suivantes :  
  
-   [Étape 1 : Copier le package de la leçon 1](../integration-services/lesson-2-1-copying-the-lesson-1-package.md)  
  
-   [Étape 2 : Ajouter et configurer le conteneur de boucles Foreach](../integration-services/lesson-2-2-adding-and-configuring-the-foreach-loop-container.md)  
  
-   [Étape 3 : Modifier le gestionnaire de connexions de fichiers plats](../integration-services/lesson-2-3-modifying-the-flat-file-connection-manager.md)  
  
-   [Étape 4 : Tester le package du tutoriel de la leçon 2](../integration-services/lesson-2-4-testing-the-lesson-2-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Démarrer la leçon  
[Étape 1 : Copier le package de la leçon 1](../integration-services/lesson-2-1-copying-the-lesson-1-package.md)  
  
## <a name="see-also"></a>Voir aussi  
[Conteneur de boucles For](../integration-services/control-flow/for-loop-container.md)  
  
  
  
