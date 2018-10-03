---
title: Sys.xml_schema_facets (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.xml_schema_facets
- xml_schema_facets_TSQL
- sys.xml_schema_facets_TSQL
- xml_schema_facets
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_facets catalog view
ms.assetid: 4402dde9-1877-4872-8550-140dc2a177d2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 34370bd923a2ea6ccd66964ff9499de740171e68
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47684107"
---
# <a name="sysxmlschemafacets-transact-sql"></a>sys.xml_schema_facets (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque facette (restriction) d’une définition de type xml (correspond à **sys.xml_types**).  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**xml_component_id**|**Int**|Identificateur du composant XML (type) auquel cette facette appartient.|  
|**facet_id**|**Int**|ID (ordinal de base 1) de la facette, unique au sein de l'ID de composant.|  
|**Type**|**char(2)**|Type de facette :<br /><br /> LG = Longueur<br /><br /> LN = Longueur minimum<br /><br /> LX = Longueur maximum<br /><br /> PT = Motif (expression régulière)<br /><br /> EU = Énumération<br /><br /> IN = Valeur inclusive minimum<br /><br /> IX = Valeur inclusive maximum<br /><br /> EN = Valeur exclusive minimum<br /><br /> EX = Valeur exclusive maximum<br /><br /> DT = Chiffres totaux<br /><br /> DF = Chiffres fractionnaires<br /><br /> WS = Normalisation des blancs|  
|**kind_desc**|**Nvarchar (60)**|Description du type de facette :<br /><br /> LENGTH<br /><br /> MINIMUM_LENGTH<br /><br /> MAXIMUM_LENGTH<br /><br /> PATTERN<br /><br /> ENUMERATION<br /><br /> MINIMUM_INCLUSIVE_VALUE<br /><br /> MAXIMUM_INCLUSIVE_VALUE<br /><br /> MINIMUM_EXCLUSIVE_VALUE<br /><br /> MAXIMUM_EXCLUSIVE_VALUE<br /><br /> TOTAL_DIGITS<br /><br /> FRACTION_DIGITS<br /><br /> WHITESPACE_NORMALIZATION|  
|**is_fixed**|**bit**|1 = La facette a une valeur fixe, spécifiée à l'avance.<br /><br /> 0 = Pas de valeur fixe. (par défaut)|  
|**value**|**nvarchar (4000)**|Valeur fixe prédéfinie de la facette.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Schémas XML &#40;système de Type XML&#41; affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
