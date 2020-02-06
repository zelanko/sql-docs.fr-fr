---
title: OLE Automation Procedures (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Ole Automation Procedures option
ms.assetid: e8982e05-4984-4406-9760-285e8c028ddf
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cb13d9b50c78ff3d067d97b2d5dd1b763e024608
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "67997961"
---
# <a name="ole-automation-procedures-server-configuration-option"></a>OLE Automation Procedures (option de configuration de serveur)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Utilisez l’option **OLE Automation Procedures** pour spécifier si les objets OLE Automation peuvent être instanciés dans des lots [!INCLUDE[tsql](../../includes/tsql-md.md)] . Cette option peut également être configurée à l’aide de la gestion basée sur une stratégie ou de la procédure stockée **sp_configure** . Pour plus d'informations, consultez [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md).  
  
 L'option **Ole Automation Procedures** peut prendre les valeurs suivantes :  
  
 0  
 Option Ole Automation Procedures désactivée. Il s'agit de la valeur par défaut des nouvelles instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 1  
 Option Ole Automation Procedures activée.  
  
 Lorsque l’option Procédures OLE Automation est activée, un appel à **sp_OACreate** entraîne le démarrage de l’environnement d’exécution partagé OLE.  
  
 Vous pouvez afficher et modifier la valeur actuelle de l’option **Procédures OLE Automation** à l’aide de la procédure stockée système **sp_configure** .  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant illustre l'affichage de la valeur actuelle de l'option Ole Automation Procedures.  
  
```  
EXEC sp_configure 'Ole Automation Procedures';  
GO  
```  
  
 L'exemple suivant illustre l'activation de l'option Ole Automation Procedures.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Ole Automation Procedures', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Configuration de la surface d'exposition](../../relational-databases/security/surface-area-configuration.md)   
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
