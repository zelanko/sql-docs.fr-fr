---
title: Modifier les paramètres de pool de ressources | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, resource pool alter
- resource pools [SQL Server], alter
ms.assetid: 49438285-a011-4dac-bd4f-f35cd90fda61
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6392c8211e073183b68d2d04e9c949317d6a33a9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "68198941"
---
# <a name="change-resource-pool-settings"></a>Modifier les paramètres de pool de ressources
  Vous pouvez modifier des paramètres de pool de ressources à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   **Avant de commencer :**  [Limitations et restrictions](#LimitationsRestrictions), [Autorisations](#Permissions)  
  
-   **Pour modifier les paramètres d’un pool de ressources avec :**  [SQL Server Management Studio](#ChgRPProp), [Transact-SQL](#ChgRPTSQL)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="LimitationsRestrictions"></a> Limitations et restrictions  
 Le pourcentage maximal de l'UC doit être supérieur ou égal au pourcentage minimal de l'UC. Le pourcentage maximal de mémoire doit être supérieur ou égal au pourcentage minimal de mémoire.  
  
 La somme des pourcentages d'UC minimal et de mémoire minimal pour tous les pools de ressources ne doit pas dépasser 100.  
  
###  <a name="Permissions"></a> Autorisations  
 La modification des paramètres du pool de ressources requiert l'autorisation CONTROL SERVER.  
  
##  <a name="ChgRPProp"></a> Modifier les paramètres du pool de ressources à l'aide de SQL Server Management Studio  
 **Pour modifier les paramètres du pool de ressources à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], ouvrez l’Explorateur d’objets et développez de manière récursive le nœud **Gestion** jusqu’à **Pools de ressources**.  
  
2.  Cliquez avec le bouton droit sur le pool de ressources à modifier, puis sélectionnez **Propriétés**.  
  
3.  Dans la page **Propriétés de Resource Governor** , sélectionnez la ligne du pool de ressources dans la grille **Pools de ressources** si elle n'est pas sélectionnée automatiquement.  
  
4.  Cliquez ou double-cliquez sur les cellules de la ligne à modifier, puis entrez les nouvelles valeurs.  
  
5.  Cliquez sur **OK**pour enregistrer les modifications.  
  
##  <a name="ChgRPTSQL"></a> Modifier les paramètres du pool de ressources à l'aide de Transact-SQL  
 **Pour modifier les paramètres du pool de ressources à l'aide de [!INCLUDE[tsql](../../includes/tsql-md.md)]**  
  
1.  Exécutez l'instruction `ALTER RESOURCE POOL` en spécifiant les valeurs de propriété à modifier.  
  
2.  Exécutez l'instruction **ALTER RESOURCE GOVERNOR RECONFIGURE** .  
  
### <a name="example-transact-sql"></a>Exemple (Transact-SQL)  
 L'exemple suivant modifie le paramètre de pourcentage maximal de l'UC pour le pool de ressources nommé `poolAdhoc`.  
  
```  
ALTER RESOURCE POOL poolAdhoc  
WITH (MAX_CPU_PERCENT = 25);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Resource Governor](resource-governor.md)   
 [Activer Resource Governor](enable-resource-governor.md)   
 [Créer un pool de ressources](create-a-resource-pool.md)   
 [Supprimer un pool de ressources](delete-a-resource-pool.md)   
 [Groupe de charge de travail de Resource Governor](resource-governor-workload-group.md)   
 [Fonction classifieur de Resource Governor](resource-governor-classifier-function.md)   
 [ALTER RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-pool-transact-sql)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
