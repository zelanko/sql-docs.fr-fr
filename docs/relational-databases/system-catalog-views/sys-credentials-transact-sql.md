---
title: sys.credentials (Transact-SQL) Microsoft Docs
ms.custom: ''
ms.date: 04/06/2020
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.credentials
- sys.credentials_TSQL
- credentials_TSQL
- credentials
dev_langs:
- TSQL
helpviewer_keywords:
- sys.credentials catalog view
ms.assetid: ea48cf80-904a-4273-a950-6d35b1b0a1b6
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f87378897256f8b4fae26b30263577bedede6175
ms.sourcegitcommit: c6a2efe551e37883c1749bdd9e3c06eb54ccedc9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80752888"
---
# <a name="syscredentials-transact-sql"></a>sys.credentials (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdbmi-asdw-pdw-md.md)]

  Retourne une ligne pour chaque identifiant de niveau serveur.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|credential_id|**Int**|ID de l'information d'identification. Unique dans le serveur.|  
|name|**sysname**|Nom de l'information d'identification. Unique dans le serveur.|  
|credential_identity|**nvarchar(4000)**|Nom de l'identité à utiliser. Il s'agit généralement d'un utilisateur Windows. Il n'est pas nécessaire qu'elle soit unique.|  
|create_date|**datetime**|Heure de création de l'information d'identification.|  
|modify_date|**datetime**|Heure de la dernière modification de l'information d'identification.|  
|target_type|**nvarchar(100)**|Type d'information d'identification. Retourne NULL pour des informations d'identification traditionnelles, CRYPTOGRAPHIC PROVIDER pour des informations d'identification mappées à un fournisseur de chiffrement. Pour plus d’informations sur les principaux fournisseurs externes de gestion, voir [Extensible Key Management &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md).|  
|target_id|**Int**|ID de l'objet auquel l'information d'identification est mappée. Retourne 0 pour des informations d'identification traditionnelles, et une valeur différente de 0 pour des informations d'identification mappées à un fournisseur de chiffrement. Pour plus d’informations sur les principaux fournisseurs externes de gestion, voir [Extensible Key Management &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md).|  

## <a name="remarks"></a>Notes  
Pour les informations d’identification au niveau de la base de données, voir [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md).
  
## <a name="permissions"></a>Autorisations  
 Nécessite `VIEW ANY DEFINITION` soit `ALTER ANY CREDENTIAL` la permission, soit la permission. De plus, le mandant `VIEW ANY DEFINITION` ne doit pas se voir refuser la permission.  
  
## <a name="see-also"></a>Voir aussi  
 [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md)   
 [Credentials &#40;Database Engine&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [Vue du catalogue de sécurité &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Principaux &#40;&#41;de moteur de base de données](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)  
  
  
