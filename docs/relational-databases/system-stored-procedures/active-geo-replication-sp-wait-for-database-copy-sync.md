---
title: sp_wait_for_database_copy_sync (Azure SQL Database) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sp_wait_for_database_copy_sync_TSQL
- sp_wait_for_database_copy_sync
dev_langs:
- TSQL
helpviewer_keywords:
- sp_wait_for_database_copy_sync
ms.assetid: 7068da7f-cb74-47f2-b064-eb076a0d3885
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: dd0d134e723a8ca45729933cbbf5b0d75bbde7e6
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774584"
---
# <a name="active-geo-replication---spwaitfordatabasecopysync"></a>Géo-réplication Active - sp_wait_for_database_copy_sync
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Cette procédure aborde la relation [!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)] entre une base de données primaire et une base de données secondaire. Appel de la **sp_wait_for_database_copy_sync** oblige l’application à attendre que toutes les transactions validées sont répliquées et acceptées par la base de données secondaire active. Exécutez **sp_wait_for_database_copy_sync** uniquement la base de données primaire.  
  
||  
|-|  
|**S'applique à**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|  
  
## <a name="syntax"></a>Syntaxe  
  
```  
sp_wait_for_database_copy_sync [ @target_server = ] 'server_name'   
     , [ @target_database = ] 'database_name'  
```  
  
## <a name="arguments"></a>Arguments  
 [ @target_server = ] 'server_name'  
 Nom du serveur SQL Database qui héberge la base de données secondaire active. server_name est de type sysname, sans valeur par défaut.  
  
 [ @target_database = ] 'database_name'  
 Nom de la base de données secondaire active. database_name est de type sysname, sans valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 Retourne 0 en cas de réussite ou un numéro d'erreur en cas d'échec.  
  
 Les conditions d'erreur les plus probables sont les suivantes :  
  
-   Le nom du serveur ou le nom de la base de données est manquant.  
  
-   Le lien est introuvable sur le nom du serveur ou la base de données spécifié.  
  
-   La connectivité de l'interlien est perdue. **sp_wait_for_database_copy_sync** retournera après expiration du délai de connexion.  
  
## <a name="permissions"></a>Autorisations  
 Tout utilisateur dans la base de données primaire peut appeler cette procédure stockée système. La connexion doit être un utilisateur dans les bases de données primaire et secondaire active.  
  
## <a name="remarks"></a>Notes  
 Toutes les transactions validées avant un **sp_wait_for_database_copy_sync** appel sont envoyés à la base de données secondaire active.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant appelle **sp_wait_for_database_copy_sync** pour vous assurer que toutes les transactions sont validées dans la base de données primaire, db0, soient envoyées à sa base de données secondaire active sur l’ubfyu5ssyt du serveur cible.  
  
```  
USE db0;  
GO  
EXEC sys.sp_wait_for_database_copy_sync @target_server = N'ubfyu5ssyt1', @target_database = N'db0';  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Sys.dm_continuous_copy_status &#40;base de données SQL Azure&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-continuous-copy-status-azure-sql-database.md)   
 [Fonctions et vues de gestion dynamique de géo-réplication &#40;base de données SQL Azure&#41;](../../relational-databases/system-dynamic-management-views/geo-replication-dynamic-management-views-and-functions-azure-sql-database.md)  
  
  
