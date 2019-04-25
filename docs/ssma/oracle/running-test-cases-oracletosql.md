---
title: Exécuter des cas de Test (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: fc208cdb-7373-4f6b-8f6c-cdff9d3dcd02
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 537865967d0e43b7dd9501f9fbb7b9605f5b9367
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62625790"
---
# <a name="running-test-cases-oracletosql"></a>Exécution de cas de test (OracleToSQL)
Lorsque le testeur de SSMA exécute un cas de Test, il exécute les objets sélectionnés pour le test et crée un rapport sur les résultats de la vérification. Si les résultats sont identiques sur les deux plateformes, le test a réussi. La correspondance des objets entre Oracle et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est déterminée en fonction des paramètres de mappage de schéma pour le projet SSMA actuel.  
  
Une condition requise pour le test a réussi est que tous les objets Oracle sont convertis et chargées dans la base de données cible. En outre, les données de table doivent être migrées afin que le contenu des tables sur les deux plateformes est synchronisé.  
  
## <a name="run-test-case"></a>Exécuter des cas de Test  
Pour exécuter le cas de Test préparée :  
  
1.  Cliquez sur le **exécuter** bouton.  
  
2.  Dans le **se connecter à Oracle** boîte de dialogue, entrez les informations de connexion, puis cliquez sur **Connect**.  
  
Lorsque le test est terminé, le rapport de cas de Test est créé. Cliquez sur le **rapport** bouton pour afficher la [rapport de cas de Test](viewing-test-case-reports-oracletosql.md). Le résultat du test (rapport de cas de Test) est automatiquement stocké dans le [référentiel des résultats des tests](using-test-repositories-oracletosql.md) pour une utilisation ultérieure.  
  
## <a name="test-case-execution-steps"></a>Étapes d’exécution de cas de test  
  
### <a name="prerequisites"></a>Prérequis  
Testeur de SSMA vérifie si toutes les conditions préalables sont remplies pour l’exécution de test avant le début du test. Si certaines conditions ne sont pas satisfaites, un message d’erreur s’affiche.  
  
### <a name="initialization"></a>Initialisation  
À ce stade, SSMA testeur crée des objets auxiliaires (tables, déclencheurs et vues) dans le schéma SSMATESTER_ORACLE du serveur Oracle. Ils permettent le suivi des modifications apportées dans les objets affectés choisis pour la vérification.  
  
Supposons que la table vérifiée est nommée USER_TABLE. Pour une telle table, les objets auxiliaires suivants sont créés dans Oracle.  
  
||||  
|-|-|-|  
|Nom|Type|Description|  
|USER_TABLE$ Trg|déclencheur|Déclencheur d’audit les modifications dans la table vérifiée.|  
|USER_TABLE$AUD|table|Tableau dans lequel sont enregistrés les lignes supprimées et remplacées.|  
|USER_TABLE$ AUDID|table|Tableau dans lequel les lignes nouvelles et modifiées sont enregistrés.|  
|USER_TABLE|vue|Représentation sous forme simplifiée de modifications de la table.|  
|$ USER_TABLE NOUVEAU|vue|Simplifiée de la représentation sous forme de lignes insérées et remplacés.|  
|USER_TABLE$ NEW_ID|vue|Identification des lignes insérées et modifiées.|  
|USER_TABLE$ ANCIEN|vue|Simplifiée de la représentation sous forme de lignes supprimés et remplacés.|  
  
L’objet suivant est créé dans le schéma de table vérifié au niveau [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
||||  
|-|-|-|  
|Nom|Type|Description|  
|USER_TABLE$ Trg|déclencheur|Déclencheur d’audit les modifications dans la table vérifiée.|  
  
Et les objets suivants sont créés au [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]dans la base de données ssmatesterdb.  
  
||||  
|-|-|-|  
|Créer une vue d’abonnement|Type|Description|  
|USER_TABLE$ Aud|table|Tableau dans lequel sont enregistrés les lignes supprimées et remplacées.|  
|USER_TABLE$AudID|table|Tableau dans lequel les lignes nouvelles et modifiées sont enregistrés.|  
|USER_TABLE|vue|Représentation sous forme simplifiée de modifications de la table.|  
|USER_TABLE$ nouveau|vue|Simplifiée de la représentation sous forme de lignes insérées et remplacés.|  
|USER_TABLE$new_id|vue|Identification des lignes insérées et modifiées.|  
|USER_TABLE$ ancien|vue|Simplifiée de la représentation sous forme de lignes supprimés et remplacés.|  
  
### <a name="test-object-calls"></a>Appels d’objet de test  
À ce stade, testeur de SSMA appelle chaque objet sélectionné pour le test, compare les résultats et affiche le rapport.  
  
### <a name="finalization"></a>Finalisation  
Pendant la finalisation SSMA testeur nettoie les objets auxiliaires créés à le **initialisation** étape.  
  
## <a name="next-step"></a>Étape suivante  
[Affichage des rapports de cas de Test &#40;OracleToSQL&#41;](../../ssma/oracle/viewing-test-case-reports-oracletosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Sélection et la configuration des objets à tester &#40;OracleToSQL&#41;](../../ssma/oracle/selecting-and-configuring-objects-to-test-oracletosql.md)  
[Sélectionner et configurer les objets affectés &#40;OracleToSQL&#41;](../../ssma/oracle/selecting-and-configuring-affected-objects-oracletosql.md)  
[Test des objets de base de données migrés &#40;OracleToSQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
