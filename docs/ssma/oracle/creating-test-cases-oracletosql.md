---
title: Création de cas de Test (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Test Case Wizard
ms.assetid: 22f38901-ec35-4707-a911-784e6ad8dafb
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: a2c1bd3fea167a784d86f7e323566f73c3a01f86
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63287706"
---
# <a name="creating-test-cases-oracletosql"></a>Création de cas de test (OracleToSQL)
Utilisez l’Assistant de cas de Test pour créer un test. Cet Assistant vous permet de créer des cas de test en choisissant testé et vérifié les objets et en spécifiant les paramètres de tests.  
  
## <a name="starting-the-test-case-wizard"></a>Démarrage de l’Assistant de cas de Test  
Pour démarrer l’Assistant de cas de Test cliquez sur **nouveau cas de Test...**  à partir de la **testeur** menu.  
  
Au démarrage, l’Assistant recherche schéma SSMATESTER_ORACLE sur le serveur Oracle source. Il est le schéma d’extension testeur utilisé pour le stockage d’objets auxiliaires. Si l’Assistant de cas de Test ne peut pas trouver SSMATESTER_ORACLE, il affiche une fenêtre de boîte de dialogue qui propose de créer le schéma. (Cette situation se produit généralement lors de la première exécution de testeur de SSMA.)  
  
Si vous obtenez la boîte de dialogue, cliquez sur **Oui** pour créer le schéma SSMATESTER_ORACLE sur le serveur source. Notez que vous devez disposer des privilèges d’Oracle pour créer un nouvel utilisateur et de créer des objets dans le schéma de cet utilisateur.  
  
## <a name="overview-of-creating-test-cases-using-the-wizard"></a>Présentation de la création de cas de Test à l’aide de l’Assistant  
Le processus de création d’un cas de test se compose de cinq étapes :  
  
1.  [Initialisation de cas de Test &#40;OracleToSQL&#41;](../../ssma/oracle/initializing-test-cases-oracletosql.md)  
  
2.  [Sélection et la configuration des objets à tester &#40;OracleToSQL&#41;](../../ssma/oracle/selecting-and-configuring-objects-to-test-oracletosql.md)  
  
3.  [Sélectionner et configurer les objets affectés &#40;OracleToSQL&#41;](../../ssma/oracle/selecting-and-configuring-affected-objects-oracletosql.md)  
  
4.  [Personnalisation de l’ordre des appels &#40;OracleToSQL&#41;](../../ssma/oracle/customizing-calls-order-oracletosql.md)  
  
5.  [Terminer la préparation du cas de Test &#40;OracleToSQL&#41;](../../ssma/oracle/finishing-test-case-preparation-oracletosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Test des objets de base de données migrés &#40;OracleToSQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
