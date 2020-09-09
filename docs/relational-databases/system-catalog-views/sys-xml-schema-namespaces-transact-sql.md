---
description: sys.xml_schema_namespaces (Transact-SQL)
title: sys.xml_schema_namespaces (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.xml_schema_namespaces_TSQL
- sys.xml_schema_namespaces
- xml_schema_namespaces
- xml_schema_namespaces_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_namespaces catalog view
ms.assetid: 3ed42dd6-929a-41de-80e8-d3a0a488bc7a
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 8709142f4ff0e1db417cb67fdb5ea516400ead82
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89545363"
---
# <a name="sysxml_schema_namespaces-transact-sql"></a>sys.xml_schema_namespaces (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Retourne une ligne pour chaque espace de noms XML défini par XSD. Les tuples suivants sont uniques : **collection_id**, **namespace_id**et **collection_id**, et **Name**.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**xml_collection_id**|**int**|ID de la collection de schémas XML contenant cet espace de noms.|  
|**name**|**nvarchar(4000)**|Nom de l'espace de noms XML. Un **nom** vide indique qu’il n’y a pas d’espace de noms cible.|  
|**xml_namespace_id**|**int**|Valeur ordinale comptée à partir de 1 qui identifie de manière unique l'espace de noms XML dans la base de données.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Schémas XML &#40;les affichages catalogue du système de type XML&#41; &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
