---
title: "Chapitre, propriété (ADO) | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- ADORecordsetConstruction::Chapter
- ADORecordsetConstruction::put_Chapter
- ADORecordsetConstruction::get_Chapter
helpviewer_keywords: Chapter property [ADO]
ms.assetid: 8aa90cb0-f588-4141-9dc9-3b22918394ee
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 026fc2e66f9dca3243791f3cd2c1e984f13087d8
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="chapter-property-ado"></a>Chapitre, propriété (ADO)
Obtient ou définit un OLE DB **chapitre** objet à partir de/sur un [ADORecordsetConstruction Interface](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md) objet. Lorsque vous utilisez **put_Chapter** pour définir le **chapitre** de l’objet, un sous-ensemble de lignes est transformé en ADO [objet Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet. Cela définit le chapitre actif de la **ensemble de lignes**objet. Cette propriété est en lecture/écriture.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT get_Chapter([out, retval] long* plChapter);  
HRESULT put_Chapter([in] long lChapter);  
```  
  
## <a name="parameters"></a>Paramètres  
 *plChapter*  
 Pointeur vers le descripteur d’un chapitre.  
  
 *LChapter*  
 Descripteur d’un chapitre.  
  
## <a name="return-values"></a>Valeurs de retour  
 Cette méthode de propriété renvoie les valeurs HRESULT standards, notamment S_OK et E_FAIL.  
  
## <a name="applies-to"></a>S'applique à  
 [ADORecordsetConstruction, interface](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)
