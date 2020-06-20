---
title: Supprimer les références aux procédures stockées système déconseillées | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- undocumented system stored procedures [SQL Server]
- system stored procedures [SQL Server]
ms.assetid: 487d24fc-41d5-495e-843c-0ac974ec472f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 65e7da666beaf84050dd8d60caf4cac5bfc013c7
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85036611"
---
# <a name="remove-references-to-deprecated-system-stored-procedures"></a>Supprimer les références aux procédures stockées système déconseillées
  Le Conseiller de mise à niveau a détecté des instructions faisant référence à des procédures stockées système non documentées et à des procédures stockées étendues qui ne sont plus disponibles dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les instructions faisant référence à ces objets échoueront. N'utilisez pas les objets système et les API non documentés car la fonctionnalité peut être modifiée ou supprimée sans préavis dans une version ultérieure.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
  
### <a name="documented-system-stored-procedures"></a>Procédures stockées système documentées  
 Les procédures stockées système documentées suivantes ont été supprimées :  
  
-   sp_addalias  
  
-   sp_addgroup  
  
-   sp_changegroup  
  
-   sp_dropgroup  
  
-   sp_helpgroup  
  
### <a name="undocumented-system-stored-procedures"></a>Procédures stockées système non documentées  
 Les procédures stockées système non documentées et les procédures stockées étendues suivantes ont été supprimées :  
  
-   sp_articlesynctranprocs  
  
-   sp_diskdefault  
  
-   sp_EventLog  
  
-   sp_GetMBCSCharLen  
  
-   sp_helplog  
  
-   sp_helpsql  
  
-   sp_IsMBCSLeadByte  
  
-   sp_lock2  
  
-   sp_MSget_current_activity  
  
-   sp_MSset_current_activity  
  
-   sp_MSobjessearch  
  
-   xp_enum_ActiveScriptEngines  
  
-   xp_eventlog  
  
-   xp_GetAdminGroupName  
  
-   xp_GetFileDetails  
  
-   xp_GetLocalSystemAccountName  
  
-   xp_IsNTAdmin  
  
-   xp_MSLocalSystem  
  
-   xp_MSnt2000  
  
-   xp_MSplatform  
  
-   xp_SetSecurity  
  
-   xp_varbintohexstr  
  
## <a name="corrective-action"></a>Action corrective  
  
### <a name="documented-system-stored-procedures"></a>Procédures stockées système documentées  
 Modifiez vos applications d'après le tableau suivant.  
  
|À la place de|Action|  
|----------------|-------------|  
|sp_addalias|Remplacez les alias par une combinaison de comptes d'utilisateurs et de rôles de base de données. Pour plus d'informations, consultez « CREATE USER (Transact-SQL) » et « CREATE ROLE (Transact-SQL) » dans la documentation en ligne de SQL Server. Supprimez les alias dans les bases de données mises à niveau à l'aide de sp_dropalias.|  
|sp_addgroupsp_changegroup<br /><br /> sp_dropgroup<br /><br /> sp_helpgroup|Utilisez des rôles. Pour plus d'informations, consultez « Server-Level Roles » et « Database-Level Roles » dans la documentation en ligne de SQL Server.|  
  
### <a name="undocmented-system-stored-procedures"></a>Procédures stockées système Undocmented  
 Vous pouvez créer des procédures stockées CLR dotées de fonctionnalités équivalentes pour remplacer ces procédures stockées système non documentées. Pour plus d'informations, consultez la rubrique « Procédures stockées CLR » dans la documentation en ligne de SQL Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Le conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
