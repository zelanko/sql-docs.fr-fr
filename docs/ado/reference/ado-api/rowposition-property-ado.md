---
description: RowPosition, propriété (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 330c090c9e4eedd6a083d58a55243d470514541f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442461"
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
