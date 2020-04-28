---
title: sys. database_scoped_credentials (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/27/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sys.database_scoped_credentials
- sys.database_scoped_credentials_TSQL
- database_scoped_credentials
- database_scoped_credentials_TSQL
helpviewer_keywords:
- sys.database_scoped_credentials catalog view
ms.assetid: 68e8aa6b-bcdc-42aa-93d8-d498f724c188
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 03687ea50b04c96aa4dbafab9d02d2bbc33a14b3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68079420"
---
# <a name="sysdatabase_scoped_credentials-transact-sql"></a>sys. database_scoped_credentials (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Retourne une ligne pour chaque information d’identification délimitée à la base de données dans la base de données.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|name|**sysname**|Nom des informations d’identification délimitées à la base de données. Est unique dans la base de données.|  
|credential_id|**int**|ID des informations d’identification délimitées à la base de données. Est unique dans la base de données.|  
|principal_id|**int**|ID du principal de la base de données propriétaire de la clé.|  
|credential_identity|**nvarchar(4000)**|Nom de l'identité à utiliser. Il s'agit généralement d'un utilisateur Windows. Il n'est pas nécessaire qu'elle soit unique.|  
|create_date|**datetime**|Heure à laquelle les informations d’identification délimitées à la base de données ont été créées.|  
|modify_date|**datetime**|Heure à laquelle les informations d’identification délimitées à la base de données ont été modifiées pour la dernière fois.|  
|target_type|**nvarchar(100**|Type d’informations d’identification délimitées à la base de données. Retourne `NULL` pour les informations d’identification délimitées à la base de données.|  
|target_id|**int**|ID de l’objet auquel les informations d’identification délimitées à la base de données sont mappées. Retourne 0 pour les informations d’identification délimitées à la base de données|  
  
## <a name="permissions"></a>Autorisations  
 Requiert l'autorisation `CONTROL` sur la base de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations d’identification &#40;Moteur de base de données&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CRÉER des informations d’identification délimitées à la base de données &#40;Transact-SQL&#41;](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)   
 [MODIFICATION des informations d’identification limitées à la base de données &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-credential-transact-sql.md)   
 [SUPPRIMER les informations d’identification délimitées à la base de données &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)   
 [CRÉER des informations d’identification &#40;&#41;Transact-SQL](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  
