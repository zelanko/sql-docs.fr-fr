---
title: Sys.xml_schema_collections (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.xml_schema_collections_TSQL
- sys.xml_schema_collections
- xml_schema_collections
- xml_schema_collections_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_collections catalog view
ms.assetid: f3f7f3dc-029f-4942-ab3c-75fa9814e40f
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0e891585d5e44c4b2562d5fa704848f7abfa8292
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47632577"
---
# <a name="sysxmlschemacollections-transact-sql"></a>sys.xml_schema_collections (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Renvoie une ligne par collection de schémas XML. Une collection de schémas XML est un ensemble nommé de définitions XSD. La collection de schémas XML elle-même est contenue dans un schéma relationnel et identifiée par un nom [!INCLUDE[tsql](../../includes/tsql-md.md)] d'étendue sur le schéma. Les tuples suivants sont uniques : xml_collection_id et schema_id et  name.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|xml_collection_id|**Int**|ID de la collection de schémas XML. Unique dans la base de données.|  
|schema_id|**Int**|ID du schéma relationnel qui contient cette collection de schémas XML.|  
|principal_id|**Int**|ID du propriétaire spécifique s’il est différent du propriétaire du schéma. Par défaut, le propriétaire du schéma détient les objets contenus dans le schéma. Toutefois, un autre propriétaire peut être spécifié à l’aide de l’instruction ALTER AUTHORIZATION pour modifier la propriété.<br /><br /> NULL = Pas d'autre propriétaire individuel.|  
|NAME|**sysname**|Nom de la collection de schémas XML.|  
|create_date|**datetime**|Date de création de la collection de schémas XML.|  
|modify_date|**datetime**|Date de dernière modification de la collection de schémas XML.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Schémas XML &#40;système de Type XML&#41; affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)   
 [Questions fréquentes (FAQ) sur l’interrogation des catalogues système SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
