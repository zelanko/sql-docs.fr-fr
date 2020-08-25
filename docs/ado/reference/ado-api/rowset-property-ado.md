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
ms.openlocfilehash: f966261864cb7717b31e4851062228c3e6d63e92
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777618"
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
 [ADORecordsetConstruction, interface](./adorecordsetconstruction-interface.md)