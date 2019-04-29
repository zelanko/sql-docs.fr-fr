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
manager: craigg
ms.openlocfilehash: 36f91ea537b1ad2a5e52221400f41bf88dc544b0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63028036"
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
