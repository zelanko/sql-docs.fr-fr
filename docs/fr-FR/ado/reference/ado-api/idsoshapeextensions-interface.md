---
title: Interface de IDSOShapeExtensions | Documents Microsoft
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
- IDSOShapeExtensions interface [ADO]
ms.assetid: ad4ba313-1161-4bc7-b8f6-4083305bc81e
caps.latest.revision: 4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 86bf0db62ea607bf9957ed2566d7d223540090dd
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="idsoshapeextensions-interface"></a>Interface de IDSOShapeExtensions
Obtient l’objet sous-jacent de la Source de données OLE DB pour le fournisseur SHAPE.  
  
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
  
## <a name="requirements"></a>Spécifications  
 **Version :** ADO 2.0 et versions ultérieur  
  
 **Bibliothèque :** msado15.dll  
  
 **UUID :** 00000283-0000-0010-8000-00AA006D2EA4
