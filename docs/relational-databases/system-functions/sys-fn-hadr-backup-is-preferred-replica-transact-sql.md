---
description: sys. fn_hadr_backup_is_preferred_replica (Transact-SQL)
title: sys. fn_hadr_backup_is_preferred_replica (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fn_hadr_backup_is_preferred_replica_TSQL
- sys.fn_hadr_backup_is_preferred_replica
- fn_hadr_backup_is_preferred_replica_TSQL
- fn_hadr_backup_is_preferred_replica
dev_langs:
- TSQL
helpviewer_keywords:
- backup on secondary replicas
- active secondary replicas [SQL Server], backup on secondary replicas
- sys.fn_hadr_backup_is_preferred_replica function
ms.assetid: 61b9be77-e2f6-4da1-b2ae-a62cbe226145
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ce16f8300546c77114a27706a7b7ed32806f98ac
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88427811"
---
# <a name="sysfn_hadr_backup_is_preferred_replica--transact-sql"></a>sys. fn_hadr_backup_is_preferred_replica (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Utilisé pour déterminer si le réplica actuel est le réplica de sauvegarde par défaut.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sys.fn_hadr_backup_is_preferred_replica ( 'dbname' )  
```  
  
## <a name="arguments"></a>Arguments  
 '*dbname*'  
 Nom de la base de données actuellement sauvegardée. *dbname* est de type sysname.  
  
## <a name="returns"></a>Retours  
 Retourne le type de données **bool**: 1 si la base de données sur l’instance actuelle se trouve sur le réplica préféré, sinon 0.  
  
## <a name="remarks"></a>Notes  
 Utilisez cette fonction dans un script de sauvegarde pour déterminer si la base de données active est sur le réplica préféré pour les sauvegardes. Vous pouvez exécuter un script sur chaque réplica de disponibilité. Chacun de ces travaux examine les mêmes données pour déterminer quel travail doit s’exécuter. par conséquent, un seul des travaux planifiés passe à l’étape de sauvegarde. L'exemple de code devrait ressembler à ce qui suit :  
  
```  
If sys.fn_hadr_backup_is_preferred_replica( @dbname ) <> 1   
BEGIN  
-- If this is not the preferred replica, exit (probably without error).  
END  
-- If this is the preferred replica, continue to do the backup.  
  
```  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-sysfn_hadr_backup_is_preferred_replica"></a>R. Utilisation de sys.fn_hadr_backup_is_preferred_replica  
 L'exemple suivant retourne 1 si la base de données active est le réplica de sauvegarde par défaut.  
  
```  
SELECT sys.fn_hadr_backup_is_preferred_replica ('TestDB');  
GO  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Tâches associées  
  
-   [Configurer la sauvegarde sur des réplicas de disponibilité &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de groupes de disponibilité Always On &#40;Transact-SQL&#41;](../../relational-databases/system-functions/always-on-availability-groups-functions-transact-sql.md)   
 [Groupes de disponibilité Always On &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-availability-group-transact-sql.md)   
 Secondaires [actifs : sauvegarde sur les réplicas secondaires &#40;Always on les groupes de disponibilité&#41;](../../database-engine/availability-groups/windows/active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md) [Always on affichages catalogue de groupes de disponibilité &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)      
  
  
