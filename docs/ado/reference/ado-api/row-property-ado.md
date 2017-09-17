---
title: "Row, propriété (ADO) | Documents Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- ADORecordConstruction::PutRow
- ADORecordConstruction::GetRow
- ADORecordConstruction::get_Row
- ADORecordConstruction::Row
- ADORecordConstruction::put_Row
helpviewer_keywords:
- Row property [ADO]
ms.assetid: 21019d89-2dd1-4a26-ac6f-384b81d66949
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 19b935d43739d1a1ce19f414cae12b00c311b261
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

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
 [Interface ADORecordConstruction](../../../ado/reference/ado-api/adorecordconstruction-interface.md)
