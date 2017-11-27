---
title: ConnectOptionEnum | Documents Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: ConnectOptionEnum
helpviewer_keywords: ConnectOptionEnum enumeration [ADO]
ms.assetid: bff07eeb-dee3-4e4e-9b2d-d56061ea744d
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 56f0ad9e79cdc7c570f805d76ec1ca68d7a77602
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="connectoptionenum"></a>ConnectOptionEnum
Spécifie si le [ouvrir](../../../ado/reference/ado-api/open-method-ado-connection.md) méthode d’un [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet doit retourner une fois établie la connexion (synchrone) ou avant (de façon asynchrone).  
  
|Constante|Valeur| Description|  
|--------------|-----------|-----------------|  
|**adAsyncConnect**|16|Ouvre la connexion de façon asynchrone. Le [ConnectComplete](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md) événement peut être utilisé pour déterminer quand la connexion est disponible.|  
|**adConnectUnspecified**|-1|Valeur par défaut. Ouvre la connexion de façon synchrone.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC équivalent  
 Package : **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.ConnectOption.ASYNCCONNECT|  
|AdoEnums.ConnectOption.CONNECTUNSPECIFIED|  
  
## <a name="applies-to"></a>S'applique à  
 [Open, méthode (objet Connection ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)
