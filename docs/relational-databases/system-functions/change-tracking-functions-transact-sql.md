---
title: Fonctions Change Tracking (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/08/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- functions [SQL Server], change tracking
- change tracking [SQL Server], functions
ms.assetid: 04eb53c4-8b69-414e-9696-185d227fea35
author: rothja
ms.author: jroth
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8dc2dceec177922369fe2bbef74bafeeef2ca27c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68042960"
---
# <a name="change-tracking-functions-transact-sql"></a>Fonctions de suivi des modifications (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Les enregistrements de suivi des modifications insèrent, mettent à jour et suppriment les activités appliquées aux tables faisant l'objet d'un suivi, en fournissant les détails des modifications dans un format relationnel simple à utiliser. Les fonctions suivantes retournent des informations sur les modifications.  
  
|Fonction|Description|  
|--------------|-----------------|  
|[CHANGETABLE (MODIFICATIONS)](../../relational-databases/system-functions/changetable-transact-sql.md)|Retourne les informations de suivi de toutes les modifications apportées à une table depuis une version spécifiée.|  
|[CHANGETABLE (VERSION)](../../relational-databases/system-functions/changetable-transact-sql.md)|Retourne les informations de suivi des modifications les plus récentes pour une ligne spécifiée.|  
|[CHANGE_TRACKING_MIN_VALID_VERSION ()](../../relational-databases/system-functions/change-tracking-min-valid-version-transact-sql.md)|Retourne la version minimale qui peut être utilisée pour obtenir les informations de suivi des modifications à partir de la table spécifiée lorsque vous utilisez la fonction [CHANGETABLE](../../relational-databases/system-functions/changetable-transact-sql.md) .|  
|[CHANGE_TRACKING_CURRENT_VERSION](../../relational-databases/system-functions/change-tracking-current-version-transact-sql.md)|Obtient une version associée à la dernière transaction validée. Vous pouvez utiliser cette version lors de la prochaine énumération des modifications à l’aide de CHANGETABLE.|  
|[CHANGE_TRACKING_IS_COLUMN_IN_MASK](../../relational-databases/system-functions/change-tracking-is-column-in-mask-transact-sql.md)|Interprète la valeur SYS_CHANGE_COLUMNS retournée par la fonction CHANGETABLE (CHANGEs...).|  
|[WITH CHANGE_TRACKING_CONTEXT](../../relational-databases/system-functions/with-change-tracking-context-transact-sql.md)|Active la spécification d'un contexte de modification, tel qu'un ID d'appelant, lorsqu'une application modifie des données.|  
  
## <a name="see-also"></a>Voir aussi  
 [Suivi des modifications de données &#40;SQL Server&#41;](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
  
