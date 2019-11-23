---
title: Activation de l’intégration du CLR | Microsoft Docs
ms.custom: ''
ms.date: 09/17/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- clr enabled option
- common language runtime [SQL Server], enabling
ms.assetid: eb3e9c64-7486-42e7-baf6-c956fb311a2c
author: rothja
ms.author: jroth
ms.openlocfilehash: 07066dc7ffbd48273ace55e0c9867661b2cbfe59
ms.sourcegitcommit: 445842da7c7d216b94a9576e382164c67f54e19a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2019
ms.locfileid: "71680855"
---
# <a name="clr-integration---enabling"></a>Intégration du CLR - Activation
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  La fonctionnalité d'intégration du Common Language Runtime (CLR) est désactivée par défaut et doit être activée pour pouvoir utiliser des objets implémentés à l'aide de l'intégration du CLR. Pour activer l’intégration du CLR, utilisez l’option **CLR activé** de la procédure stockée **sp_configure** dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]:  
  
```sql  
EXEC sp_configure 'clr enabled', 1;  
RECONFIGURE;  
GO  
```  
  
 Vous pouvez désactiver l’intégration du CLR en affectant à l’option **clr enabled** la valeur 0. Lorsque vous désactivez l’intégration du CLR, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] arrête d’exécuter toutes les routines CLR définies par l’utilisateur et décharge tous les domaines d’application. Les fonctionnalités qui reposent sur le CLR, telles que le type de données **hierarchyid** , la fonction `FORMAT`, la réplication et la gestion basée sur des stratégies, ne sont pas affectées par ce paramètre et continuent de fonctionner.
  
> [!NOTE]  
>  Pour activer l’intégration du CLR, vous devez disposer de l’autorisation de niveau serveur ALTER SETTINGs, qui est implicitement détenue par les membres des rôles serveur fixes **sysadmin** et **ServerAdmin** .  
  
> [!NOTE]  
>  Il est possible que les ordinateurs dotés de grandes quantités de mémoire et d'un grand nombre de processeurs ne puissent pas charger la fonctionnalité d'intégration du CLR de SQL Server au démarrage du serveur. Pour résoudre ce problème, démarrez le serveur à l’aide de l’option de démarrage du service[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **-gmemory_to_reserve** et spécifiez une valeur de mémoire suffisamment élevée. Pour plus d’informations, consultez [Options de démarrage du service moteur de base de données](../../database-engine/configure-windows/database-engine-service-startup-options.md).  
  
> [!NOTE]  
>  L'exécution du CLR (Common Language Runtime) n'est pas prise en charge sous l'option Regroupement léger. Avant d'activer l'intégration du CLR, vous devez désactiver le regroupement léger. Pour plus d’informations, consultez [lightweight pooling Server Configuration Option](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md).  
  
## <a name="see-also"></a>Voir aussi  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [clr enabled (option de configuration de serveur)](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [Rôles de niveau serveur](../../relational-databases/security/authentication-access/server-level-roles.md)  
  
  
