---
title: xp_cmdshell (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- xp_cmdshell
ms.assetid: c147c9e1-b81d-49c8-b800-3019f4d86a13
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f59953bff75a352770c3df3d0910eeaa0b97c38e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48208693"
---
# <a name="xpcmdshell-server-configuration-option"></a>xp_cmdshell (option de configuration de serveur)
  L’option **xp_cmdshell** est une option de configuration de serveur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui permet aux administrateurs système de contrôler l’autorisation d’exécuter la procédure stockée étendue **xp_cmdshell** sur un système. Par défaut, l’option **xp_cmdshell** est désactivée sur toutes les nouvelles installations et peut être activée au moyen de la gestion basée sur une stratégie ou en exécutant la procédure stockée système **sp_configure** comme dans l’exemple de code suivant :  
  
```  
-- To allow advanced options to be changed.  
EXEC sp_configure 'show advanced options', 1;  
GO  
-- To update the currently configured value for advanced options.  
RECONFIGURE;  
GO  
-- To enable the feature.  
EXEC sp_configure 'xp_cmdshell', 1;  
GO  
-- To update the currently configured value for this feature.  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [Administrer des serveurs à l'aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
