---
title: Sys.Schemas (Transact-SQL) | Microsoft Docs
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
ms.openlocfilehash: 67aaff898ab07a4d314eb08cd72cf2c896d5ed7e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47649017"
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
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle **public** . Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Affichages catalogue de schémas &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/c516fb1c-b6ed-48ae-99c7-a78bc4336c8e)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)  
  
  
