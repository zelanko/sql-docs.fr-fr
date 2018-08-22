---
title: Exécuter des cas de Test (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Tester Component,Execution Steps
ms.assetid: 195ffdef-cfde-4bf4-a3ae-e7402bb07972
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: e74fe0d569c627df15b4a75200b6821a236404ef
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "40394645"
---
# <a name="running-test-cases-sybasetosql"></a>Exécution de cas de test (SybaseToSQL)
Lorsque le testeur de SSMA exécute un cas de Test, il exécute les objets sélectionnés pour le test et crée un rapport sur les résultats de la vérification. Si les résultats sont identiques sur les deux plateformes, le test a réussi. La correspondance des objets entre Sybase et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est déterminée en fonction des paramètres de mappage de schéma pour le projet SSMA actuel.  
  
Une condition requise pour le test a réussi est que tous les objets Sybase sont convertis et chargées dans la base de données cible. En outre, les données de table doivent être migrées afin que le contenu des tables sur les deux plateformes est synchronisé.  
  
## <a name="run-test-case"></a>Exécuter des cas de Test  
Pour exécuter le cas de Test préparée :  
  
1.  Cliquez sur le **exécuter** bouton.  
  
2.  Dans le **se connecter à Sybase** boîte de dialogue, entrez les informations de connexion, puis cliquez sur **Connect**.  
  
Lorsque le test est terminé, le rapport de cas de Test est créé. Cliquez sur le **rapport** bouton pour afficher la [affichage de rapports de cas de Test &#40;SybaseToSQL&#41;](../../ssma/sybase/viewing-test-case-reports-sybasetosql.md). Le résultat du test (rapport de cas de Test) est automatiquement stocké dans le [référentiels de Test à l’aide de &#40;SybaseToSQL&#41; ](../../ssma/sybase/using-test-repositories-sybasetosql.md) pour une utilisation ultérieure.  
  
## <a name="test-case-execution-steps"></a>Étapes d’exécution de cas de test  
  
### <a name="prerequisites"></a>Prérequis  
Testeur de SSMA vérifie si toutes les conditions préalables sont remplies pour l’exécution de test avant le début du test. Si certaines conditions ne sont pas satisfaites, un message d’erreur s’affiche.  
  
### <a name="initialization"></a>Initialisation  
À ce stade, SSMA testeur crée auxiliaires objets (tables, déclencheurs et vues) à la fois au niveau du Sybase et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ils permettent le suivi des modifications effectuées dans les tables concernées choisis pour la vérification si le mode de comparaisons de table est **change uniquement**.  
  
Supposons que la table vérifiée est nommée USER_TABLE. Pour une telle table, les objets auxiliaires suivants sont créés dans Sybase.  
  
Les objets suivants sont créés à Sybase dans la base de données SSMATESTER2005db ou SSMATESTER2008db et au [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans la base de données ssmatesterdb_syb.  
  
|Nom   |Type|Description|  
|--------|--------|---------------|  
|USER_TABLE$ Trg|Déclencheur|Déclencheur d’audit les modifications dans la table vérifiée.|  
|USER_TABLE$ Aud|Table de charge de travail|Tableau dans lequel sont enregistrés les lignes supprimées et remplacées.|  
|USER_TABLE$ AudID|Table de charge de travail|Tableau dans lequel les lignes nouvelles et modifiées sont enregistrés.|  
|USER_TABLE|Affichage|Représentation sous forme simplifiée de modifications de la table.|  
|USER_TABLE$ nouveau|Affichage|Simplifiée de la représentation sous forme de lignes insérées et remplacés.|  
|USER_TABLE$ new_id|Affichage|Identification des lignes insérées et modifiées.|  
|USER_TABLE$ ancien|Affichage|Simplifiée de la représentation sous forme de lignes supprimés et remplacés.|  
  
L’objet suivant est créé dans la base de données de table vérifié dans Sybase et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Nom   |Type|Description|  
|--------|--------|---------------|  
|USER_TABLE$ Trg|Déclencheur|Déclencheur d’audit les modifications dans la table vérifiée.|  
  
### <a name="test-object-calls"></a>Appels d’objet de test  
À ce stade, testeur de SSMA appelle chaque objet sélectionné pour le test, compare les résultats et affiche le rapport.  
  
### <a name="finalization"></a>Finalisation  
Pendant la finalisation SSMA testeur nettoie les objets auxiliaires créés à le **initialisation** étape.  
  
## <a name="next-step"></a>Étape suivante  
[Affichage des rapports de cas de Test &#40;SybaseToSQL&#41;](../../ssma/sybase/viewing-test-case-reports-sybasetosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Sélection et la configuration des objets à tester &#40;SybaseToSQL&#41;](../../ssma/sybase/selecting-and-configuring-objects-to-test-sybasetosql.md)  
[Sélectionner et configurer les objets affectés &#40;SybaseToSQL&#41;](../../ssma/sybase/selecting-and-configuring-affected-objects-sybasetosql.md)  
[Test des objets de base de données migrés &#40;SybaseToSQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
