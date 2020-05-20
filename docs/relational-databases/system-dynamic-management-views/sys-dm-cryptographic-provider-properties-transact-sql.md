---
title: sys. dm_cryptographic_provider_properties (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_cryptographic_provider_properties_TSQL
- sys.dm_cryptographic_provider_properties
- sys.dm_cryptographic_provider_properties_TSQL
- dm_cryptographic_provider_properties
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_cryptographic_provider_properties dynamic management view
ms.assetid: 024b0095-6766-4189-a39a-d316c5ec2874
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0b08159d666fb18cc92feb88f087168b249ff523
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82824694"
---
# <a name="sysdm_cryptographic_provider_properties-transact-sql"></a>sys.dm_cryptographic_provider_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne des informations sur les fournisseurs de services de chiffrement inscrits.  
  
 
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|provider_id|**int**|Numéro d'identification du fournisseur de services de chiffrement.|  
|guid|**uniqueidentifier**|GUID unique du fournisseur.|  
|provider_version|**nvarchar(256)**|Version du fournisseur au format'*AA.bb.CCCC.DD*'.|  
|sqlcrypt_version|**nvarchar(256)**|Version principale de l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] API de chiffrement au format'*AA.bb.CCCC.DD*'.|  
|friendly_name|**nvarchar(2048)**|Nom fourni par le fournisseur.|  
|authentication_type|**nvarchar(256)**|WINDOWS, de base ou autre.|  
|symmetric_key_support|**tinyint**|0 (non pris en charge)<br /><br /> 1 (pris en charge)|  
|symmetric_key_export|**tinyint**|0 (non pris en charge)<br /><br /> 1 (pris en charge)|  
|symmetric_key_import|**tinyint**|0 (non pris en charge)<br /><br /> 1 (pris en charge)|  
|symmetric_key_persistance|**tinyint**|0 (non pris en charge)<br /><br /> 1 (pris en charge)|  
|asymmetric_key_support|**tinyint**|0 (non pris en charge)<br /><br /> 1 (pris en charge)|  
|asymmetric_key_export|**tinyint**|0 (non pris en charge)<br /><br /> 1 (pris en charge)|  
|symmetric_key_import|**tinyint**|0 (non pris en charge)<br /><br /> 1 (pris en charge)|  
|symmetric_key_persistance|**tinyint**|0 (non pris en charge)<br /><br /> 1 (pris en charge)|  
  
## <a name="remarks"></a>Remarques  
 La vue sys.dm_cryptographic_provider_properties est visible au public.  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Gestion de clés extensible &#40;&#41;EKM](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [CRÉER un fournisseur de services de CHIFFREment &#40;&#41;Transact-SQL](../../t-sql/statements/create-cryptographic-provider-transact-sql.md)   
 [Fonctions et vues de gestion dynamique relatives à la sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  
