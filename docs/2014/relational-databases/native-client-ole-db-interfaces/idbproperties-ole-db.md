---
title: IDBProperties (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 2e5a4fd8-5164-495a-9986-3477aef8d8a5
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7598f1c865395f2a43eba8f67c86a68bd46d586b
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82707363"
---
# <a name="idbproperties-ole-db"></a>IDBProperties (OLE DB)
  La spécification standard OLE DB permet aux fournisseurs de spécifier VT_EMPTY pour `DBPROPINFO::vValues`. Toutefois, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB retourne toujours VT_EMPTY quand vous appelez `IDBProperties::GetPropertyInfo` avec `DBPROPSET_ROWSETALL` pour récupérer les propriétés de l’ensemble de lignes.  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  
