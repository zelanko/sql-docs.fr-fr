---
title: Créer un groupe de charge de travail | Microsoft Docs
description: Découvrez comment créer un groupe de charge de travail à l’aide de SQL Server Management Studio ou de Transact-SQL. Vous devez disposer de l’autorisation CONTROL SERVER.
ms.custom: ''
ms.date: 03/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, workload group create
- workload groups [SQL Server], create
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.openlocfilehash: b9ad4bf1f8c344a6ea4babe8d4ce737b2d6fe3d4
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96504830"
---
# <a name="create-a-workload-group"></a>Créer un groupe de charge de travail

[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Vous pouvez créer un groupe de charge de travail à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   **Avant de commencer :**  [Limitations et restrictions](#LimitationsRestrictions), [Autorisations](#Permissions)  
  
-   **Pour créer un groupe de charge de travail avec :**  [SQL Server Management Studio](#CreRPProp), [Transact-SQL](#CreRPTSQL)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> Limitations et restrictions

 **REQUEST_MAX_MEMORY_GRANT_PERCENT**  
  
 La mémoire consommée par la création d'index sur une table partitionnée non-alignée est proportionnelle au nombre de partitions impliquées. Si la mémoire totale requise dépasse la limite par requête (REQUEST_MAX_MEMORY_GRANT_PERCENT) imposée par le paramètre du groupe de charge de travail, cette création d'index peut ne pas aboutir. Étant donné que le groupe de charge de travail par défaut permet à une requête de dépasser la limite par requête avec la mémoire minimale requise pour démarrer en vue de la compatibilité SQL Server 2005, l'utilisateur peut être en mesure d'exécuter la même création d'index dans le groupe de charge de travail par défaut, si le pool de ressources par défaut possède assez de mémoire totale configurée pour exécuter une telle requête.  
  
 La création d'index est autorisée à utiliser un espace de travail de mémoire supérieur à celui qui lui a été initialement alloué, pour des raisons de performances. Cette gestion spéciale est prise en charge par Resource Governor. Toutefois, l'allocation initiale et toute allocation de mémoire supplémentaire sont limitées par les paramètres du pool de ressources et du groupe de charge de travail.  
  
###  <a name="permissions"></a><a name="Permissions"></a> Autorisations

 La création d'un groupe de charge de travail nécessite l'autorisation CONTROL SERVER.  
  
##  <a name="create-a-workload-group-using-sql-server-management-studio"></a><a name="CreRPProp"></a> Créer un groupe de charge de travail avec SQL Server Management Studio

 **Pour créer un groupe de charge de travail à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
1.  Dans l'Explorateur d'objets, développez de manière récursive le nœud **Gestion** vers le bas et en incluant le pool de ressources qui contient le groupe de charge de travail à modifier.  
  
2.  Cliquez avec le bouton droit sur le dossier **Groupes de charge de travail** , puis sélectionnez **Nouveau groupe de charge de travail**.  
  
3.  Dans la grille **Pools de ressources** , assurez-vous que le pool de ressources où vous souhaitez ajouter le groupe de charge de travail est mis en surbrillance.  
  
4.  La grille **Groupes de charge de travail pour le pool de ressources** comportera une nouvelle ligne avec un nom vide et des valeurs par défaut dans les autres colonnes.  
  
5.  Cliquez sur la cellule **Nom** et entrez un nom pour le groupe de charge de travail.  
  
6.  Cliquez ou double-cliquez sur toutes les autres cellules de la ligne dont vous souhaitez modifier les paramètres par défaut, puis entrez les nouvelles valeurs.  
  
7.  Cliquez sur **OK** pour enregistrer les modifications.  

##  <a name="create-a-workload-group-using-transact-sql"></a><a name="CreRPTSQL"></a> Créer un groupe de charge de travail avec Transact-SQL  
 **Pour créer un groupe de charge de travail à l'aide de [!INCLUDE[tsql](../../includes/tsql-md.md)]**  
  
1.  Exécutez l'instruction CREATE WORKLOAD GROUP en spécifiant les valeurs de propriété à définir.  
  
2.  Exécutez l'instruction ALTER RESOURCE GOVERNOR RECONFIGURE.  
  
### <a name="example-transact-sql"></a>Exemple (Transact-SQL)

 L'exemple suivant crée un groupe de charge de travail nommé `groupAdhoc` dans le pool de ressources nommé `poolAdhoc`.  
  
```sql
CREATE WORKLOAD GROUP groupAdhoc  
USING poolAdhoc;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi

 [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)   
 [Activer Resource Governor](../../relational-databases/resource-governor/enable-resource-governor.md)   
 [Créer un pool de ressources](../../relational-databases/resource-governor/create-a-resource-pool.md)   
 [Modifier les paramètres de groupe de charge de travail](../../relational-databases/resource-governor/change-workload-group-settings.md)   
 [Créer et tester une fonction classifieur définie par l’utilisateur](../../relational-databases/resource-governor/create-and-test-a-classifier-user-defined-function.md)   
 [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-workload-group-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)   
 [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)  
  
  
