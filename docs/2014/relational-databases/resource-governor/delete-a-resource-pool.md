---
title: Supprimer un pool de ressources | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Resource Governor, resource pool delete
- resource pools [SQL Server], delete
ms.assetid: 3bdd348b-6582-4ffa-80ef-d49e50596ce5
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: bef2fd0d8fece165347531de290828921a45d074
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153440"
---
# <a name="delete-a-resource-pool"></a>Supprimer un pool de ressources
  Vous pouvez supprimer un pool de ressources à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de Transact-SQL.  
  
-   **Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)  
  
-   **Pour supprimer un pool de ressources, utilisez :** [SQL Server Management Studio](#DelRPSSMS), [Transact-SQL](#DelRPTSQL)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
 Vous ne pouvez pas supprimer un pool de ressources s'il contient des groupes de charge de travail.  
  
###  <a name="LimitationsRestrictions"></a> Limitations et restrictions  
 Vous ne pouvez pas supprimer les pools de ressources par défaut ou internes de Resource Governor. Vous ne pouvez pas supprimer un pool de ressources s'il contient des groupes de charge de travail. Pour plus d’informations, consultez [Delete a Workload Group](delete-a-workload-group.md).  
  
###  <a name="Permissions"></a> Permissions  
 La suppression d'un pool de ressources requiert l'autorisation CONTROL SERVER.  
  
##  <a name="DelRPSSMS"></a> Supprimer un pool de ressources à l'aide de l'Explorateur d'objets  
 **Pour supprimer un pool de ressources à l'aide de SQL Server Management Studio**  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], ouvrez l'Explorateur d'objets et développez de manière récursive le nœud **Gestion** jusqu'à **Resource Governor**inclus.  
  
2.  Cliquez avec le bouton droit sur le pool de ressources à supprimer, puis sélectionnez **Supprimer**.  
  
3.  Dans la fenêtre **Supprimer un objet** , le pool de ressources est répertorié dans la liste **Objet à supprimer** . Pour supprimer le pool de ressources, cliquez sur **OK**.  
  
    > [!NOTE]  
    >  Si le pool de ressources que vous cherchez à supprimer contient un groupe de charge de travail, l'action échoue.  
  
##  <a name="DelRPTSQL"></a> Supprimer un pool de ressources à l'aide de Transact-SQL  
 **Pour supprimer un pool de ressources à l'aide de Transact-SQL**  
  
1.  Exécutez l'instruction `DROP RESOURCE POOL` en spécifiant le nom du pool de ressources à supprimer.  
  
2.  Exécutez l'instruction **ALTER RESOURCE GOVERNOR RECONFIGURE** .  
  
### <a name="example-transact-sql"></a>Exemple (Transact-SQL)  
 L'exemple suivant supprime un groupe de charge de travail nommé `poolAdhoc`.  
  
```  
DROP RESOURCE POOL poolAdhoc;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Resource Governor](resource-governor.md)   
 [Pool de ressources de Resource Governor](resource-governor-resource-pool.md)   
 [Créer un pool de ressources](create-a-resource-pool.md)   
 [Modifier les paramètres de pool de ressources](change-resource-pool-settings.md)   
 [Groupe de charge de travail de Resource Governor](resource-governor-workload-group.md)   
 [Fonction classifieur de Resource Governor](resource-governor-classifier-function.md)   
 [DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-workload-group-transact-sql)   
 [DROP RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-resource-pool-transact-sql)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
