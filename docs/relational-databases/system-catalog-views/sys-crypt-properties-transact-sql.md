---
title: Sys.crypt_properties (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- crypt_properties
- crypt_properties_TSQL
- sys.crypt_properties_TSQL
- sys.crypt_properties
dev_langs: TSQL
helpviewer_keywords: sys.crypt_properties catalog view
ms.assetid: d5684f5a-30b1-418e-ae4d-ab040db9257e
caps.latest.revision: "29"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ded0c42bbfd7c16b30ab93c9212c6c69b0e2a587
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="syscryptproperties-transact-sql"></a>sys.crypt_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Renvoie une ligne pour chaque propriété de chiffrement associée à un élément sécurisable.  
  
||  
|-|  
|**S’applique aux**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] ([Aperçu dans certaines régions](http://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)).|  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**classe**|**tinyint**|Identifie la classe de l'élément sur lequel la propriété est définie.<br /><br /> 1 = Objet ou colonne|  
|**class_desc**|**nvarchar (60)**|Description de la classe de l'élément sur lequel la propriété est définie.<br /><br /> OBJECT_OR_COLUMN|  
|**major_id**|**int**|ID de l'élément sur lequel la propriété est définie, interprété en fonction de la classe|  
|**empreinte numérique**|**varbinary(32)**|Utilisation du hachage SHA-1 du certificat ou de la clé asymétrique.|  
|**crypt_type**|**char (4)**|Type de chiffrement.<br /><br /> SPVC = Chiffrement par clé privée de certificat<br /><br /> SPVA = Chiffrement par clé privée asymétrique<br /><br /> CPVC = Signature de compteur par clé privée de certificat<br /><br /> CPVA = Signature de compteur par clé asymétrique|  
|**crypt_type_desc**|**nvarchar (60)**|Description du type de chiffrement.<br /><br /> SIGNATURE BY CERTIFICATE<br /><br /> SIGNATURE BY ASYMMETRIC KEY<br /><br /> COUNTER SIGNATURE BY CERTIFICATE<br /><br /> COUNTER SIGNATURE BY ASYMMETRIC KEY|  
|**crypt_property**|**varbinary(max)**|Bits signés ou chiffrés.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Securables](../../relational-databases/security/securables.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
