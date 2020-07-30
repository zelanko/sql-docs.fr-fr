---
title: sys. database_credentials (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/27/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.database_credentials
- sys.database_credentials_TSQL
- database_credentials
- database_credentials_TSQL
helpviewer_keywords:
- sys.database_credentials catalog view
ms.assetid: 796322df-e62a-45bf-b519-89e1d521abce
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5b78875b7c6f3440bd747045d1b90d0f8ef323c4
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87394884"
---
# <a name="sysdatabase_credentials-transact-sql"></a>sys. database_credentials (Transact-SQL)
[!INCLUDE [sqlserver2016-asdb-asdbmi-asa](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asa.md)]

  Retourne une ligne pour chaque information d’identification délimitée à la base de données dans la base de données.  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Utilisez à la place [sys. database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md) .    
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|credential_id|**int**|ID des informations d’identification délimitées à la base de données. Est unique dans la base de données.|  
|name|**sysname**|Nom des informations d’identification délimitées à la base de données. Est unique dans la base de données.|  
|credential_identity|**nvarchar(4000)**|Nom de l'identité à utiliser. Il s'agit généralement d'un utilisateur Windows. Il n'est pas nécessaire qu'elle soit unique.|  
|create_date|**datetime**|Heure à laquelle les informations d’identification délimitées à la base de données ont été créées.|  
|modify_date|**datetime**|Heure à laquelle les informations d’identification délimitées à la base de données ont été modifiées pour la dernière fois.|  
|target_type|**nvarchar(100**|Type d’informations d’identification délimitées à la base de données. Retourne NULL pour les informations d’identification délimitées à la base de données.|  
|target_id|**int**|ID de l’objet auquel les informations d’identification délimitées à la base de données sont mappées. Retourne 0 pour les informations d’identification délimitées à la base de données|  
  
## <a name="permissions"></a>Autorisations  
 Requiert l'autorisation `CONTROL` sur la base de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations d’identification &#40;Moteur de base de données&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CRÉER des informations d’identification délimitées à la base de données &#40;Transact-SQL&#41;](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)   
 [MODIFICATION des informations d’identification limitées à la base de données &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-credential-transact-sql.md)   
 [SUPPRIMER les informations d’identification délimitées à la base de données &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  
