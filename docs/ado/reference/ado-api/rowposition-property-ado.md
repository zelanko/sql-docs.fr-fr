---
title: RowPosition, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a333a2be2728f3c0b412246b0a793dae64096ae5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67931223"
---
# <a name="rowposition-property-ado"></a>RowPosition, propriété (ADO)
Obtient ou définit un objet **RowPosition** OLE DB à partir de/sur un objet **ADORecordsetConstruction** . Quand vous utilisez **put_RowPosition** pour définir l’objet **RowPosition** , l’objet **Recordset** résultant utilise l’objet **RowPosition** pour déterminer la ligne actuelle.  
  
 En lecture/écriture.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT get_RowPosition([out, retval] IUnknown** ppRowPos);  
HRESULT put_RowPosition([in] IUnknown* pRowPos);  
```  
  
## <a name="parameters"></a>Paramètres  
 *ppRowPos*  
 Pointeur vers un objet OLE DB **RowPosition** .  
  
 *PRowPos*  
 Objet **RowPosition** OLE DB.  
  
## <a name="return-values"></a>Valeurs de retour  
 Cette méthode de propriété retourne les valeurs HRESULT standard, y compris S_OK et E_FAIL.  
  
## <a name="remarks"></a>Notes  
 Quand cette propriété est définie, si l’objet **rowset** de l’objet **RowPosition** est différent de l’objet **rowset** sur l’objet **Recordset** , le précédent remplace ce dernier. Le même comportement s’applique également au **chapitre** actuel du **RowPosition** .  
  
## <a name="applies-to"></a>S'applique à  
 [ADORecordsetConstruction, interface](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)
