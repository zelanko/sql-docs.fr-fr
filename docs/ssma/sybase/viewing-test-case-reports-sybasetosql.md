---
title: Affichage des rapports de cas de Test (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Tester Component,Test Case Reports
ms.assetid: cb75d281-43ef-4f4a-b754-2c4ee3b62ae7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 840f73d0732d0789d378c6f1bceb100c58e01bb6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47624467"
---
# <a name="viewing-test-case-reports-sybasetosql"></a>Affichage des rapports de cas de test (SybaseToSQL)
Le rapport de cas de Test affiche les résultats des tests de vérification et les informations de test généraux. En cas de défaillance de test, les informations sur toutes les données qui ne correspondent pas dans les objets vérifiés s’affiche également.  
  
## <a name="report-structure"></a>Structure de rapport  
La partie supérieure du rapport affiche ces statistiques :  
  
-   Le nombre total d’objets testés et le nombre d’objets pour lesquels le test a réussi.  
  
-   Le nombre total de tables vérifiés et les clés étrangères et le nombre de tables et les clés étrangères correctement mis en correspondance.  
  
-   L’heure de début, heure de fin du cas de test et la durée totale nécessaire pour l’exécution.  
  
Le reste du rapport affiche des informations dans quatre catégories :  
  
**Erreurs de configuration requise**  
Affiche les erreurs qui s’est produite sur le **conditions préalables** étape. En règle générale, il est ignoré.  
  
**Initialisation**  
Indique l’état de l’exécution en tant que **réussite** ou **échec**.  
  
**Objets résultat de test**  
Comparaison des résultats (réussite ou échec) et les incompatibilités SSMA testeur détectée en cas d’échec.  
  
**Finalisation**  
Indique l’état de l’exécution en tant que **réussite** ou **échec**.  
  
## <a name="see-also"></a>Voir aussi  
[Cas de Test en cours d’exécution &#40;SybaseToSQL&#41;](../../ssma/sybase/running-test-cases-sybasetosql.md)  
[Test des objets de base de données migrés &#40;SybaseToSQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
