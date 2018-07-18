---
title: Prochaine Position d’extraction | Documents Microsoft
description: Lignes de l’extraction - prochaine position d’extraction
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 46e6e3b9898d6c1adbe4df4bdc2b33444b623df9
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/16/2018
ms.locfileid: "35690112"
---
# <a name="fetching-rows---next-fetch-position"></a>Lignes de l’extraction - prochaine Position d’extraction
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Le pilote OLE DB pour SQL Server assure le suivi de la prochaine position d’extraction donc qui une séquence d’appels à la **GetNextRows** (méthode) (sans ignore, change de direction, ou des intervenants appelle à la **FindNextRow** **Recherche**, ou **RestartPosition** méthodes) lit l’ensemble de lignes sans ignorer ou répéter n’importe quelle ligne. La prochaine position d’extraction est modifiée en appelant **IRowset::GetNextRows**, **IRowset::RestartPosition**, ou **IRowsetIndex::Seek**, ou en appelant **FindNextRow** avec une valeur null *pBookmark* valeur. Appel de **FindNextRow** avec une valeur non null *pBookmark* valeur n’affecte pas la prochaine position d’extraction.  
  
## <a name="see-also"></a>Voir aussi  
 [Récupération de lignes](../../oledb/ole-db-rowsets/fetching-rows.md)  
  
  
