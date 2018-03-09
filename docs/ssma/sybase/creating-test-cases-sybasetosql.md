---
title: "Création de cas de Test (SybaseToSQL) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-sybase
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords: Tester component,Test Case Wizard
ms.assetid: b52dfd93-95af-4299-bc8f-83f2a7a6a518
caps.latest.revision: "5"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8028f170d5f3154b9874cda16cc18bd7b36a84b8
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="creating-test-cases-sybasetosql"></a>Création de cas de Test (SybaseToSQL)
Utilisez l’Assistant de cas de Test pour créer un test. Cet Assistant vous permet de créer des cas de test en choisissant testé et vérifié les objets et en spécifiant les paramètres de tests.  
  
## <a name="starting-the-test-case-wizard"></a>Démarrage de l’Assistant de cas de Test  
Pour démarrer l’Assistant de cas de Test cliquez sur **nouveau cas de Test...** à partir de la **testeur** menu.  
  
Au démarrage, l’Assistant recherche de base de données ssmatester2005db ou ssmatester2008db (selon le type de projet) sur le serveur de Sybase source. Il est le schéma d’extension testeur utilisé pour stocker des objets auxiliaires. Si l’Assistant de cas de Test ne peut pas trouver ssmatester2005db ou ssmatester2008db, il affiche une boîte de dialogue qui propose de créer la base de données extension testeur. (Cette situation se produit généralement lors de la première exécution de SSMA testeur.)  
  
Si vous obtenez la boîte de dialogue, cliquez sur **Oui** pour créer la base de données Sybase testeur sur le serveur source. Puis une nouvelle fenêtre de boîte de dialogue s’affiche où vous devez ajouter un ou plusieurs périphériques sur lequel rechercher la nouvelle base de données testeur. Cliquez sur **ajouter** pour ajouter un périphérique. Dans le **espace d’Allocation pour Tester la base de données** boîte de dialogue Sélectionner le périphérique et spécifier la taille utilisée par la base de données de la tester. En outre, vous pouvez définir l’unité distincte pour les journaux de base de données. Notez que vous devez disposer des privilèges pour créer des bases de données Sybase.  
  
## <a name="overview-of-creating-test-cases-using-the-wizard"></a>Présentation de la création du cas de Test à l’aide de l’Assistant  
Le processus de création d’un cas de test se compose de cinq étapes :  
  
1.  [Lors de l’initialisation des cas de Test &#40; SybaseToSQL &#41; ](../../ssma/sybase/initializing-test-cases-sybasetosql.md).  
  
2.  [Sélection et configuration d’objets à Test &#40; SybaseToSQL &#41; ](../../ssma/sybase/selecting-and-configuring-objects-to-test-sybasetosql.md).  
  
3.  [Sélectionner et configurer les objets affectés &#40; SybaseToSQL &#41; ](../../ssma/sybase/selecting-and-configuring-affected-objects-sybasetosql.md).  
  
4.  [Personnalisation des appels ordre &#40; SybaseToSQL &#41; ](../../ssma/sybase/customizing-calls-order-sybasetosql.md).  
  
5.  [Terminer la préparation du cas de Test &#40; SybaseToSQL &#41; ](../../ssma/sybase/finishing-test-case-preparation-sybasetosql.md).  
  
## <a name="see-also"></a>Voir aussi  
[Test de migration des objets de base de données &#40; SybaseToSQL &#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
