---
title: "Création de cas de Test (OracleToSQL) | Documents Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Test Case Wizard
ms.assetid: 22f38901-ec35-4707-a911-784e6ad8dafb
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: c40ee9da718fec017381740d69b6fa71045572bd
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="creating-test-cases-oracletosql"></a>Création de cas de Test (OracleToSQL)
Utilisez l’Assistant de cas de Test pour créer un test. Cet Assistant vous permet de créer des cas de test en choisissant testé et vérifié les objets et en spécifiant les paramètres de tests.  
  
## <a name="starting-the-test-case-wizard"></a>Démarrage de l’Assistant de cas de Test  
Pour démarrer l’Assistant de cas de Test cliquez sur **nouveau cas de Test...** à partir de la **testeur** menu.  
  
Au démarrage, l’Assistant recherche des schémas SSMATESTER_ORACLE sur le serveur Oracle source. Il est le schéma d’extension testeur utilisé pour stocker des objets auxiliaires. Si l’Assistant de cas de Test ne peut pas trouver SSMATESTER_ORACLE, il affiche une boîte de dialogue qui propose de créer le schéma. (Cette situation se produit généralement lors de la première exécution de SSMA testeur.)  
  
Si vous obtenez la boîte de dialogue, cliquez sur **Oui** pour créer le schéma SSMATESTER_ORACLE sur le serveur source. Notez que vous devez disposer des privilèges d’Oracle pour créer un nouvel utilisateur et de créer des objets dans le schéma de cet utilisateur.  
  
## <a name="overview-of-creating-test-cases-using-the-wizard"></a>Présentation de la création du cas de Test à l’aide de l’Assistant  
Le processus de création d’un cas de test se compose de cinq étapes :  
  
1.  [Lors de l’initialisation des cas de Test &#40; OracleToSQL &#41;](../../ssma/oracle/initializing-test-cases-oracletosql.md)  
  
2.  [Sélection et configuration d’objets pour Test &#40; OracleToSQL &#41;](../../ssma/oracle/selecting-and-configuring-objects-to-test-oracletosql.md)  
  
3.  [Sélection et configuration affectées objets &#40; OracleToSQL &#41;](../../ssma/oracle/selecting-and-configuring-affected-objects-oracletosql.md)  
  
4.  [Personnalisation des relations entre les appels ordre &#40; OracleToSQL &#41;](../../ssma/oracle/customizing-calls-order-oracletosql.md)  
  
5.  [Terminer la préparation du cas de Test &#40; OracleToSQL &#41;](../../ssma/oracle/finishing-test-case-preparation-oracletosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Test de migration des objets de base de données &#40; OracleToSQL &#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  

