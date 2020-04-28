---
title: sys. pdw_health_alerts (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: system-objects
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 49c01e5f-ee47-41a0-871d-35a759f50851
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: c47bcc342bf8a052aed93649ca0ad8475d937608
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68127541"
---
# <a name="syspdw_health_alerts-transact-sql"></a>sys. pdw_health_alerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Stocke les propriétés des différentes alertes qui peuvent se produire sur le système. Il s’agit d’une table de catalogue pour les alertes.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|alert_id|**int**|Identificateur unique de l’alerte.<br /><br /> Clé pour cette vue.|NOT NULL|  
|component_id|**int**|ID du composant auquel cette alerte s’applique. Le composant est un identificateur de composant général, tel que « alimentation », et n’est pas spécifique à une installation. Consultez [sys. pdw_health_components &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).|NOT NULL|  
|alert_name|**nvarchar(255)**|Nom de l’alerte.|NOT NULL|  
|state|**nvarchar(32)**|État de l’alerte.|NOT NULL<br /><br /> Valeurs possibles :<br /><br /> Quotidiennes<br /><br /> 'Ne fonctionne pas'<br /><br /> Détérioré<br /><br /> Défectueux|  
|severity|**nvarchar(32)**|Gravité de l’alerte.|NOT NULL<br /><br /> Valeurs possibles :<br /><br /> D’information<br /><br /> Tres<br /><br /> Erreurs|  
|type|**nvarchar(32)**|Type of alert.|NOT NULL<br /><br /> Valeurs possibles :<br /><br /> StatusChange-l’état de l’appareil a changé.<br /><br /> Seuil-une valeur a dépassé la valeur de seuil.|  
|description|**nvarchar(4000)**|Description de l’alerte.|NOT NULL|  
|condition|**nvarchar(255)**|Utilisé lorsque type = Threshold. Définit le mode de calcul du seuil d’alerte.|NULL|  
|status|**nvarchar(32)**|État des alertes|NULL|  
|condition_value|**bit**|Indique si l’alerte est autorisée à se produire pendant le fonctionnement du système.|NULL<br /><br /> Valeurs possibles<br /><br /> 0-l’alerte n’est pas générée.<br /><br /> 1-l’alerte est générée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue SQL Data Warehouse et Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
