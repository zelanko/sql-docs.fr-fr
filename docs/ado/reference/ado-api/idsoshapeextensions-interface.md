---
title: Interface IDSOShapeExtensions | Microsoft Docs
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 7d49db4cb1d471d06b6e834e46218307bc25a008
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82758705"
---
# <a name="idsoshapeextensions-interface"></a>IDSOShapeExtensions, interface
Obtient l’objet source de données OLE DB sous-jacent pour le fournisseur de formes.  
  
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
|[GetDataProviderDSO, méthode](../../../ado/reference/ado-api/getdataproviderdso-method.md)|Récupère l’objet source de données OLE DB sous-jacent à partir du fournisseur Shape.|  
  
## <a name="requirements"></a>Configuration requise  
 **Version :** ADO 2,0 et versions ultérieures  
  
 **Bibliothèque :** msado15. dll  
  
 **UUID :** 00000283-0000-0010-8000-00AA006D2EA4
