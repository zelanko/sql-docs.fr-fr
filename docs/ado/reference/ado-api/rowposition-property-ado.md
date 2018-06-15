---
title: RowPosition, propriété (ADO) | Documents Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
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
manager: craigg
ms.openlocfilehash: 0b852ff5fab54e11f3fd39c2ca92266c95587987
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35281338"
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
 [ADORecordsetConstruction, interface](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)
