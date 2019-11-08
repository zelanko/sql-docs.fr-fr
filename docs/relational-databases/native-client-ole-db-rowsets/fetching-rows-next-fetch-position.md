---
title: Position d’extraction suivante | Microsoft Docs
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
ms.openlocfilehash: 632622f985e363d87cd820729afb6f69826c903b
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73788987"
---
# <a name="fetching-rows---next-fetch-position"></a>Récupération de lignes - Prochaine position de récupération (fetch)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le fournisseur d’OLE DB Native Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] effectue le suivi de la position d’extraction suivante afin qu’une séquence d’appels à la méthode **GetNextRows** (sans ignorer, modifier la direction ou des appels intermédiaires à la méthode **FindNextRow**, **Seek** **ou Méthodes RestartPosition** ) lit la totalité de l’ensemble de lignes sans ignorer ou répéter une ligne. La prochaine position de récupération (fetch) est modifiée en appelant **IRowset::GetNextRows**, **IRowset::RestartPosition**, **IRowsetIndex::Seek** ou **FindNextRow** avec une valeur *pBookmark* Null. L’appel de **FindNextRow** avec une valeur *pBookmark* non Null n’affecte pas la prochaine position de récupération.  
  
## <a name="see-also"></a>Voir aussi  
 [Récupération de lignes](../../relational-databases/native-client-ole-db-rowsets/fetching-rows.md)  
  
  
