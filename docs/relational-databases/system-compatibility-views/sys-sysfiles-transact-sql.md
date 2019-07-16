---
title: sys.sysfiles (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysfiles
- sys.sysfiles_TSQL
- sys.sysfiles
- sysfiles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysfiles system table
- sys.sysfiles compatibility view
ms.assetid: 3b47f38d-1cff-404d-89d3-9342c451c802
author: rothja
ms.author: jroth
ms.openlocfilehash: 2a3554e254be0623e36719fe76b2d811908a939d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68053467"
---
# <a name="syssysfiles-transact-sql"></a>sys.sysfiles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque fichier de la base de données.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**fileid**|**smallint**|Numéro unique d'identification de fichier pour chaque base de données.|  
|**groupid**|**smallint**|Numéro d'identification du groupe de fichiers.|  
|**size**|**int**|Taille du fichier, en pages de 8 Ko.|  
|**maxsize**|**Int**|Taille maximale du fichier, en pages de 8 Ko.<br /><br /> 0 = Croissance nulle.<br /><br /> -1 = Le fichier peut croître tant que le disque n'est pas saturé.<br /><br /> 268435456 = Le fichier journal peut croître pour atteindre une taille maximale de 2 To.<br /><br /> Remarque : Bases de données qui sont mis à niveau avec une taille de fichier journal illimitée signalera -1 pour la taille maximale du fichier journal.|  
|**growth**|**int**|Taille de croissance de la base de données. Peut être le nombre de pages ou le pourcentage de taille de fichier, en fonction de la valeur de **état**.<br /><br /> 0 = Croissance nulle.|  
|**status**|**Int**|Bits d’état pour le **croissance** valeur en mégaoctets (Mo) ou kilo-octets (Ko).<br /><br /> 0x2 = Fichier disque.<br /><br /> 0x40 = Fichier journal.<br /><br /> 0x100000 = Croissance. Cette valeur est un pourcentage et non le nombre de pages.|  
|**perf**|**Int**|Réservé.|  
|**name**|**sysname**|Nom logique du fichier.|  
|**filename**|**nvarchar(260)**|Nom de l'unité physique. Inclut le chemin d'accès complet du fichier.|  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des Tables système avec les vues système &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Affichages de compatibilité &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
