---
title: Sys.sysfiles (Transact-SQL) | Documents Microsoft
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
- sysfiles
- sys.sysfiles_TSQL
- sys.sysfiles
- sysfiles_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sysfiles system table
- sys.sysfiles compatibility view
ms.assetid: 3b47f38d-1cff-404d-89d3-9342c451c802
caps.latest.revision: "40"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 78460b9ee96ef8ba2646a53de9c036af029ed6bd
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="syssysfiles-transact-sql"></a>sys.sysfiles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque fichier de la base de données.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**fileid**|**smallint**|Numéro unique d'identification de fichier pour chaque base de données.|  
|**GroupID**|**smallint**|Numéro d'identification du groupe de fichiers.|  
|**taille**|**int**|Taille du fichier, en pages de 8 Ko.|  
|**MaxSize**|**int**|Taille maximale du fichier, en pages de 8 Ko.<br /><br /> 0 = Croissance nulle.<br /><br /> -1 = Le fichier peut croître tant que le disque n'est pas saturé.<br /><br /> 268435456 = Le fichier journal peut croître pour atteindre une taille maximale de 2 To.<br /><br /> Remarque : Les bases de données qui sont mis à niveau avec une taille de fichier journal illimitée signalera -1 pour la taille maximale du fichier journal.|  
|**croissance**|**int**|Taille de croissance de la base de données. Peut être le nombre de pages ou le pourcentage de la taille du fichier, en fonction de la valeur de **état**.<br /><br /> 0 = Croissance nulle.|  
|**status**|**int**|Bits d’état pour le **croissance** valeur en mégaoctets (Mo) ou kilo-octets (Ko).<br /><br /> 0x2 = Fichier disque.<br /><br /> 0x40 = Fichier journal.<br /><br /> 0x100000 = Croissance. Cette valeur est un pourcentage et non le nombre de pages.|  
|**performances**|**int**|Réservé.|  
|**nom**|**sysname**|Nom logique du fichier.|  
|**nom de fichier**|**nvarchar (260)**|Nom de l'unité physique. Inclut le chemin d'accès complet du fichier.|  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des Tables système pour les vues système &#40; Transact-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Affichages de compatibilité &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
