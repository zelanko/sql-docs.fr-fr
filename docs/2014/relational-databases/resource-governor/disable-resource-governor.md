---
title: Désactiver Resource Governor | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, disabling
ms.assetid: 2c2d2db0-34a5-4f50-b783-17693e3ce3f1
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 75feaf114355c3a23abad6ec23be9011e0de5e06
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63209714"
---
# <a name="disable-resource-governor"></a>Désactiver Resource Governor
  Vous pouvez désactiver Resource Governor à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de Transact-SQL.  
  
-   **Avant de commencer :**  [Limitations et restrictions](#LimitationsRestrictions), [Autorisations](#Permissions)  
  
-   **Pour désactiver Resource Governor avec :**  [Explorateur d’objets](#RGOffObjEx), [Propriétés de Resource Governor](#RGOffProp), [Transact-SQL](#RGOffTSQL)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
 La désactivation de Resource Governor entraîne les résultats suivants :  
  
-   La fonction classifieur n'est pas exécutée.  
  
-   Toutes les nouvelles connexions sont classées automatiquement dans le groupe de charge de travail par défaut.  
  
-   Les demandes initiées par le système sont classées dans le groupe de charge de travail interne.  
  
-   Tous les paramètres de groupe de charges de travail et de pool de ressources existants sont réinitialisés à leurs valeurs par défaut. Dans ce cas, aucun événement n'est déclenché lorsque les limites sont atteintes.  
  
-   La surveillance système normale n'est pas affectée.  
  
-   La configuration peut être modifiée, mais les modifications n'entrent en vigueur qu'une fois que Resource Governor est activé.  
  
-   Lors du redémarrage de SQL Server, Resource Governor ne chargera pas sa configuration, mais à la place aura uniquement des pools de ressources et les groupes de charge de travail par défaut et internes.  
  
###  <a name="LimitationsRestrictions"></a> Limitations et restrictions  
 Vous ne pouvez pas utiliser l'instruction `ALTER RESOURCE GOVERNOR` pour désactiver le gouverneur de ressources pendant une transaction utilisateur.  
  
###  <a name="Permissions"></a> Autorisations  
 La désactivation de Resource Governor requiert l'autorisation CONTROL SERVER.  
  
##  <a name="RGOffObjEx"></a> Désactiver Resource Governor à l'aide de l'Explorateur d'objets  
 **Pour désactiver Resource Governor à l'aide de l'Explorateur d'objets**  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], ouvrez l'Explorateur d'objets et développez de manière récursive le nœud **Gestion** jusqu'au **Resource Governor**.  
  
2.  Cliquez avec le bouton droit sur **Resource Governor**, puis sélectionnez **Désactiver**.  
  
##  <a name="RGOffProp"></a> Désactiver Resource Governor à l'aide des propriétés de Resource Governor  
 **Pour désactiver Resource Governor à l'aide de la page Propriétés de Resource Governor**  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], ouvrez l'Explorateur d'objets et développez de manière récursive le nœud **Gestion** jusqu'au **Resource Governor**.  
  
2.  Cliquez avec le bouton droit sur **Resource Governor** , puis sélectionnez **Propriétés**afin d’ouvrir la page **Propriétés de Resource Governor** .  
  
3.  Activez la case à cocher **Activer Resource Governor** , vérifiez que la case à cocher n'est pas sélectionnée, puis cliquez sur **OK**.  
  
##  <a name="RGOffTSQL"></a> Désactiver Resource Governor à l'aide de Transact-SQL  
 **Pour désactiver Resource Governor à l'aide de Transact-SQL**  
  
1.  Exécutez l'instruction **ALTER RESOURCE GOVERNOR DISABLE** .  
  
### <a name="example-transact-sql"></a>Exemple (Transact-SQL)  
 L'exemple suivant active Resource Governor.  
  
```  
ALTER RESOURCE GOVERNOR DISABLE;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Resource Governor](resource-governor.md)   
 [Activer Resource Governor](enable-resource-governor.md)   
 [Pool de ressources de Resource Governor](resource-governor-resource-pool.md)   
 [Groupe de charge de travail de Resource Governor](resource-governor-workload-group.md)   
 [Fonction classifieur de Resource Governor](resource-governor-classifier-function.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
