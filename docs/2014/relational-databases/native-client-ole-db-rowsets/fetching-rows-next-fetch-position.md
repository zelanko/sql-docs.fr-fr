---
title: Prochaine Position d’extraction | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
ms.assetid: 9ef74b3f-c9c0-492f-9b93-d65738a61abd
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1d6fa0247cafa0d0750f224e3b369965fd4e7989
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37423568"
---
# <a name="next-fetch-position"></a>Prochaine position d'extraction
  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB fournisseur assure le suivi de la prochaine position d’extraction par conséquent, qui une séquence d’appels à la **GetNextRows** (méthode) (sans ignore, change de direction, ou des intervenants appelle à la  **FindNextRow**, **recherche**, ou **RestartPosition** méthodes) lit l’ensemble de lignes entier sans ignorer ou répéter n’importe quelle ligne. La prochaine position d’extraction est modifiée en appelant **IRowset::GetNextRows**, **IRowset::RestartPosition**, ou **IRowsetIndex::Seek**, ou en appelant **FindNextRow** avec une valeur null *pBookmark* valeur. Appel **FindNextRow** avec une valeur non null *pBookmark* valeur n’affecte pas la prochaine position d’extraction.  
  
## <a name="see-also"></a>Voir aussi  
 [Récupération de lignes](fetching-rows.md)  
  
  
