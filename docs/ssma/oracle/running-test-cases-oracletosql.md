---
title: "Exécuter des cas de Test (OracleToSQL) | Documents Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc208cdb-7373-4f6b-8f6c-cdff9d3dcd02
caps.latest.revision: 6
author: sabotta
ms.author: carlasab
manager: v-thobro
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: d810cee8f3d8b521350aa99a83ca6f7148cd5064
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="running-test-cases-oracletosql"></a>Cas de Test en cours d’exécution (OracleToSQL)
Lorsque le testeur de SSMA s’exécute à un cas de Test, il exécute les objets sélectionnés pour le test et crée un rapport sur les résultats de la vérification. Si les résultats sont identiques sur les deux plateformes, le test a réussi. La correspondance des objets entre Oracle et [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] est déterminé en fonction des paramètres de mappage de schéma pour le projet SSMA actuel.  
  
Une condition requise pour un test réussi est que tous les objets Oracle sont convertis et chargées dans la base de données cible. En outre, les données de table doivent être migrées et que le contenu des tables sur les deux plateformes est synchronisé.  
  
## <a name="run-test-case"></a>Exécuter des cas de Test  
Pour exécuter le cas de Test préparée :  
  
1.  Cliquez sur le **exécuter** bouton.  
  
2.  Dans le **se connecter à Oracle** boîte de dialogue, entrez les informations de connexion, puis cliquez sur **connexion**.  
  
Lorsque le test est terminé, le rapport de cas de Test est créé. Cliquez sur le **rapport** bouton pour afficher la [cas de Test, rapport](http://msdn.microsoft.com/en-us/8da14323-9dd6-4019-bf79-3e8b972a9bc0). Le résultat du test (rapport de cas de Test) est automatiquement stocké dans le [référentiel des résultats des tests](http://msdn.microsoft.com/en-us/f941cce4-d3e3-4aeb-a88a-4f101a97a9f4) pour une utilisation ultérieure.  
  
## <a name="test-case-execution-steps"></a>Étapes d’exécution des cas de test  
  
### <a name="prerequisites"></a>Conditions préalables  
Testeur de SSMA vérifie si toutes les conditions préalables sont remplies pour que l’exécution du test avant le début du test. Si certaines conditions ne sont pas satisfaites, un message d’erreur s’affiche.  
  
### <a name="initialization"></a>Initialisation  
À ce stade, SSMA testeur crée des objets auxiliaires (tables, déclencheurs et vues) dans le schéma SSMATESTER_ORACLE du serveur Oracle. Elles permettent les modifications de suivi effectuées dans les objets affectés choisis pour la vérification.  
  
Supposons que la table vérifiée est nommée USER_TABLE. Pour une telle table, les objets auxiliaires suivants sont créés dans Oracle.  
  
||||  
|-|-|-|  
|Nom|Type| Description|  
|USER_TABLE$ Trg|déclencheur|Déclencheur d’audit les modifications dans la table vérifiée.|  
|USER_TABLE$ AUD|table|Tableau dans lequel sont enregistrés les lignes supprimées et remplacées.|  
|USER_TABLE$ AUDID|table|Tableau dans lequel les lignes nouvelles et modifiées sont enregistrés.|  
|USER_TABLE|vue|Représentation simplifiée des modifications de la table.|  
|$ USER_TABLE NEW|vue|Simplifiée de la représentation sous forme de lignes insérées et remplacés.|  
|USER_TABLE$ NEW_ID|vue|Identification des lignes insérées et modifiés.|  
|USER_TABLE$ ANCIEN|vue|Simplifiée de la représentation sous forme de lignes supprimés et remplacés.|  
  
L’objet suivant est créé dans le schéma de table vérifié au niveau [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
||||  
|-|-|-|  
|Nom|Type| Description|  
|USER_TABLE$ Trg|déclencheur|Déclencheur d’audit les modifications dans la table vérifiée.|  
  
Et les objets suivants sont créés au [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]dans la base de données ssmatesterdb.  
  
||||  
|-|-|-|  
|Nom|Type| Description|  
|USER_TABLE$ Aud|table|Tableau dans lequel sont enregistrés les lignes supprimées et remplacées.|  
|USER_TABLE$ AudID|table|Tableau dans lequel les lignes nouvelles et modifiées sont enregistrés.|  
|USER_TABLE|vue|Représentation simplifiée des modifications de la table.|  
|$ USER_TABLE nouveau|vue|Simplifiée de la représentation sous forme de lignes insérées et remplacés.|  
|USER_TABLE$ new_id|vue|Identification des lignes insérées et modifiés.|  
|$ USER_TABLE ancien|vue|Simplifiée de la représentation sous forme de lignes supprimés et remplacés.|  
  
### <a name="test-object-calls"></a>Appels de l’objet de test  
À ce stade, SSMA testeur appelle chaque objet sélectionné pour le test, compare les résultats et affiche le rapport.  
  
### <a name="finalization"></a>Finalisation  
Lors de la finalisation SSMA testeur nettoie les objets auxiliaires créés lors de la **initialisation** étape.  
  
## <a name="next-step"></a>Étape suivante  
[Affichage de rapports de cas de Test &#40; OracleToSQL &#41;](../../ssma/oracle/viewing-test-case-reports-oracletosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Sélection et configuration d’objets pour Test &#40; OracleToSQL &#41;](../../ssma/oracle/selecting-and-configuring-objects-to-test-oracletosql.md)  
[Sélection et configuration affectées objets &#40; OracleToSQL &#41;](../../ssma/oracle/selecting-and-configuring-affected-objects-oracletosql.md)  
[Test de migration des objets de base de données &#40; OracleToSQL &#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  

