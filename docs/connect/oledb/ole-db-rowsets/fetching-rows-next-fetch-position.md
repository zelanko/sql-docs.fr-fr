---
title: Prochaine position de récupération (fetch) (pilote OLE DB) | Microsoft Docs
description: OLE DB Driver pour SQL Server effectue le suivi de la position d’extraction suivante afin qu’une séquence d’appels à la méthode GetNextRows lise l’ensemble de lignes entier.
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0ba713e9da40255d992e7cccf8c8430a205cadf4
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88861580"
---
# <a name="fetching-rows---next-fetch-position-ole-db-driver"></a>Récupération de lignes - Prochaine position de récupération (fetch) (pilote OLE DB)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Le pilote OLE DB pour SQL Server effectue le suivi de la prochaine position de récupération (fetch) afin qu’une séquence d’appels à la méthode **GetNextRows** (sans sauts, modifications de direction ou appels intermédiaires aux méthodes **FindNextRow**, **Seek** ou **RestartPosition**) puisse lire l’intégralité de l’ensemble de lignes sans ignorer ou répéter la moindre ligne. La prochaine position de récupération (fetch) est modifiée en appelant **IRowset::GetNextRows**, **IRowset::RestartPosition**, **IRowsetIndex::Seek** ou **FindNextRow** avec une valeur *pBookmark* Null. L’appel de **FindNextRow** avec une valeur *pBookmark* non Null n’affecte pas la prochaine position de récupération.  
  
## <a name="see-also"></a>Voir aussi  
 [Récupération de lignes](../../oledb/ole-db-rowsets/fetching-rows.md)  
  
  
