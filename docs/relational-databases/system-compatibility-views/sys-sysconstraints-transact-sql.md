---
title: sys. sysconstraints (Transact-SQL) | Microsoft Docs
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
ms.openlocfilehash: dfd88dec92d2707b72c829aa53f2798d3d64fee3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68089196"
---
# <a name="syssysconstraints-transact-sql"></a>sys.sysconstraints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Contient le mappage des contraintes vers les objets détenant ces contraintes dans la base de données.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**constid**|**int**|Numéro de contrainte.|  
|**identifi**|**int**|Identificateur de la table qui détient la contrainte.|  
|**colid**|**smallint**|ID de la colonne sur laquelle la contrainte est définie.<br /><br /> 0 = Contrainte de niveau table|  
|**spare1**|**tinyint**|Réservé|  
|**statu**|**int**|Pseudo-masque de bits indiquant l'état. Il peut prendre les valeurs suivantes :<br /><br /> 1 = Contrainte PRIMARY KEY<br /><br /> 2 = Contrainte UNIQUE KEY<br /><br /> 3 = Contrainte FOREIGN KEY<br /><br /> 4 = Contrainte CHECK<br /><br /> 5 = Contrainte DEFAULT<br /><br /> 16 = Contrainte de niveau colonne<br /><br /> 32 = Contrainte de niveau table|  
|**interventions**|**int**|Réservé|  
|**Erreurs**|**int**|Réservé|  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage de tables système à des vues système &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Vues de compatibilité &#40;&#41;Transact-SQL](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
