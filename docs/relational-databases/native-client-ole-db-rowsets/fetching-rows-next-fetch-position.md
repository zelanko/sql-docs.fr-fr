---
title: Prochaine Position d’extraction | Microsoft Docs
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 83fe35036c9249c4b07878a992069dad706c4cca
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67967438"
---
# <a name="fetching-rows---next-fetch-position"></a>Récupération de lignes - Prochaine position de récupération (fetch)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB fournisseur assure le suivi de la prochaine position d’extraction par conséquent, qui une séquence d’appels à la **GetNextRows** (méthode) (sans ignore, change de direction, ou des intervenants appelle à la  **FindNextRow**, **recherche**, ou **RestartPosition** méthodes) lit l’ensemble de lignes entier sans ignorer ou répéter n’importe quelle ligne. La prochaine position de récupération (fetch) est modifiée en appelant **IRowset::GetNextRows**, **IRowset::RestartPosition**, **IRowsetIndex::Seek** ou **FindNextRow** avec une valeur *pBookmark* Null. L’appel de **FindNextRow** avec une valeur *pBookmark* non Null n’affecte pas la prochaine position de récupération.  
  
## <a name="see-also"></a>Voir aussi  
 [Récupération de lignes](../../relational-databases/native-client-ole-db-rowsets/fetching-rows.md)  
  
  
