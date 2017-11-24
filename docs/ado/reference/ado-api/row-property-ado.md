---
title: "Row, propriété (ADO) | Documents Microsoft"
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
- ADORecordConstruction::PutRow
- ADORecordConstruction::GetRow
- ADORecordConstruction::get_Row
- ADORecordConstruction::Row
- ADORecordConstruction::put_Row
helpviewer_keywords: Row property [ADO]
ms.assetid: 21019d89-2dd1-4a26-ac6f-384b81d66949
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 85843aa10143bcb2ff1ec86ea85d9237bb063762
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="row-property-ado"></a>Propriété de ligne (ADO)
Obtient ou définit un OLE DB **ligne** objet à partir d’ou sur un [ADORecordConstruction Interface](../../../ado/reference/ado-api/adorecordconstruction-interface.md) objet. Lorsque vous utilisez **put Row** pour définir un **ligne** de l’objet, une ligne est transformée en ADO **enregistrement** objet.  
  
## <a name="readwritesyntax"></a>En lecture/écriture. Syntaxe  
  
```  
HRESULT get_Row([out, retval] IUnknown** ppRow);  
HRESULT put_Row([in] IUnknown* pRow);  
```  
  
## <a name="parameters"></a>Paramètres  
 *ppRow*  
 Pointeur vers un OLE DB **ligne** objet.  
  
 *PRow*  
 OLE DB **ligne** objet.  
  
## <a name="return-values"></a>Valeurs de retour  
 Cette méthode de propriété renvoie les valeurs HRESULT standards, notamment S_OK et E_FAIL.  
  
## <a name="applies-to"></a>S'applique à  
 [ADORecordConstruction, interface](../../../ado/reference/ado-api/adorecordconstruction-interface.md)
