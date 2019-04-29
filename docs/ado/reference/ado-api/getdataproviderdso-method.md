---
title: Getdataproviderdso, méthode | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- GetDataProviderDSO Method [ADO]
ms.assetid: 5a4c6bd5-0c79-4f81-a977-0561392d8d50
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0c7d864d61d2782955a52ce6e20a7025379cc946
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63028066"
---
# <a name="getdataproviderdso-method"></a>GetDataProviderDSO, méthode
Récupère l’objet de Source de données OLE DB sous-jacent à partir du fournisseur de forme.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HRESULT GetDataProviderDSO(  
      IUnknown **ppDataProviderDSOIUnknown  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *ppDataProviderDSOIUnknown*  
 [out]  Un pointeur vers un pointeur qui retourne l’IUnknown de l’objet de Source de données OLE DB sous-jacent.  
  
## <a name="remarks"></a>Notes  
 Cette méthode n’addref pas le pointeur d’interface. Si l’appelant souhaite maintenez le pointeur, l’appelant doit effectuer le requis addref et release.  
  
## <a name="applies-to"></a>S'applique à  
 [IDSOShapeExtensions, interface](../../../ado/reference/ado-api/idsoshapeextensions-interface.md)
