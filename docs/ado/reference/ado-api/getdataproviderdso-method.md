---
description: GetDataProviderDSO, méthode
title: Méthode GetDataProviderDSO | Microsoft Docs
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 1a45d78960b8b6b1ba2534e39f080a6c94fc0655
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443571"
---
# <a name="getdataproviderdso-method"></a>GetDataProviderDSO, méthode
Récupère l’objet source de données OLE DB sous-jacent à partir du fournisseur Shape.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HRESULT GetDataProviderDSO(  
      IUnknown **ppDataProviderDSOIUnknown  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *ppDataProviderDSOIUnknown*  
 à  Pointeur vers un pointeur qui retourne l’IUnknown de l’objet OLE DB source de données sous-jacent.  
  
## <a name="remarks"></a>Notes  
 Cette méthode ne fait pas de AddRef avec le pointeur d’interface. Si l’appelant envisage de conserver le pointeur, l’appelant doit faire les AddRef et Release requis.  
  
## <a name="applies-to"></a>S’applique à  
 [IDSOShapeExtensions, interface](../../../ado/reference/ado-api/idsoshapeextensions-interface.md)
