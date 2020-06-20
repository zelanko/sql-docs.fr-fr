---
title: Activer Resource Governor | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, enabling
ms.assetid: 4d17af53-cf11-4ce4-aab4-deda94a49836
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7b1b0f780457aa5a4d26cbb463c9f31a94185f0d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85063576"
---
# <a name="enable-resource-governor"></a>Activer Resource Governor
  Resource Governor est désactivé par défaut. Vous pouvez activer Resource Governor à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de Transact-SQL.  
  
-   **Avant de commencer :**  [Limitations et restrictions](#LimitationsRestrictions), [Autorisations](#Permissions)  
  
-   **Pour activer Resource Governor avec :**  [Explorateur d’objets](#RGOnObjEx), [Propriétés de Resource Governor](#RGOnProp), [Transact-SQL](#RGOnTSQL)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
 L'activation de Resource Governor entraîne les résultats suivants :  
  
-   La fonction classifieur est exécutée pour les nouvelles connexions afin que leurs charges de travail puissent être assignées aux groupes de charge de travail.  
  
-   Les limites de ressource qui sont spécifiées dans la configuration de Resource Governor sont honorées et appliquées.  
  
-   Les demandes qui ont existé avant d'activer Resource Governor sont affectées par les éventuelles modifications de configuration qui ont été effectuées lorsque Resource Governor était désactivé.  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> Limitations et restrictions  
 Vous ne pouvez pas utiliser l'instruction `ALTER RESOURCE GOVERNOR` pour activer le gouverneur de ressources dans une transaction utilisateur.  
  
###  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 L'activation de Resource Governor requiert l'autorisation CONTROL SERVER.  
  
##  <a name="enable-resource-governor-using-object-explorer"></a><a name="RGOnObjEx"></a> Activer Resource Governor à l'aide de l'Explorateur d'objets  
 **Pour activer Resource Governor à l'aide de l'Explorateur d'objets**  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], ouvrez l'Explorateur d'objets et développez de manière récursive le nœud **Gestion** jusqu'au **Resource Governor**.  
  
2.  Cliquez avec le bouton droit sur **Resource Governor**, puis sélectionnez **Activer**.  
  
##  <a name="enable-resource-governor-using-resource-governor-properties"></a><a name="RGOnProp"></a> Activer Resource Governor à l'aide des propriétés de Resource Governor  
 **Pour activer Resource Governor à l'aide de la page Propriétés de Resource Governor**  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], ouvrez l'Explorateur d'objets et développez de manière récursive le nœud **Gestion** jusqu'au **Resource Governor**.  
  
2.  Cliquez avec le bouton droit sur **Resource Governor** , puis sélectionnez **Propriétés**afin d’ouvrir la page **Propriétés de Resource Governor** .  
  
3.  Activez la case à cocher **Activer Resource Governor** , puis cliquez **OK**.  
  
##  <a name="enable-resource-governor-using-transact-sql"></a><a name="RGOnTSQL"></a> Activer Resource Governor à l'aide de Transact-SQL  
 **Pour activer Resource Governor à l'aide de Transact-SQL**  
  
1.  Exécutez l'instruction **ALTER RESOURCE GOVERNOR RECONFIGURE** .  
  
### <a name="example-transact-sql"></a>Exemple (Transact-SQL)  
 L'exemple suivant active Resource Governor.  
  
```  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Resource Governor](resource-governor.md)   
 [Désactiver Resource Governor](disable-resource-governor.md)   
 [Pool de ressources de Resource Governor](resource-governor-resource-pool.md)   
 [Groupe de charge de travail de Resource Governor](resource-governor-workload-group.md)   
 [Fonction classifieur de Resource Governor](resource-governor-classifier-function.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
