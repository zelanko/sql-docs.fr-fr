---
title: Activation de l’intégration du CLR | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- clr enabled option
- common language runtime [SQL Server], enabling
ms.assetid: eb3e9c64-7486-42e7-baf6-c956fb311a2c
author: rothja
ms.author: jroth
ms.openlocfilehash: d7187906f1376deb81ca7ff4770af7b12b63c022
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84953657"
---
# <a name="enabling-clr-integration"></a>Activation de l'intégration du CLR
  La fonctionnalité d'intégration du Common Language Runtime (CLR) est désactivée par défaut et doit être activée pour pouvoir utiliser des objets implémentés à l'aide de l'intégration du CLR. Pour activer l’intégration du CLR, utilisez l’option **CLR activé** de la procédure stockée **sp_configure** :  
  
```  
  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'clr enabled', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
 Vous pouvez désactiver l’intégration du CLR en affectant à l’option **clr enabled** la valeur 0. Lorsque vous désactivez l'intégration du CLR, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] arrête l'exécution de toutes les routines CLR et décharge tous les domaines d'application.  
  
> [!NOTE]  
>  Pour activer l’intégration du CLR, vous devez disposer de l’autorisation de niveau serveur ALTER SETTINGs, qui est implicitement détenue par les membres des rôles serveur fixes **sysadmin** et **ServerAdmin** .  
  
> [!NOTE]  
>  Il est possible que les ordinateurs dotés de grandes quantités de mémoire et d'un grand nombre de processeurs ne puissent pas charger la fonctionnalité d'intégration du CLR de SQL Server au démarrage du serveur. Pour résoudre ce problème, démarrez le serveur à l’aide de l’option de démarrage du service **-gmemory_to_reserve** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et spécifiez une valeur de mémoire suffisamment élevée. Pour plus d’informations, consultez [Options de démarrage du service moteur de base de données](../../database-engine/configure-windows/database-engine-service-startup-options.md).  
  
> [!NOTE]  
>  L'exécution du CLR (Common Language Runtime) n'est pas prise en charge sous l'option lightweight pooling. Avant d'activer l'intégration du CLR, vous devez désactiver le regroupement léger. Pour plus d’informations, consultez [lightweight pooling Server Configuration Option](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md).  
  
## <a name="see-also"></a>Voir aussi  
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [CLR Enabled (option de configuration de serveur)](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [GRANT &#40;&#41;Transact-SQL](/sql/t-sql/statements/grant-transact-sql)   
 [Rôles de niveau serveur](../security/authentication-access/server-level-roles.md)  
  
  
