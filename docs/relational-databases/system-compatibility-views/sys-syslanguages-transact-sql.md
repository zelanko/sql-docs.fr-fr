---
title: sys. syslanguages (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.syslanguages
- sys.syslanguages_TSQL
- syslanguages
- syslanguages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- syslanguages system table
- sys.syslanguages compatibility view
ms.assetid: f216d1cd-997c-42f0-a737-abbdfcd88383
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bc152b8241b775f9fd686f8a31363cb4fca39de4
ms.sourcegitcommit: f76b4e96c03ce78d94520e898faa9170463fdf4f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70874872"
---
# <a name="syssyslanguages-transact-sql"></a>sys.syslanguages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Contient une ligne pour chaque langue présente dans l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|langid|**smallint**|ID unique de la langue.|  
|dateformat|**nchar(3)**|Ordre des éléments de la date, par exemple JMA.|  
|datefirst|**tinyint**|Premier jour de la semaine : 1 pour lundi, 2 pour mardi, etc., jusqu'à 7 pour dimanche.|  
|upgrade|**int**|Réservé pour le système.|  
|name|**sysname**|Nom officiel de la langue, par exemple « Français ».|  
|alias|**sysname**|Nom de la langue de remplacement, par exemple « French ».|  
|mois|**nvarchar(372)**|Liste des noms complets des mois, séparés par des virgules, dans l'ordre, de janvier à décembre. Chaque nom peut comporter jusqu'à 20 caractères.|  
|mois courts|**nvarchar(132)**|Liste des noms abrégés des mois, séparés par des virgules, dans l'ordre, de janvier à décembre. Chaque nom peut comporter jusqu'à 9 caractères.|  
|jours|**nvarchar(217)**|Liste des noms des jours, séparés par des virgules, dans l'ordre, de lundi à dimanche. Chaque nom peut comporter jusqu'à 30 caractères.|  
|lcid|**int**|Identificateur des paramètres régionaux [!INCLUDE[msCoName](../../includes/msconame-md.md)] de la langue.|  
|msglangid|**smallint**|ID du groupe de messages du [!INCLUDE[ssDE](../../includes/ssde-md.md)].|  
  
 Les langues suivantes sont contenues dans [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
|Nom en anglais|LCID Windows|ID du groupe de messages [!INCLUDE[ssDE](../../includes/ssde-md.md)]|  
|---------------------|------------------|-----------------------------------------|  
|English|1033|1033|  
|German|1031|1031|  
|French|1036|1036|  
|Japanese|1041|1041|  
|Danois|1030|1030|  
|Spanish|3082|3082|  
|Italian|1040|1040|  
|Dutch|1043|1043|  
|Norvégien|2068|2068|  
|Portugais|2070|2070|  
|Finlandais|1035|1035|  
|Swedish|1053|1053|  
|Czech|1029|1029|  
|Hongrois|1038|1038|  
|Polish|1045|1045|  
|Romanian|1048|1048|  
|Croatian|1050|1050|  
|Slovak|1051|1051|  
|Slovene|1060|1060|  
|Greek|1032|1032|  
|Bulgarian|1026|1026|  
|Russian|1049|1049|  
|Turkish|1055|1055|  
|British English|2057|1033|  
|Estonien|1061|1061|  
|Latvian|1062|1062|  
|Lithuanian|1063|1063|  
|Portuguese (Brazil)|1046|1046|  
|Traditional Chinese|1028|1028|  
|Korean|1042|1042|  
|Simplified Chinese|2052|2052|  
|Arabic|1025|1025|  
|Thai|1054|1054|  
  
## <a name="see-also"></a>Voir aussi  
 [Vues &#40;de compatibilité Transact-&#41; SQL](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)   
 [Mappage de tables système à des &#40;vues système Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)  
  
  
