---
title: "Activation de l’intégration de CLR | Documents Microsoft"
ms.custom: 
ms.date: 08/01/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- clr enabled option
- common language runtime [SQL Server], enabling
ms.assetid: eb3e9c64-7486-42e7-baf6-c956fb311a2c
caps.latest.revision: "19"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 86547cd78253d17ccacebe1d9b0db9e3cdda0c8a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="clr-integration---enabling"></a>Intégration du CLR - activation
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]La fonctionnalité d’intégration du common language runtime (CLR) est désactivée par défaut et doit être activée pour pouvoir utiliser des objets implémentés à l’aide de l’intégration du CLR. Pour activer l’intégration du CLR, utilisez le **clr activé** option de le **sp_configure** procédure stockée dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]:  
  
```tsql  
  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'clr enabled', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
 Vous pouvez désactiver l’intégration de CLR en définissant le **clr activé** option à 0. Lorsque vous désactivez l'intégration du CLR, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] arrête l'exécution de toutes les routines CLR et décharge tous les domaines d'application.  
  
> [!NOTE]  
>  Pour activer l’intégration du CLR, vous devez disposer de ALTER SETTINGS autorisation au niveau serveur, qui est implicitement détenue par les membres de la **sysadmin** et **serveradmin** rôles serveur fixes.  
  
> [!NOTE]  
>  Il est possible que les ordinateurs dotés de grandes quantités de mémoire et d'un grand nombre de processeurs ne puissent pas charger la fonctionnalité d'intégration du CLR de SQL Server au démarrage du serveur. Pour résoudre ce problème, démarrez le serveur à l’aide de la **-gmemory_to_reserve** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] option de démarrage du service et spécifiez une valeur de mémoire suffisamment élevée. Pour plus d’informations, consultez [Options de démarrage du service moteur de base de données](../../database-engine/configure-windows/database-engine-service-startup-options.md).  
  
> [!NOTE]  
>  L'exécution du CLR (Common Language Runtime) n'est pas prise en charge sous l'option lightweight pooling. Avant d'activer l'intégration du CLR, vous devez désactiver le regroupement léger. Pour plus d’informations, consultez [lightweight pooling Server Configuration Option](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md).  
  
## <a name="see-also"></a>Voir aussi  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [clr enabled (option de configuration de serveur)](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [Rôles de niveau serveur](../../relational-databases/security/authentication-access/server-level-roles.md)  
  
  
