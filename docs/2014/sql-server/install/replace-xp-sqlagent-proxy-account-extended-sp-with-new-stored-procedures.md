---
title: Remplacer l’utilisation de la procédure stockée étendue xp_sqlagent_proxy_account par de nouvelles procédures stockées | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- xp_sqlagent_proxy_account
ms.assetid: 0e3cc931-6237-41dd-bf0d-0c03f4d8fff2
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4faff8420e318f7250cfc67dda173197d8028f0b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66092758"
---
# <a name="replace-usage-of-the-xp_sqlagent_proxy_account-extended-stored-procedure-with-new-stored-procedures"></a>Utiliser de nouvelles procédures stockées à la place de la procédure stockée étendue xp_sqlagent_proxy_account
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent prend en charge plusieurs proxies. Vous définissez ces proxies à l'aide d'un nouvel ensemble de procédures stockées. Pour plus d'informations sur les nouvelles procédures stockées de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez les rubriques suivantes dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   « sp_add_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)]) »  
  
-   « sp_delete_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)]) »  
  
-   « sp_enum_login_for_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)]) »  
  
-   « sp_enum_proxy_for_subsystem ([!INCLUDE[tsql](../../includes/tsql-md.md)]) »  
  
-   « sp_enum_sqlagent_subsystems ([!INCLUDE[tsql](../../includes/tsql-md.md)]) »  
  
-   « sp_grant_proxy_to_subsystem ([!INCLUDE[tsql](../../includes/tsql-md.md)]) »  
  
-   « sp_grant_login_to_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)]) »  
  
-   « sp_help_proxy" ([!INCLUDE[tsql](../../includes/tsql-md.md)]) »  
  
-   « sp_revoke_login_from_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)]) »  
  
-   « sp_revoke_proxy_from_subsystem ([!INCLUDE[tsql](../../includes/tsql-md.md)]) »  
  
-   « sp_update_proxy ([!INCLUDE[tsql](../../includes/tsql-md.md)]) »  
  
> [!NOTE]  
>  Après la mise à [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]niveau vers, toutes les instructions qui utilisent le **xp_sqlagent_proxy_account** procédure stockée étendue ne fonctionneront pas. Utilisez **sp_xp_cmdshell_proxy_account** au lieu de **xp_sqlagent_proxy_account** pour définir le proxy pour **xp_cmdshell**.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau de l'Agent SQL Server](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
