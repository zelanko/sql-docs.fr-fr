---
title: Modifier les paramètres de pool de ressources | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, resource pool alter
- resource pools [SQL Server], alter
ms.assetid: 49438285-a011-4dac-bd4f-f35cd90fda61
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 8549b5a3a1675353ad0adce42fc63a460f893cae
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "72905015"
---
# <a name="change-resource-pool-settings"></a>Modifier les paramètres de pool de ressources
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

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
  
1.  Exécutez l’instruction **ALTER RESOURCE POOL** ou **ALTER EXTERNAL RESOURCE POOL** en spécifiant les valeurs de propriétés à modifier.  
  
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
 [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)   
 [Activer Resource Governor](../../relational-databases/resource-governor/enable-resource-governor.md)   
 [Créer un pool de ressources](../../relational-databases/resource-governor/create-a-resource-pool.md)   
 [Supprimer un pool de ressources](../../relational-databases/resource-governor/delete-a-resource-pool.md)   
 [Groupe de charge de travail de Resource Governor](../../relational-databases/resource-governor/resource-governor-workload-group.md)   
 [Fonction classifieur de Resource Governor](../../relational-databases/resource-governor/resource-governor-classifier-function.md)   
 [ALTER RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-pool-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)   
 [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)   
 [ALTER EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)  
  
  
