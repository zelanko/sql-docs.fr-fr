---
title: "Modifier les paramètres de groupe de charge de travail | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- workload groups [SQL Server], alter
- Resource Governor, workload group alter
ms.assetid: 73b6109c-2ad0-4915-b11b-d40d5a0fdc25
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7ee33f07052addb06e1dd2fe56f6153498fdbc9b
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="change-workload-group-settings"></a>Modifier les paramètres de groupe de charge de travail
  Vous pouvez modifier les paramètres d'un groupe de charge de travail à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
-   **Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)  
  
-   **To change the settings for a workload group, using:**  [SQL Server Management Studio](#ChgWGProp), [Transact-SQL](#ChgWGTSQL)  
  
## <a name="before-you-begin"></a>Avant de commencer  
  
###  <a name="LimitationsRestrictions"></a> Limitations et restrictions  
 Vous pouvez modifier les paramètres du groupe de charge de travail par défaut et des groupes de charge de travail définis par l'utilisateur.  
  
 **REQUEST_MAX_MEMORY_GRANT_PERCENT**  
  
 La mémoire consommée par la création d'index sur une table partitionnée non-alignée est proportionnelle au nombre de partitions impliquées. Si la mémoire totale requise dépasse la limite par requête (REQUEST_MAX_MEMORY_GRANT_PERCENT) imposée par le paramètre du groupe de charge de travail, cette création d'index peut ne pas aboutir. Étant donné que le groupe de charge de travail par défaut permet à une requête de dépasser la limite par requête avec la mémoire minimale requise pour démarrer en vue de la compatibilité SQL Server 2005, l'utilisateur peut être en mesure d'exécuter la même création d'index dans le groupe de charge de travail par défaut, si le pool de ressources par défaut possède assez de mémoire totale configurée pour exécuter une telle requête.  
  
 La création d'index est autorisée à utiliser un espace de travail de mémoire supérieur à celui qui lui a été initialement alloué, pour des raisons de performances. Cette gestion spéciale est prise en charge par Resource Governor. Toutefois, l'allocation initiale et toute allocation de mémoire supplémentaire sont limitées par les paramètres du pool de ressources et du groupe de charge de travail.  
  
###  <a name="Permissions"></a> Autorisations  
 La modification des paramètres de groupe de charge de travail nécessite l'autorisation CONTROL SERVER.  
  
##  <a name="ChgWGProp"></a> Modifier les paramètres de groupe de charge de travail à l'aide de SQL Server Management Studio  
 **Pour modifier les paramètres de groupe de charge de travail à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
1.  Dans l'Explorateur d'objets, développez de manière récursive le nœud **Gestion** vers le bas et en incluant le dossier **Groupes de charge de travail** qui contient le groupe de charge de travail à modifier.  
  
2.  Cliquez avec le bouton droit sur le groupe de charge de travail à modifier, puis sélectionnez **Propriétés**.  
  
3.  Dans la page **Propriétés de Resource Governor** , sélectionnez la ligne pour le groupe de charge de travail dans la grille **Groupes de charges de travail pour le pool de ressources** si elle n'est pas sélectionnée automatiquement.  
  
4.  Cliquez ou double-cliquez sur les cellules de la ligne à modifier, puis entrez les nouvelles valeurs.  
  
5.  Cliquez sur **OK**pour enregistrer les modifications.  
  
##  <a name="ChgWGTSQL"></a> Modifier les paramètres de groupe de charge de travail à l'aide de Transact-SQL  
 **Pour modifier les paramètres de groupe de charge de travail à l'aide de Transact-SQL**  
  
1.  Exécutez l'instruction ALTER WORKLOAD GROUP en spécifiant les valeurs de propriété à modifier.  
  
2.  Exécutez l'instruction ALTER RESOURCE GOVERNOR RECONFIGURE.  
  
### <a name="example-transact-sql"></a>Exemple (Transact-SQL)  
 L'exemple suivant modifie le paramètre de pourcentage maximal d'allocation de mémoire pour le groupe de charge de travail nommé `groupAdhoc`.  
  
```  
ALTER WORKLOAD GROUP groupAdhoc  
WITH (REQUEST_MAX_MEMORY_GRANT_PERCENT = 30);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)   
 [Créer un groupe de charge de travail](../../relational-databases/resource-governor/create-a-workload-group.md)   
 [Créer un pool de ressources](../../relational-databases/resource-governor/create-a-resource-pool.md)   
 [Modifier les paramètres de pool de ressources](../../relational-databases/resource-governor/change-resource-pool-settings.md)   
 [ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-workload-group-transact-sql.md)   
 [ALTER RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-pool-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  
