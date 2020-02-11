---
title: disallow results from triggers (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- triggers [SQL Server], result sets
- result sets [SQL Server], triggers
- disallow results from triggers option
ms.assetid: 47149073-307d-47a5-b7d2-66a737d3231d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0606379484fe14b0dfa1d93b604b8ee2b6eb7981
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62782534"
---
# <a name="disallow-results-from-triggers-server-configuration-option"></a>disallow results from triggers (option de configuration de serveur)
  L’option **disallow results from triggers** permet de spécifier si les déclencheurs doivent ou non retourner des ensembles de résultats. Les déclencheurs qui renvoient des jeux de résultats peuvent provoquer un comportement inattendu des applications qui ne sont pas conçues pour interagir avec eux.  
  
> [!IMPORTANT]  
>  
  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Nous vous conseillons de définir cette valeur sur 1.  
  
 L’option **disallow results from triggers** est activée quand la valeur 1 lui est attribuée. La valeur par défaut de cette option est 0 (désactivé). Si cette option est définie sur 1 (activé), toute tentative de la part d'un déclencheur de renvoyer un ensemble de résultats échoue, tandis l'utilisateur obtient le message d'erreur suivant :  
  
 « Msg 524, Niveau 16, État 1, Procédure \<nom_procédure>, Ligne \<n°_ligne>  
  
 « Un déclencheur a retourné un ensemble de résultats et l'option de serveur « disallow_results_from_triggers » a la valeur TRUE. »  
  
 L’option **disallow results from triggers** s’applique au niveau de l’instance [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et détermine le comportement de tous les déclencheurs qui existent au sein de l’instance.  
  
 L’option **disallow results from triggers** est une option avancée. Si vous utilisez la procédure stockée système **sp_configure** pour changer sa valeur, vous ne pouvez modifier l’option disallow results from triggers que si l’option **show advanced options** a la valeur 1. Le paramètre prend effet immédiatement (sans redémarrage du serveur).  
  
## <a name="see-also"></a>Voir aussi  
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
