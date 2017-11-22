---
title: Sys.sysaltfiles (Transact-SQL) | Documents Microsoft
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
- sys.sysaltfiles_TSQL
- sys.sysaltfiles
- sysaltfiles_TSQL
- sysaltfiles
dev_langs: TSQL
helpviewer_keywords:
- sysaltfiles system table
- sys.sysaltfiles compatibility view
ms.assetid: 698dec23-5336-4108-87a5-f8e407f8da09
caps.latest.revision: "35"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e79cd2d5a4e0833af0fe03e2787e065606f7b105
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="syssysaltfiles-transact-sql"></a>sys.sysaltfiles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Sous certaines conditions, contient des lignes correspondant aux fichiers d'une base de données.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**fileid**|**smallint**|Numéro d'identification du fichier. Il est unique pour chaque base de données.|  
|**GroupID**|**smallint**|Numéro d'identification du groupe de fichiers.|  
|**taille**|**int**|Taille du fichier, en pages de 8 kilo-octets (Ko).|  
|**MaxSize**|**int**|Taille maximale du fichier, en pages de 8 Ko.<br /><br /> 0 = Croissance nulle.<br /><br /> -1 = Le fichier peut croître tant que le disque n'est pas saturé.<br /><br /> 268435456 = Le fichier journal peut croître pour atteindre une taille maximale de 2 To.<br /><br /> Remarque : Les bases de données qui sont mis à niveau avec une taille de fichier journal illimitée signalera -1 pour la taille maximale du fichier journal.|  
|**croissance**|**int**|Taille de croissance de la base de données.<br /><br /> 0 = Croissance nulle. Il peut s'agir du nombre de pages ou du pourcentage de la taille du fichier selon la valeur de status. Si **état** est 0 x 100000, **croissance** est le pourcentage du fichier taille ; sinon, c’est le nombre de pages.|  
|**status**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**performances**|**int**|Réservé.|  
|**dbid**|**smallint**|Numéro d'identification de la base de données à laquelle le fichier appartient.|  
|**nom**|**sysname**|Nom logique du fichier.|  
|**nom de fichier**|**nvarchar (260)**|Nom de l'unité physique. Inclut le chemin d'accès complet du fichier.|  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des Tables système pour les vues système &#40; Transact-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Affichages de compatibilité &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
