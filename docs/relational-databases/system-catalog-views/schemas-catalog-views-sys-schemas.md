---
title: sys.schemas (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- schemas_TSQL
- sys.schemas_TSQL
- schemas
- sys.schemas
dev_langs:
- TSQL
helpviewer_keywords:
- sys.schemas catalog view
ms.assetid: 29af5ce5-2af7-4103-8f08-3ec92603ba05
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8519dc4846f148b1b4d1bc83589baf0cc6a81e12
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65983142"
---
# <a name="schemas-catalog-views---sysschemas"></a>Affichages - catalogue de schémas sys.schemas
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Contient une ligne pour chaque schéma de base de données.  
  
> [!NOTE]  
>  Les schémas de base de données diffèrent des schémas XML, qui sont utilisés pour définir le modèle de contenu des documents XML.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**nom**|**sysname**|Nom du schéma. Unique dans la base de données.|  
|**schema_id**|**Int**|Identificateur du schéma. Unique dans la base de données.|  
|**principal_id**|**Int**|Identificateur du principal qui possède ce schéma.|  
  
## <a name="remarks"></a>Notes  
Schémas de base de données agissent comme des espaces de noms ou des conteneurs pour les objets, tels que des tables, vues, procédures et fonctions, qui se trouve dans le **sys.objects** vue de catalogue.  

Chaque schéma a un propriétaire. Le propriétaire est une sécurité [principal](../../relational-databases/security/authentication-access/principals-database-engine.md).
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle **public** . Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
[Principaux](../../relational-databases/security/authentication-access/principals-database-engine.md)

[Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   

[Affichages catalogue de schémas &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/c516fb1c-b6ed-48ae-99c7-a78bc4336c8e)   

[sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)  
  
  
