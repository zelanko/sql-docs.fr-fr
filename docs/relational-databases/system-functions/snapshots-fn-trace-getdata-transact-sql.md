---
description: snapshots.fn_trace_getdata (Transact-SQL)
title: captures instantanées. fn_trace_getdata (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- snapshots.fn_trace_getdata
dev_langs:
- TSQL
helpviewer_keywords:
- snapshots.fn_trace_getdata function
ms.assetid: ac28ef48-f4f4-4bf2-ba22-d44e1be88172
author: rothja
ms.author: jroth
ms.openlocfilehash: f022a27c8a8e47cd12994d0d03ddb5af9a2f920c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88464773"
---
# <a name="snapshotsfn_trace_getdata-transact-sql"></a>snapshots.fn_trace_getdata (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Cette fonction retourne tous les événements capturés pour la trace spécifiée.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
snapshots.fn_trace_gettable ( trace_info_id, start_time, end_time )  
```  
  
## <a name="arguments"></a>Arguments  
 *trace_info_id*  
 Identificateur unique de la clé primaire dans la table de captures instantanées. trace_info de la base de données de l’entrepôt de données de gestion. *trace_info_id* est de **type int**.  
  
 *heure-début*  
 Heure de démarrage de la trace. *start_time* est de **type DateTime**.  
  
 *heure-fin*  
 Heure de fin de la trace. *end_time* est de **type DateTime**.  
  
## <a name="table-returned"></a>Table retournée  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|\<All trace columns>|\<Varies>|Données de trace de la table snapshots.trace_data de la base de données de l'entrepôt de données de gestion.<br /><br /> Pour obtenir la liste des colonnes pour la trace spécifiée, utilisez la requête suivante :<br /><br /> `SELECT * FROM sys.trace_columns`<br /><br /> **Remarque :** Les colonnes retournées par la fonction captures instantanées. fn_trace_gettable correspondent aux valeurs de la colonne nom de la vue système sys. trace_columns. La seule différence est que la colonne GroupID n'est pas retournée par la fonction.|  
  
## <a name="permissions"></a>Autorisations  
 Requiert l'autorisation SELECT pour mdw_reader.  
  
## <a name="see-also"></a>Voir aussi  
 [Collecte de données](../../relational-databases/data-collection/data-collection.md)  
  
  
