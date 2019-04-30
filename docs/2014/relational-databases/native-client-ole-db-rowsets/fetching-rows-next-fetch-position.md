---
title: Prochaine Position d’extraction | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: 2c47f1a8692cf7d2e3fb4f00c64770b3b0c69e5a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63183639"
---
# <a name="next-fetch-position"></a>Prochaine position d'extraction
  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB fournisseur assure le suivi de la prochaine position d’extraction par conséquent, qui une séquence d’appels à la **GetNextRows** (méthode) (sans ignore, change de direction, ou des intervenants appelle à la  **FindNextRow**, **recherche**, ou **RestartPosition** méthodes) lit l’ensemble de lignes entier sans ignorer ou répéter n’importe quelle ligne. La prochaine position de récupération (fetch) est modifiée en appelant **IRowset::GetNextRows**, **IRowset::RestartPosition**, **IRowsetIndex::Seek** ou **FindNextRow** avec une valeur *pBookmark* Null. L’appel de **FindNextRow** avec une valeur *pBookmark* non Null n’affecte pas la prochaine position de récupération.  
  
## <a name="see-also"></a>Voir aussi  
 [Récupération de lignes](fetching-rows.md)  
  
  
