---
title: Sys.database_credentials (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 02/27/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.database_credentials
- sys.database_credentials_TSQL
- database_credentials
- database_credentials_TSQL
helpviewer_keywords:
- sys.database_credentials catalog view
ms.assetid: 796322df-e62a-45bf-b519-89e1d521abce
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cc6e8fe546412d4549c0724b34e434994ffa744d
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sysdatabasecredentials-transact-sql"></a>Sys.database_credentials (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Retourne une ligne pour chaque base de données étendue des informations d’identification dans la base de données.  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Utilisez [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md) à la place.    
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|credential_id|**int**|ID de la base de données d’une étendue d’informations d’identification. Est unique dans la base de données.|  
|name|**sysname**|Nom de la base de données d’une étendue d’informations d’identification. Est unique dans la base de données.|  
|credential_identity|**nvarchar(4000)**|Nom de l'identité à utiliser. Il s'agit généralement d'un utilisateur Windows. Il n'est pas nécessaire qu'elle soit unique.|  
|create_date|**datetime**|Heure à laquelle les informations d’identification de la portée de la base de données a été créée.|  
|modify_date|**datetime**|Heure de dernière modification à laquelle les informations d’identification de la portée de la base de données.|  
|target_type|**nvarchar (100)**|Type de base de données d’une étendue d’informations d’identification. Retourne NULL pour la base de données étendue des informations d’identification.|  
|target_id|**int**|ID de l’objet mappé vers les informations d’identification de la portée de la base de données. Informations d’identification d’une étendue retourne 0 pour la base de données|  
  
## <a name="permissions"></a>Permissions  
 Requiert l'autorisation `CONTROL` sur la base de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations d’identification &#40; moteur de base de données &#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CRÉER des informations d’identification inclus dans l’étendue de base de données &#40; Transact-SQL &#41;](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)   
 [MODIFIER les informations d’identification inclus dans l’étendue de base de données &#40; Transact-SQL &#41;](../../t-sql/statements/alter-database-scoped-credential-transact-sql.md)   
 [SUPPRIMER les informations d’identification inclus dans l’étendue de base de données &#40; Transact-SQL &#41;](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  
