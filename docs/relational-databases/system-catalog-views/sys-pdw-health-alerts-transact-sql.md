---
description: sys.pdw_health_alerts (Transact-SQL)
title: sys.pdw_health_alerts (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
ms.assetid: 49c01e5f-ee47-41a0-871d-35a759f50851
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016'
ms.openlocfilehash: fcdb396016c58f82f3e67f08af2b5489adb40731
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97472940"
---
# <a name="syspdw_health_alerts-transact-sql"></a>sys.pdw_health_alerts (Transact-SQL)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  Stocke les propriétés des différentes alertes qui peuvent se produire sur le système. Il s’agit d’une table de catalogue pour les alertes.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|alert_id|**int**|Identificateur unique de l’alerte.<br /><br /> Clé pour cette vue.|NOT NULL|  
|component_id|**int**|ID du composant auquel cette alerte s’applique. Le composant est un identificateur de composant général, tel que « alimentation », et n’est pas spécifique à une installation. Consultez [sys.pdw_health_components &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).|NOT NULL|  
|alert_name|**nvarchar(255)**|Nom de l’alerte.|NOT NULL|  
|state|**nvarchar(32)**|État de l’alerte.|NOT NULL<br /><br /> Valeurs possibles :<br /><br /> Quotidiennes<br /><br /> 'Ne fonctionne pas'<br /><br /> Détérioré<br /><br /> Défectueux|  
|severity|**nvarchar(32)**|Gravité de l’alerte.|NOT NULL<br /><br /> Valeurs possibles :<br /><br /> D’information<br /><br /> Tres<br /><br /> Erreurs|  
|type|**nvarchar(32)**|Type of alert.|NOT NULL<br /><br /> Valeurs possibles :<br /><br /> StatusChange-l’état de l’appareil a changé.<br /><br /> Seuil-une valeur a dépassé la valeur de seuil.|  
|description|**nvarchar(4000)**|Description de l’alerte.|NOT NULL|  
|condition|**nvarchar(255)**|Utilisé lorsque type = Threshold. Définit le mode de calcul du seuil d’alerte.|NULL|  
|status|**nvarchar(32)**|État des alertes|NULL|  
|condition_value|**bit**|Indique si l’alerte est autorisée à se produire pendant le fonctionnement du système.|NULL<br /><br /> Valeurs possibles<br /><br /> 0-l’alerte n’est pas générée.<br /><br /> 1-l’alerte est générée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de catalogue Azure Synapse Analytics et Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
