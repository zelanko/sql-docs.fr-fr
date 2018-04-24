---
title: Méthode de GetDataProviderDSO | Documents Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- GetDataProviderDSO Method [ADO]
ms.assetid: 5a4c6bd5-0c79-4f81-a977-0561392d8d50
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fca773c6db137999da36daf0151a51a1becf79c6
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="getdataproviderdso-method"></a>GetDataProviderDSO (méthode)
Récupère l’objet de Source de données OLE DB sous-jacent à partir du fournisseur de forme.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HRESULT GetDataProviderDSO(  
      IUnknown **ppDataProviderDSOIUnknown  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *ppDataProviderDSOIUnknown*  
 [out]  Pointeur vers un pointeur qui retourne l’interface IUnknown de l’objet de Source de données OLE DB sous-jacent.  
  
## <a name="remarks"></a>Notes  
 Cette méthode n’effectue pas addref le pointeur d’interface. Si l’appelant veut maintenez le pointeur, l’appelant doit effectuer le requis addref et release.  
  
## <a name="applies-to"></a>S'applique à  
 [IDSOShapeExtensions, interface](../../../ado/reference/ado-api/idsoshapeextensions-interface.md)
