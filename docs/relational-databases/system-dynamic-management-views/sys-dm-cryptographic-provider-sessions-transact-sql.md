---
title: sys. dm_cryptographic_provider_sessions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_cryptographic_provider_sessions
- dm_cryptographic_provider_sessions_TSQL
- sys.dm_cryptographic_provider_sessions_TSQL
- dm_cryptographic_provider_sessions
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_cryptographic_provider_sessions dynamic management function
ms.assetid: 9a4de02b-1a07-4850-979a-0861fddb7f9d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 852566e9f337536717273c18b8034f3854fd7d48
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85894566"
---
# <a name="sysdm_cryptographic_provider_sessions-transact-sql"></a>sys.dm_cryptographic_provider_sessions (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Retourne des informations sur les sessions ouvertes d'un fournisseur de chiffrement.  
 
## <a name="syntax"></a>Syntaxe  
  
```  
  
sys.dm_cryptographic_provider_sessions(session_identifier)  
```  
  
## <a name="arguments"></a>Arguments  
 *session_identifier*  
 Entier indiquant les sessions à retourner.  
  
 0 = connexion en cours uniquement  
  
 1 = toutes les connexions de chiffrement  
  
## <a name="table-returned"></a>Table retournée  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**provider_id**|**int**|Numéro d'identification du fournisseur de services de chiffrement.|  
|**session_handle**|**varbytes (8)**|Descripteur de session de chiffrement.|  
|**identity**|**nvarchar(128)**|Identité utilisée pour l'authentification auprès du fournisseur de chiffrement.|  
|**SPID**|**short**|ID de session (SPID) de la connexion. Pour plus d’informations, consultez [@@SPID &#40;Transact-SQL&#41;](../../t-sql/functions/spid-transact-sql.md).|  
  
## <a name="remarks"></a>Remarques  
 La vue **sys. dm_cryptographic_provider_sessions** est visible par le public pour la connexion actuelle. Pour afficher toutes les connexions de chiffrement, vous devez disposer de l’autorisation **Control** Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Gestion de clés extensible &#40;&#41;EKM](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [CRÉER un fournisseur de services de CHIFFREment &#40;&#41;Transact-SQL](../../t-sql/statements/create-cryptographic-provider-transact-sql.md)   
 [Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
