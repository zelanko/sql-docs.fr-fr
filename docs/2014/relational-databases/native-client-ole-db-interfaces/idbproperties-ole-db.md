---
title: IDBProperties (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 2e5a4fd8-5164-495a-9986-3477aef8d8a5
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 71999899b70c8eab76e26dba22f09884618277d2
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37413607"
---
# <a name="idbproperties-ole-db"></a>IDBProperties (OLE DB)
  La spécification standard OLE DB permet aux fournisseurs de spécifier VT_EMPTY pour `DBPROPINFO::vValues`. Toutefois, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB Native Client retourne toujours VT_EMPTY lorsque vous appelez `IDBProperties::GetPropertyInfo` avec `DBPROPSET_ROWSETALL` pour récupérer les propriétés de l’ensemble de lignes.  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  
