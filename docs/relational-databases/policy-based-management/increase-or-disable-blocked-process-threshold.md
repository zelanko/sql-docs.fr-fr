---
description: Augmenter la valeur de l'option blocked process threshold ou la désactiver
title: Augmenter la valeur de l’option blocked process threshold ou la désactiver | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 71db8ef6-341b-4465-99db-5c63e48d4c7d
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: d3ddb1a904207960565b7d134961300b7e0ca591
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88423733"
---
# <a name="increase-or-disable-blocked-process-threshold"></a>Augmenter la valeur de l'option blocked process threshold ou la désactiver
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
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
 [blocked process threshold (option de configuration de serveur)](../../database-engine/configure-windows/blocked-process-threshold-server-configuration-option.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôler et appliquer les bonnes pratiques à l’aide de la gestion basée sur des stratégies](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
