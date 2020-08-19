---
description: Extraction de lignes-Next Fetch (Native Client OLE DB Provider)
title: Position d’extraction suivante (fournisseur OLE DB Native Client) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
ms.assetid: 9ef74b3f-c9c0-492f-9b93-d65738a61abd
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c0f1fd4da86bdd0c7cbe0df0c832554566e93b88
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88448370"
---
# <a name="fetching-rows---next-fetch--native-client-ole-db-provider"></a>Extraction de lignes-Next Fetch (Native Client OLE DB Provider)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client effectue le suivi de la position d’extraction suivante afin qu’une séquence d’appels à la méthode **GetNextRows** (sans sauts, modifications de direction ou appels intermédiaires aux méthodes **FindNextRow**, **Seek**ou **RestartPosition** ) Lise l’ensemble de lignes entier sans ignorer ou répéter une ligne. La prochaine position de récupération (fetch) est modifiée en appelant **IRowset::GetNextRows**, **IRowset::RestartPosition**, **IRowsetIndex::Seek** ou **FindNextRow** avec une valeur *pBookmark* Null. L’appel de **FindNextRow** avec une valeur *pBookmark* non Null n’affecte pas la prochaine position de récupération.  
  
## <a name="see-also"></a>Voir aussi  
 [Récupération de lignes](../../relational-databases/native-client-ole-db-rowsets/fetching-rows.md)  
  
  
