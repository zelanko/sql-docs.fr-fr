---
title: Prochaine Position d’extraction | Documents Microsoft
description: Lignes de l’extraction - prochaine position d’extraction
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
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
ms.openlocfilehash: 9613ea77a5eaac5136c6ca744a7201621fa3b876
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="fetching-rows---next-fetch-position"></a>Lignes de l’extraction - prochaine Position d’extraction
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le pilote OLE DB pour SQL Server assure le suivi de la prochaine position d’extraction donc qui une séquence d’appels à la **GetNextRows** (méthode) (sans ignore, change de direction, ou des intervenants appelle à la **FindNextRow** **Recherche**, ou **RestartPosition** méthodes) lit l’ensemble de lignes sans ignorer ou répéter n’importe quelle ligne. La prochaine position d’extraction est modifiée en appelant **IRowset::GetNextRows**, **IRowset::RestartPosition**, ou **IRowsetIndex::Seek**, ou en appelant **FindNextRow** avec une valeur null *pBookmark* valeur. Appel de **FindNextRow** avec une valeur non null *pBookmark* valeur n’affecte pas la prochaine position d’extraction.  
  
## <a name="see-also"></a>Voir aussi  
 [Extraction de lignes](../../oledb/ole-db-rowsets/fetching-rows.md)  
  
  
