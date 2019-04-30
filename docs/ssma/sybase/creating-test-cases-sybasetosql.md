---
title: Création de cas de Test (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Tester component,Test Case Wizard
ms.assetid: b52dfd93-95af-4299-bc8f-83f2a7a6a518
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 3fd443ff2ad58aa503fac2960016cb55f35b8a7f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63298373"
---
# <a name="creating-test-cases-sybasetosql"></a>Création de cas de test (SybaseToSQL)
Utilisez l’Assistant de cas de Test pour créer un test. Cet Assistant vous permet de créer des cas de test en choisissant testé et vérifié les objets et en spécifiant les paramètres de tests.  
  
## <a name="starting-the-test-case-wizard"></a>Démarrage de l’Assistant de cas de Test  
Pour démarrer l’Assistant de cas de Test cliquez sur **nouveau cas de Test...**  à partir de la **testeur** menu.  
  
Au démarrage, l’Assistant recherche ssmatester2005db de base de données ou ssmatester2008db (selon le type de projet) sur le serveur de Sybase source. Il est le schéma d’extension testeur utilisé pour le stockage d’objets auxiliaires. Si l’Assistant de cas de Test ne peut pas trouver ssmatester2005db ou ssmatester2008db, il affiche une fenêtre de boîte de dialogue qui envisage de créer la base de données extension testeur. (Cette situation se produit généralement lors de la première exécution de testeur de SSMA.)  
  
Si vous obtenez la boîte de dialogue, cliquez sur **Oui** pour créer la base de données Sybase testeur sur le serveur source. Puis une nouvelle fenêtre de boîte de dialogue s’affiche où vous devez ajouter un ou plusieurs périphériques sur lequel rechercher la nouvelle base de données de testeur. Cliquez sur **ajouter** pour ajouter un appareil. Dans le **espace d’Allocation pour la base de données du testeur** boîte de dialogue Sélectionner le périphérique et spécifier la taille utilisée par la base de données de testeur. En outre, vous pouvez définir l’appareil distinct pour les journaux de base de données. Notez que vous devez disposer des privilèges de Sybase pour créer des bases de données.  
  
## <a name="overview-of-creating-test-cases-using-the-wizard"></a>Présentation de la création de cas de Test à l’aide de l’Assistant  
Le processus de création d’un cas de test se compose de cinq étapes :  
  
1.  [Initialisation de cas de Test &#40;SybaseToSQL&#41;](../../ssma/sybase/initializing-test-cases-sybasetosql.md).  
  
2.  [Sélection et la configuration des objets à tester &#40;SybaseToSQL&#41;](../../ssma/sybase/selecting-and-configuring-objects-to-test-sybasetosql.md).  
  
3.  [Sélectionner et configurer les objets affectés &#40;SybaseToSQL&#41;](../../ssma/sybase/selecting-and-configuring-affected-objects-sybasetosql.md).  
  
4.  [Personnalisation de l’ordre des appels &#40;SybaseToSQL&#41;](../../ssma/sybase/customizing-calls-order-sybasetosql.md).  
  
5.  [Terminer la préparation du cas de Test &#40;SybaseToSQL&#41;](../../ssma/sybase/finishing-test-case-preparation-sybasetosql.md).  
  
## <a name="see-also"></a>Voir aussi  
[Test des objets de base de données migrés &#40;SybaseToSQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
