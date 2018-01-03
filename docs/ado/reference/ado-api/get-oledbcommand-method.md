---
title: "get_OLEDBCommand méthode | Documents Microsoft"
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
helpviewer_keywords: get_OLEDBCommand method [ADO]
ms.assetid: 23d551f5-3d5b-434b-ade6-fef15f1710e7
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bb9a2fc69b7919cc738c4050c410a167352d3801
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="getoledbcommand-method"></a>get_OLEDBCommand (méthode)
Retourne le sous-jacent commande OLE DB, tout d’abord propager les informations de paramètre défini sur la commande ADO à la commande OLE DB.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HRESULT get_OLEDBCommand(  
      IUnknown **ppOLEDBCommand  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *ppOLEDBCommand*  
 [out] Pointeur vers un emplacement du pointeur où le pointeur IUnknown pour la commande OLE DB sous-jacent sera écrit.  
  
## <a name="applies-to"></a>S'applique à  
 [IADOCommandConstruction](http://msdn.microsoft.com/en-us/d8e54333-00eb-4b72-bf4a-ca92c7ca5f86)
