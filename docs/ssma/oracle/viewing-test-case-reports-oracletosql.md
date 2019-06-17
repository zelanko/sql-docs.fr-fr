---
title: Affichage des rapports de cas de Test (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 8da14323-9dd6-4019-bf79-3e8b972a9bc0
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 2d40fd986c68968680bcd39821d762101723b87b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63283636"
---
# <a name="viewing-test-case-reports-oracletosql"></a>Affichage des rapports de cas de test (OracleToSQL)
Le rapport de cas de Test affiche les résultats des tests de vérification et les informations de test généraux. En cas de défaillance de test, les informations sur toutes les données qui ne correspondent pas dans les objets vérifiés s’affiche également.  
  
## <a name="report-structure"></a>Structure de rapport  
La partie supérieure du rapport affiche ces statistiques :  
  
-   Le nombre total d’objets testés et le nombre d’objets pour lesquels le test a réussi.  
  
-   Le nombre total de tables vérifiés et les clés étrangères et le nombre de tables et les clés étrangères correctement mis en correspondance.  
  
-   L’heure de début, heure de fin du cas de test et la durée totale nécessaire pour l’exécution.  
  
Le reste du rapport affiche des informations dans quatre catégories :  
  
**Erreurs de configuration requise**  
Affiche les erreurs qui s’est produite sur le **étape des prérequis.** En règle générale, il est ignoré.  
  
**Initialisation**  
Indique l’état de l’exécution en tant que **réussite** ou **échec**.  
  
**Objets résultat de test**  
Comparaison des résultats (réussite ou échec) et les incompatibilités SSMA testeur détectée en cas d’échec.  
  
**Finalisation**  
Indique l’état de l’exécution en tant que **réussite** ou **échec**.  
  
## <a name="see-also"></a>Voir aussi  
[Cas de Test en cours d’exécution &#40;OracleToSQL&#41;](../../ssma/oracle/running-test-cases-oracletosql.md)  
[Test des objets de base de données migrés &#40;OracleToSQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
