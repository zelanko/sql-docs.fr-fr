---
title: Créer un pool de ressources | Microsoft Docs
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
- resource pools [SQL Server], create
- Resource Governor, resource pool create
ms.assetid: 44dd0567-a4c8-4c72-89ff-e76f6ddef344
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 501252864b260c77697a1bc7cb82a3e415c33916
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36053033"
---
# <a name="create-a-resource-pool"></a>Créer un pool de ressources
  Vous pouvez créer un pool de ressources à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   **Avant de commencer :**  [Limitations et restrictions](#LimitationsRestrictions), [Autorisations](#Permissions)  
  
-   **Pour créer un pool de ressources, à l’aide de :**  [SQL Server Management Studio](#CreRPProp), [Transact-SQL](#CreRPTSQL)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="LimitationsRestrictions"></a> Limitations et restrictions  
 Le pourcentage maximal de l'UC doit être supérieur ou égal au pourcentage minimal de l'UC. Le pourcentage maximal de mémoire doit être supérieur ou égal au pourcentage minimal de mémoire.  
  
 La somme des pourcentages d'UC minimal et de mémoire minimal pour tous les pools de ressources ne doit pas dépasser 100.  
  
###  <a name="Permissions"></a> Permissions  
 La création d'un pool de ressources requiert l'autorisation CONTROL SERVER.  
  
##  <a name="CreRPProp"></a> Créer un pool de ressources à l'aide de SQL Server Management Studio  
 **Pour créer un pool de ressources à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], ouvrez l'Explorateur d'objets et développez de manière récursive le nœud **Gestion** jusqu'à **Resource Governor**inclus.  
  
2.  Cliquez avec le bouton droit sur **Resource Governor**, puis sélectionnez **Propriétés**.  
  
3.  Dans la grille **Pools de ressources** , cliquez sur la première colonne dans la ligne vide. Cette colonne est marquée d'un astérisque (*).  
  
4.  Double-cliquez sur la cellule vide dans la colonne **Nom** . Tapez le nom de votre choix pour le pool de ressources.  
  
5.  Cliquez ou double-cliquez sur toutes les autres cellules de la ligne que vous souhaitez modifier, puis entrez les nouvelles valeurs.  
  
6.  Cliquez sur **OK**pour enregistrer les modifications.  
  
##  <a name="CreRPTSQL"></a> Créer un pool de ressources à l'aide de Transact-SQL  
 **Pour créer un pool de ressources à l'aide de [!INCLUDE[tsql](../../includes/tsql-md.md)]**  
  
1.  Exécutez l'instruction `CREATE RESOURCE POOL` en spécifiant les valeurs de propriété à définir.  
  
2.  Exécutez l'instruction **ALTER RESOURCE GOVERNOR RECONFIGURE** .  
  
### <a name="example-transact-sql"></a>Exemple (Transact-SQL)  
 L'exemple suivant crée un pool de ressources nommé `poolAdhoc`.  
  
```  
CREATE RESOURCE POOL poolAdhoc  
WITH (MAX_CPU_PERCENT = 20);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Resource Governor](resource-governor.md)   
 [Activer Resource Governor](enable-resource-governor.md)   
 [Resource Governor Resource Pool](resource-governor-resource-pool.md)   
 [Modifier les paramètres de pool de ressources](change-resource-pool-settings.md)   
 [Supprimer un pool de ressources](delete-a-resource-pool.md)   
 [Configurer Resource Governor à l'aide d'un modèle](configure-resource-governor-using-a-template.md)   
 [Groupe de charge de travail de Resource Governor](resource-governor-workload-group.md)   
 [Fonction classifieur de Resource Governor](resource-governor-classifier-function.md)   
 [CREATE RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
