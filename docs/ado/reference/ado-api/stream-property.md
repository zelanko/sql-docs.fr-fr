---
title: Stream propriété | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADOStreamConstruction::GetStream
- ADOStreamConstruction::PutStream
- ADOStreamConstruction::put_Stream
- ADOStreamConstruction::Stream
- ADOStreamConstruction::get_Stream
helpviewer_keywords:
- Stream property
ms.assetid: 4a44f9f6-0265-4c00-8def-d85b6af923b1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ddeaadb1f25c3ea50e59c20d48f14e31831f2639
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47822012"
---
# <a name="stream-property"></a>Stream, propriété
Obtient ou définit un OLE DB **Stream** objet à partir de/sur un **ADOStreamConstruction** objet.  
  
 En lecture/écriture.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT get_Stream([out, retval] IUnknown** ppStream);  
HRESULT put_Stream([in] IUnknown* pStream);  
```  
  
## <a name="parameters"></a>Paramètres  
 *ppStream*  
 Pointeur vers un OLE DB **Stream** objet.  
  
 *pStream*  
 OLE DB **Stream** objet.  
  
## <a name="return-values"></a>Valeurs de retour  
 Cette méthode de propriété renvoie les valeurs HRESULT standard. Cela inclut S_OK et E_FAIL.  
  
## <a name="applies-to"></a>S'applique à  
 [ADOStreamConstruction, interface](../../../ado/reference/ado-api/adostreamconstruction-interface.md)
