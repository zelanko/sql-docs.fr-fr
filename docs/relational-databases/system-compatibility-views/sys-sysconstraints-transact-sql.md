---
title: Sys.sysconstraints (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysconstraints
- sys.sysconstraints
- sysconstraints_TSQL
- sys.sysconstraints_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sys.sysconstraints compatibility view
- sysconstraints system table
ms.assetid: f2b2e2ad-ba24-48a1-913c-8ee4e0895dc4
caps.latest.revision: "32"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ee37d3cf7749511eacd433a191acf7fd1350cd3d
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="syssysconstraints-transact-sql"></a>sys.sysconstraints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Contient le mappage des contraintes vers les objets détenant ces contraintes dans la base de données.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**constid**|**int**|Numéro de contrainte.|  
|**id**|**int**|Identificateur de la table qui détient la contrainte.|  
|**colid**|**smallint**|ID de la colonne sur laquelle la contrainte est définie.<br /><br /> 0 = Contrainte de niveau table|  
|**spare1**|**tinyint**|Réservé|  
|**status**|**int**|Pseudo-masque de bits indiquant l'état. Il peut prendre les valeurs suivantes :<br /><br /> 1 = Contrainte PRIMARY KEY<br /><br /> 2 = Contrainte UNIQUE KEY<br /><br /> 3 = Contrainte FOREIGN KEY<br /><br /> 4 = Contrainte CHECK<br /><br /> 5 = Contrainte DEFAULT<br /><br /> 16 = Contrainte de niveau colonne<br /><br /> 32 = Contrainte de niveau table|  
|**actions**|**int**|Réservé|  
|**erreur**|**int**|Réservé|  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des Tables système pour les vues système &#40; Transact-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Affichages de compatibilité &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
