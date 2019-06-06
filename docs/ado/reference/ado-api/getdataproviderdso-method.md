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
manager: jroth
ms.openlocfilehash: 5187e8f9fdce65b8e746a4a18a353462bb353d4f
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66698038"
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
