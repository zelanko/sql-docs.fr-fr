---
title: sys.xml_schema_model_groups (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.xml_schema_model_groups
- xml_schema_model_groups
- sys.xml_schema_model_groups_TSQL
- xml_schema_model_groups_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_model_groups catalog view
ms.assetid: 566556dc-a8c8-465c-9196-c7e0ae092a8a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 49264895f37b31d6899fa926912cc2531dde4f55
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85738727"
---
# <a name="sysxml_schema_model_groups-transact-sql"></a>sys.xml_schema_model_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Retourne une ligne par composant de schéma XML qui est un groupe de modèles, **symbol_space** de **M**..  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**\<inherited columns>**||Hérite des colonnes de [sys.xml_schema_components](../../relational-databases/system-catalog-views/sys-xml-schema-components-transact-sql.md).|  
|**compositor**|**Char(1**|Type de compositeur du groupe :<br /><br /> A = \<all> groupe XSD<br /><br /> C = \<choice> groupe XSD<br /><br /> S = \<sequence> groupe XSD|  
|**compositor_desc**|**nvarchar (60)**|Description du type de compositeur du groupe :<br /><br /> XSD_ALL_GROUP<br /><br /> XSD_CHOICE_GROUP<br /><br /> XSD_SEQUENCE_GROUP|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Schémas XML &#40;les affichages catalogue du système de type XML&#41; &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
