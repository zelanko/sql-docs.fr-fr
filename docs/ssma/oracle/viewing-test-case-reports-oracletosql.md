---
title: Affichage des rapports de cas de Test (OracleToSQL) | Documents Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-oracle
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8da14323-9dd6-4019-bf79-3e8b972a9bc0
caps.latest.revision: "6"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: ea0d497348f6fb146f5633d561385f44816a8871
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="viewing-test-case-reports-oracletosql"></a>Affichage des rapports de cas de Test (OracleToSQL)
Le rapport de cas de Test affiche les résultats de test de vérification et les informations de test général. En cas d’échec d’un test, les informations sur toutes les données ne correspondent pas dans les objets vérifiés s’affiche également.  
  
## <a name="report-structure"></a>Structure de rapport  
La partie supérieure du rapport montre ces statistiques :  
  
-   Nombre total d’objets testées et le nombre d’objets pour lesquels le test a réussi.  
  
-   Le nombre total de tables vérifiées et les clés étrangères et le nombre de tables et des clés étrangères correctement mis en correspondance.  
  
-   L’heure de début, heure de fin du cas de test et le temps total nécessaire pour l’exécution.  
  
Le reste du rapport affiche des informations dans quatre catégories :  
  
**Erreurs de configuration requise**  
Affiche toutes les erreurs qui se sont produites à le **étape de la configuration requise.** En règle générale, il est ignoré.  
  
**Initialisation**  
Indique l’état de l’exécution en tant que **réussite** ou **échec**.  
  
**Objets résultat de test**  
Une comparaison des résultats (réussite ou échec) et les incompatibilités SSMA testeur détecté en cas d’échec.  
  
**Finalisation**  
Indique l’état de l’exécution en tant que **réussite** ou **échec**.  
  
## <a name="see-also"></a>Voir aussi  
[Exécuter des cas de Test &#40; OracleToSQL &#41;](../../ssma/oracle/running-test-cases-oracletosql.md)  
[Test de migration des objets de base de données &#40; OracleToSQL &#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
