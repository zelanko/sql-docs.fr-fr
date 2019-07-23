---
title: Position d’extraction suivante | Microsoft Docs
description: Récupération de lignes - Prochaine position de récupération (fetch)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 2ea743770323505c611210c0bb3acd0e93c719cd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67994192"
---
# <a name="fetching-rows---next-fetch-position"></a>Récupération de lignes - Prochaine position de récupération (fetch)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Le pilote OLE DB pour SQL Server effectue le suivi de la prochaine position de récupération (fetch) afin qu’une séquence d’appels à la méthode **GetNextRows** (sans sauts, modifications de direction ou appels intermédiaires aux méthodes **FindNextRow**, **Seek** ou **RestartPosition**) puisse lire l’intégralité de l’ensemble de lignes sans ignorer ou répéter la moindre ligne. La prochaine position de récupération (fetch) est modifiée en appelant **IRowset::GetNextRows**, **IRowset::RestartPosition**, **IRowsetIndex::Seek** ou **FindNextRow** avec une valeur *pBookmark* Null. L’appel de **FindNextRow** avec une valeur *pBookmark* non Null n’affecte pas la prochaine position de récupération.  
  
## <a name="see-also"></a>Voir aussi  
 [Récupération de lignes](../../oledb/ole-db-rowsets/fetching-rows.md)  
  
  
