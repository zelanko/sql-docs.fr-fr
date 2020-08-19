---
description: Rowset, propriété (ADO)
title: Rowset, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADORecordsetConstruction::PutRowset
- ADORecordsetConstruction::GetRowset
- ADORecordsetConstruction::Rowset
- ADORecordsetConstruction::put_Rowset
- ADORecordsetConstruction::get_Rowset
helpviewer_keywords:
- Rowset property [ADO]
ms.assetid: 7d359294-4ff2-47e0-8111-0c221b24d80e
author: rothja
ms.author: jroth
ms.openlocfilehash: 8f6342de5be5b2c6ba6e1bf58408cfabc6e31088
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442231"
---
# <a name="rowset-property-ado"></a>Rowset, propriété (ADO)
Obtient ou définit un objet d' **ensemble de lignes** OLE DB à partir de/sur un objet **ADORecordsetConstruction** . Lorsque vous utilisez put_Rowset, l’ensemble de lignes est converti en objet **Recordset** ADO.  
  
 En lecture/écriture.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT get_Rowset([out, retval] IUnknown** ppRowset);  
HRESULT put_Rowset([in] IUnknown* pRowset);  
```  
  
## <a name="parameters"></a>Paramètres  
 *ppRowset*  
 Pointeur vers un objet d' **ensemble de lignes** OLE DB.  
  
 *PRowset*  
 Objet d' **ensemble de lignes** OLE DB.  
  
## <a name="return-values"></a>Valeurs de retour  
 Cette méthode de propriété retourne les valeurs HRESULT standard, y compris S_OK et E_FAIL.  
  
## <a name="applies-to"></a>S'applique à  
 [ADORecordsetConstruction, interface](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)
