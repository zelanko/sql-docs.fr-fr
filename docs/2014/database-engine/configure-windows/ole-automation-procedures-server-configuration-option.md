---
title: OLE Automation Procedures (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Ole Automation Procedures option
ms.assetid: e8982e05-4984-4406-9760-285e8c028ddf
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d8a01c5bf886006e2f4eb6a352ea7f2a7b43ac29
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48055999"
---
# <a name="ole-automation-procedures-server-configuration-option"></a>OLE Automation Procedures (option de configuration de serveur)
  Utilisez l'option `Ole Automation Procedures` pour spécifier si les objets OLE Automation peuvent être instanciés dans des traitements [!INCLUDE[tsql](../../includes/tsql-md.md)]. Cette option peut également être configurée à l’aide de la gestion basée sur une stratégie ou de la procédure stockée **sp_configure** . Pour plus d'informations, consultez [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md).  
  
 Le `Ole Automation Procedures` option peut être définie sur les valeurs suivantes.  
  
 0  
 Option Ole Automation Procedures désactivée. Il s'agit de la valeur par défaut des nouvelles instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 1  
 Option Ole Automation Procedures activée.  
  
 Lorsque l’option Procédures OLE Automation est activée, un appel à **sp_OACreate** entraîne le démarrage de l’environnement d’exécution partagé OLE.  
  
 La valeur actuelle de la `Ole Automation Procedures` option peut être affichée et modifiée à l’aide du **sp_configure** procédure stockée système.  
  
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
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Configuration de la surface d'exposition](../../relational-databases/security/surface-area-configuration.md)   
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)  
  
  
