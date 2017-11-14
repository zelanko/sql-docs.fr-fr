---
title: "RowPosition, propriété (ADO) | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- ADORecordConstruction::put_RowPosition
- ADORecordConstruction::PutRowPosition
- ADORecordConstruction::GetRowPosition
- ADORecordConstruction::RowPosition
- ADORecordConstruction::get_RowPosition
helpviewer_keywords:
- RowPosition property [ADO]
ms.assetid: 9d068fed-39bf-4842-afc3-686a2af2145d
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 00206531bf8154d509f79e7229b1a2da319fa5fa
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="rowposition-property-ado"></a>RowPosition, propriété (ADO)
Obtient ou définit un OLE DB **RowPosition** objet à partir de/sur un **ADORecordsetConstruction** objet. Lorsque vous utilisez **put_RowPosition** pour définir le **RowPosition** objet, résultant **Recordset** object utilise le **RowPosition** à l’objet déterminer la ligne actuelle.  
  
 En lecture/écriture.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT get_RowPosition([out, retval] IUnknown** ppRowPos);  
HRESULT put_RowPosition([in] IUnknown* pRowPos);  
```  
  
## <a name="parameters"></a>Paramètres  
 *ppRowPos*  
 Pointeur vers un OLE DB **RowPosition** objet.  
  
 *PRowPos*  
 OLE DB **RowPosition** objet.  
  
## <a name="return-values"></a>Valeurs de retour  
 Cette méthode de propriété renvoie les valeurs HRESULT standards, notamment S_OK et E_FAIL.  
  
## <a name="remarks"></a>Notes  
 Lorsque cette propriété est définie, si le **ensemble de lignes** de l’objet sur le **RowPosition** objet est différent de la **ensemble de lignes** sur l’objet le **Recordset**de l’objet, le premier remplace ce dernier. Le même comportement s’applique à actuel **chapitre** de la **RowPosition** également.  
  
## <a name="applies-to"></a>S'applique à  
 [Interface ADORecordsetConstruction](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)

