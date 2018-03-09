---
title: Sys.cryptographic_providers (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- cryptographic_providers
- sys.cryptographic_providers
- sys.cryptographic_providers_TSQL
- cryptographic_providers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.cryptographic_providers catalog view
ms.assetid: 9da0da95-792e-48b4-9f60-47f0729c279c
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c453171a7378a0fb7201c8a2e577b207e5042337
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="syscryptographicproviders-transact-sql"></a>sys.cryptographic_providers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque fournisseur de chiffrement inscrit.  
    
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**provider_id**|**int**|Numéro d'identification du fournisseur de services de chiffrement.|  
|**nom**|**sysname**|Nom du fournisseur de chiffrement.|  
|**GUID**|**uniqueidentifier**|GUID unique du fournisseur.|  
|**version**|**nvarchar(50)**|Version du fournisseur dans le format '*aa.bb.cccc.dd*'.|  
|**dll_path**|**nvarchar(512)**|Chemin d'accès à la DLL qui implémente l'interface de programmation d'applications (API, Application Program Interface) EKM (Extensible Key Management).|  
|**is_enabled**|**bit**|Indique si le fournisseur est activé sur le serveur ou non.<br /><br /> 0 = non activé (valeur par défaut)<br /><br /> 1 = activé|  
  
## <a name="remarks"></a>Notes  
 Le **sys.cryptographic_providers** est visible au public.  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Gestion de clés extensible &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../t-sql/statements/create-cryptographic-provider-transact-sql.md)  
  
  
