---
title: IDBProperties (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 2e5a4fd8-5164-495a-9986-3477aef8d8a5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3b6dada26e15fc83d890b270ad553eb051bb08fa
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62692180"
---
# <a name="idbproperties-ole-db"></a>IDBProperties (OLE DB)
  La spécification standard OLE DB permet aux fournisseurs de spécifier VT_EMPTY pour `DBPROPINFO::vValues`. Toutefois, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB Native Client retourne toujours VT_EMPTY lorsque vous appelez `IDBProperties::GetPropertyInfo` avec `DBPROPSET_ROWSETALL` pour récupérer les propriétés de l’ensemble de lignes.  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  
