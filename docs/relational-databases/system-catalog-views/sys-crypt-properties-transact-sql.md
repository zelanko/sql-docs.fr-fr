---
title: sys. crypt_properties (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- crypt_properties
- crypt_properties_TSQL
- sys.crypt_properties_TSQL
- sys.crypt_properties
dev_langs:
- TSQL
helpviewer_keywords:
- sys.crypt_properties catalog view
ms.assetid: d5684f5a-30b1-418e-ae4d-ab040db9257e
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9655866d4fd2d6f98b38532f77f94bc12f16f9b4
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68109480"
---
# <a name="syscrypt_properties-transact-sql"></a>sys.crypt_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Renvoie une ligne pour chaque propriété de chiffrement associée à un élément sécurisable.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**class**|**tinyint**|Identifie la classe de l'élément sur lequel la propriété est définie.<br /><br /> 1 = Objet ou colonne<br /> 5 = Assembly|  
|**class_desc**|**nvarchar(60)**|Description de la classe de l'élément sur lequel la propriété est définie.<br /><br /> OBJECT_OR_COLUMN<br /> ASSEMBLY|  
|**major_id**|**int**|ID de l'élément sur lequel la propriété est définie, interprété en fonction de la classe|  
|**d**|**varbinary(32)**|Utilisation du hachage SHA-1 du certificat ou de la clé asymétrique.|  
|**crypt_type**|**Char (4)**|Type de chiffrement.<br /><br /> SPVC = signé par la clé privée du certificat<br /><br /> SPVA = signed par clé privée asymétrique<br /><br /> CPVC = Signature de compteur par clé privée de certificat<br /><br /> CPVA = Signature de compteur par clé asymétrique|  
|**crypt_type_desc**|**nvarchar(60)**|Description du type de chiffrement.<br /><br /> SIGNATURE BY CERTIFICATE<br /><br /> SIGNATURE BY ASYMMETRIC KEY<br /><br /> COUNTER SIGNATURE BY CERTIFICATE<br /><br /> COUNTER SIGNATURE BY ASYMMETRIC KEY|  
|**crypt_property**|**varbinary(max)**|Bits signés ou chiffrés. Pour un module signé, il s’agit des bits de signature du module.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Éléments sécurisables](../../relational-databases/security/securables.md)   
 [CRÉER un certificat &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [CRÉER une clé symétrique &#40;&#41;Transact-SQL](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [CRÉER une clé asymétrique &#40;&#41;Transact-SQL](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
