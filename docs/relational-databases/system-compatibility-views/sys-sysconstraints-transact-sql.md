---
title: Sys.sysconstraints (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysconstraints
- sys.sysconstraints
- sysconstraints_TSQL
- sys.sysconstraints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysconstraints compatibility view
- sysconstraints system table
ms.assetid: f2b2e2ad-ba24-48a1-913c-8ee4e0895dc4
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: fce3ca4a2055d7f4eb10cfdcac7f09c7fd004282
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47806877"
---
# <a name="syssysconstraints-transact-sql"></a>sys.sysconstraints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Contient le mappage des contraintes vers les objets détenant ces contraintes dans la base de données.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**constid**|**Int**|Numéro de contrainte.|  
|**id**|**Int**|Identificateur de la table qui détient la contrainte.|  
|**colid**|**smallint**|ID de la colonne sur laquelle la contrainte est définie.<br /><br /> 0 = Contrainte de niveau table|  
|**spare1**|**tinyint**|Réservé|  
|**status**|**Int**|Pseudo-masque de bits indiquant l'état. Il peut prendre les valeurs suivantes :<br /><br /> 1 = Contrainte PRIMARY KEY<br /><br /> 2 = Contrainte UNIQUE KEY<br /><br /> 3 = Contrainte FOREIGN KEY<br /><br /> 4 = Contrainte CHECK<br /><br /> 5 = Contrainte DEFAULT<br /><br /> 16 = Contrainte de niveau colonne<br /><br /> 32 = Contrainte de niveau table|  
|**actions**|**Int**|Réservé|  
|**Erreur**|**Int**|Réservé|  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des Tables système avec les vues système &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Affichages de compatibilité &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
