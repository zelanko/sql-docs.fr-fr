---
title: Création de cas de test (OracleToSQL) | Microsoft Docs
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
manager: shamikg
ms.openlocfilehash: 697f7049a60aa7ae2b8c89d1fb6c5ce8e3d29312
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68266133"
---
# <a name="creating-test-cases-oracletosql"></a>Création de cas de test (OracleToSQL)
Utilisez l’Assistant cas de test pour créer un test. Cet Assistant vous permet de créer des cas de test en choisissant des objets testés et vérifiés et en spécifiant les paramètres de test.  
  
## <a name="starting-the-test-case-wizard"></a>Démarrage de l’Assistant cas de test  
Pour démarrer l’Assistant cas de test **, cliquez sur nouveau cas de test...** dans le menu **testeur** .  
  
Au démarrage, l’Assistant recherche les SSMATESTER_ORACLE de schéma sur le serveur Oracle source. Il s’agit du schéma d’extension du testeur utilisé pour le stockage des objets auxiliaires. Si l’Assistant cas de test ne trouve pas SSMATESTER_ORACLE, il affiche une fenêtre de boîte de dialogue qui propose de créer le schéma. (Cette situation se produit généralement lors de la première exécution du testeur SSMA.)  
  
Si vous accédez à la boîte de dialogue, cliquez sur **Oui** pour créer SSMATESTER_ORACLE schéma sur le serveur source. Notez que vous devez disposer de privilèges Oracle pour créer un nouvel utilisateur et créer des objets dans le schéma de cet utilisateur.  
  
## <a name="overview-of-creating-test-cases-using-the-wizard"></a>Vue d’ensemble de la création de cas de test à l’aide de l’Assistant  
Le processus de création d’un cas de test consiste en cinq étapes :  
  
1.  [Initialisation des cas de test &#40;OracleToSQL&#41;](../../ssma/oracle/initializing-test-cases-oracletosql.md)  
  
2.  [Sélection et configuration des objets pour tester &#40;OracleToSQL&#41;](../../ssma/oracle/selecting-and-configuring-objects-to-test-oracletosql.md)  
  
3.  [Sélection et configuration des objets affectés &#40;OracleToSQL&#41;](../../ssma/oracle/selecting-and-configuring-affected-objects-oracletosql.md)  
  
4.  [Personnalisation de l’ordre des appels &#40;OracleToSQL&#41;](../../ssma/oracle/customizing-calls-order-oracletosql.md)  
  
5.  [Fin de la préparation du cas de test &#40;OracleToSQL&#41;](../../ssma/oracle/finishing-test-case-preparation-oracletosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Test des objets de base de données migrés &#40;OracleToSQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
