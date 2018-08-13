---
title: Sys.sysobjects (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
caps.latest.revision: 41
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 5e291474c080374a0b0e92d6500610f16f73c818
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39564913"
---
# <a name="syssysobjects-transact-sql"></a>sys.sysobjects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Contient une ligne pour chaque objet créé dans une base de données, tel qu'une contrainte, une valeur par défaut, un journal, une règle et une procédure stockée.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|NAME|**sysname**|Nom de l'objet|  
|id|**Int**|Numéro d’identification|  
|xtype|**char(2)**|Type d'objet. Il peut s'agir de l'un des types d'objets suivants :<br /><br /> AF = Fonction d'agrégation (CLR)<br /><br /> C = contrainte CHECK<br /><br /> D = Valeur par défaut ou contrainte DEFAULT<br /><br /> F = Contrainte FOREIGN KEY<br /><br /> L = Journal<br /><br /> FN = Fonction scalaire<br /><br /> FS = Fonction scalaire d'assembly (CLR)<br /><br /> FT = Fonction table d'assembly (CLR)<br /><br /> IF = Fonction de table inline<br /><br /> IT = table interne<br /><br /> P = Procédure stockée<br /><br /> PC = procédure stockée d’Assembly (CLR)<br /><br /> PK = Contrainte PRIMARY KEY (de type K)<br /><br /> RF = Procédure stockée à filtre de réplication<br /><br /> S = Table système<br /><br /> SN = Synonyme<br /><br /> SQ = File d'attente du service<br /><br /> TA = Déclencheur d'assembly DML (CLR)<br /><br /> TF = Fonction de table<br /><br /> TR = déclencheur SQL DML<br /><br /> TT = Type de table<br /><br /> U = Table utilisateur<br /><br /> UQ = Contrainte UNIQUE (de type K)<br /><br /> V = Vue<br /><br /> X = Procédure stockée étendue|  
|uid|**smallint**|ID de schéma du propriétaire de l'objet. Pour les bases de données mises à niveau à partir d'une version antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l'ID de schéma correspond à l'ID d'utilisateur du propriétaire. Déborde ou retourne la valeur NULL si le nombre d'utilisateurs et de rôles dépasse 32 767.<br /><br /> **\*\* Important \* \* ** si vous utilisez une des opérations suivantes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instructions DDL, vous devez utiliser le [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) vue au lieu de sys.sysobjects de catalogue.<br /><br /> CRÉER &AMP;#124; ALTER &AMP;#124; DROP USER<br /><br /> CRÉER &AMP;#124; ALTER &AMP;#124; DROP ROLE<br /><br /> CRÉER &AMP;#124; ALTER &AMP;#124; DROP APPLICATION ROLE<br /><br /> CREATE SCHEMA<br /><br /> ALTER AUTHORIZATION ON OBJECT|  
|info|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|status|**Int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|base_schema_ver|**Int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|replinfo|**Int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|parent_obj|**Int**|Numéro d'identification de l'objet parent. Par exemple, l'ID de table s'il s'agit d'un déclencheur ou d'une contrainte.|  
|crdate|**datetime**|Date de création de l'objet.|  
|ftcatid|**smallint**|Identificateur du catalogue de texte intégral pour toutes les tables utilisateur enregistrées pour l'indexation de texte intégral et 0 pour toutes les tables utilisateur non enregistrées.|  
|schema_ver|**Int**|Numéro de version incrémenté à chaque modification du schéma d'une table. Retourne toujours 0.|  
|stats_schema_ver|**Int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|Type|**char(2)**|Type d'objet. Il peut s'agir de l'une des valeurs suivantes :<br /><br /> AF = Fonction d'agrégation (CLR)<br /><br /> C = contrainte CHECK<br /><br /> D = Valeur par défaut ou contrainte DEFAULT<br /><br /> F = Contrainte FOREIGN KEY<br /><br /> FN = Fonction scalaire<br /><br /> FS = Fonction scalaire d'assembly (CLR)<br /><br /> FT = Fonction table d'assembly (CLR)IF = Fonction de table inline<br /><br /> IT = Table interne<br /><br /> K = Contrainte PRIMARY KEY ou UNIQUE<br /><br /> L = Journal<br /><br /> P = Procédure stockée<br /><br /> PC = procédure stockée d’Assembly (CLR)<br /><br /> R = Règle<br /><br /> RF = Procédure stockée à filtre de réplication<br /><br /> S = Table système<br /><br /> SN = Synonyme<br /><br /> SQ = File d'attente du service<br /><br /> TA = Déclencheur d'assembly DML (CLR)<br /><br /> TF = Fonction de table<br /><br /> TR = déclencheur SQL DML<br /><br /> TT = Type de table<br /><br /> U = Table utilisateur<br /><br /> V = Vue<br /><br /> X = Procédure stockée étendue|  
|userstat|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|sysstat|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|indexdel|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|refdate|**datetime**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|version|**Int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|deltrig|**Int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|instrig|**Int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|updtrig|**Int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|seltrig|**Int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|catégorie|**Int**|Utilisé pour la publication, les contraintes et l'identité.|  
|cache|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des Tables système avec les vues système &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Affichages de compatibilité &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
