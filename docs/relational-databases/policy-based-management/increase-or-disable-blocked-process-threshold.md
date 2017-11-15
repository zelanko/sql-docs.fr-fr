---
title: "Augmenter la valeur de l’option blocked process threshold ou la désactiver | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Best Practices [Database Engine]
ms.assetid: 71db8ef6-341b-4465-99db-5c63e48d4c7d
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 624fc53530880e625cd76276443ff4d4db5fe6a5
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="increase-or-disable-blocked-process-threshold"></a>Augmenter la valeur de l'option blocked process threshold ou la désactiver
  Cette règle vérifie que l'option blocked process threshold (seuil de processus bloqué) est définie sur 0 (désactivé) ou sur une valeur supérieure ou égale à 5 (secondes). Si vous affectez à cette option une valeur comprise entre 1 et 4, le moniteur de blocage risque de s'exécuter en permanence. Les valeurs 1 à 4 ne doivent être utilisées que pour le dépannage et jamais à long terme ni dans un environnement de production sans l'aide du service clientèle et du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Pour résoudre ce problème, définissez l'option blocked process threshold sur la valeur 5 (secondes) ou une valeur supérieure ou désactivez cette option en la définissant sur 0. Pour définir l'option blocked process threshold sur la valeur `5` secondes, exécutez l'instruction suivante :  
  
```  
sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE ;  
GO  
sp_configure 'blocked process threshold', 5 ;  
GO  
RECONFIGURE ;  
GO  
```  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [Seuil de processus bloqué (option de configuration de serveur)](../../database-engine/configure-windows/blocked-process-threshold-server-configuration-option.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôler et appliquer les meilleures pratiques à l'aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
