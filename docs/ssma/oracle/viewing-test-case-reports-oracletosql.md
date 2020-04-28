---
title: Affichage des rapports de cas de test (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 8da14323-9dd6-4019-bf79-3e8b972a9bc0
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 75ce91d7948b53522f6ac861a078f8f902b23ab7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68086790"
---
# <a name="viewing-test-case-reports-oracletosql"></a>Affichage des rapports de cas de test (OracleToSQL)
Le rapport cas de test affiche les résultats de la vérification de test et les informations de test générales. En cas d’échec d’un test, des informations sur les données incompatibles dans les objets vérifiés s’affichent également.  
  
## <a name="report-structure"></a>Structure du rapport  
Le haut du rapport présente les statistiques suivantes :  
  
-   Le nombre total d’objets testés et le nombre d’objets pour lesquels le test a réussi.  
  
-   Le nombre total de tables vérifiées et de clés étrangères, ainsi que le nombre de tables et de clés étrangères correctement mis en correspondance.  
  
-   L’heure de début, l’heure de fin du cas de test et la durée totale d’exécution.  
  
Le reste du rapport affiche des informations dans quatre catégories :  
  
**Erreurs de configuration requise**  
Affiche toutes les erreurs qui se sont produites à l' **étape conditions préalables.** Normalement, elle est ignorée.  
  
**Initialisation**  
Affiche l’état de **réussite** ou d' **échec**de l’exécution.  
  
**Résultat des objets de test**  
Une comparaison des résultats (réussite ou échec) et l’incompatibilité du testeur SSMA détecté en cas de défaillance.  
  
**Finalisation**  
Affiche l’état de **réussite** ou d' **échec**de l’exécution.  
  
## <a name="see-also"></a>Voir aussi  
[Exécution de cas de test &#40;OracleToSQL&#41;](../../ssma/oracle/running-test-cases-oracletosql.md)  
[Test des objets de base de données migrés &#40;OracleToSQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
