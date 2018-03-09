---
title: sys.sysobjects (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sysobjects_TSQL
- sysobjects
- sysobjects_TSQL
- sys.sysobjects
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysobjects compatibility view
- sysobjects system table
ms.assetid: 44fdc387-67b0-4139-8bf5-ed26cf640cd1
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 58b3ba692fd946c15e3f00a7d1179f10df5d0b37
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="syssysobjects-transact-sql"></a>sys.sysobjects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Contient une ligne pour chaque objet créé dans une base de données, tel qu'une contrainte, une valeur par défaut, un journal, une règle et une procédure stockée.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|name|**sysname**|Nom de l'objet|  
|id|**int**|Numéro d’identification|  
|xtype|**char(2)**|Type d'objet. Il peut s'agir de l'un des types d'objets suivants :<br /><br /> AF = Fonction d'agrégation (CLR)<br /><br /> C = contrainte CHECK<br /><br /> D = Valeur par défaut ou contrainte DEFAULT<br /><br /> F = Contrainte FOREIGN KEY<br /><br /> L = Journal<br /><br /> FN = Fonction scalaire<br /><br /> FS = Fonction scalaire d'assembly (CLR)<br /><br /> FT = Fonction table d'assembly (CLR)<br /><br /> IF = Fonction de table inline<br /><br /> IT = table interne<br /><br /> P = Procédure stockée<br /><br /> PC = procédure stockée d’Assembly (CLR)<br /><br /> PK = Contrainte PRIMARY KEY (de type K)<br /><br /> RF = Procédure stockée à filtre de réplication<br /><br /> S = Table système<br /><br /> SN = Synonyme<br /><br /> SQ = File d'attente du service<br /><br /> TA = Déclencheur d'assembly DML (CLR)<br /><br /> TF = Fonction de table<br /><br /> TR = déclencheur DML SQL<br /><br /> TT = Type de table<br /><br /> U = Table utilisateur<br /><br /> UQ = Contrainte UNIQUE (de type K)<br /><br /> V = Vue<br /><br /> X = Procédure stockée étendue|  
|uid|**smallint**|ID de schéma du propriétaire de l'objet. Pour les bases de données mises à niveau à partir d'une version antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l'ID de schéma correspond à l'ID d'utilisateur du propriétaire. Déborde ou retourne la valeur NULL si le nombre d'utilisateurs et de rôles dépasse 32 767.<br /><br /> **\*\*Important \* \***  si vous utilisez une des opérations suivantes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instructions DDL, vous devez utiliser le [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) affichage au lieu de sys.sysobjects catalogue.<br /><br /> CRÉER &#124; ALTER &#124; SUPPRIMEZ L’UTILISATEUR<br /><br /> CRÉER &#124; ALTER &#124; SUPPRIMER LE RÔLE<br /><br /> CRÉER &#124; ALTER &#124; SUPPRIMER LE RÔLE D’APPLICATION<br /><br /> CREATE SCHEMA<br /><br /> ALTER AUTHORIZATION ON OBJECT|  
|info|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|status|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|base_schema_ver|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|replinfo|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|parent_obj|**int**|Numéro d'identification de l'objet parent. Par exemple, l'ID de table s'il s'agit d'un déclencheur ou d'une contrainte.|  
|crdate|**datetime**|Date de création de l'objet.|  
|ftcatid|**smallint**|Identificateur du catalogue de texte intégral pour toutes les tables utilisateur enregistrées pour l'indexation de texte intégral et 0 pour toutes les tables utilisateur non enregistrées.|  
|schema_ver|**int**|Numéro de version incrémenté à chaque modification du schéma d'une table. Retourne toujours 0.|  
|stats_schema_ver|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|type|**char(2)**|Type d'objet. Il peut s'agir de l'une des valeurs suivantes :<br /><br /> AF = Fonction d'agrégation (CLR)<br /><br /> C = contrainte CHECK<br /><br /> D = Valeur par défaut ou contrainte DEFAULT<br /><br /> F = Contrainte FOREIGN KEY<br /><br /> FN = Fonction scalaire<br /><br /> FS = Fonction scalaire d'assembly (CLR)<br /><br /> FT = Fonction table d'assembly (CLR)IF = Fonction de table inline<br /><br /> IT = Table interne<br /><br /> K = Contrainte PRIMARY KEY ou UNIQUE<br /><br /> L = Journal<br /><br /> P = Procédure stockée<br /><br /> PC = procédure stockée d’Assembly (CLR)<br /><br /> R = Règle<br /><br /> RF = Procédure stockée à filtre de réplication<br /><br /> S = Table système<br /><br /> SN = Synonyme<br /><br /> SQ = File d'attente du service<br /><br /> TA = Déclencheur d'assembly DML (CLR)<br /><br /> TF = Fonction de table<br /><br /> TR = déclencheur DML SQL<br /><br /> TT = Type de table<br /><br /> U = Table utilisateur<br /><br /> V = Vue<br /><br /> X = Procédure stockée étendue|  
|userstat|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|sysstat|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|indexdel|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|refdate|**datetime**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|version|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|deltrig|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|instrig|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|updtrig|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|seltrig|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|catégorie|**int**|Utilisé pour la publication, les contraintes et l'identité.|  
|cache|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des Tables système pour les vues système &#40; Transact-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Affichages de compatibilité &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
