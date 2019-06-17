---
title: Idsoshapeextensions, Interface | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- IDSOShapeExtensions interface [ADO]
ms.assetid: ad4ba313-1161-4bc7-b8f6-4083305bc81e
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: e187cc35238440e67ce3f56343b103a9943f8f75
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66719226"
---
# <a name="idsoshapeextensions-interface"></a>IDSOShapeExtensions, interface
Obtient l’objet de Source de données OLE DB sous-jacent pour le fournisseur SHAPE.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
interface IDSOShapeExtensions: public IUnknown {  
public:  
      HRESULT  GetDataProviderDSO(  
            IUnknown **ppDataProviderDSOIUnknown  
      );  
};  
```  
  
## <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[GetDataProviderDSO, méthode](../../../ado/reference/ado-api/getdataproviderdso-method.md)|Récupère l’objet de Source de données OLE DB sous-jacent à partir du fournisseur de forme.|  
  
## <a name="requirements"></a>Configuration requise  
 **Version :** ADO 2.0 et versions ultérieur  
  
 **Bibliothèque :** msado15.dll  
  
 **UUID :** 00000283-0000-0010-8000-00AA006D2EA4
