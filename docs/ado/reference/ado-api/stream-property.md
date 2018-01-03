---
title: "La propriété du flux | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- ADOStreamConstruction::GetStream
- ADOStreamConstruction::PutStream
- ADOStreamConstruction::put_Stream
- ADOStreamConstruction::Stream
- ADOStreamConstruction::get_Stream
helpviewer_keywords: Stream property
ms.assetid: 4a44f9f6-0265-4c00-8def-d85b6af923b1
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d50f804682699b1e2a434ed26eae445f062927af
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="stream-property"></a>Propriété de flux de données
Obtient ou définit un OLE DB **flux** objet à partir de/sur un **ADOStreamConstruction** objet.  
  
 En lecture/écriture.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT get_Stream([out, retval] IUnknown** ppStream);  
HRESULT put_Stream([in] IUnknown* pStream);  
```  
  
## <a name="parameters"></a>Paramètres  
 *ppStream*  
 Pointeur vers un OLE DB **flux** objet.  
  
 *pStream*  
 OLE DB **flux** objet.  
  
## <a name="return-values"></a>Valeurs de retour  
 Cette méthode de propriété renvoie les valeurs HRESULT standards. Cela inclut le S_OK et E_FAIL.  
  
## <a name="applies-to"></a>S'applique à  
 [ADOStreamConstruction, interface](../../../ado/reference/ado-api/adostreamconstruction-interface.md)
