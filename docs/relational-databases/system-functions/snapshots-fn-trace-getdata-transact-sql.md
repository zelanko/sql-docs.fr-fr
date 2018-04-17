---
title: snapshots.fn_trace_getdata remplacé (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- snapshots.fn_trace_getdata
dev_langs:
- TSQL
helpviewer_keywords:
- snapshots.fn_trace_getdata function
ms.assetid: ac28ef48-f4f4-4bf2-ba22-d44e1be88172
caps.latest.revision: 19
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 63e524e8a3e14abdb2ca96d4378391e3d25746a0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="snapshotsfntracegetdata-transact-sql"></a>snapshots.fn_trace_getdata (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cette fonction retourne tous les événements capturés pour la trace spécifiée.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
snapshots.fn_trace_gettable ( trace_info_id, start_time, end_time )  
```  
  
## <a name="arguments"></a>Arguments  
 *trace_info_id*  
 L’identificateur unique pour la clé primaire dans la table snapshots.trace_info dans les données de gestion de l’entrepôt de base de données. *trace_info_id* est **int**.  
  
 *start_time*  
 Heure de démarrage de la trace. *start_time* est **datetime**.  
  
 *end_time*  
 Heure de fin de la trace. *end_time* est **datetime**.  
  
## <a name="table-returned"></a>Table retournée  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|\<Toutes les colonnes de trace >|\<Varie >|Données de trace de la table snapshots.trace_data de la base de données de l'entrepôt de données de gestion.<br /><br /> Pour obtenir la liste des colonnes pour la trace spécifiée, utilisez la requête suivante :<br /><br /> `SELECT * FROM sys.trace_columns`<br /><br /> **Remarque :** les colonnes sont retournées par la fonction snapshots.fn_trace_gettable correspondent aux valeurs dans la colonne name dans la vue système sys.trace_columns. La seule différence est que la colonne GroupID n'est pas retournée par la fonction.|  
  
## <a name="permissions"></a>Autorisations  
 Requiert l'autorisation SELECT pour mdw_reader.  
  
## <a name="see-also"></a>Voir aussi  
 [Collecte de données](../../relational-databases/data-collection/data-collection.md)  
  
  
