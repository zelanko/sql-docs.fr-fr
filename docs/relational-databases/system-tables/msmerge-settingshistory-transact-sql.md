---
title: MSmerge_settingshistory (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_settingshistory
- MSmerge_settingshistory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_settingshistory system table
ms.assetid: 0bdf2d5f-5502-44cd-aa9d-2d5006ad20ce
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 89a936fa8dad5df860f72295c93c915b055a3c48
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85784810"
---
# <a name="msmerge_settingshistory-transact-sql"></a>MSmerge_settingshistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  La table **MSmerge_settingshistory** permet de conserver un historique des modifications apportées aux propriétés de l’article et de la publication pour la réplication de fusion, avec une ligne pour chaque modification apportée à une topologie de réplication de fusion. Cette table contient également des informations sur la date et l'heure à laquelle les paramètres de propriété initiaux ont été définis. Cette table est stockée dans les bases de données de publication et d’abonnement.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**EventTime**|**datetime**|Date et heure auxquels l'événement s'est produit.|  
|**pubid**|**uniqueidentifier**|Numéro d'identification unique d'une publication donnée.|  
|**artid**|**uniqueidentifier**|Numéro d'identification unique de l'article donné.|  
|**événement**|**tinyint**|Spécifie le type d'événement qui est enregistré, à savoir :<br /><br /> **1** -paramètre de propriété de niveau de publication initial.<br /><br /> **2** -modification d’une propriété de publication.<br /><br /> **101** -paramètre initial de la propriété de l’article.<br /><br /> **102** -modification d’une propriété d’article.|  
|**propertyname**|**sysname**|Nom de la propriété définie ou modifiée.|  
|**previousvalue**|**sysname**|Valeur précédente de la propriété si une propriété a été modifiée.|  
|**NewValue**|**sysname**|Valeur à laquelle la propriété a été modifiée ou créée.|  
|**eventtext**|**nvarchar (2000)**|Chaîne de caractères décrivant l'événement.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
