---
description: get_OLEDBCommand, méthode
title: Méthode get_OLEDBCommand | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- get_OLEDBCommand method [ADO]
ms.assetid: 23d551f5-3d5b-434b-ade6-fef15f1710e7
author: rothja
ms.author: jroth
ms.openlocfilehash: 56148afcd3c7d3e18e856c6e50a44f35aaa1bc64
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88775128"
---
# <a name="get_oledbcommand-method"></a>get_OLEDBCommand, méthode
Retourne la commande de OLE DB sous-jacente, en propageant tout d’abord les informations sur les paramètres définis sur la commande ADO à la commande OLE DB.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HRESULT get_OLEDBCommand(  
      IUnknown **ppOLEDBCommand  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *ppOLEDBCommand*  
 à Pointeur vers un emplacement de pointeur où le pointeur IUnknown pour la commande de OLE DB sous-jacente sera écrit.  
  
## <a name="applies-to"></a>S'applique à  
 [IADOCommandConstruction](/previous-versions/windows/desktop/aa965677(v=vs.85))